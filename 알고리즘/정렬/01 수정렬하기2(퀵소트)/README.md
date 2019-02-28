>### 문제 : https://www.acmicpc.net/problem/2751
````c
///////////////////////////////백 준 코 드///////////////////////////////////
#include <stdio.h>
#include <stdlib.h>

void swap(int &a, int &b)
{
    int temp = a;
    a = b;
    b = temp;
}

int partition(int* v, int left, int right)
{
    int mid = left + (right - left) / 2;
    int pivot = v[mid];
    swap(v[mid], v[right]);
    int low = left;
    for (int i = left; i < right; i++)
    {
        if (v[i] < pivot)
        {
            swap(v[i], v[low]);
            low++;
        }
    }
    swap(v[low], v[right]);
    return low;
}

void quicksort(int *v, int left, int right)
{
    if (left < right)
    {
        int mid = partition(v, left, right);
        quicksort(v, left, mid - 1);
        quicksort(v, mid + 1, right);
    }
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

    int *vList = (int*)malloc(sizeof(int) * N);
    
    for (int i = 0; i < N; i++)
    {
        scanf("%d", &vList[i]);
    }

    quicksort(vList, 0, N - 1);

    for (int i = 0; i < N; i++)
    {
        printf("%d\n", vList[i]);
    }

    free(vList);
    return 0;
}
///////////////////////////////시 간 초 과 코 드/////////////////////////////////
int partition(int *v, int left, int right)
{
    int pivot = v[left];
    int low = left;
    int high = right;

    while (low++ < high)
    {
        while (v[low] < pivot && low < right)
        {
            low++;
        }

        while (v[high] > pivot && high > left)
        {
            high--;
        }

        if (low < high)
            swap(v[low], v[high]);
    }
    swap(v[high], v[left]);

    return high;
}
````
> 백준 강의 코드와 인터넷 검색(https://gmlwjd9405.github.io/2018/05/10/algorithm-quick-sort.html)을 통해 수정한 코드 둘다 구현해 보았지만, 후자가 시간이 더 걸리나보다.