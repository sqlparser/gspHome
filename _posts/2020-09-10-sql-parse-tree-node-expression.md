---
layout: page
title: "SQL parse tree node and expression modification"
excerpt: "A general review/summary of General SQL Parser: sql parser tree node and expression modification"
permalink: gsp-sql-parse-tree-node-and-expression-modification-cn.html
categories:
  - get-started-cn
  - sql-syntax
---

通过 setLeftOperand(null) 来删除该表达式的左节点， 通过 setRightOperand(null) 来删除该表达式的右节点。

```sql
columnA*2
```

通过以下代码，
```java
TExpression parent  = columnAExpr.getParentExpr();
if (columnAExpr == parent.getLeftOperand()){
    parent.setLeftOperand(null);
}else if (columnAExpr == parent.getRightOperand()){
    parent.setRightOperand(null);
}
```
表达式将变为
```sql
2
```

### setLeftOperand(null) 的工作原理

```java
public void setLeftOperand(TExpression leftOperand) {
    if (leftOperand == null){
        TParseTreeNode.removeTokensBetweenNodes(this.leftOperand,this.rightOperand);
    }

    this.setNewSubNode(this.leftOperand,leftOperand,null);
    this.leftOperand = leftOperand;
    if (leftOperand != null){
        leftOperand.setParentExpr(this);
    }
}
```

1. 移除 left and right node 间的操作符，在上例中为 `*`
2. 调用 TParseTreeNode.setNewSubNode() 来移除原有 node。

```java
public void setNewSubNode( TParseTreeNode oldSubNode, TParseTreeNode newSubNode,TParseTreeNode anchorNode){
  if (newSubNode == null){
      //remove the old node
      if (oldSubNode != null){
          oldSubNode.removeTokens();
      }
  }else {
      if (oldSubNode == null){
          // add a total new where clause, we need to find an anchor
          if (newSubNode.getNodeStatus()!=ENodeStatus.nsNormal){
              doAppendNewNode(newSubNode,anchorNode,false);
          }

      }else{
          //replace old where clause
          if (newSubNode.getNodeStatus()!=ENodeStatus.nsNormal){
              oldSubNode.replaceWithNewNode(newSubNode);
          }
      }
  }
}
```

### 利用 TParseTreeNodeList.removeItem(int index) 来移除 expression list 中的 expresssion

```sql
(1,2,3,4)
```

调用
```java
expressionList.removeItem(0);
```
结果为：
```sql
(2,3,4)
```

### 其它类型 Expression 的操作
利用 TParseTreeNode 和 TSourceToken 的下列基本方法，我们可以实现对其它类型 Expression 的改动并调用 toString() 输出改动后的文本结果。
```java
//  TParseTreeNode:

public TSourceToken getStartToken()
public TSourceToken getEndToken()
public void setStartToken(TSourceToken newStartToken)
public void setEndToken(TSourceToken newEndToken) 

public void removeTokens() // 从链表中移除该 node 对应的所有 token， 并确保 node 和 startToken, endToken状态的准确
public void appendNewNode(TParseTreeNode newNode, boolean needCommaBefore)
public void replaceWithNewNode(TParseTreeNode newNode)
public void setText(String nodeText)

public void setNewSubNode( TParseTreeNode oldSubNode, TParseTreeNode newSubNode,TParseTreeNode anchorNode)

public void setAnchorNode(TParseTreeNode anchorNode)

public static void removeTokensBetweenNodes(TParseTreeNode startNode, TParseTreeNode endNode)

public ENodeStatus getNodeStatus()
```

```java
// TSourceToken:

public Stack<TParseTreeNode> getNodesStartFromThisToken()
public Stack<TParseTreeNode> getNodesEndWithThisToken()

// 双向链表中， 通过以下方法把 token 加入链表，或从链表中移除。
public TSourceToken getNextTokenInChain()
public void setNextTokenInChain(TSourceToken nextTokenInChain)
public TSourceToken getPrevTokenInChain()
public void setPrevTokenInChain(TSourceToken prevTokenInChain)

public void removeFromChain()
```


### 参考代码
[testExpression](https://github.com/sqlparser/gsp_demo_java/blob/master/src/test/java/common/testExpression.java)
中的 
1. public void testRemove1()
2. public void testRemoveExprList()
