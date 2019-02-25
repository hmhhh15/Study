>### 문제 : https://www.acmicpc.net/problem/1676
````c
#include <stdio.h>

int factorialFiveNum(int n)
{
    if (n >= 5)
        return (n / 5) + factorialFiveNum(n / 5);
    else
        return 0;
}

int main()
{
    /*  
        N!에서 뒤에서부터 처음 0이 아닌 숫자가 나올 때까지 0의 개수를 구하는 프로그램을 작성하시오.
        첫째 줄에 N이 주어진다. (0 ≤ N ≤ 500)
        첫째 줄에 구한 0의 개수를 출력한다.
    */
    int N;
    
    scanf("%d", &N);

    printf("%d\n", factorialFiveNum(N));
    return 0;
}
````
> 0의 개수는 소인수분해시 5의 개수만 세면됨. n/5 + n/25 + n/125 ~