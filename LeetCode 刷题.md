# LeetCode 刷题

一、数组

二、链表

三、栈

1. 【[LeetCode 150 - 逆波兰表达式求值](https://leetcode.cn/problems/evaluate-reverse-polish-notation/description/)】（**🌟**）：使用栈存储操作数，从左到右遍历逆波兰表达式，若遇到操作数，则将操作数进栈，若遇到运算符，则将两个操作数出栈，先出栈的为右操作数，后出栈的为左操作数，两个操作数进行运算后的结果压入栈。

   ```cpp
   bool isNumber(string token) {
     return !(token == "+" || token == "-" || token == "*" || token == "/");
   }
   
   class Solution {
    public:
     int evalRPN(vector<string>& tokens) {
       stack<int> stk;
       int size = tokens.size();
       for (decltype(tokens.size()) index = 0; index < size; ++index) {
         string token = tokens[index];
         /* 若当前字符为数字则将其转换为整型并压入栈中 */
         if (isNumber(token)) {
           stk.push(stoi(token));
         } else {
           int right = stk.top();
           stk.pop();
           int left = stk.top();
           stk.pop();
           /* 字符串的首字符为 char 类型，因此使用单引号 */
           switch (token[0]) {
             case '+':
               stk.push(left + right);
               break;
             case '-':
               stk.push(left - right);
               break;
             case '*':
               stk.push(left * right);
               break;
             case '/':
               stk.push(left / right);
               break;
           }
         }
       }
       /* 结果在栈顶 */
       return stk.top();
     }
   };
   
   ```

   

