# terminology
- connected : 每個點之間都有 path 連接 
# Q1 : G is planar graph
- 證明這些線段不可能相交於內點
- by contradiction, 假設有兩條邊 ab, cd 相交於內點 O
	- |ab| = |cd| = 1
# Q2 : 再用 planar graph 的邊數估計
- 設 G 有 n 個頂點、m 條邊
- 假設原來有 k 個連通分支，則只需要再補 k-1 條邊，就可以形成連通圖
	- 一樣是 n 個頂點、m + (n-1) 條邊
- 由 Euler's formula 的推論可以知道 (n>3)
	- m + (k-1) $\leq$ 3n - 6
	- m $\leq$ 3n - 6 - (k-1) $\leq$ 3n
