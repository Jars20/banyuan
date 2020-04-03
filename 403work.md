# 1. 汉诺塔
``````````````````c

#include <stdio.h>

(void)hanio(int n,char A,char B,char c)
{
    if (n==1)
        printf("%c-->%c/n",A,B);
    else{
        hanio(n-1,A,C,B);
        printf("%c-->%c\n",A,B);
        hanio(n-1,C,B,A);
    }
    
}




``````````````````
