#include<iostream>
#include<conio.h>
using namespace std;
struct num
{
	int a[3][3];
	int x;
	int y;
}T;
void init(num &T)
{
	cout << "" << endl;
	for (int i = 0;i<3;i++)
	{
		for (int j = 0; j < 3; j++)
			cin >>T. a[i][j];
	}
}
void show(num T)
{
	cout << "------------" << endl;
	for (int i = 0; i < 3; i++)
	{
		cout << "  ";
		for (int j = 0; j < 3; j++)
			cout<<T.a[i][j]<<"  ";
		cout << endl;
	}
	cout << "------------" << endl;
}

void getzero(num &T)
{
	int get = 0;
	for (int i = 0; i < 3; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			if (T.a[i][j] == 0)
			{
				T.x = i;
				T.y = j;
				get = 1;
				break;
			}
		}
		if (get)
			break;
	}
}
void change(num& T, int x1, int y1, int x2, int y2)
{
	int t;
	t = T.a[x1][y1];
	T.a[x1][y1] = T.a[x2][y2];
	T.a[x2][y2] = t;
}
void move(num &T)
{
	getzero(T);
	char ch;
	ch = _getch();
	switch (ch)
	{
	case 'A':
		if (T.y > 0)
		{
			change(T, T.x, T.y, T.x, T.y-1);
			show(T);
		}
		break;
	case'D':
		if (T.y < 2)
		{
			change(T, T.x, T.y, T.x, T.y+1);
			show(T);
		}
		break;
	case'W':
		if (T.x > 0)
		{
			change(T, T.x, T.y, T.x-1, T.y);
			show(T);
		}
		break;
	case'S':
		if (T.x < 2)
		{
			change(T, T.x, T.y, T.x+1, T.y);
			show(T);
		}
		break;
	}
}
void win(num T)
int main()
{
	init(T);
	show(T);
	for (int i = 0; i < 10; i++)
		move(T);
	return 0;
}
