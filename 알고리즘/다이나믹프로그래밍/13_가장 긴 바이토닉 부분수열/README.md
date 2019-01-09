>### 문제 : https://www.acmicpc.net/problem/11054
````c
#include <iostream>
#include <vector>
using namespace std;

int main()
{
	size_t size, max(0);
	vector<size_t> arr;
	vector<size_t> left;
	vector<size_t> right;

	cin >> size;

	arr.resize(size);
	left.resize(size,1);
	right.resize(size,1);

	for (size_t i = 0; i < size; i++)
	{
		size_t temp;
		cin >> temp;
		arr[i] = temp;
	}
	
	for (size_t i = 0; i < size; i++)
	{
		size_t lMax(0);

		for (size_t j = 0; j < i; j++)
		{
			if (arr[i] > arr[j] && left[j] > lMax)
			{
				lMax = left[j];
			}
		}
		left[i] = lMax + 1;
	}

	for (size_t i = size -1; i > 0; i--)
	{
		size_t RMax(0);

		for (size_t j = size -1; j > i; j--)
		{
			if (arr[i] > arr[j] && right[j] > RMax)
			{
				RMax = right[j];
			}
		}
		right[i] = RMax + 1;
	}

	for (size_t i = 0; i < size; i++)
	{
		size_t tempMax = left[i] + right[i] - 1;

		if (tempMax > max)
		{
			max = tempMax;
		}
	}
	cout << max;
	return 0;
}
````
> i를 마지막으로 왼쪽부터 증가부분수열 길이 left[i], 오른쪽부터 증가부분수열 길이 right[i], 두개 더해서 중복 i를 -1한 길이