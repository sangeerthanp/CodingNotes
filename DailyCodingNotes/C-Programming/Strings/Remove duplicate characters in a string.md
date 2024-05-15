
input: Engineering 
output: Engier


```c
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int
main ()
{
  int i, j, k;
  char arr[100];
  scanf ("%[^\n]s", arr);
  arr[strcspn (arr, "\n")] = '\0';
  for (i = 0; arr[i] != '\0'; i++)
	{
	  if (isalpha (arr[i]))
		{
		  for (j = i + 1; arr[j] != '\0'; j++)
			{
			  if (arr[i] == arr[j])
				{
				  for (k = j; arr[k] != '\0'; k++)
					{
					  arr[k] = arr[k + 1];
					}
				  j--;
				}
			}
		}
	}
  printf ("%s", arr);
}
```