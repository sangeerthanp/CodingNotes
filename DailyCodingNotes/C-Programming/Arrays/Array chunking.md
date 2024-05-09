```c
#include<stdio.h>

void chunktheArray(int arr[],int n,int chunk){
    int numchunks;
    numchunks = (n+chunk-1)/chunk;
    for(int i=0;i<numchunks;i++){
        int start = i * chunk;
        int end = (i+1) * chunk;
        if(end > n){
            end = n;
        }
        printf("[");
        for(int j=start;j<end;j++){
            printf("%d",arr[j]);
            if(j < end-1){
                printf(",");
            }
        }
        printf("]");
    }
}

int main(){
    int n;
    int chunk;
    scanf("%d",&n);
    int arr[n];
    for(int i=0;i<n;i++){
        scanf("%d",&arr[i]);
    }
    printf("Enter chunk:");
    scanf("%d",&chunk);
    chunktheArray(arr,n,chunk);
}
```

![[Pasted image 20240509220520.png]]
