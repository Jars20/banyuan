# 双向链表的增删

## 双向链表的创建
````````````````c
Node *initNode(Node *pre, int elem){
    Node *node = (Node *)malloc (sizeof(Node));
    Node ->pre = NULL;
    Node ->next = NULL;
    Node ->elem =elem;
    //与前节点相连
    Node ->pre = pre;
    pre -> next = Node;

    return Node;
}
````````````````
## 遍历至指定位置
```````````````c
Node *getPreNode(Node *head, int pos, int min , int max) {
    if (pos > max   || pos < min) {
        printf("位置有误\n");
        return NULL;
    }

    Node *temp = head;

    for (int i = 0; i < pos; i++) {
        temp = temp->next;
    }

    return temp;
}
```````````````
## 增
```````````````c
void add(Node *head, int elem, int pos) {
    Node *pre = getPreNode(head, pos, 0, length);

    if (pre == NULL) {
        return;
    }

    Node *next = pre->next;//需要插入位置的后结点

    //创建一个新结点
    Node *add = (Node *)malloc(sizeof(Node));
    add->elem = elem;

    //和前结点建立双层逻辑
    add->pre = pre;
    pre->next = add;

    if (next != NULL) {
        //和后结点建立双层逻辑
        add->next = next;
        next->pre = add;
    } else {
        add->next = NULL;
    }

    length ++;//表长度+1
}
```````````````

## 删
``````````````c
void delete(Node *head, int pos) {
    Node *pre = getPreNode(head, pos, 0, length - 1);

    if (pre == NULL) {
        return;
    }

    Node *del = pre->next;//需要删除的结点
    Node *next = del->next;//需要删除结点的后结点

    pre->next = next;//将前结点的next指针指向后结点

    if (next != NULL) {
        next->pre = pre;    //将后结点的pre指针指向前结点
    }

    free(del);//释放删除结点空间
    del = NULL;
    length --;//表长度-1
}
```````````````

# 约瑟夫环问题
```````````````c
// 1. init SeqList
    CircleLinkedNode* head = init_circle_linked_list();

    for (int i = 0; i < n; i++) {
        add_circle_linked_list(head, n-i, 0);
    }
    display_circle_linked_list(head);

    // 2. 循环计数，遇到m则将这个元素删除
    CircleLinkedNode* curr_pos = head->next; // 当前位置
    while(head->next) {
        // 计数到m则将当前元素删除 
        int count = 0;
        while(1) {
            count++;
            if (count == m) {
                break;
            }
            curr_pos = curr_pos->next;
        }
        printf("%5d", curr_pos->elem);
        CircleLinkedNode* t = curr_pos->next;
        delete_circle_linked_list_node(head, curr_pos);
        curr_pos = t;
    }
    printf("\n");
    return 0;
````````````````


# 通过stack解决后缀表达式的运算
```````````````c
# include <stdio.h>
int f (int A ,int B,char p){
    switch(p){
        case '+':
            return A+B;
        case '-':
            return A-B;
        case '*':
            return A*B;
        case '/':
            return A/B;
        default:
            return 0;
        
    }
    
}

void push(int *p, int top, int elem) {                       //入栈
    p[++top] = elem;
    return ;
}
int pop(int *p, int top) {                                  //出栈
    if (top == -1) {
        printf("格式错误 \n");
        return 0;
    }
    else
    return p[top--];
}


int rpn (char *a){
    int b[]={0};
    int num =0;
    int k=0;//b的top
    while(a[num]!='\0'){
        num++;
    }
    for(int i=0;i<num;i++){
        if(a[i] >= '0'&& a[i] <= '9'){
            push(b,k,a[i]-'0');
        }
        else{
            int A= pop(b, k);
            int B= pop(b, k);
            int C= f(A,B,a[i]);
            push(b,k,C);
        }
    }
    
    return b[k];
    
    
}

int main (void){
    char a[] ="5 1 2 + 4 * + 3 -";
    int r = rpn (a);
    printf ("结果为%4d\n", r);
    return  0;
    
}
