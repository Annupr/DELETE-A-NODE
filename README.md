# DELETE-A-NODE
Here is the program to delete a node in simple link list by position
#include<stdio.h>
#include<stdlib.h>
struct Node{
	int data;
	struct Node *next;
	};

void create(struct Node **head_ref,int ele)
{
	/*struct Node *new_node=(struct Node *)malloc(sizeof(struct Node*));
	new_node->data=ele;
	new_node->next=(*head_ref);
	*head_ref=new_node;*/
		struct Node* new_node = (struct Node*)malloc(sizeof(struct Node*));
	 // put in the data
	 new_node->data=ele;
	 //make next of new node is head
	 new_node->next=(*head_ref);
	 (*head_ref)=new_node;
}
void del_pos(struct Node **head_ref,int pos)
{	
	int i;
	struct Node *ptr=*head_ref;
	if(*head_ref==NULL)
	{
		printf("\nlink list is empty...\n");
		return;
	}
	if(pos==0)
	{
		*head_ref=ptr->next;
		free(ptr);
		return;
	}
	for(i=0;ptr!=NULL&&i<pos-1;i++){
		ptr=ptr->next;
	}
	struct Node * temp=ptr->next;
	ptr->next=temp->next;
	free(temp);
}


void printList(struct Node *ptr)
{
	while(ptr!=NULL)
	{
		printf("%d ",ptr->data);
		ptr=ptr->next;
	}
	printf("\n");
}
void main(){
	struct Node *head=NULL;
	int n,i,ele,pos;
	printf("\nEnter the range");
	scanf("%d",&n);
	
	for(i=0;i<n;i++)
	{
		printf("\n enter element no %d : \n",n-i);
		scanf("%d",&ele);
		create(&head,ele);
	}
	printf("\nthe input link list is\n");
	printList(head);
	printf("\n Enter the position :");
	scanf("%d",&pos);
	if(pos<=n){
		del_pos(&head,pos);
		printf("\nthe new link list is\n");
	printList(head);
	}else{
		printf("\nIncorrect input...");
	}
	
}
