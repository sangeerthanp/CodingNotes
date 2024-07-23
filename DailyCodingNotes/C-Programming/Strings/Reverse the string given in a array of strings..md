
	Input: 5
		apple mango orange guava grapes
	Output:
		ognam
		avaug


```c
#include<stdio.h>
#include<string.h>
int main(){
    int n;
    scanf("%d",&n);
    char arr[n][100];
    for(int i=0;i<n;i++){
        scanf("%s",arr[i]);
    }
    for(int i=0;i<n;i++){
        if(i%2!=0){
            int len = strlen(arr[i]);
            for(int j=len-1;j>=0;j--){
                printf("%c",arr[i][j]);
            }
            printf("\n");
        }
    }
}


```