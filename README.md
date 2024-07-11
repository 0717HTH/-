# -
有效括号字符串为空 ""、"(" + A + ")" 或 A + B ，其中 A 和 B 都是有效的括号字符串，+ 代表字符串的连接。  例如，""，"()"，"(())()" 和 "(()(()))" 都是有效的括号字符串。 如果有效字符串 s 非空，且不存在将其拆分为 s = A + B 的方法，我们称其为原语（primitive），其中 A 和 B 都是非空有效括号字符串。  给出一个非空有效字符串 s，考虑将其进行原语化分解，使得：s = P_1 + P_2 + ... + P_k，其中 P_i 是有效括号字符串原语。  对 s 进行原语化分解，删除分解中每个原语字符串的最外层括号，返回 s 。   
代码如下
char* removeOuterParentheses(char* s) {
    int count=0;//用count来计数
    int top=-1;//栈顶指针
    char* Stack=(char*)malloc((strlen(s)+1)*sizeof(char));//通过malloc函数创建一栈
    for(int i=0;i<strlen(s);i++){//遍历
        if(s[i]=='('){//第一个（不入栈，其余的（入栈
            if(count!=0){
            Stack[++top]=s[i];
            }
            count++;//注意！：count++必须放在后面，不然第一个左括号会入栈
        }
        if(s[i]==')'){//最后外层最后一个）不入栈，其余）入栈
            count--;
            if(count!=0){
                Stack[++top]=s[i];
            }
        }
    }
    Stack[++top]='\0';//最后让栈最后一个元素为、0，否则会报错
    return Stack;//返回栈
}
