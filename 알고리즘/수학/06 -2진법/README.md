>### 문제 : https://www.acmicpc.net/problem/2089
````c
#include <stdio.h>
#include <math.h>

int main()
{
    int N;
    char str[100] = "";

    scanf("%d", &N);

    //0시작이면 0출력
    if (N == 0)
    {
        printf("0\n");
        return 0;
    }

    int i = 0;

    while (1)
    {
        if (N == 1)
        {
            str[i] = '1';
            break;
        }

        if (N == -1)
        {
            str[i] = '1';
            i++;
            str[i] = '1';
            break;
        }

        int temp = abs((N) % (-2));

        str[i] = '0' + temp;

        if (temp && N < 0)
        {
            N = (N - 1) / (-2);
        }
        else
        {
            N /= (-2);
        }

        i++;
    }

    //뒤에서부터 출력
    for (; i >= 0; i--)
    {
        printf("%c", str[i]);
    }
    printf("\n");

    return 0;
}

````
> 음수인경우 나머지가 있을시 다르게 처리를 해주어야했다. 뒤부터 출력하기위해 <string.h> 추가하고 strrev를 써봤지만, 알고리즘 프로그램에서 인식못해 에러가 나서 변경.