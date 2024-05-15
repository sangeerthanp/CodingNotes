```c
#include<stdio.h>
#include<string.h>
int main(){
    char arr[100];
    int index = 0;
    char newarr[index];
    scanf("%[^\n]s",arr);
    arr[strcspn(arr, "\n")] = '\0';
    for(int i=0;arr[i] !='\0';i++){
        if(arr[i] != 'A' &&arr[i] != 'E' &&arr[i] != 'I' &&arr[i] != 'O' &&arr[i] != 'U' &&arr[i] != 'a' &&arr[i] != 'e' &&arr[i] != 'i' &&arr[i] != 'o' &&arr[i] != 'u'){
            newarr[index++] = arr[i];
        }
    }
    newarr[index] = '\0';
    printf("%s",newarr);
}
```

==arr[strcspn(arr, "\n")] = '\0';==  is used to remove the newline in the string 