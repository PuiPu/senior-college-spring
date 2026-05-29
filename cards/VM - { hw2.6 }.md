# Question
簡介何謂 recursive virtualization(遞歸虛擬化)? Popek and Goldberg 對傳統第三代計算機要實現 recursive virtualization 需要那些條件?
# Answer
**遞歸虛擬化 (Recursive Virtualization)** 是指在一台虛擬機器中再次執行虛擬機器系統的技術。簡單來說，這意味著虛擬機器監視器 (VMM) 本身作為一個虛擬機器，在另一個處於特權模式 (Privileged mode) 的 VMM 控制下，運行於使用者模式 (User mode)。

根據 **Popek and Goldberg** 的研究，針對傳統第三代計算機實現遞歸虛擬化，需滿足以下兩大核心條件（正式定義於其第二定理）：

1. **系統必須是可虛擬化的 (Virtualizable)**：該計算機架構必須首先滿足其第一定理，即所有的敏感指令 (Sensitive instructions) 都必須是特權指令 (Privileged instructions)，確保 VMM 能夠攔截所有關鍵操作。
2. **必須能建構出無時間依賴性 (No timing dependences) 的 VMM**：
    - 由於 VMM 運行在另一個虛擬機器中，效能可能會受到影響。
    - 如果 VMM 的行為依賴於精確的時間關係（例如計時器），當其在使用者模式下執行時，效能的波動可能導致其行為與原生平台不一致，從而違反虛擬化的「等效性 (Equivalence)」原則。

**Popek and Goldberg 的第二定理 (Theorem 2)** 總結如下： 一個傳統第三代計算機是可遞歸虛擬化的，若且唯若：

- (a) 它是可虛擬化的。
- (b) 可以為其建構一個沒有任何時間依賴性的 VMM。

在實際應用中，遞歸虛擬化通常很少超過兩層，因為每一層 VMM 都會消耗系統資源（特別是記憶體），隨著層數增加，可用資源會迅速萎縮。