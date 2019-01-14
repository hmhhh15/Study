>### 문제 : https://www.acmicpc.net/problem/2579
````c
#include <iostream>
#include <vector>
using namespace std;

int main()
{
	size_t size;
	vector<int> d;
	vector<int> arr;

	cin >> size;

	d.resize(size + 1);
	arr.resize(size + 1);

	for (size_t i = 1; i <= size; i++)
	{
		size_t temp;
		cin >> temp;
		arr[i] = temp;
	}

	d[1] = arr[1];
	d[2] = arr[1] + arr[2];

	for (size_t i = 3; i <= size; i++)
	{
		d[i] = d[i - 2] + arr[i];

		size_t dTemp = d[i - 3] + arr[i - 1] + arr[i];

		if (d[i] < dTemp)
			d[i] = dTemp;
	}

	cout << d[size];
	return 0;
}
````
> 마지막 계단을 밟았을 때 최대 점수 d[i], 한칸 전을 밟았을 때와 두칸전을 밟았을 때의 큰값 + 마지막 계단 값