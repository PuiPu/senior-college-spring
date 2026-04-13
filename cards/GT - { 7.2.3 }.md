# terminology
- clique : simple graph, is a sunset S of V such that G[S] is complete
	- S is clique of G iff S is an independent set of $G^c$
- Ramsey number ?
	- r(k, l)
		- either, clique of k vertices
		- or, independent set of l vertices
# prove
![[Pasted image 20260413123109.png]]
1. by thm 7.7, we know $r_n = (3,3,...,3) \leq (2,3,...,3) + (3,2,...,3) + \cdots + (3,3,...,2) - n + 2$
2. $(2,3,...,3) = (3,2,...,3) = (3,3,...,2) = r_{n-1}$
3. $r_n \leq n \cdot r_{n-1} - n + 2 = n(r_{n-1} - 1) + 2$