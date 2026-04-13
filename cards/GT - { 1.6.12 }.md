## case 1 : uv $\notin$ E(G)
- 依照補圖的定義，uv $\in$ $G'$ 
	- $d_{G'}(u,v) = 1$
## case 2 : uv $\in$ E(G)
- 此時，uv 在 G' 中的距離至多 2
- 需先證明 : 必存在一點 w，使得 w 在 G 既不與 u 相鄰，也不跟 v 相鄰
	- if not, 則對每點頂點 x $\in$ V(G)，x 至少與 u, v 其中之一相鄰
		- x 與 u 或 v 之一相鄰
		- y 與 u 或 v 之一相鄰
		- 而且 u, v 本身相鄰
- 所以 x 到 y 必定存在一條長度至多 3 的路徑 (x-u-v-y)
	- diam(x,y) $\leq$ 3
	- 對所有的 x, y 都成立，故 diam(G) $\leq$ 3