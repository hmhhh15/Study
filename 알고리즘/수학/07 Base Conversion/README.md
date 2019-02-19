>### 문제 : https://www.acmicpc.net/problem/11576
````c
#include <stdio.h>
#include <vector>
using namespace std;

void BaseConversion(int num, int base)
{
    vector<int> vTemp;

    while (num)
    {
        vTemp.push_back(num % base);
        num /= base;
    }

    for (size_t i = vTemp.size(); i > 0; i--)
    {
        printf("%d ", vTemp[i - 1]);
    }
}

int main()
{
    int A, B, size, num = 0;

    scanf("%d %d", &A, &B);
    scanf("%d", &size);

    vector<int> vA;
    vA.resize(size);

    for (size_t i = 0; i < size; i++)
    {
        scanf("%d",&vA[i]);
    }

    for (size_t i = 0; i < size; i++)
    {
        num = num * A + vA[i];
    }

    BaseConversion(num, B);

    return 0;
}

````
> 