```c
#define ABS(val) ((val) < 0 ? (val) * -1 : (val) )

#define MIN(num1,num2) ((num1) < (num2) ? (num1) : (num2))

  

void subStr(char *str, char *sub, int start, int copySize) {

    memcpy(sub, &str[start], copySize);

    sub[copySize] = '\0';

}

  

long long getPalindrome(long prefix, bool isEvenLen) {

    long long result = prefix;

    if (!isEvenLen) {

        prefix = prefix / 10;

    }

    while (prefix > 0) {

        result = result * 10 + prefix % 10;

        prefix /= 10;

    }

    return result;

}

  

char* nearestPalindromic(char* n) {

    int len = strlen(n);

    if ( len == 1) {

        n[0] = (((n[0] - '0') - 1) + '0');

        return n;

    }

    char* returnString = malloc(len+3);

    bool isEvenLen = len % 2 == 0;

    int prefixLen = isEvenLen ? (len / 2) - 1 : len/2;

    char* prefixSub = malloc(prefixLen + 2);

    subStr(n, prefixSub, 0, prefixLen + 1);

    char* nEnd;

    long long prefix = strtoll(prefixSub, &nEnd, 10);

    long long combination[5] = {0};

  

    combination[0] = getPalindrome(prefix, isEvenLen);

    combination[1] = getPalindrome(prefix - 1, isEvenLen);

    combination[2] = getPalindrome(prefix + 1, isEvenLen);

    combination[3] = (long long) ( pow(10, len - 1) - 1);

    combination[4] = (long long) ( pow(10, len) + 1);

  

    long long diff = INT64_MAX, result = 0, origNum = strtol(n, &nEnd, 10);

    for ( int i = 0; i < 5; i++) {

        long long currDiff = origNum - combination[i];

        currDiff = ABS(currDiff);

        if (!currDiff) {

            continue;

        } else if ( currDiff == diff && combination[i] > result) {

            continue;

        } else if (MIN(currDiff, diff) == currDiff) {

            result = combination[i];

            diff = currDiff;

        }

    }    

    sprintf(returnString, "%lld", result);

    free(prefixSub);

    return returnString;

}
```