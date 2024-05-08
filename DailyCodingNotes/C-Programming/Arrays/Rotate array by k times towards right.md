```c
#include<stdio.h>

int
rotateArrayByTimes (int arr[], int length, int times)
{
  for (int j = 1; j <= times; j++)
	{
	  int temp = arr[length - 1];
	  for (int i = length - 1; i > 0; i--)
		{
		  arr[i] = arr[i - 1];
		}
	  arr[0] = temp;
	}
  return length;
}

int
main ()
{
  int n;
  scanf ("%d", &n);
  int arr[n];
  for (int i = 0; i < n; i++)
	{
	  scanf ("%d", &arr[i]);
	}
  int k;
  scanf ("%d", &k);
  int length = rotateArrayByTimes (arr, n, k);
  for (int i = 0; i < length; i++)
	{
	  printf ("%d ", arr[i]);
	}
}
```
