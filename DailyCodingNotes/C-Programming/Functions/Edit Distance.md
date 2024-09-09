```c
#include<stdio.h>  
#include<string.h>  
int n,m,dp[100][100];  
int min(int a,int b,int c){  
    int min=a>b?b:a;  
    min=min>c?c:min;  
    return min;  
}  
int mindist(char**ch,char**c){  
    for(int i=0;i<=m;i++)  
    dp[i][0]=i;  
    for(int i=0;i<=n;i++)  
    dp[0][i]=i;  
    for(int i=1;i<=m;i++){  
        for(int j=1;j<=n;j++){  
            if(ch[i-1]==c[j-1])  
            dp[i][j]=dp[i-1][j-1];  
            else  
            dp[i][j]=min(dp[i-1][j-1],dp[i-1][j],dp[i][j-1])+1;  
        }  
    }  
    return dp[m][n];  
}  
int main(){  
    char ch[100],c[100];  
    scanf("%s %s",ch,c);  
    m=strlen(ch),n=strlen(c);  
    printf("%d",mindist(ch,c));  
}
```

```c
#include<stdio.h>
#include<string.h>
int dp[100][100];

int min(int a,int b, int c){
    int min = a>b?b:a;
    min = min>c?c:min;
    return min;
}
int editDistance(char * s,char * t,int m,int n){
    for(int i=0;i<=m;i++) dp[i][0] = i;
    for(int i=0;i<=n;i++) dp[0][i] = i;
    for(int i=1;i<=m;i++){
        for(int j=1;j<=n;j++){
            if(s[i-1] == t[j-1]){
                dp[i][j] = dp[i-1][j-1];
            }
            else{
                dp[i][j] = min(dp[i-1][j-1],dp[i-1][j],dp[i][j-1]) +1;
            }
        }
    }
    return dp[m][n];
}
int main(){
    char s[100] , t[100];
    fgets(s,100,stdin);
    s[strcspn(s,"\n")] = '\0';
    fgets(t,100,stdin);
    t[strcspn(t,"\n")] = '\0';
    int m = strlen(s);
    int n = strlen(t);
    int res = editDistance(s,t,m,n);
    printf("%d",res);
}
```