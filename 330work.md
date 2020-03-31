# 1.实现计算长方体体积的函数
`````````````````c
#include <stdio.h>

double cuboid (double length ,double width ,double height){
    
    double S，V;
    S=length*width;
    V=S*height;
    return V;
}
```````````````````
# 2.实现计算第n项斐波拉契数列的函数（n>=0)
````````````c
#include <stdio.h>

int fib (int n){
    if (n==0){
        return 0;
    }
    else if (n==1){
        return 1;
    }
    else {
        return fib(n-1) + fib(n-2)
    }

}
``````````````

#  3.实现计算三个数最大数值的函数 
``````````````c
#include <stdio.h>

int max (int a ,int b,int c){

    int temp=a;
    if(b>a){
        temp=b
    }
    if (temp>c){
        return temp;
    }
    else 
        return c;
}
`````````````````