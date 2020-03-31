#  1.将输入的小写字母转成大写字母，大写字母转成小写字母，其他符号不变
````````````````c
#include <stdio.h>

int main ()
{
    char c;
    while ((c=getchar())!=EOF){
        if (c>'A'&&c<'Z'){
            c+='a'-'A';
        }
         if (c>'a'&&c<'z'){
            c-='a'-'A';
         }        
        printf("%c",c);
    }
    printf("\n");
    return 0;
}
````````````````

# 2.数组中查找值
```````````````c

#include <stdio.h>
/*
 从a数组里面查找x这个元素，如果找到则返回x对应的位置，如果找不到则返回-1
 */
int search(int a[ ], int n, int x);

int main ()
{
    int b[] = {10, 8, 6, 3, 12};
    
    int result = search(b, sizeof(b), 3);
    
    printf("result is %d", result);
    printf("\n");
}

int search(int a[ ], int n, int x){
    int i;
    for(i=0;i<n;i++){
        if (a[i]=x){
            return i;
        }
    }
    return -1;
}
```````````````

# 3.数组中查找最小值
```````````````c
#include <stdio.h>
/*
 从a里面找最小元素，返回它的下标
 */
int min(int a[], int n);

int main ()
{
    int b[] = {10, 8, 6, 4, 5, 3, 3};
    
    int result = min(b, sizeof(b)/sizeof(b[0]));
    
    printf("result is %d", result);
    printf("\n");
}

int min (int a[],int n){
    int k=0;
    int min=a[k];
    for(int i=0;i<n;++i){
        if(a[i]<min){
            min=a[i];
            k=i;
        }
    }
    return k;
}



```````````````

# 3.统计100个随机数的分布，照纵向分布打印出来



``````````````c
#include <stdio.h>
#include <time.h>
#include <stdlib.h>


int main ()
{
    // 生成100个随机数的数组, 分布到0-100
    srand((unsigned int)time(NULL));
    int a[100];
    int num[11]={0};
    for (int i = 0; i < 100; i++) {
        a[i] = rand() % 101;
        num [a[i]/10]++;
    }
    printf("\n ------分布图------\n");
    for (int j = 0; j <11 ; j++){
        printf ("%3d  ",j*10);

        for (int i=0;i <num [j];i++){
            printf ("* ");
        }
        printf("\n");
    }
    
}

//纵向可能实现思路：二维数组？
`````````````````