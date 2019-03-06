>### 문제 : https://www.acmicpc.net/problem/11650
````c
#include <stdio.h>

struct point
{
    int x;
    int y;
};

void swap(point &a, point &b)
{
    point temp = a;
    a = b;
    b = temp;
}

point list[100000];

int partition(int left, int right)
{
    int mid = (left + right) / 2;
    point pivot = list[mid];
    int low = left;

    swap(list[mid], list[right]);

    for (int i = left; i < right; i++)
    {
        if (list[i].x < pivot.x)
        {
            swap(list[i], list[low]);
            low++;
        }
        else if (list[i].x == pivot.x)
        {
            if (list[i].y < pivot.y)
            {
                swap(list[i], list[low]);
                low++;
            }
        }
    }
    swap(list[low], list[right]);
    return low;
}

void quickSort(int left, int right)
{
    if (left < right)
    {
        int mid = partition(left, right);
        quickSort(left, mid - 1);
        quickSort(mid + 1, right);
    }
}

int main()
{
    /*
        2차원 평면 위의 점 N개가 주어진다. 좌표를 x좌표가 증가하는 순으로,
        x좌표가 같으면 y좌표가 증가하는 순서로 정렬한 다음 출력하는 프로그램을 작성하시오.
        첫째 줄에 점의 개수 N (1 ≤ N ≤ 100,000)이 주어진다.
        둘째 줄부터 N개의 줄에는 i번점의 위치 xi와 yi가 주어진다. (-100,000 ≤ xi, yi ≤ 100,000)
        좌표는 항상 정수이고, 위치가 같은 두 점은 없다.
        첫째 줄부터 N개의 줄에 점을 정렬한 결과를 출력한다.
    */
    int N;
    scanf("%d", &N);
    for (int i = 0; i < N; i++)
    {
        scanf("%d %d", &list[i].x, &list[i].y);
    }

    quickSort(0, N - 1);

    for (int i = 0; i < N; i++)
    {
        printf("%d %d\n", list[i].x, list[i].y);
    }
    return 0;
}
//////////////////////////////// pair 이용한 방법 //////////////////////////////////
#include <stdio.h>
#include <algorithm>
#include <vector>
using namespace std;

int main()
{
    /*
        2차원 평면 위의 점 N개가 주어진다. 좌표를 x좌표가 증가하는 순으로, 
        x좌표가 같으면 y좌표가 증가하는 순서로 정렬한 다음 출력하는 프로그램을 작성하시오.
        첫째 줄에 점의 개수 N (1 ≤ N ≤ 100,000)이 주어진다. 
        둘째 줄부터 N개의 줄에는 i번점의 위치 xi와 yi가 주어진다. (-100,000 ≤ xi, yi ≤ 100,000) 
        좌표는 항상 정수이고, 위치가 같은 두 점은 없다.
        첫째 줄부터 N개의 줄에 점을 정렬한 결과를 출력한다.
    */
    int n;
    scanf("%d", &n);
    vector<pair<int, int>> a(n);
    for (int i = 0; i < n; i++) 
    {
        scanf("%d %d", &a[i].first, &a[i].second);
    }

    sort(a.begin(), a.end());

    for (int i = 0; i < a.size(); i++) 
    {
        printf("%d %d\n", a[i].first, a[i].second);
    }
    return 0;
}
````
> 메모리는 퀵소트를 이용한 방법이 더 적었다.