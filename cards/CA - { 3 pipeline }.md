## DLX datapath
- 5 stages
	- IF : Instruction Fetch
	- ID : Instruction Decode
	- EX : Execute
	- MEM : Memory Access
	- WB : Write Back
- pipeline register
	- 每個 stage 中間都需要 register
	- 作用
		- 隔離不同 instruction
		- 保存中間結果
	- 例如
		- IF/ID
		- ID/EX
		- EX/MEM
		- MEM/WB
## hazard : limit to pipelining
- def: 讓下一個新的 clock cycle 的指令沒有辦法執行
- type
	- structural hazard
		- reason : 多條 instruction 同時搶同一硬體資源 (some combination of instructions cannot accommodated because of resource conflicts)
		- solution : stall (pipeline bubble)
	- data hazard
		- reason : 後面 instruction 需要前面 instruction 的結果 
		- type
			- RAW
				```
				add r1, r2, r3
				sub r4, r1, r2
				```
				- 還沒寫進去就要讀取
				- 最常見，最重要
			- WAR
				```
				sub r4, r1, r3
				add r1, r2, r3
				```
				- 後者太早寫
			- WAW
				```
				sub r1, r4, r3
				add r1, r2, r3
				```
				- 同時要寫同一個 register
				- DLX 不會出現 (writes are always in stage 5)
	- control hazard
		- reason : branch/jump
		- solution : 