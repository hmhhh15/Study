>### 문제 : https://www.acmicpc.net/problem/2745
````c
#include <stdio.h>
#include <string.h>

int main()
{
    char N[35] = "";
    int B, result = 0;

    scanf("%s %d", N, &B);
    int len = strlen(N);
    
    for (int i = 0; i < len; i++)
    {
        if (N[i] > '9')
            result = result * B + N[i] - 'A' + 10;
        else
            result = result * B + N[i] - '0';
    }

    printf("%d\n", result);

    return 0;
}

````
> 앞에 숫자부터 진법 수를 곱해가며 ++