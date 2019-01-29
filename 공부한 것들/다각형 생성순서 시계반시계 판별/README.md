````c
#include <iostream>
#include <Windows.h>
#include <list>

//아래 코드를 리스트로 표현한 코드
bool isClockwise(list<POINT> lp)
{
    int sum = 0;
    auto p1 = lp.begin();
    for (auto p2 = ++lp.begin(); p2 != lp.end(); p2++)
    {
        sum += ((*p2).x - (*p1).x) * ((*p2).y + (*p1).y);
        p1++;
    }
    sum += (((*lp.begin()).x - lp.back().x)) * ((*lp.begin()).y + (lp.back()).y);
    return sum < 0; //윈도우 좌표는 y축이 반대
}

///////////////////////////////////////////////////////////

public bool IsClockwise(IList<Vector> vertices)
{
    double sum = 0.0;
    for (int i = 0; i < vertices.Count; i++) {
        Vector v1 = vertices[i];
        Vector v2 = vertices[(i + 1) % vertices.Count]; // % is the modulo operator
        sum += (v2.X - v1.X) * (v2.Y + v1.Y);
    }
    return sum > 0.0;
}

````
>https://stackoverflow.com/questions/1165647/how-to-determine-if-a-list-of-polygon-points-are-in-clockwise-order