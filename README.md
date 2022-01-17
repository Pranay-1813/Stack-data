# Stack-data
Stack data


/*Name- Pranay Bhagat
Roll no- A110
Problem Statement- Implement stack as an abstract data type using linked list and use this ADT for conversion of infix expression to postfix, prefix, and evaluation of postfix and prefix expression.*/
#include <stdio.h>
#include <stdlib.h> 

struct abc
{
 int data;
 struct abc *next;
}; 
struct abc *top;
int isempty();
int isfull();
struct abc *push(int);
void pop();
void show(struct abc*);
int main(void) 
{
  int choice,a;
  do
  {
    printf("1. Insert\n2. Pop\n3. Show\n4. Exit\n");
    printf("Enter your choice:\n");
    scanf("%d",&choice);
    switch(choice)
    {
      case 1:
      printf("Enter the element to be inserted:\n");
      scanf("%d",&a);
      top=push(a);
      break;

      case 2:
      pop();
      break;

      case 3:
      show(top);
      break;

      case 4:
      printf("You have opted to exit the program.\n");
      break;

      default:
      printf("Enter a valid choice.\n");
      break;
    }
  }while(choice!=4);
  return 0;
}
int isempty()
{
  if(top==NULL)
  {
    return 1;
  }
  else
  {
    return 0;
  }
}
int isfull()
{
  struct abc *temp;
  temp=(struct abc*)malloc(sizeof(struct abc));
  if(temp==NULL)
  {
    return 1;
  }
  else
  {
    return 0;
  }
}
struct abc *push(int x)
{
  if(isfull())
  {
    printf("Can't insert because stack is full.\n");
  }
  else
  {
    struct abc *temp;
    temp=(struct abc*)malloc(sizeof(struct abc));
    temp->data=x;
    temp->next=top;
    top=temp;
    printf("Element is inserted.\n");
  }
  return top;
}
void show(struct abc *top)
{
  struct abc *p;
  p=top;
   printf("Elements in the stack are:\n");
  while(p!=NULL)
  {
    printf("%d\n", p->data);
    p=p->next;
  }
}
void pop()
{
  if(isempty())
  {
    printf("The stack is already empty.\n");
  }
  else
  {
    struct abc *p;
    p=top;
    top=top->next;
    free(p);
  }
}
