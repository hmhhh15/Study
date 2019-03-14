>### 문제 : https://www.acmicpc.net/problem/10989
````c
#include <stdio.h>

int main()
{
    /*
        N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.
        첫째 줄에 수의 개수 N(1 ≤ N ≤ 10,000,000)이 주어진다. 
        둘째 줄부터 N개의 줄에는 숫자가 주어진다. 이 수는 10,000보다 작거나 같은 자연수이다.
        첫째 줄부터 N개의 줄에 오름차순으로 정렬한 결과를 한 줄에 하나씩 출력한다.
    */
    
    int N;
    int cnt[10001] = { 0, };
    int temp = 0;

    scanf("%d",&N);
    for (size_t i = 0; i < N; i++)
    {
        scanf("%d", &temp);
        cnt[temp]++;
    }

    for (size_t i = 1; i <= 10000; i++)
    {
       if(cnt[i] > 0)
        {
           for (size_t j = 0; j < cnt[i]; j++)
           {
               printf("%d\n", i);
           }
        }
    }
    
    return 0;
}
````
> 