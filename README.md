Roses are red
Violets are blue

```cpp
#include <iostream>
using namespace std;

int Max(int a,int b,int c = 0)
{
  if (a >= b && a >= c)return a;
	if (b >= a && b >= c)return b;
	return c;
}

int main()
{
	int row,col;	
	cin >> row >> col;
	
	int max[503][503];
	int wall;
	int m = 0;
	
	for(int i = 0; i < row; i++)
	{
		for(int j = 0; j < col; j++)
		{
			cin >> wall;
			if(i == 0)
			{
				max[i][j] = wall;
			}
			else
			{
				if(j == 0)
				{
					max[i][j] = Max(max[i-1][j],max[i-1][j+1]) + wall;
				}
				if (j == col-1)
				{
					max[i][j] = Max(max[i-1][j],max[i-1][j-1]) + wall;
				}
				else
				{
					max[i][j] = Max(max[i-1][j-1],max[i-1][j],max[i-1][j+1]) + wall;
				}
			}
			
			if (i == row-1)
			{
				m = Max(m,max[i][j]);
			}
		}
	}
	cout << m << endl;
	
	return 0;
}
```
