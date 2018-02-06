上次用**尾插法**建立的链表，这次改用**头插法**建立，代码如下：
```
#include <stdio.h>
#include <stdlib.h>

//头插法建立链表
 
//定义链表结点 
typedef struct node{
	int data;
	struct node *next;
}Lnode;


//创建n个结点的链表，因为要通过参数改变指针变量，
//所以形参采用二重指针形式，生成链表带有头结点； 
void createLnode(Lnode **L, int n){
	//声明指针p，用来指向新生成的链表结点； 
	Lnode *p;
	*L = (Lnode*)malloc(sizeof(Lnode));
	(*L)->next = NULL;
	p = *L;
	int i;
	//循环插入结点 
	for(i=0;i<n;i++){
		p = (Lnode*)malloc(sizeof(Lnode));
		scanf("%d", &p->data);
		p->next = (*L)->next;
		(*L)->next = p; 
	}
}

//遍历链表，用于检查链表是否成功建立 
void listLnode(Lnode *L){
	//声明指针p，用于跟踪链表结点 
	Lnode *p;
	//L->next指向链表第一个结点 
	p = L->next;
	while(p != NULL){
		printf("%d ",p->data);
		p = p->next;
	}	
}

int main(){
	//声明一个结构指针，并获得内存空间； 
	Lnode *L = (Lnode*)malloc(sizeof(Lnode));
	//将指针L的地址(双重指针)传给函数，生成5个结点的链表 
	createLnode(&L, 5);
	//遍历链表 
	listLnode(L);
}
```
编译运行程序，依次输入5个整数，回车，运行结果如下：

![](https://thumbnail0.baidupcs.com/thumbnail/f47d6e982bd49b8a6a10e7066cf4f70f?fid=427924432-250528-95786580069134&time=1517929200&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-fS1Pyzrq57kwVyGsIrWWDEQwfvc%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=857885373484580519&dp-callid=0&size=c710_u400&quality=100&vuk=-&ft=video)

成功用头插法建立链表！