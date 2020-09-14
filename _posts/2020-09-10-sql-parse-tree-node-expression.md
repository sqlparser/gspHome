---
layout: page
title: "SQL parse tree node and expression modification"
excerpt: "A general review/summary of General SQL Parser: sql parser tree node and expression modification"
permalink: gsp-sql-parse-tree-node-and-expression-modification-cn.html
categories:
  - get-started-cn
  - sql-syntax
---

表达式的修改及结果。

### 删除表达式的子节点

```sql
d.cntrb_date1 >= '$From_Date$'
```
After remove d.cntrb_date1, the remain expression will be 
```sql
'$From_Date$'
```

通过以下代码实现上面的删除功能：
```java
expression.setLeftOperand(null);
assertTrue(expression.toString().equalsIgnoreCase("'$From_Date$'"));
```

####  API
setLeftOperand(null) 删除该表达式的左节点， setRightOperand(null) 删除该表达式的右节点。

#### 相关属性的变化
如果一个节点被删除， 那么该节点的属性：
1. getNodeStatus() 为 ENodeStatus.nsRemoved
2. getStartToken(), getEndToken() 返回 null
3. toString(), 返回 null

判断一个节点是否被删除， 用 getNodeStatus() == ENodeStatus.nsRemoved

如果一个表达式的 left operann and right operand 都被删除， 那么该表达式的状态也处于被删除。
以上属性同样满足。

#### 利用 TParseTreeNodeList.removeItem(int index) 来移除 expression list 中的 expresssion

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


### 更改表达式
```sql
d.cntrb_date1 >= '$From_Date$'
```
After set '$From_Date$' to 1 , the expression will be 
```sql
d.cntrb_date1 >= 1
```

通过以下代码实现上面的更改功能：
```java
expression.getRightOperand().setString("1");
assertTrue(expression.toString().equalsIgnoreCase("d.cntrb_date1 >= 1"));
```

### 增加表达式
增加表达式一般通过修改原有表达式来实现，例如：
```sql
d.cntrb_date1 >= '$From_Date$'
```
想变为：
```sql
d.cntrb_date1 >= '$From_Date$' + 1
```


通过以下代码实现上面的更改功能：
```java
expression.getRightOperand().setString(expression.getRightOperand().toString()+" + 1");
assertTrue(expression.toString().equalsIgnoreCase("d.cntrb_date1 >= '$From_Date$' + 1"));
```



### setLeftOperand(null) 的工作原理

```java
public void setLeftOperand(TExpression leftOperand) {
	if (leftOperand == null){
		TParseTreeNode.removeTokensBetweenNodes(this.leftOperand,this.rightOperand);
	}

	this.setNewSubNode(this.leftOperand,leftOperand,null);
	this.leftOperand = leftOperand;
	if (this.getNodeStatus() == ENodeStatus.nsRemoved){
		// remove this expr cascade due to the left operand was removed
		if (this.getParentExpr() != null){
			if (this == this.getParentExpr().getLeftOperand()){
				if ((this.getParentExpr().getRightOperand() != null)&&(this.getParentExpr().getRightOperand().getNodeStatus() != ENodeStatus.nsRemoved)){
					this.getParentExpr().refreshAllNodesTokenCount();
					this.getParentExpr().removeTokensBetweenToken(this.getParentExpr().getStartToken(),this.getParentExpr().getRightOperand().getStartToken().getPrevTokenInChain());
					this.getParentExpr().updateNodeWithTheSameStartToken(TParseTreeNode.nodeChangeStartToken ,this.getParentExpr().getRightOperand().getStartToken());
				}
			}else{
				if ((this.getParentExpr().getLeftOperand() != null)&&(this.getParentExpr().getLeftOperand().getNodeStatus() != ENodeStatus.nsRemoved)){
					this.getParentExpr().refreshAllNodesTokenCount();
					this.getParentExpr().removeTokensBetweenToken(this.getParentExpr().getLeftOperand().getEndToken().getNextTokenInChain(),this.getParentExpr().getEndToken());
					this.getParentExpr().updateMeNodeWithTheSameEndToken(TParseTreeNode.nodeChangeEndToken ,this.getParentExpr().getLeftOperand().getEndToken());
				}
			}
		}
		this.setStartTokenDirectly(null);
		this.setEndTokenDirectly(null);
	}
	if (leftOperand != null){
		leftOperand.setParentExpr(this);
	}
}
```

1. 移除 left and right node 间的操作符，在上例中为 `*`
2. 调用 TParseTreeNode.setNewSubNode() 来移除原有 node
3. 如果移除 left or right operand 后， 导致整个 expression 处于被移除状态， 在父表达式中删除自己




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

[testModifyExpr](https://github.com/sqlparser/gsp_demo_java/blob/master/src/test/java/common/testModifyExpr.java)
