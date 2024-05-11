```c
#include<stdio.h>
#include<stdbool.h>

void uniqueElement (int arr[], int n)
{
  for (int i = 0; i < n; i++)
	{
	  bool match_found = false;
	  for (int j = 0; j < n; j++)
		{
		  if ((arr[i] == arr[j]) && i != j)
			{
			  match_found = true;
			}
		}
	  if (!match_found)
		{
		  printf ("%d ", arr[i]);
		}
	}
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
  uniqueElement (arr, n);
}

```