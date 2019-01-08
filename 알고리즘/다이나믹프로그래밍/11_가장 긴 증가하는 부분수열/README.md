>### 문제 : https://www.acmicpc.net/problem/11053
````c
#include <iostream>
#include <vector>
using namespace std;

int main()
{
	ios_base::sync_with_stdio(false);

	int input;
	cin >> input;

	vector<int> d;		
	vector<int> arr;	//입력받을 배열
	int max(1);		//가장 긴 길이

	d.resize(input);
	arr.resize(input);

	for (int i = 0; i < input; i++)
	{
		int temp;
		cin >> temp;
		arr[i] = temp;
	}

	for (int i = 0; i < input; i++)
	{
		d[i] = 1;

		for (int j = 0; j < i; j++)
		{
			if (arr[i] > arr[j] && d[i] <= d[j])
			{
				d[i] = d[j] + 1;
			}
		}

		if (max < d[i])
			max = d[i];
	}
	cout << max << endl;
	return 0;
}
````
> d[i]는 좌측부터 i로 끝날 때의 최고 길이, 좌측에 i보다 작은 값이 있다면 max ++
