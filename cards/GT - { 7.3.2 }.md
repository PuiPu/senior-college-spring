# terminology
- regular graph (正則圖)
	- 5-regular graph 代表每個點的 degree 都是 5
- Turan's thorem
- 用到的性質 ![[Pasted image 20260413195516.png]]

# 問題
1. 有 14 個 members 要玩 bridge(橋牌)
2. 規定 4 個人彼此不能有任何人是彼此搭檔過的，才能開始進行一局遊戲
3. at one meeting, 每個人都已經跟 5 個人搭檔過了
4. 現在來了一個新搭檔，證明至少還有一局可以玩
# 化減
1. 14 個 members 看成頂點，每個人都跟五個人搭檔過，也就是每個點的 degree = 5
2. 因此，G 是一個 14 個 vertices 的 5-regular graph
3. 現在有一個新成員 x 要加入，要證明至少可以一局可以進行
	1. 也就等於證明存在 3 個人彼此沒有搭檔過，加上一個新的 x 跟這 3 個人不認識，就可以進行新的一局
	2. 那證明 3 個人彼此沒搭檔過，就等於在 G 找一個 $K_3$ - free 的圖
4. 在 G 找一個 $K_3$ - free，等價於在 $\bar{G}$ 找三角形
	1. 考慮補圖 $\bar{G}$ ，那就是 (14-1)-5 = 8 regular graph (14 個 vertices 每個點最多只能跟自己除外的所有點 14-1=13 個連接)
5. 8 regular graph 的邊數為 |E($\bar{G}$)| = $\frac{14 \cdot 8}{2} = 56$ 
6. by Turan's theorem, 沒有三角形的 simple graph 最多 $\lfloor \frac{14^2}{4} \rfloor = 49$
7. 但是，56 > 49，所以在 $\bar{G}$ 有三角形
	1. 設三角形的點為 a,b,c，彼此互相連接
	2. 那也就是在 G 彼此不相連，在 G 存在大小為 3 的 independent set (亦即 3 人彼此都搭檔過)，再加上新會員 x 與原來任何人都不認識，所以 4 個人彼此沒有搭檔過