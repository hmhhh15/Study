>### 문제 : https://www.acmicpc.net/problem/11005
````c
#include <stdio.h>

int main()
{
    int N, B;
    char str[35] = "";
    scanf("%d %d", &N, &B);

    int i = 0;
    while (N)
    {
        char temp = N % B + '0';

        if (temp > '9')
            temp += 7;

        str[i] = temp;
        N /= B;
        i++;
    }

    for (; i > 0; i--)
    {
        printf("%c", str[i - 1]);
    }

    return 0;
}

````
> 