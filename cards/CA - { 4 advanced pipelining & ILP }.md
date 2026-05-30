# ILP (Instruction Level Parallelism)
> 如果有 dependency 那也不能 parallelism (平行化)
- 核心概念 : 讓彼此沒有相依性的指令重疊執行 (overlap execution)
- 目的 : 
	- 提高
		- instruction overlap (這就是 pipeline 的核心精神)
		- CPU throughput
	- 降低
		- CPI
		- stall
# static v.s. dynamic scheduling
- static scheduling
	- compiler 事先安排
	- ex.
		- loop unrolling
		- instruction scheduling
- dynamic scheduling
	- hardware runtime 決定
	- ex.
		- scoreboard
		- tomasulo
	- 優點
		- runtime 才知道真正的 dependency
		- 可 out-of-order execution
# dependency
- Data dependency (true dependency)
- Name dependency
	- anti-dependence (WAR hazard)
	- output dependence (WAW hazard)
- control dependency
# 