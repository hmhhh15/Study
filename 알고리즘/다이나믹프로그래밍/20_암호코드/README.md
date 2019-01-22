>### 문제 : https://www.acmicpc.net/problem/2011
````c
#include <stdio.h>
#include <string.h>

int main()
{
    char str[5001];
    size_t d[5001] = { 1, };
    size_t mod = 1000000;
    scanf("%s", str);

    size_t len = strlen(str);
    
    //시작이 0이면 검사 필요x
    if (str[0] == '0')
    {
        printf("0");
        return 0;
    }

    if (str[len - 1] == '0')
        d[1] = 0;
    else
        d[1] = 1;

    for (size_t i = 2; i <= len; i++)
    {
        size_t left = str[len - i];
        size_t right = str[len - i + 1];

        if (left > '2' && right == '0')
        {
            printf("0"); return 0;
        }

        if (left == '0')
        {
            d[i] = 0; continue;
        }

        d[i] = d[i - 1];

        if (left == '1' || left == '2' && right < '7')
        {
            d[i] = (d[i - 1] + d[i - 2]) % mod;
        }
    }

    printf("%d", d[len]);

	return 0;
}
````
> d[i]는 뒤에서 i번째 단어로 시작하는 해석 가짓 수