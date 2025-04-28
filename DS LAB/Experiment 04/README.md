# Experiment 4:

## Question:

- **I. Write a C program to convert infix expression to postfix expression using stack II. Write a C program to evaluate postfix expression.**

## I. Write a C program to convert infix expression to postfix expression using stack.

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

int main() {
    // char expression[] = "1+2*(3+4-5)*(4+2/6*3)-7";
    // char expression[] = "A+B*C+D";
    char expression[] = "((A+B)-C*(D/E))+F";
    printf("The infix expression is %s\n",expression);
    printf("The postfix expression is %s",infixToPostfix(expression));

    return 0;
}
```

## Output:

```md

```

## II. Write a C program to evaluate postfix expression.

## Program:

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <ctype.h>  // for isdigit()

// Function to perform arithmetic operations
int performOperation(int operand1, int operand2, char operator) {
    switch (operator) {
        case '+': return operand1 + operand2;
        case '-': return operand1 - operand2;
        case '*': return operand1 * operand2;
        case '/': return operand1 / operand2;
        case '%': return operand1 % operand2;
        default:  return -1; // Invalid operator
    }
}

// Function to check if a character is an operator
int isOperator(char c) {
    return c == '+' || c == '-' || c == '*' || c == '/' || c == '%';
}

// Function to evaluate a postfix expression
int evaluatePostfix(char *expression) {
    int top = -1;
    int length = strlen(expression);
    int *stack = (int *)malloc(sizeof(int) * length);

    if (stack == NULL) {
        printf("Memory allocation failed!\n");
        return -1;
    }

    for (int i = 0; expression[i] != '\0'; i++) {
        char token = expression[i];

        if (isdigit(token)) {
            stack[++top] = token - '0';  // Convert character digit to integer
        } else if (isOperator(token)) {
            int operand2 = stack[top--];
            int operand1 = stack[top--];
            stack[++top] = performOperation(operand1, operand2, token);
        }
    }

    int result = stack[top];
    free(stack);
    return result;
}

int main() {

    //char expression[] = "12*2/4+5-";   // Example: 1 * 2 / 2 + 4 - 5 = 0
    char expression[] = "234*+5+";   // Example: 2 + 3 * 4  + 5 = 19
    int result = evaluatePostfix(expression);
    printf("The result after evaluation is: %d\n", result);

    return 0;
}
```

## Output:

```md

```
