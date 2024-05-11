```c
#include<stdio.h>

int findFirstOccurrence (int arr[], int n, int num)
{
  int found = 0;
  for (int i = 0; i < n; i++)
	{
	  if (found || arr[i] != num)
		{
		  arr[i - found] = arr[i];
		}
	  else
		{
		  found = 1;
		}
	}
  return found;
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
  int num;
  printf ("Enter num:");
  scanf ("%d", &num);
  int found = findFirstOccurrence (arr, n, num);
  if (!found)
	{
	  printf ("Not found");
	}
  else
	{
	  n--;
	  for (int i = 0; i < n; i++)
		{
		  printf ("%d ", arr[i]);
		}
	}
}

```