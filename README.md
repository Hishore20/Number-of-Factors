# Number-of-Factors


Alice has learnt factorization recently. Bob doesnt think she has learnt it properly and hence he has decided to quiz her. Bob gives Alice a very large number and asks her to find out the number of factors of that number. To make it a little easier for her, he represents the number as a product of N numbers. Alice is frightened of big numbers and hence is asking you for help. Your task is simple. Given N numbers, you need to tell the number of distinct factors of the product of these N numbers.

Input:

First line of input contains a single integer T, the number of test cases.

Each test starts with a line containing a single integer N.
The next line consists of N space separated integers (Ai).


Output:

For each test case, output on a separate line the total number of factors of the product of given numbers.


Constraints:

1<=T<=100
1 <=N <=10
2 <=Ai <=1000000
Logic Test Case 1

Input (stdin)
3

3

3 5 7

3

2 4 6

2

5 5

Expected Output

8

10

3
Logic Test Case 2

Input (stdin)

0

Expected Output

0




#include<stdio.h>
#include<stdlib.h>
#include<math.h>
#define SIZE 300
int main()
{
	int anum[SIZE],t,a,out=1,r,i,j,k,l,d,n,count[30],prime[SIZE],m;
	scanf("%d",&t);
	for(i=0;i<t;i++)
	{
		scanf("%d",&n);
		l=0;
		r=0;
		out=1;
		for(j=0;j<30;j++)
		{
			count[j]=0;
			prime[j]=0;
			anum[j]=-1;
		}
		for(j=0;j<n;j++)
		{
			scanf("%d",&a);
			d=sqrt(a);
			for(k=2;k<=(d+1);k++)
			{
				if(a%k==0)
				{
					for(m=0;m<r;m++)
					{
						if(prime[m]==k)
						{
							l=anum[m];
							break;
						}
					}
					if(m==r)
					{
						prime[r]=k;
						anum[r]=r;l=r;
						r++;
					}
					while(a%k==0)
					{
						count[l]=count[l]+1;
						a=a/k;
					}
				}
			}
			if(a>1)
			{
				for(m=0;m<r;m++)
				{
					if(prime[m]==a)
					{
						l=anum[m];
			
						
						break;
					}
				}
				if(m==r)
				{
					prime[r]=a;
					anum[r]=r;l=r;
					r++;
				}
 
				count[l]++;
			}
		}
		
		for(j=0;j<r;j++)
		{
			
		
			count[j]=count[j]+1;
			out=out*count[j];
		}
		printf("%d\n",out);
	}
	return 0;
}  
