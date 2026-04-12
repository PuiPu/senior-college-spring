# termonolgy
- $deg(V_i) = d_i$

# Q1 : prove is even
1. handshaking theorem : $\Sigma^{n}_{i=1} d_i = \Sigma^{n}_{i=1}deg(v_i) = 2|E(G)|$
2. 所以 $\Sigma^{n}_{i=1}d_i$ 是 even
# Q2 : prove Erdős–Gallai 不等式
- $\Sigma^{n}_{i=1} d_i$ 為各頂點度數總和
- 把度數總和分成兩邊來看
	- $S$ 內部的邊，每條邊會對度數總和貢獻 2 
	- S 與 $V(G) \backslash S$ 之間的邊，每條邊會對度數總和貢獻 1
- 因此，$\Sigma^{k}_{i=1} d_i = 2 \cdot e(S) + e(S, V(G) \backslash S)$
- 估計 $2 \cdot e(S)$
	- 因為 G 是 "simple graph"，$S$ 中最多只有 $\dbinom{k}{2}$ 條邊
	- $e(S) \leq \dbinom{k}{2}$
	- $2 \cdot e(S) \leq (k)(k-1)$
- 分析 $e(S, V(G) \backslash S)$
	- 對每個 $i > k$ ，頂點 