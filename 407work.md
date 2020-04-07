# 顺序表增加元素扩容内存和删除元素
```````````````````````c
#include <stdio.h>
#include <stdlib.h>
#define SIZE 5
#define ADDNUM 9
#define ADDPOS 0
#define DELPOS 0
#define SEARCHNUM 4
#define MODIFYNUM 27

typedef struct {
    int *head;       //顺序表指针变量
    int length;      //记录当前顺序表的长度
    int capacity;    //记录顺序表分配的存储容量

} SeqList;

/*初始化顺序表*/
SeqList initSeqList() {
    SeqList list;
    list.head = (int *)malloc(SIZE * sizeof(int));

    if (!list.head) {
        printf("初始化失败！\n");
        exit(0);
    }

    list.length = 0;
    list.capacity = SIZE;
    return list;
}

/*显示顺序表*/
void displayList(SeqList list) {
    for (int i = 0; i < list.length; i++) {
        printf("%d  ", list.head[i]);
    }

    printf("\n");
}

/*增*/
SeqList add(SeqList list, int elem, int pos) {
    //插入位置判断，取值范围为0～length
    if (pos > list.length  || pos < 0) {
        printf("插入位置有误\n");
        return list;
    }

    //重新分配内存
    if (list.length == list.capacity) {
        int *temp = (int *)realloc(list.head, (list.capacity <<=1) * sizeof(int));

        if (!temp) {
            printf("内存分配失败！\n");
            return list;
        }

        list.head = temp;
        list.capacity <<= 1;
    }

    //插入位置及以后的元素依次后移一位
    for (int i = list.length - 1; i >= pos ; i--) {
        list.head[i + 1] = list.head[i];
    }

    list.head[pos] = elem;//元素插入空出的位置

    list.length++;//表长度+1
    return list;
}

/*删*/
SeqList delete(SeqList list , int pos) {
    //删除位置判断，取值范围为0～length-1
    if (pos >= list.length || pos < 0) {
        printf("删除位置有误\n");
        return list;
    }

    //将删除位置后续元素依次前移
    for (int i = pos ; i < list.length - 1 ; i++) {
        list.head[i] = list.head[i + 1];
    }
    free (list.head[list.length]);  //释放最后一位
    list.length--;//表长度-1

    return list;
}

int main(void) {
    SeqList list = initSeqList();

    for (int i = 0; i < SIZE; i++) {
        list.head[i] = i + 1;
        list.length++;
    }

    printf("顺序表中存储的元素分别是：\n");
    displayList(list);

    printf("在顺序表的第%d个位置插入元素：%d\n", ADDPOS, ADDNUM);
    list = add(list, ADDNUM, ADDPOS);
    displayList(list);

    printf("删除第%d个元素\n", DELPOS);
    list = delete(list, DELPOS);
    displayList(list);


    
    printf("内存空间为%d  数组长度为%d\n", list.capacity, list.length);

    free(list.head);
    list.head = NULL;

    return 0;
}
````````````````````````````
# 链表的插入与删除
```````````````````````c
void add(Node* head,int pos,Node* new ){
    Node* tail=head ->next;
    if (pos < 0||pos > head->elem){
        printf("无效的插入位置");
    }
    for (int i=0;i<pos;i++){
        tail=tail->next;
        }
    tail ->next =new;
    return;
}

void delete(Node* head,int pos){
    Node *pre =head;
    Node *q;
    if (pos < 0||pos > head->elem){
        printf("无效的删除位置");
    }
    for (int i=0;i<pos;i++){
        pre = pre -> next;
    }
    q=pre ->next;
    pre ->next =q->next;
    free(q);
    return;
}
``````````````````````````