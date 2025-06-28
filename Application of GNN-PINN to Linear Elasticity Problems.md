---
date: 2025-06-28
aliases:
  - GNN-PINN
---

# **模型训练中能量计算差异：势能计算函数需重构**

## **本构关系计算体系不兼容：**
- **超弹性模型（基于 F）**  
  ![Pasted image 20250628150342](images/Pasted%20image%2020250628150342.png)
  
- **线弹性模型（基于 ϵ）**  
  ![Pasted image 20250628150405](images/Pasted%20image%2020250628150405.png)

- 两类模型能量表达式需要传入的参数不同，无法直接替换：
  - 线弹性模型  
    ![Pasted image 20250628150423](images/Pasted%20image%2020250628150423.png)
  - 超弹性模型  
    ![Pasted image 20250628150509](images/Pasted%20image%2020250628150509.png)

## **需要改变utils_potential_energy.py计算内部能量的方式**
- 返回变形梯度F（超弹性模型需传入的参数）的函数  
  ![Pasted image 20250628150648](images/Pasted%20image%2020250628150648.png)
  
- 计算总势能  
  ![Pasted image 20250628150716](images/Pasted%20image%2020250628150716.png)

# **模型评估中计算误差**

## **需要修改utils_evaluation.py的评估体系**
- **超弹性体系下的模型评估**  
  ![Pasted image 20250628150840](images/Pasted%20image%2020250628150840.png)
