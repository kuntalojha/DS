# Experiment 5:

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
    int i,j=0 ; 
    char *m=(char*)malloc(sizeof(char)*n); 
    for (i = n-1; i >=0; i--) { 
        char temp = str[i]; 
        if (temp=='(') 
           m[j] = ')'; 
        else if(temp==')') 
           m[j] = '('; 
        else{ 
           m[j]= temp; 
        } 
    j++; 
} 
    m[n]='\0'; 
    return m; 
} 

int main() {
    // char expression[] = "A+B*C+D";
    // char expression[] = "((A+B)-C*(D/E))+F";
    char expression[] = "1+2*(3+4-5)*(4+2/6*3)-7";
    char *revexp,*postfix,*revpost;
    revexp=reverse(expression); 
    postfix=(infixToPostfix(revexp));
    revpost=(reverse(postfix));
    printf("Infix Expression: %s\n", expression);
    printf("Prefix Expression: %s\n", revpost);
    return 0;
}
```

## Output:

```md

``` 
