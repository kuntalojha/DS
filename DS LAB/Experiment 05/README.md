# Experiment 4:

## Question:

- **Write a C program to convert infix expression to prefix expression using stack**

## Program:

```c
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>

// Function to return precedence of operators
int prec(char c) {
    if (c == '^')
        return 3;
    else if (c == '/' || c == '*')
        return 2;
    else if (c == '+' || c == '-')
        return 1;
    else
        return -1;
}

// Function to perform infix to postfix conversion
char * infixToPostfix(char * exp)
{
    int j = 0,i = 0;
    int top = -1;//Indicates the stack is empty
    int len = strlen(exp);
    char *result=(char*)malloc(sizeof(char)*len);//To store Postfix expression
    char *stack=(char *)malloc(sizeof(char)*len);
    while(exp[i] != '\0')
    {
        char c = exp[i];
        if (isalnum(c))                //Checking whether the character is alphanumeric
            result[j++] = c;
        else if (c == '(')             //checking whether the character is '('
            stack[++top] = '(';
        else if (c == ')') {           //checking whether the character is ')'
            while (top != -1 && stack[top] != '(') {
                result[j++] = stack[top--];
            }
            top--;
        }
        else {
            while (top != -1 && (prec(c) < prec(stack[top]) ||      //if the character is operator
                                 prec(c) == prec(stack[top]))) {
                result[j++] = stack[top--];
            }
            stack[++top] = c;
        }i++;
    }

    // Pop all the remaining elements from the stack and store it in the result
    while (top != -1) {
        result[j++] = stack[top--];
    }
    result[j] = '\0';
    return result;

}

char * reverse(char *str) {
    int n = strlen(str);
    int i ;
    for (i = 0; i < n/2; i++) {
        char temp = str[i];
        str[i] = str[n-i-1];
        str[n-i-1] = temp;
    }
    return str;
}

int main() {
    // char expression[] = "A+B*C+D";
    //char expression[] = "((A+B)-C*(D/E))+F";
     char expression[] = "1+2*(3+4-5)*(4+2/6*3)-7";
    printf("The infix expression is %s\n",expression);
    // printf("The postfix expression is %s",infixToPostfix(expression));

    char *postfix = infixToPostfix(expression);
    // printf("The postfix expression is %s\n",postfix);

    char *prefix = reverse(postfix);
    printf("The prefix expression is %s\n",prefix);
    return 0;
}
```

## Output:

```md

```
