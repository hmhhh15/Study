>### 문제 : https://www.acmicpc.net/problem/11653
````c
#include <stdio.h>
#include <vector>

int main()
{
    /*  
        정수 N이 주어졌을 때, 소인수분해하는 프로그램을 작성하시오.
        첫째 줄에 정수 N (1 ≤ N ≤ 10,000,000)이 주어진다.
    */
    
    int N;
    scanf("%d", &N);

    for (int i = 2; i*i <= N; i++)
    {
        while (N % i == 0)
        {
            printf("%d\n", i);
            N /= i;
        }
    }
    //나머지 소수 프린트
    if (N > 1)
        printf("%d\n", N);

    return 0;
}

````
> 에라토스네네스 체를 사용하여 소수인 경우만 나누는 식으로 짜보았으나 느렸고, 소수를 굳이 구하지 않아도 이 방법으로 빠르게 구할 수 있었다. 