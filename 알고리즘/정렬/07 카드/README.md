>### 문제 : https://www.acmicpc.net/problem/11652
````c
#include <stdio.h>
#include <map>
using namespace std;

int main()
{
    /*
        준규는 숫자 카드 N장을 가지고 있다. 숫자 카드에는 정수가 하나 적혀있는데,
        적혀있는 수는 -2^62보다 크거나 같고, 2^62보다 작거나 같다.
        준규가 가지고 있는 카드가 주어졌을 때, 가장 많이 가지고 있는 정수를 구하는 프로그램을 작성하시오. 
        만약, 가장 많이 가지고 있는 정수가 여러 가지라면, 작은 것을 출력한다.
        첫째 줄에 준규가 가지고 있는 숫자 카드의 개수 N (1 <= N <= 1000000)이 주어진다. 
        둘째 줄부터 N개 줄에는 숫자 카드에 적혀있는 정수가 주어진다.
        첫째 줄에 준규가 가장 많이 가지고 있는 정수를 출력한다.
    */

    int N;
    scanf("%d", &N);
    map<long long, int> m;

    while (N--)
    {
        long long temp;
        scanf("%lld", &temp);
        m[temp] += 1;
    }
    
    int cnt = 0;
    long long ans = (*m.begin()).first;

    for (auto p : m)
    {
        if (p.second > cnt)
        {
            ans = p.first;
            cnt = p.second;
        }
        else if (p.second == cnt && p.first < ans)
        {
            ans = p.first;
        }
    }

    printf("%lld", ans);
    
    return 0;
}
````
> 