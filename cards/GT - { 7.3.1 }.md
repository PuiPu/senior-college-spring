# terminology
- Turan's theorem
# A
- 這題就是要考 Turan's theorem 而已
- 題目有 9 個人
	- 1 個認識其他 2 人
	- 2 個認識其他 4 人
	- 4 個認識其他 5 人
	- 2 個認識其他 6 人
- 要 show 3 個人，彼此互相認識
- 化成圖來解
	- 9 個人 $\rightarrow$ 在 G 有 9 個 vertices
	- 只要認識，就會有一條 edge 連接
	- show 3 個人彼此互相認識 $\equiv$ G 裡有 三角形 存在
- degree sequence
	- 2, 4, 4, 5, 5, 5, 5, 6, 6
- sum of d(v) = 2 + 4 + 4 + 5 + 5 + 5 + 5 + 6 + 6 = 42
- 邊數 = |E(G)| = $\frac{42}{2} = 21$
- by Turan's theorem, 若有一個 9 個頂點的 simple graph 不含三角形，其邊數最多 $\lfloor  \frac{9^2}{4} \rfloor = 20$ 
- 但是 21 > 20，與不存在三角形矛盾，所以必定存在一個三角形，也就是存在3個人彼此相識