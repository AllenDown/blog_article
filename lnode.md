## 单向链表的简单实现（C语言版）
半夜睡不着觉，爬起来写了个链表哈哈！先偷懒直接代码注释啦；
    #include <stdio.h>
    #include <stdlib.h>

    //定义一个结构体代表链表结点 
    struct node{ 
        int data; //结点中存放数据 
        struct node *next; //指向下一个结点的指针 
    };

    //为求方便给结点类型一个新的类型名Lnode 
    typedef struct node Lnode;

    int main(){
        //定义三个指针 1.head:头指针；2.P:每次通过该指针获取新的内存空间；
        //3.P1:作为记忆连接结点使用; 
        Lnode *head, *p1, *p;
        //获取头结点，此时三个指针指向同一片内存空间 
        head = (Lnode*)malloc(sizeof(Lnode));
        p = head;
        p1 = head;
        //输入整数，存到头结点data中 
        scanf("%d", &p->data);
        //设定当数据域data=0即用户输入0时退出循环，链表建立结束
        while(p->data != 0){	
            //获取新的内存空间 
            p = (Lnode*)malloc(sizeof(Lnode));
            //连接结点 
            p1->next = p;
            //用p1跟踪当前最后一个结点 
            p1 = p;
            //存放结点数据 
            scanf("%d", &p->data);
        }; 
        //让尾结点指针变量指向NULL 
        p->next = NULL;
        //让p1指向头结点，用于遍历链表
        p1 = head; 
        //遍历链表
        while(p1->next != NULL){
            printf("%d\n", p1->data);
            p1 = p1->next;
        };
        return 0;
    } 
编译运行代码，输入**1,2,3,4,5,0**; 运行结果如下：
![](https://thumbnail0.baidupcs.com/thumbnail/9743b920bcc10bdf6ce76e10acc5740e?fid=427924432-250528-1093112864283835&time=1517767200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-JsBpCOtGPuvOp%2F2naSdNs9eXVqo%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=814109238043827141&dp-callid=0&size=c710_u400&quality=100&vuk=-&ft=video)