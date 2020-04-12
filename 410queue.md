# 分析用数组法表示queue的不足，提出改进办法

不足：数组法（顺序表）表示的Queue，在重复的入队和出队中，因为队尾与队头元素的下标越来越大，会产生即使队列长度不大但数组已经占用了极大内存的现象，造成内存溢出，我们称它为假溢出现象。

解决思路：循环队列。规定了数组的大小Maxsize，数据的入队和出队在下标为0～Maxsize-1的范围中循环，避免数据出队后还占据空闲顺序表位置。

# LinkQueue
```c
# include<stdio.h>
# include <stdlib.h>

typedef struct{
    int data;
    struct LinkNode *next;
} LinkNode;
typedef struct {
    LinkNode *front , *rear;
    int len;
} RecentCounter;

RecentCounter* recentCounterCreate() {
    RecentCounter *p =(RecentCounter*) malloc(sizeof(RecentCounter));
    p->front=p->rear=NULL;
    p->len =0;
    return p;
    
}

void EnQueue(RecentCounter *p,int elem){
    LinkNode *pnew_node =(LinkNode*)malloc(sizeof(LinkNode));
    pnew_node->data = elem;
    pnew_node->next = NULL;
    p ->rear->next = pnew_node;
    p ->rear =pnew_node;
    
}

int DeQueue(RecentCounter *p){
    if(p->front=p->rear){
        return -1;
    }
    LinkNode *temp=p->front->next;
    int r = temp->data;
    p->front->next=temp->next;
    if(p->rear=temp){
        p->rear=p->front;
    }
    free(temp);
    p->len--;
    return r;
}


int recentCounterPing(RecentCounter* obj, int t) {
  //判断recentcounter队列中有多少属于（t-3000，t）之间
  //用队列头部数值与t-3000判断，若front属于，则返回len+1；如果头部小于t-3000，则头部出队
    if(obj->front->data < (t-3000)){
        DeQueue(obj);
    }
    return len;
}

void recentCounterFree(RecentCounter* obj) {
    while (obj->len>0){
        DeQueue(obj);
    }
    free(obj);
    return obj ->len;
}

/**
 * Your RecentCounter struct will be instantiated and called as such:
 * RecentCounter* obj = recentCounterCreate();
 * int param_1 = recentCounterPing(obj, t);
 
 * recentCounterFree(obj);
*/
```
