
| Input | Output                           |
| ----- | -------------------------------- |
| 1 100 | 13 31<br>17 71<br>37 73<br>79 97 |
| 1 50  | 13 31                            |


```c
#include<stdio.h>
#include<math.h>

int isPrimeAna(int num1,int num2){
    int hash1[10] = {0};
    int hash2[10] = {0};
    while(num1 != 0){
        hash1[num1 % 10]++;
        num1 /= 10;
    }
    while(num2 != 0){
        hash2[num2 % 10]++;
        num2 /= 10;
    }
    
    for(int i=0;i<10;i++){
        if(hash1[i] != hash2[i]) return 0;
    }
    return 1;
}


void getPrime(int s,int e){
    int flag;
    int newarr[100],index=0;
    for(int i=s;i<=e;i++){
        flag = 1;
        if(i==0||i==1) continue;
        for(int j=2;j<=i/2;j++){
            if(i%j == 0){
                flag = 0;
                break;
            }
        }
        if(flag) newarr[index++] = i;
    }
    for(int i=0;i<index;i++){
        for(int j=i+1;j<index;j++){
            if(isPrimeAna(newarr[i],newarr[j])){
                printf("%d %d\n",newarr[i],newarr[j]);
            }
        }
    }
}

int main(){
    int start,end;
    scanf("%d %d",&start,&end);
    getPrime(start,end);
}
```