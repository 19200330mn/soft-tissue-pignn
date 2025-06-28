---
date: 2025-06-28
aliases:
  - GNN-PINN
---
# <mark style="background: #BBFABBA6;">模型训练中能量计算差异：势能计算函数需重构</mark>
## <mark style="background: #ADCCFFA6;">本构关系计算体系不兼容：</mark>
- <mark style="background: #CACFD9A6;">超弹性模型（基于 F）</mark>
	![[Pasted image 20250628150342.png]]
- <mark style="background: #CACFD9A6;">线弹性模型（基于 ϵ）</mark>
	![[Pasted image 20250628150405.png]]
- 两类模型能量表达式需要传入的参数不同，无法直接替换。
	- 线弹性模型
		![[Pasted image 20250628150423.png]]
	- 超弹性模型
		![[Pasted image 20250628150509.png]]
## <mark style="background: #ADCCFFA6;">需要改变utils_potential_energy.py计算内部能量的方式</mark>
- 返回变形梯度F（超弹性模型需传入的参数）的函数
	![[Pasted image 20250628150648.png]]
- 计算总势能
	![[Pasted image 20250628150716.png]]
	
# <mark style="background: #BBFABBA6;">模型评估中计算误差</mark>
## <mark style="background: #ADCCFFA6;">需要修改utils_evaluation.py的评估体系</mark>
- <mark style="background: #CACFD9A6;">超弹性体系下的模型评估</mark>
	![[Pasted image 20250628150840.png]]
