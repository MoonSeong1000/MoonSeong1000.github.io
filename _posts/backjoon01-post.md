---
title: "백준-미로찾기"
date: 2019-07-26 18:00
categories: Algoritm
---

```class
baekjoon 미로찾기
```
```cpp
#include <iostream>
#include <algorithm>
#include <string>
#include <vector>
#include <stack>
#include <queue>
#include <deque>
using namespace std;

int N, M;
typedef pair<int, int> p;
int map[101][101];
bool visit[101][101];
queue<p> q;
int dx[4] = { -1,0,1,0 };
int dy[4] = { 0,1,0,-1 };
bool flag = false;
int check[101][101];

void search(int x, int y) {
	visit[x][y] = true;
	q.push(make_pair(x,y));
	check[0][0] = 1;
	while (!q.empty()) {
		p aa = q.front();
		cout << endl;
		x = aa.first;
		y = aa.second;
		if (x == N - 1 && y == M - 1) {
			break;
		}
		q.pop();
		for (int i = 0; i < 4; i++) {
			int nextX = x + dx[i];
			int nextY = y + dy[i];
			if (nextX < N && 0 <= nextX && nextY < M && 0 <= nextY) {
				if (visit[nextX][nextY] == false && map[nextX][nextY] == 1) {
					check[nextX][nextY] = check[x][y] + 1;
					visit[nextX][nextY] = true;
					q.push(make_pair(nextX, nextY));
				}
			}
		}
	}

	cout << check[N-1][M-1] << endl;
}

int main() {
	cin >> N >> M;
	for (int i = 0; i < N; i++) {
		for (int j = 0; j < M; j++) {
			scanf("%1d", &map[i][j]);
		}
	}
	
	search(0, 0);
}


```
