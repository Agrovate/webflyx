#include<stdio.h>
#include<stdlib.h>
void Nqueen(int);
int place(int);
int col[30],count=0;
void main()
{
int i,n;
printf("\n Enter the number of queens: ");
scanf("%d",&n);
Nqueen(n);
printf("\n Total no.of solutions are %d", count);
}
int place(int r)
{
int i;
for(i=1;i<r;i++)//i-->row r-->current row
{
if((col[i]==col[r]) ||(abs(i-r)==abs(col[i]-col[r])))
//if q is already placed in column col[k] OR (k,col[k]) cell and
//one of the previously placed queen are in same diagonal
return 0;
}
return 1;
}
void Nqueen(int n)
{
int r=1,i,j;//r-->row
col[r]=0;
while(r!=0)
{
col[r]=col[r]+1;
while((col[r]<=n) && !place(r))
col[r]=col[r]+1;
if(col[r]<=n) //if 1
{
if(r==n)
{
count++;
printf("\nSolution # %d\n",count);
for(i=1;i<=n;i++)
{
for(j=1;j<=n;j++)
{
if(j==col[i])
printf("Q ");
else
printf("* ");
}
printf("\n\n");
}
}
else
{
r++;
col[r]=0;
}
}//if 1
else
r --; //backtracking
}//while
}