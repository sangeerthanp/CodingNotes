```c\#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    fgets(arr,sizeof(arr),stdin);
    for(int i=0;i<strlen(arr);i++){
        if(arr[i] == 'A'||arr[i] == 'E'||arr[i] == 'I'||arr[i] == 'O'||arr[i] == 'U'||arr[i] == 'a'||arr[i] == 'e'||arr[i] == 'i'||arr[i] == 'o'||arr[i] == 'u'){
            continue;
        }
        printf("%c",arr[i]);
    }
}
```