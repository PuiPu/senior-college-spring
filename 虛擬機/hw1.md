## Q1
```
Please describe the key applied fields with level of abstraction and virtualization. Comparing the same and difference for these two approaches.
```
1. difference
	1. virtualization may hide the detail of low-level
	2. virtualization may not hide 
[[VM - { hw1.1 }]]


## Q2
```
請圖解敘述 Goldberg 對虛擬化之 Formal description.
```
![[Pasted image 20260403165222.png]]
1. construction of an isomorphism : map a virtual guest system to real host
2. state mapping function $V$
	1. map guest system states $S_i$ to host system states $S_i'$
	2. including registers, memory, files resource mapping
3. guest operation $e$
	1. in guest system, execute a sequence of operations (ex. an instruction), transform from state $S_i$ to $S_j$
4. host operation $e'$
	1. in host system, execute a sequence of operations (ex. 模擬指令 or system call), transform from $S_i'$ to $S_j'$
5. formal definition logic requirement
	> 成功的 virtualization 必須滿足 $e' \: \circ \: V(S_i) = V \: \circ \: e(S_i)$
	- **路徑 A**：先將客體狀態 Si​ 透過 V 映射到主體，再執行主體操作 e′。
	- **路徑 B**：先在客體執行操作 e 改變狀態，再透過 V 映射到主體。
	- **結論**：無論走哪條路徑，最終在主體系統上產生的狀態結果必須是**等效**的
## Q3
```
請圖示 Computer System Architecture 有那些 implementation layer
提供那些 interface 被常應用於 Virtual Machine?
```
![[Pasted image 20260403180123.png]]
1. implementation layer
	1. application
	2. library
	3. operation system
	4. execution 
	5. memory/IO/Bus
[[VM - { hw1.3 }]]

## Q4
```
對 Process VM, High Level Language VM, Hosted System VM, Whole System VM, Co-designed VM 簡述其各別的範例與其應用.
```
1. process VM
	1. example : Digital FX!32、IA-32 EL、Aries
	2. implement : 
		1. 跨平台的軟體相容性 (portable)
2. high level language VM
	1. example : java virtual machine (JVM)、Microsoft .NET CLI、Pascal P-code VM
	2. implement :
		1. 完全平台獨立性 & 網路計算安全
3. hosted system VM
	1. example : VMware workstation / GSX server、virtual PC
	2. implement
		1. 多作業系統環境測試
4. whole system VM
	1. example : virtual PC 於 Macintosh 平台 (在 PowerPC 硬體上執行完整的 windows 系統及應用程式)
	2. implement
		1. 常用於非相容硬體上的模擬完整電腦環境
5. co-designed VM
	1. example : Transmeta Crusoe、IBM AS/400(iSeries)、IBM Daisy 研究系統
	2. implement
		1. 硬體與虛擬軟體 (VMM) 同步開發
		2. 高效能、低功耗或設計簡化
[[VM - { hw1.4 }]]
## Q5
```
Interpretation 技術被分類為那幾種方式 ? 請比較列出各方式及其優缺點.
```
1. decode and dispatch interpretation
2. indirect threaded interpretation
3. predecoding
4. direct threaded interpretation
[[VM - { hw1.5 }]]

## Q6
```
簡述 Dynamic Binary Translation 的架構與執行流程, 比起 interpretation 兩者在效率上的差距來自何處?
```
1. dynamic binary translation component
	1. Emulation Manager, EM
	2. Interpreter
	3. Translator
	4. code cache
	5. map table
	6. map table
	7. profile database
2. execution flow
	1. 初始詮釋
	2. 熱點偵測
	3. 轉換與快取
	4. 直接執行
	5. 連結與最佳化
3. 效能差距來源
> 翻譯技術在 steady-state 效能大幅領先詮譯技術，主因如下
	1. 執行媒介不同
	2. 記憶體架構壓力
	3. 最佳化機會
[[VM - { hw1.6 }]]
## Q7
```
請簡述 shade simulation tool 與 emulation 的關係, 她使用那種技術提升性能?
```
1. Shade 與 Emulation 關係
	1. 模擬是核心組件
	2. ISA 翻譯
	3. 低優化需求
2. Shade 提升性能技術
	1. Trace Cache (TC)
	2. 暫存器永久映射
	3. chaining
	4. 優化 TLB
	5. 簡單快取管理
[[VM - { hw1.7 }]]
## Q8
```
決定 compatibility 有那些條件? 請用 isomorphism 圖示 說明 Process VM 如何進行可達到相容性?
```
1. 決定相容性的主要條件
	1. 相容性層級
		1. 本質相容性 (intrinsic compatibility)
		2. 外在相容性 (extrinsic compatibility)
	2. 充分相容條件 (sufficient conditions)
		1. 控制移交點的狀態等效
		2. 回復執行點的狀態等效
2. isomorphism 圖示 ![[Pasted image 20260403165222.png]]
	1. **狀態對映** V
	2. **使用者指令模擬** e′(Si′​)
	3. **OS 呼叫模擬** e′(Sj′​)
[[VM - { hw1.8 }]]
## Q9
```
Process VM 使用 State Mapping 技術, 需考慮那些問題, 請列出解法
```
1. 暫存器狀態對應 (Register Mapping)
2. 記憶體位址空間對映 (Memory Address Space Mapping)
3. 安全與 runtime 保護問題
4. 例外與精確狀態回復 (Precise State Recovery)
[[VM - { hw1.9 }]]
## Q10
```
Exception 與 interrupt 如何被 emulation? 如何精確確定 guest state?

若使用 binary translation 如何定位出 program counter? 對Process VM若使用不同的OS, 如何實現 windows callback function ?
```
1. 例外與中斷模擬 (Emulation)
2. 精確課體狀態 (Precise Guest State) 的確定
3. 二進位翻譯中 Program Counter (PC) 的定位
4. process VM 中 Windows Callback function 的實現
[[VM - { hw1.10 }]]