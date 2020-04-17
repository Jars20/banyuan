# 1.bit运算
### 新生报道有1000人, 按每个班最多32个人进行划分,应该如何用bit运算得出最少需要多少个班?
## 答：

(需要的班数最少的情况，即此时每个班全是32人，最多有一个班人数未满，此时班级数为（1000/32）+1，即求该式的bit运算)

将1000转化为2进制数，为（0011 1110 1000）

32等于2的5次方，1000/32可以通过右移5位(>>5)来得到结果为（0000 0001 1111），即有31个班坐满。

（0000 0001 1111）加（0000 0000 0001）得（0000 0010 0000），转化为十进制数为32

# 2.使用直线划分空间
## 问题:

### 写出公式L(n); n表示直线数量, L(n)表示通过n根直线可以划分出的最多的空间数量

## 使用C语言实现计算L(n)的函数:
```c
 int calc_spaces(int n); // n >= 0
 ```
## 答：
```c
int calc_spaces(int n){
    int k=1;
    int i;
    for (i=n;i>0;i--){
        k=k+i;
    }
    return k;
}
```

# 3. 打印三角形
### 观察上图三角形的规律,实现函数根据输入n打印n行如图所示三角形:
```c
void draw(unsigned int n); // n > 0
```
## 答：
```c
void draw(unsigned int n){
    int i,j,k;
    int a[n][n];
    a[0][0]=1;
    for (i=1;i<n;i++){
        a[i][0]=i+1;
        for(j=0;j<=i;j++){
            if(j==0)
                a[i][j]=a[i][0];
            else if(i>=1&&j>=1&&j!=i){
                a[i][j] = a[i-1][j-1]+a[i-1][j];
            }
            else if(j==i)
                a[i][j]=i+1;
        }
    }
    for (i=0;i<n;i++){
        for (k=1; k<n-i;k++){
                   printf("  ");
                 }
        for (j=0; j<=i; j++) {
            printf("%4d",a[i][j]);
        }
        printf("\n");
    }
}

```
# 4.实现atof函数
## 函数定义
```c
double my_atof(char *nptr);
```
## 函数描述

### my_atof() 会扫描参数nptr字符串，跳过前面的空格字符，直到遇上数字或 . 符号才开始做转换，而再遇到非数字或字符串结束时('\0')才结束转换，并将结果返回。

## 答：
```c
double my_atof(char *nptr){
    double s = 0.0;
    double d = 10.0;
    while(*nptr==' '){
        nptr++;
    }
    while (*nptr>'0'&&*nptr<'9'&&*nptr!='.') {
        s = s*10.0 + *nptr-'0';
        nptr++;
    }
    if (*nptr=='.'){
        nptr++;
        while (*nptr>'0'&&*nptr<'9') {
            s = s + (*nptr - '0')/d;
            d = d * 10.0;
            nptr++;
        }
    }
    
    return s;
}
```


# 5.使用栈的数据结构实现队列的功能
### 函数声明如下:
```c

enqueue(Queue* queue, int data); // 函数类型请自己考虑
int dequeue(Queue* queue);
```
### Queue 的定义在stack.h文件中


### 上面的两个函数里面只能调用已有的函数,不能使用其他方法对入参queue进行操作

测试用例如下:
```c
int main(void) {
    Queue* queue = init_stack();
    int a[5] = {1, 2, 3, 4, 5};
    for( int i = 0; i < 5; i++) {
	enqueue(queue, a[i]);
    }

    for (int i = 0; i < 5; i++) {
	int out = dequeue(queue);
	printf("%3d", out);
    }
    printf("\n");
    return 0;
}
```
## 答：
```c
Queue *enqueue(Queue* queue, int data){
    push(queue, data);
    return queue;
}

int dequeue(Queue* queue){
    Queue *pre = queue;
    Queue *pos = pre->next;
    if(pos==NULL){
        printf("队列已空\n");
        return -1;
    }
    while(pos!=NULL&&pos->next!=NULL){
        pre=pos;
        pos=pos->next;
    }
    int i = pop(pre);
    return i;
}


```

