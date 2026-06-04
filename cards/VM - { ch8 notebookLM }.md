根據來源檔案（Chapter 8），以下是關於 **系統虛擬機器 (System Virtual Machines)** 的考試重點整理：

1. 系統虛擬機的核心概念與動機

- **定義**：系統虛擬機在單一主體平台上支援一個完整的客體作業系統及其所有應用程式。
- **主要應用動機**：
    - **系統軟體開發**：在獨立環境測試新系統，避免臭蟲導致整台機器崩潰。
    - **事件監控與封裝**：方便進行執行追蹤（Tracing）、狀態傾印（Dumping）以及檢查點（Checkpointing）以利環境遷移。
    - **資源管理**：透過時間分片（Time sharing）讓多個虛擬機共用物理資源，VMM 擁有最終控制權。

2. 虛擬化的充足條件：Popek & Goldberg 定理

這是 Chapter 8 最核心的理論部分：

- **指令分類**：
    - **特權指令 (Privileged)**：在使用者模式執行會產生 Trap 的指令。
    - **控制敏感指令 (Control-sensitive)**：企圖修改系統資源配置（如記憶體映射）的指令。
    - **行為敏感指令 (Behavior-sensitive)**：執行結果取決於資源配置（如處理器模式）的指令。
- **定理 1 (Theorem 1)**：若一個指令集架構 (ISA) 的**敏感指令是特權指令的子集**，則該架構是可（有效）虛擬化的。
- **關鍵指令 (Critical Instructions)**：指那些「敏感但非特權」的指令。這類指令在虛擬機中執行不會觸發 Trap，導致 VMM 無法攔截與模擬，是硬體設計上的障礙。

3. 資源虛擬化技術

**A. 處理器虛擬化 (Processor Virtualization)**

- **處理非虛擬化架構**：對於像 IA-32 這種含有關鍵指令的架構，需使用以下技術：
    - **補丁技術 (Patching)**：掃描二進碼並將關鍵指令替換為 Trap 或 Jump。
    - **模擬碼快取 (Caching Emulation Code)**：將關鍵指令周邊區塊翻譯成模擬常式並快取，以提升效能。
- **遞歸虛擬化 (Recursive Virtualization)**：在虛擬機中再執行 VMM。條件是系統必須可虛擬化且 VMM 不具備時間依賴性。

**B. 記憶體虛擬化 (Memory Virtualization)**

- **陰影分頁表 (Shadow Page Tables)**：客體 OS 維護「虛擬到真實 (V-to-R)」映射，而 VMM 維護「虛擬到物理 (V-to-P)」的陰影表，硬體實際使用後者進行地址轉換。
- **TLB 虛擬化**：在具備架構化 TLB 的系統中，VMM 透過映射真實 ASID (Address Space ID) 來區分不同虛擬機的地址空間，避免頻繁清除 TLB。

**C. I/O 虛擬化 (I/O Virtualization)**

- **設備類型**：分為專用 (Dedicated)、分割 (Partitioned)、共享 (Shared) 或列隊 (Spooled) 設備。
- **虛擬化層次**：可以在系統呼叫、驅動程式或操作層級（I/O Bus）進行攔截模擬。

4. 硬體輔助技術 (Hardware Assists)

為了減少 VMM 的軟體負擔：

- **IEF (Interpretive Execution Facility)**：IBM 提出，透過 **SIE 指令** 讓硬體直接執行大部分客體操作，只有在必要時（如 I/O 或異常）才「退出 (Exit)」回 VMM。
- **Intel VT-x (Vanderpool)**：引入 **VMX 根/非根操作模式**。客體作業系統可運行在 Ring 0 而非被壓縮至 Ring 1/3，解決了特權級壓縮問題。
- **VMCS (Virtual Machine Control Structure)**：VT-x 用來自動管理與保存虛擬機架構狀態的硬體資料結構。

5. 虛擬機類型比較

- **原生型 (Native)**：VMM 直接運行在硬體之上。
- **裝載型 (Hosted)**：VMM 運行在主體 OS 之上（如早期 VMware），優點是能利用主體 OS 的設備驅動程式。