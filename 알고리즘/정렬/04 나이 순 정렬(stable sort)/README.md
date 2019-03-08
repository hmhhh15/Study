>### 문제 : https://www.acmicpc.net/problem/10814
````c
#include <iostream>
#include <string>
#include <vector>
using namespace std;

struct Member
{
    int age;
    string name;
};

void Merge(vector<Member> &list, vector<Member> &temp, int start, int end, int mid)
{
    int i = start;
    int j = mid + 1;
    int k = start;
    
    while (i <= mid && j <= end)
    {
        if (list[i].age <= list[j].age)
            temp[k++] = list[i++];
        else
            temp[k++] = list[j++];
    }

    while (i <= mid)
        temp[k++] = list[i++];

    while (j <= end)
        temp[k++] = list[j++];
    
    for (int r = start; r <= end; r++)
    {
        list[r] = temp[r];
    }
}

void Sort(vector<Member> &list, vector<Member> &temp, int start, int end)
{
    if (start == end) return;

    int mid = (start + end) / 2;
    Sort(list, temp, start, mid);
    Sort(list, temp, mid + 1, end);
    Merge(list, temp, start, end, mid);
}

int main()
{
    /*
       온라인 저지에 가입한 사람들의 나이와 이름이 가입한 순서대로 주어진다. 이때, 회원들을 나이가 증가하는 순으로, 
       나이가 같으면 먼저 가입한 사람이 앞에 오는 순서로 정렬하는 프로그램을 작성하시오.
       첫째 줄에 온라인 저지 회원의 수 N이 주어진다. (1 ≤ N ≤ 100,000)
       둘째 줄부터 N개의 줄에는 각 회원의 나이와 이름이 공백으로 구분되어 주어진다. 
       나이는 1보다 크거나 같으며, 200보다 작거나 같은 정수이고, 이름은 알파벳 대소문자로 이루어져 있고, 
       길이가 100보다 작거나 같은 문자열이다. 입력은 가입한 순서로 주어진다.
       첫째 줄부터 총 N개의 줄에 걸쳐 온라인 저지 회원을 나이 순, 
       나이가 같으면 가입한 순으로 한 줄에 한 명씩 나이와 이름을 공백으로 구분해 출력한다.
    */
    int N;
    cin >> N;

    vector<Member> vlist(N);
    vector<Member> vTemp(N);

    for (int i = 0; i < N; i++)
    {
        cin >> vlist[i].age >> vlist[i].name;
    }

    Sort(vlist, vTemp, 0, N - 1);

    for (int i = 0; i < N; i++)
    {
        cout << vlist[i].age << " " << vlist[i].name << "\n";
    }

    return 0;
}
//////////////////////////////// stable_sort 이용한 방법 //////////////////////////////////
#include <iostream>
#include <algorithm>
#include <string>
#include <vector>
using namespace std;

struct Member
{
    int age;
    string name;
};

bool cmp(const Member &a, const Member &b)
{
    return a.age < b.age;
}

int main()
{
    /*
       온라인 저지에 가입한 사람들의 나이와 이름이 가입한 순서대로 주어진다. 이때, 회원들을 나이가 증가하는 순으로, 
       나이가 같으면 먼저 가입한 사람이 앞에 오는 순서로 정렬하는 프로그램을 작성하시오.
       첫째 줄에 온라인 저지 회원의 수 N이 주어진다. (1 ≤ N ≤ 100,000)
       둘째 줄부터 N개의 줄에는 각 회원의 나이와 이름이 공백으로 구분되어 주어진다. 
       나이는 1보다 크거나 같으며, 200보다 작거나 같은 정수이고, 이름은 알파벳 대소문자로 이루어져 있고, 
       길이가 100보다 작거나 같은 문자열이다. 입력은 가입한 순서로 주어진다.
       첫째 줄부터 총 N개의 줄에 걸쳐 온라인 저지 회원을 나이 순, 
       나이가 같으면 가입한 순으로 한 줄에 한 명씩 나이와 이름을 공백으로 구분해 출력한다.
    */
    int N;
    cin >> N;

    vector<Member> vlist(N);

    for (int i = 0; i < N; i++)
    {
        cin >> vlist[i].age >> vlist[i].name;
    }

    stable_sort(vlist.begin(), vlist.end(), cmp);

    for (int i = 0; i < N; i++)
    {
        cout << vlist[i].age << " " << vlist[i].name << "\n";
    }

    return 0;
}
````
> 순서도 유지해야되는 정렬을 생각해서 합병정렬을 사용해보았고, 나중에 stable_sort라는것도 있단걸 알았다.