
| Input              | Output        |
| ------------------ | ------------- |
| 5<br>5 2 9 1 5     | 1 2 5 5 9     |
| 5<br>8, 3, 1, 7, 4 | 1, 3, 4, 7, 8 |

```c
#include<stdio.h>
void sortArray(int arr[],int n){
    int max = 0;
    for(int i=0;i<n;i++){
        for(int j=i+1;j<n;j++){
            if(arr[i] > arr[j]){
                int temp = arr[j];
                arr[j] = arr[i];
                arr[i] = temp;
            }
        }
    }
    for(int i=0;i<n;i++){
        printf("%d ",arr[i]);
    }
}

int main(){
    int n;
    scanf("%d",&n);
    int arr[n];
    for(int i=0;i<n;i++){
        scanf("%d",&arr[i]);
    }
    sortArray(arr,n);
}
```
