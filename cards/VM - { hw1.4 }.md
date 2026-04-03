根據來源檔案，以下為 Process VM、High-Level Language VM、Hosted System VM、Whole System VM 及 Co-designed VM 的範例與應用簡述：

1. 程序虛擬機器 (Process VM)

- **範例**：**Digital FX!32**（在 Alpha 平台上執行 Windows IA-32 應用程式）、**IA-32 EL**（在 Itanium 平台上支援 IA-32 程式）、**Aries**（支援 PA-RISC 程式於 Itanium 平台）。
- **應用**：主要提供跨平台的軟體相容性，允許原本為特定作業系統和指令集架構（ISA）編譯的二進制執行檔，在不同的主體平台上執行。此外，也應用於**同一架構的動態二進制最佳化**（如 HP Dynamo），在程式執行時即時提升效能。

2. 高階語言虛擬機器 (High-Level Language VM, HLL VM)

- **範例**：**Java 虛擬機器 (JVM)**、**Microsoft .NET 公用語言基礎架構 (CLI)**、早期的 **Pascal P-code VM**。
- **應用**：旨在實現完全的**平台獨立性**與網路計算安全。開發者只需將程式編譯成虛擬 ISA（如 Java bytecode），即可在任何安裝了該 HLL VM 的硬體/作業系統上執行，廣泛應用於網際網路應用程式、行動裝置及企業軟體開發。

3. 主體裝載系統虛擬機器 (Hosted System VM)

- **範例**：**VMware Workstation/GSX Server**、**Virtual PC**。
- **應用**：這種虛擬機安裝在現有的主體作業系統（如 Windows 或 Linux）之上，應用於**多作業系統環境測試**、軟體開發以及伺服器整合。其優勢在於能直接利用主體作業系統提供的裝置驅動程式，簡化硬體支援的複雜度。

4. 全系統虛擬機器 (Whole System VM)

- **範例**：**Virtual PC** 於 Macintosh 平台（在 PowerPC 硬體上執行完整的 Windows 系統及其應用程式）。
- **應用**：當主體與客體系統的作業系統與指令集完全不同時，虛擬化整個軟體堆疊（包含作業系統和所有應用程式）。這常用於在非相容硬體上模擬完整電腦環境，解決**遺留軟體支援**或跨平台辦公需求。

5. 共同設計虛擬機器 (Co-designed VM)

- **範例**：**Transmeta Crusoe**、**IBM AS/400 (iSeries)**、IBM Daisy 研究系統。
- **應用**：硬體與虛擬軟體（VMM）同步開發，用於**硬體架構創新**。例如，Transmeta 使用 VLIW 核心配合軟體模擬 IA-32 指令以降低功耗；IBM 則藉此維持軟體介面穩定，同時在底層自由更換硬體架構（如從專屬 CISC 轉向 PowerPC）。其核心目標通常是**高效能、低功耗或設計簡化**。