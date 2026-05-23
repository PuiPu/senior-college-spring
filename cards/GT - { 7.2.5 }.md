hard
設 G=C3∨C5G=C_3\vee C_5G=C3​∨C5​。

---

### (1) GGG 不含 K6K_6K6​

C3C_3C3​ 的 clique 最大為 3，C5C_5C5​ 的 clique 最大為 2（因無三角形）。  
join 後 clique 最大為

3+2=53+2=53+2=5

故不含 K6K_6K6​。

---

### (2) 任意 2-edge-colouring 皆有單色三角形

設 C3={a1,a2,a3}C_3=\{a_1,a_2,a_3\}C3​={a1​,a2​,a3​}，C5={b1,…,b5}C_5=\{b_1,\dots,b_5\}C5​={b1​,…,b5​}。

若 C3C_3C3​ 單色則完成。否則可設

a1a2, a2a3 紅,a1a3 藍.a_1a_2,\ a_2a_3 \text{ 紅},\quad a_1a_3 \text{ 藍}.a1​a2​, a2​a3​ 紅,a1​a3​ 藍.

對任一 bib_ibi​，為避免單色三角形，可得

bia2 必為藍.b_ia_2 \text{ 必為藍}.bi​a2​ 必為藍.

若某 bibi+1b_ib_{i+1}bi​bi+1​ 為藍，則

a2bibi+1a_2b_ib_{i+1}a2​bi​bi+1​

為藍三角形，矛盾。  
故 C5C_5C5​ 全為紅邊。

又每個 bib_ibi​ 至少有一條紅邊連到 a1a_1a1​ 或 a3a_3a3​，且相鄰兩點不能同時連到同一個（否則成紅三角形）。  
因此 b1,…,b5b_1,\dots,b_5b1​,…,b5​ 必須在兩類間交替，但 C5C_5C5​ 為奇圈，不可能，矛盾。

---

故任意 2-edge-colouring 必有單色三角形。

G 無 K6 且 G→(K3,K3)\boxed{G \text{ 無 } K_6 \text{ 且 } G \to (K_3,K_3)}G 無 K6​ 且 G→(K3​,K3​)​
