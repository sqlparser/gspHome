User should be careful When use acceptChildren() method in the `public void preVisit(TExpression node) ` or `public void postVisit(TExpression node) ` method of  your customzied visitor class that extends TParseTreeVisitor.

```csharp
class TreeVisitor extends TParseTreeVisitor {

    public void preVisit(TExpression node) {
        switch (node.getExpressionType()) {
                case logical_and_t:
                case logical_or_t:
                        node.getLeftOperand().acceptChildren(this);
                        node.getRightOperand().acceptChildren(this);
                    break;
                default:
                    break;        
        }
    }
```

The above code will cause the left and right sub-expression repeatedly visited, if the expression itself is deeply nested, then the performance will be impacted severly.

Since the `acceptChildren()` method of `TExpression` will iterate all sub-expression for you automatically, you **shouldn't** call `acceptChildren()` in the `preVisit()` method of your own visitor. Only add your business code in the `preVisit()` method and let the `acceptChildren()` method of `TExpression` do the iteration for you.

Below is the code of the `acceptChildren()` method of `TExpression` for your reference.

```csharp
    public void acceptChildren(TParseTreeVisitor v){
        v.preVisit(this);
        switch(expressionType){
            case simple_object_name_t:
                objectOperand.acceptChildren(v);
                break;
            case list_t:
            case collection_constructor_list_t:
            case collection_constructor_multiset_t:
            case collection_constructor_set_t:
                if (exprList != null){
                    for(int i=0;i<exprList.size();i++){
                        exprList.getExpression(i).acceptChildren(v);
                    }
                }
                break;
            case function_t:
            case new_structured_type_t:
            case type_constructor_t:
                functionCall.acceptChildren(v);
                break;
            case cursor_t:
            case subquery_t:
            case multiset_t:
                subQuery.acceptChildren(v);
                break;
            case case_t:
                caseExpression.acceptChildren(v);
                break;
            case pattern_matching_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                if (likeEscapeOperand != null){
                    likeEscapeOperand.acceptChildren(v);
                }
                break;
            case exists_t:
                subQuery.acceptChildren(v);
                break;
            case new_variant_type_t:
                newVariantTypeArgumentList.acceptChildren(v);
                break;
            case unary_plus_t:
            case unary_minus_t:
            case unary_prior_t:
                rightOperand.acceptChildren(v);
                break;
            case arithmetic_plus_t:
            case arithmetic_minus_t:
            case arithmetic_times_t:
            case arithmetic_divide_t:
            case power_t:
            case range_t:
            case concatenate_t:
            case period_ldiff_t:
            case period_rdiff_t:
            case period_p_intersect_t:
            case period_p_normalize_t:
            case contains_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case assignment_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case sqlserver_proprietary_column_alias_t:
                rightOperand.acceptChildren(v);
                break;
            case arithmetic_modulo_t:
            case bitwise_exclusive_or_t:
            case bitwise_or_t:
            case bitwise_and_t:
            case bitwise_xor_t:
            case exponentiate_t:
            case scope_resolution_t:
            case at_time_zone_t:
            case member_of_t:
            case arithmetic_exponentiation_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case at_local_t:
            case day_to_second_t:
            case year_to_month_t:
                leftOperand.acceptChildren(v);
                break;
            case parenthesis_t:
                leftOperand.acceptChildren(v);
                break;
            case simple_comparison_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case group_comparison_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case in_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case floating_point_t:
                leftOperand.acceptChildren(v);
                break;
            case logical_and_t:
            case logical_or_t:
            case logical_xor_t:
            case is_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case logical_not_t:
                rightOperand.acceptChildren(v);
                break;
            case null_t:
                leftOperand.acceptChildren(v);
                break;
            case between_t:
                if (betweenOperand != null){
                    betweenOperand.acceptChildren(v);
                }
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case is_of_type_t:
                leftOperand.acceptChildren(v);
                break;
            case collate_t: //sql server,postgresql
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case left_join_t:
            case right_join_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case ref_arrow_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case typecast_t:
                leftOperand.acceptChildren(v);
                break;
            case arrayaccess_t:
                arrayAccess.acceptChildren(v);
                break;
            case unary_connect_by_root_t:
                rightOperand.acceptChildren(v);
                break;
            case interval_t:
                intervalExpr.acceptChildren(v);
                break;
            case unary_binary_operator_t:
                rightOperand.acceptChildren(v);
                break;
            case left_shift_t:
            case right_shift_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case array_constructor_t:
                if (subQuery != null){
                    subQuery.acceptChildren(v);
                }else if (exprList != null){
                    exprList.acceptChildren(v);
                }else if (arrayConstruct != null){
                    arrayConstruct.acceptChildren(v);
                }
                break;
            case row_constructor_t:
                if (exprList != null){
                    exprList.acceptChildren(v);
                }
                break;
            case unary_squareroot_t:
            case unary_cuberoot_t:
            case unary_factorialprefix_t:
            case unary_absolutevalue_t:
            case unary_bitwise_not_t:
                getRightOperand().acceptChildren(v);
                break;
            case unary_factorial_t:
                getLeftOperand().acceptChildren(v);
                break;
            case bitwise_shift_left_t:
            case bitwise_shift_right_t:
                getLeftOperand().acceptChildren(v);
                getRightOperand().acceptChildren(v);
                break;
            case multiset_union_t:
            case multiset_union_distinct_t:
            case multiset_intersect_t:
            case multiset_intersect_distinct_t:
            case multiset_except_t:
            case multiset_except_distinct_t:
                getLeftOperand().acceptChildren(v);
                getRightOperand().acceptChildren(v);
                break;
            case json_get_text:
            case json_get_text_at_path:
            case json_get_object:
            case json_get_object_at_path:
            case json_left_contain:
            case json_right_contain:
            case json_exist:
            case json_any_exist:
            case json_all_exist:
                getLeftOperand().acceptChildren(v);
                getRightOperand().acceptChildren(v);
                break;
            case interpolate_previous_value_t:
                getLeftOperand().acceptChildren(v);
                getRightOperand().acceptChildren(v);
                break;
            case submultiset_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case overlaps_t:
                leftOperand.acceptChildren(v);
                rightOperand.acceptChildren(v);
                break;
            case is_a_set_t:
                leftOperand.acceptChildren(v);
                break;
            case array_t:
                if (getExprList() != null){
                    getExprList().acceptChildren(v);
                }
                break;
            default:;
        }

        v.postVisit(this);
    }

```