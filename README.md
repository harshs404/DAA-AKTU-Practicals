# DAA-AKTU-Practicals
AKTU DAA Practicals
# ____________N Queen_________________
#include<stdio.h>
#include<math.h>
int board[20],count;
int main()
{
 int n,i,j;
 void queen(int row,int n);

 printf(" - N Queens Problem Using Backtracking -");
 printf("\n\nEnter number of Queens:");
 scanf("%d",&n);
 queen(1,n);
 return 0;
}
void print(int n)
{
 int i,j;
 printf("\n\nSolution %d:\n\n",++count);

 for(i=1;i<=n;++i)
  printf("\t%d",i);

 for(i=1;i<=n;++i)
 {
  printf("\n\n%d",i);
  for(j=1;j<=n;++j)
  {
   if(board[i]==j)
    printf("\t1");
   else
    printf("\t-");
  }
 }
}
int place(int row,int column)
{
 int i;
 for(i=1;i<=row-1;++i)
 {

  if(board[i]==column)
   return 0;
  else
   if(abs(board[i]-column)==abs(i-row))
    return 0;
 }

 return 1;
}
void queen(int row,int n)
{
 int column;
 for(column=1;column<=n;++column)
 {
  if(place(row,column))
  {
   board[row]=column;
   if(row==n)
    print(n);
   else
    queen(row+1,n);
  }
 }
}

# ______________Binary search___________
#include<stdio.h>
#include<stdlib.h>
int binary_search(int[], int, int, int);
void main()
{
    int i,j,n,pos,first,last,arr[100], key;
    printf("enter the size of array\n");
    scanf("%d",&n);
    printf("enter the array\n");
    for(i=0;i<n;i++)
    {
         scanf("%d",&arr[i]);
    }
    printf("enter the element to be searched\n");
    scanf("%d",&key);
    first = 0;
    last = n-1;
    pos = binary_search(arr, first, last, key);
    if(pos)
    {
         printf("\nelement %d is found at %d position",key, pos);
    }
    else
    {
         printf("\nelement not found");
    }
}
int binary_search(int arr[], int first, int last, int key)
{
    int mid;
    mid = (first + last)/2;
    if(first <= last)
    {
        if(key == arr[mid])
            {
                return mid+1;
            }
        else if(key < arr[mid])
            {
                return binary_search(arr, first, mid-1, key);
            }
        else
            {
                return binary_search(arr, mid+1, last, key);
            }
        }
     if(first > last)
     {
        return 0;
     }
}
# ___________Bubble_________
#include<stdio.h>
 int main()
{
	int a[100],n,i,j,temp;
	printf("Enter the size of array....\n");
	scanf("%d",&n);
	printf("Enter the array elements....\n");
	for(i=0;i<n;++i)
		scanf("%d",&a[i]);
    for(i=0;i<n-1;i++)
    {
     for(j=0;j<n-i;j++)
     {
        if(a[j]>a[j+1])
        {
            temp=a[j];
            a[j]=a[j+1];
            a[j+1]=temp;
        }
      }
    }
    printf("\n Sorted array is....\n ");
	for(i=0;i<n;++i)
		printf("%d ",a[i]);
 return 0;
}
#_________heap sort__________
#include <stdio.h>

void main()
{
    int heap[10], no, i, j, c, root, temp;

    printf("\n Enter no of elements :");
    scanf("%d", &no);
    printf("\n Enter the nos : ");
    for (i = 0; i < no; i++)
       scanf("%d", &heap[i]);
    for (i = 1; i < no; i++)
    {
        c = i;
        do
        {
            root = (c - 1) / 2;
            if (heap[root] < heap[c])
            {
                temp = heap[root];
                heap[root] = heap[c];
                heap[c] = temp;
            }
            c = root;
        } while (c != 0);
    }

    for (j = no - 1; j >= 0; j--)
    {
        temp = heap[0];
        heap[0] = heap[j];
        heap[j] = temp;
        root = 0;
        do
        {
            c = 2 * root + 1;
            if ((heap[c] < heap[c + 1]) && c < j-1)
                c++;
            if (heap[root]<heap[c] && c<j)
            {
                temp = heap[root];
                heap[root] = heap[c];
                heap[c] = temp;
            }
            root = c;
        } while (c < j);
    }
    printf("\n The sorted array is : ");
    for (i = 0; i < no; i++)
       printf("\t %d", heap[i]);
}
#_________insertion sort________
#include<stdio.h>
int main(){
   int i, j, count, temp, number[25];
   printf("How many numbers u are going to enter?: ");
   scanf("%d",&count);
   printf("Enter %d elements: ", count);
   for(i=0;i<count;i++)
      scanf("%d",&number[i]);
   for(i=1;i<count;i++){
      temp=number[i];
      j=i-1;
      while((temp<number[j])&&(j>=0)){
         number[j+1]=number[j];
         j=j-1;
      }
      number[j+1]=temp;
   }
   printf("Order of Sorted elements: ");
   for(i=0;i<count;i++)
      printf(" %d",number[i]);
   return 0;
}
#___________knapsack____________
# include<stdio.h>
# include<conio.h>
void knapsack(int n, float weight[], float profit[], float capacity)
{
 float x[20], tp= 0;
 int i, j, u;
 u=capacity;
 for (i=0;i<n;i++)
     x[i]=0.0;

 for (i=0;i<n;i++)
 {
 if(weight[i]>u)
      break;
 else
     {
     x[i]=1.0;
     tp= tp+profit[i];
     u=u-weight[i];
     }
 }
 if(i<n)
       x[i]=u/weight[i];
 tp= tp + (x[i]*profit[i]);
 printf("\n The result vector is:- ");
 for(i=0;i<n;i++)
        printf("%f\t",x[i]);

 printf("m Maximum profit is:- %f", tp);

}
void main()
{
 float weight[20], profit[20], capacity;
 int n, i ,j;
 float ratio[20], temp;

 printf ("\n Enter the no. of objects:- ");
 scanf ("%d", &n);

 printf ("\n Enter the wts and profits of each object:- ");
 for (i=0; i<n; i++)
 {
 scanf("%f %f", &weight[i], &profit[i]);
 }

 printf ("\n enter the capacity a city of knapsack:- ");
 scanf ("%f", &capacity);

 for (i=0; i<n; i++)
 {
 ratio[i]=profit[i]/weight[i];
 }
 for(i=0; i<n; i++)
 {
    for(j=i+1;j< n; j++)
    {
      if(ratio[i]<ratio[j])
      {
      temp= ratio[j];
      ratio[j]= ratio[i];
      ratio[i]= temp;

     temp= weight[j];
     weight[j]= weight[i];
     weight[i]= temp;

     temp= profit[j];
     profit[j]= profit[i];
     profit[i]= temp;
     }
   }
 }
 knapsack(n, weight, profit, capacity);
 getch();
}
#__________kruskal min spanning__________
#include<stdio.h>
#include<stdlib.h>

int k,n,ne=0;
int mins,mincost=0,cost[9][9],parent[9];
int find(int);

void makeset(int i);
void uni(int,int);

int main()
{
    int i,j,u,v;
    printf("\n\n\t Implementation of Kruskal's algorithm\n\n");
    printf("\nEnter the no. of vertices\n");
    scanf("%d",&n);
    printf("\nEnter the cost adjacency matrix\n");
    for(i=1;i<=n;i++)
    {
        for(j=1;j<=n;j++)
        {
            scanf("%d",&cost[i][j]);
            if(cost[i][j]==0)
                cost[i][j]=999;
        }
    }
    printf("\nThe edges of Minimum Cost Spanning Tree are\n\n");
    for(i=1;i<=n;i++)
        makeset(i);
    while(ne<=n-1)
    {
        for(i=1,mins=999;i<=n;i++)
        {
            for(j=1;j<=n;j++)
            {
                if(cost[i][j]<mins)
                {
                    mins=cost[i][j];
                    u=i;
                    v=j;
                }
            }
        }
        if(find(u)!=find(v))
        {
            uni(u,v);
            mincost +=mins;
            printf("\n%d edge (%d,%d) =%d\n",++ne,u,v,mins);
            printf("\n\tnow Minimum cost = %d\n",mincost);
        }
        cost[u][v]=cost[v][u]=999;
    }
} // end of main

void makeset(int i)
{
    parent[i]=i;
}

int find(int i)
{
    return(parent[i]);
}

void uni(int i, int j)
{
    int a,b;
    a=find(i);
    b=find(j);
    for(i=1;i<=n;i++)
    {
    if(parent[i]==b)
        parent[i]=a;
    }
}
#______linear search_________
#include<stdio.h>
int linear_search(int arr[], int, int);
void main()
{
    int n,i,arr[100],key,pos=0;
    printf("enter the no. of elements\n");
    scanf("%d",&n);
    printf("enter the array elements\n");
    for(i=0;i<n;i++)
    {
        scanf("%d",&arr[i]);
    }
    printf("Enter the element to be searched:");
    scanf("%d",&key);
    pos = linear_search(arr,n,key);
    if(pos != 0)
    {
        printf("element %d is found at %d position",key, pos);
    }
    else
    {
        printf("element not found\n");
    }
}

int linear_search(int arr[], int n, int key)
{
    if(n>=0)
    {
        if(arr[n-1]==key)
        {
            return n;
        }
        else
        {
            return linear_search(arr,n-1,key);
        }
        n--;
    }
}


#_________merge sort_____________
/*
Name: Harsh Saxena
Class: IT-C
Roll: 1803213062
DAA Lab Practical
Sub code: KCS 553
*/
#include <stdio.h>
void mergeSort(int [], int, int, int);
void partition(int [],int, int);
int main()
{
    int list[50];
    int i, size;

    printf("Enter total number of elements:");
    scanf("%d", &size);
    printf("Enter the elements:\n");
    for(i = 0; i < size; i++)
    {
         scanf("%d", &list[i]);
    }
    partition(list, 0, size - 1);
    printf("After merge sort:\n");
    for(i = 0;i < size; i++)
    {
         printf("%d   ",list[i]);
    }
    printf("\nHarsh Saxena 1803213062 IT-C");
   return 0;
}
void partition(int list[],int low,int high)
{
    int mid;
    if(low < high)
       {
        mid = (low + high) / 2;
        partition(list, low, mid);
        partition(list, mid + 1, high);
        mergeSort(list, low, mid, high);
       }
}
void mergeSort(int list[],int low,int mid,int high)
{
    int i, mi, k, lo, temp[50];
    lo = low;
    i = low;
    mi = mid + 1;
    while ((lo <= mid) && (mi <= high))
    {
        if (list[lo] <= list[mi])
        {
            temp[i] = list[lo];
            lo++;
        }
        else
        {
            temp[i] = list[mi];
            mi++;
        }
        i++;
    }
    if (lo > mid)
    {
        for (k = mi; k <= high; k++)
        {
            temp[i] = list[k];
            i++;
        }
    }
    else
    {
        for (k = lo; k <= mid; k++)
        {
             temp[i] = list[k];
             i++;
        }
    }

    for (k = low; k <= high; k++)
    {
        list[k] = temp[k];
    }
}
//the end
#_________prims algo_________
#include<stdio.h>
#include<conio.h>
int a,b,u,v,n,i,j,ne=1;
int visited[10]={0},min,mincost=0,cost[10][10];

void main()
{
	printf("\nEnter the number of nodes:");
	scanf("%d",&n);
	printf("\nEnter the adjacency matrix:\n");
	for(i=1;i<=n;i++)
	for(j=1;j<=n;j++)
	{
		scanf("%d",&cost[i][j]);
		if(cost[i][j]==0)
			cost[i][j]=999;
	}
	visited[1]=1;
	printf("\n");
	while(ne < n)
	{
		for(i=1,min=999;i<=n;i++)
		for(j=1;j<=n;j++)
		if(cost[i][j]< min)
		if(visited[i]!=0)
		{
			min=cost[i][j];
			a=u=i;
			b=v=j;
		}
		if(visited[u]==0 || visited[v]==0)
		{
			printf("\n Edge %d:(%d %d) cost:%d",ne++,a,b,min);
			mincost+=min;
			visited[b]=1;
		}
		cost[a][b]=cost[b][a]=999;
	}
	printf("\n Minimun cost=%d",mincost);
	getch();
}
__________quick sort_______
#include<stdio.h>
void quicksort(int number[25],int first,int last){
   int i, j, pivot, temp;
   if(first<last){
      pivot=first;
      i=first;
      j=last;
      while(i<j){
         while(number[i]<=number[pivot]&&i<last)
            i++;
         while(number[j]>number[pivot])
            j--;
         if(i<j){
            temp=number[i];
            number[i]=number[j];
            number[j]=temp;
         }
      }
      temp=number[pivot];
      number[pivot]=number[j];
      number[j]=temp;
      quicksort(number,first,j-1);
      quicksort(number,j+1,last);
   }
}
int main(){
   int i, count, number[25];
   printf("How many elements are u going to enter?: ");
   scanf("%d",&count);
   printf("Enter %d elements: ", count);
   for(i=0;i<count;i++)
      scanf("%d",&number[i]);
   quicksort(number,0,count-1);
   printf("Order of Sorted elements: ");
   for(i=0;i<count;i++)
      printf(" %d",number[i]);
   return 0;
}
#___________selection sort____________
#include<stdio.h>
int main(){
   int i, j, count, temp, number[25];
   printf("How many numbers u are going to enter?: ");
   scanf("%d",&count);
   printf("Enter %d elements: ", count);
   for(i=0;i<count;i++)
      scanf("%d",&number[i]);
   for(i=0;i<count;i++){
      for(j=i+1;j<count;j++){
         if(number[i]>number[j]){
            temp=number[i];
            number[i]=number[j];
            number[j]=temp;
         }
      }
   }
   printf("Sorted elements: ");
   for(i=0;i<count;i++)
      printf(" %d",number[i]);
   return 0;
}
#________heap sort___________
#include <stdio.h>

void main()
{
    int heap[10], no, i, j, c, root, temp;

    printf("\n Enter no of elements :");
    scanf("%d", &no);
    printf("\n Enter the nos : ");
    for (i = 0; i < no; i++)
       scanf("%d", &heap[i]);
    for (i = 1; i < no; i++)
    {
        c = i;
        do
        {
            root = (c - 1) / 2;
            if (heap[root] < heap[c])
            {
                temp = heap[root];
                heap[root] = heap[c];
                heap[c] = temp;
            }
            c = root;
        } while (c != 0);
    }

    for (j = no - 1; j >= 0; j--)
    {
        temp = heap[0];
        heap[0] = heap[j];
        heap[j] = temp;
        root = 0;
        do
        {
            c = 2 * root + 1;
            if ((heap[c] < heap[c + 1]) && c < j-1)
                c++;
            if (heap[root]<heap[c] && c<j)
            {
                temp = heap[root];
                heap[root] = heap[c];
                heap[c] = temp;
            }
            root = c;
        } while (c < j);
    }
    printf("\n The sorted array is : ");
    for (i = 0; i < no; i++)
       printf("\t %d", heap[i]);
}
