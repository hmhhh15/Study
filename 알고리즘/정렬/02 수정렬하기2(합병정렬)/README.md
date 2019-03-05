>### 문제 : https://www.acmicpc.net/problem/2751
````c
#include <stdio.h>
#include <stdlib.h>
int result[1000000];

void merge(int list[], int left, int right, int mid)
{
    int i = left;
    int j = mid + 1;
    int k = left;
    while (i <= mid && j <= right)
    {
        if (list[i] < list[j])
            result[k++] = list[i++];
        else
            result[k++] = list[j++];
    }
    while (i <= mid)
    {
        result[k++] = list[i++];
    }
    while (j <= right)
    {
        result[k++] = list[j++];
    }
    for (int r = left; r <= right; r++)
    {
        list[r] = result[r];
    }

}

void mergeSort(int a[], int left, int right)
{
    if (left == right) return;

    int mid = (left + right) / 2;
    mergeSort(a, left, mid);
    mergeSort(a, mid + 1, right);
    merge(a, left, right, mid);
}

int main()
{
    /*
        N개의 수가 주어졌을 때, 이를 오름차순으로 정렬하는 프로그램을 작성하시오.
        첫째 줄에 수의 개수 N(1 ≤ N ≤ 1,000,000)이 주어진다. 둘째 줄부터 N개의 줄에는 숫자가 주어진다.
        이 수는 절댓값이 1,000,000보다 작거나 같은 정수이다. 수는 중복되지 않는다.
        첫째 줄부터 N개의 줄에 오름차순으로 정렬한 결과를 한 줄에 하나씩 출력한다.
    */
    int N;
    scanf("%d", &N);

    int *a = (int*)malloc(sizeof(int) * N);

    for (int i = 0; i < N; i++)
    {
        scanf("%d", &a[i]);
    }

    mergeSort(a, 0, N - 1);

    for (int i = 0; i < N; i++)
    {
        printf("%d\n", a[i]);
    }

    return 0;
}
````
> 임시저장할 추가 공간이 따로 필요하다.