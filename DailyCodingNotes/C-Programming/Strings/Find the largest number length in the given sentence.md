
Input :- 4(range of words) 
This question is easy. 
Output:- 8(length of the largest word)

```c
#include<stdio.h>
#include<string.h>
int main ()
{
  int n;
  scanf ("%d", &n);
  char arr[n][100];
  for (int i = 0; i < n; i++){
	  scanf ("%s", arr[i]);
	}
  char largest[100];
  strcpy (largest, "");
  for (int i = 0; i < n; i++){
	  char *token = strtok (arr[i], " ");
	  while (token != NULL){
		  if (strlen (token) > strlen (largest)){
			  strcpy (largest, token);
			}
		  token = strtok (NULL, " ");
		}
	}
  int len = strlen (largest);
  printf ("%d", len);
}

```