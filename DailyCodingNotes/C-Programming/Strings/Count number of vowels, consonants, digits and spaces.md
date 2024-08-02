

| Input               | Output    |
| ------------------- | --------- |
| He speaks malayalam | He speaks |


```c
#include<stdio.h>
#include<ctype.h>
int main(){
    int vow,con,dig,spa,i;
    vow=con=dig=spa=0;
    char arr[150];
    fgets(arr,sizeof(arr),stdin);
    for (i=0;arr[i]!='\0';++i){
        arr[i] = tolower(arr[i]);
        if(arr[i] == 'a' || arr[i] == 'e' || arr[i] == 'i' || arr[i] == 'o'|| arr[i] == 'u'){
            ++vow;
        }
        else if(arr[i] >= 'a' && arr[i] <= 'z'){
            ++con;
        }
        else if(arr[i] >= '1' && arr[i] <= '9'){
            ++dig;
        }
        else if(arr[i] == ' '){
            ++spa;
        }
    }
    printf("%d\n",vow);
    printf("%d\n",con);
    printf("%d\n",dig);
    printf("%d\n",spa);
    return 0;
}

```