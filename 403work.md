# 1. 汉诺塔
``````````````````c

#include <stdio.h>


void hanio(int n,char A,char B,char C)
{
    if (n==1)
        printf("%c-->%c\n",A,B);
    else{
        hanio(n-1,A,C,B);
        printf("%c-->%c\n",A,B);
        hanio(n-1,C,B,A);
    }
}
int main(int i){
    char A='A',B='B',C='C';
    int n;
    printf("请输入汉诺塔的高度");
    scanf("%d",&n);
    hanio(n,A,B,C);
}







``````````````````
