```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

typedef struct TreeNode {
    int data;
    struct TreeNode *lchild, *rchild;
} TreeNode,*Tree;

typedef struct QNode{
    int data;
    struct QNode *next;
    
}QNode,*Queue;

QNode *initHeadNode() {
    QNode *node = (QNode *)malloc(sizeof(QNode));
    node->next = NULL;
    return node;
}

void EnQueue(Queue *pQ , int data) {
    Queue Q=*pQ;
    QNode *node = (QNode *)malloc(sizeof(QNode));
    node->data = data;
    node->next = NULL;
    while(Q){
        Q=Q->next;
    }
    Q=node;
    *pQ=Q;
    return ;
}

void DeQueue(Queue *p) {
    Queue top = *p;
    QNode* out =top;
    printf("%d", out->data);
    top->next =out->next;
    free(out);
    *p = top;

}



int insertnode(Tree *pT,int val){
    Tree T= *pT;                                                //pt为main（）中tree的地址，指向指针（Tree）tree
    if(T==NULL){
        T =(Tree)malloc(sizeof(TreeNode));
        T->data=val;
        T->lchild=NULL;
        T->rchild=NULL;
        *pT=T;                                                  //别忘了把形参的变化赋值给实参
        return 1;
    }
    else if(val > T->data){
        return insertnode(&T->rchild,val);
    }
    else if(val < T->data){
        return insertnode(&T->lchild,val);
    }
    else{
        printf("error input");
        return 0;
    }
    
}
/*        层次遍历（有问题）
void LevelOreder(Tree p){
    Queue Q;
    Q=initHeadNode();
    EnQueue(&Q, p->data);
    int sum =1;
    while(Q!=NULL){
        int temp=0;
        while(sum>0){
            DeQueue(&Q);
            if(p->lchild!=NULL){
                EnQueue(&Q, p->lchild->data);
                temp++;
            }
            if(p->rchild!=NULL){
                EnQueue(&Q, p->rchild->data);
                temp++;
            }
            sum--;
            
        }
        sum = temp;
        printf("\n");
        
    }
    
}
*/


 /*             中序遍历并且打印
  
  void InOrder(TreeNode * p){
    if (p->lchild)
        InOrder(p->lchild);
     
    printf("%d",p->data);
     
    if (p->rchild)
        InOrder(p->rchild);
    return;
}
  */

int main() {
    Tree tree=NULL;
    int i=0;
    int a[]={1,2,3,4,5};
    while(i<5){
        insertnode(&tree,a[i]);
        i++;
    }
    printf("after insert\n");
    //LevelOreder(tree);
  /*  InOrder(tree);*/
    printf("\n");
    return 1;

}
```