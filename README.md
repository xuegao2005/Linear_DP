![image-20250609182424326](https://github.com/xuegao2005/Linear_DP/blob/main/image-20250609182424326.png)

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

const int N = 510;

int n;
int a[N][N];
int f[N][N];

int main()
{
  scanf("%d", &n);
  for (int i = 1; i <= n; i ++ )
    for (int j = 1; j <= i; j ++)
      scanf("%d", &a[i][j]);

  for (int i = 0; i <= n; i ++ )
    for (int j = 0; j <= i + 1; j ++)
      f[i][j] = 0; // 初始化

  f[1][1] = a[1][1]; // 起点
  for (int i = 2; i <= n; i ++ )
    for (int j = 1; j <= i; j ++ )
      f[i][j] = max(f[i - 1][j - 1] + a[i][j], f[i - 1][j] + a[i][j]);

  int ans = 0; // 初始化答案
  for (int i = 0; i <= n; i ++ ) ans = max(ans, f[n][i]);

  printf("%d\n", ans);
  return 0;
}
```



最长上升子序列

![image-20250609194720470](../assets/image-20250609194720470.png)

```cpp
#include <iostream>
#include <algorithm>

using namespace std;

const int N = 1010;

int n;
int a[N], f[N];

int main()
{

  scanf("%d", &n);

  for (int i = 0; i < n; i ++ ) scanf("%d", &a[i]);

  for (int i = 1; i <= n; i ++ )
  {
    f[i] = 1;
    for (int j = 1; j <= i; j++ )
      if (a[j] < a[i]) // 如果 a[j] 小于 a[i]，则可以将 a[j] 是该序列的一个元素
        f[i] = max(f[i], f[j] + 1);
  }
    
  int ans = 0;
  for (int i = 1; i <= n; i ++ ) ans = max(ans, f[i]);

  printf("%d\n", ans);

  return 0;
}
```

