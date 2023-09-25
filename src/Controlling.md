# Lecture 10

P2  

## Outline   

 - More about PD (Proportional-Derivative) control   
    - Stable PD control   

 - Feedforward Motion Control   
    - Trajectory optimization   

 - Feedback Motion Control   
    - Static balance   

P3  
## PD Control for Characters   

![](./assets/10-01.png)

![](./assets/10-02.png)


P4  
## Problems with PD Control   

PD control computes torques based on **errors**   

 - Steady state error   

This arm never reaches the target angle under gravity   

![](./assets/10-03.png)  




P5   

 - Motion falls behind the reference   

![](./assets/10-04.png)


P7   
## Problems with PD Control

High-gain \\((k_p)\\) control is more precise but less stable…   


P8   
## Stability of PD Control

Semi-implicit Euler Integration   

$$
\begin{align*}
v_{n+1}  & =v_n+h\frac{f}{m} \\\\
 x_{n+1} &=x_n+hv_{n+1}
\end{align*}
$$

![](./assets/10-05.png)

$$
\begin{matrix}
f=-k_px-k_dv \quad\quad\quad\\\\
h: \text{ simulation time step}
\end{matrix}
$$



> &#x2705; PD control 的过程类似于一个弹簧系统。  



P11   
## Stability of PD Control

Semi-implicit Euler Integration   

$$
\begin{bmatrix}
 v_{n+1}\\\\
x_{n+1}
\end{bmatrix}=\begin{bmatrix}
1-k_dh  & -k_ph\\\\
 h(1-k_dh) & 1-k_ph^2
\end{bmatrix}\begin{bmatrix}
v_n \\\\
x_n
\end{bmatrix}
$$


> &#x2705; (1) 假设\\(m＝1\\)    
> &#x2705; (2) 代入 \\(f\\) 到方程组   
> &#x2705; (3) 方程组写成矩阵形式   
> &#x2705; \\(h\\) 为时间步长。  



P14  
## Stability of PD Control   

$$
A=\begin{bmatrix}
1-k_dh  & -k_ph\\\\
 h(1-k_dh) & 1-k_ph^2
\end{bmatrix}
$$


![](./assets/10-06.png)


P19   
## Stability of PD Control

\\(\lambda _1,\lambda _2 \in  \mathbb{C}  \\) are eigenvalues of \\(A\\)   

if \\(|\lambda _1|> 1\\)   

The system is unstable!    

Condition of stability: \\(|\lambda _i|\le  1 \text{ for all } \lambda _i\\)   


> &#x2705; 根据矩阵特征值的性质可直接得出结论。  
> &#x2705; 基于中间变是 \\(z_n\\) 推导的过程跳过。   


P20
## Stability of PD Control

![](./assets/10-07.png)


> &#x2705; 如果 \\(k_p\\) 和 \\(k_d\\) 变大，就必须以一个较小的时间步长进行仿真。   



P21  
 - Determining gain and damping coefficients can be difficult…   
    - A typical setting \\(k_p\\) = 200, \\(k_d\\) = 20 for a 50kg character   
    - Light body requires smaller gains   
    - Dynamic motions need larger gains   



 - High-gain/high-damping control can be unstable, so small times is necessary   
    - \\(h\\) = 0.5~1ms is often used, or 1000~2000Hz   
    - Higher gain/damping requires smaller time step   



P22   
## A More Stable PD Control

Semi-implicit Euler Integration   

$$
\begin{align*}
 v_{n+1} & = v_n+h(-k_px_n-k_dv_n) \\\\
 v_{n+1} & = x_n+hv_{n+1}
\end{align*}
$$

$$
\Downarrow 
$$


$$
\begin{align*}
 v_{n+1} & = v_n+h(-k_px_n-k_dv_{n+1}) \\\\
 x_{n+1} & = x_n+hv_{n+1}
\end{align*}
$$


> &#x2705; 解决方法：半隐式欧拉 → 隐式欧拉，即用下一时刻的力计算下一时刻的速度。  
> &#x2705; 实际上，计算 \\(f_{n＋1}\\) 只使用 \\(V_{n＋1}\\) , 不使用 \\(x_{n＋1}\\) , 因为 \\(x_{n＋1}\\) 会引入非常复杂的计算。   
> &#x2705; 由于 \\(v_{n＋1}\\) 未知，需通过解方程组来求解。   



P23  
## A More Stable PD Control

$$
\begin{bmatrix}
 v_{n+1} \\\\
x_{n+1} 
\end{bmatrix}=\frac{1}{1+hk_d} \begin{bmatrix}
 1 & -k_ph\\\\
 h & 1+k_dh-k_ph^2
\end{bmatrix}\begin{bmatrix}
 v_n\\\\
x_n
\end{bmatrix}
$$


P24  
## A More Stable PD Control

![](./assets/10-08.png)


> &#x2705; \\(v_{n}\\) 换成 \\(v_{n＋1}\\) ，很大承度上提高了稳定性。  



P25  
## Stable PD Control   

$$
\tau _{\mathrm{int} }=-K_p(q^n+\dot{q}^n \Delta t-\bar{q} ^{n+1})-K_d(\dot{q} ^n+\ddot{q} ^n \Delta t)
$$


![](./assets/10-09.png)


> &#x2705; 把隐式方法应用到角色控制上。  



P26  
## PD Control for Characters


 - Determining gain and damping coefficients can be difficult…   
    - A typical setting \\(k_p\\) = 200, \\(k_d\\) = 20 for a 50kg character   
    - Light body requires smaller gains   
    - Dynamic motions need larger gains

 - High-gain/high-damping control can be unstable, so small times is necessary  
    - \\(h\\) = 0.5~1ms is often used, or 1000~2000Hz   
    - \\(h\\) = 1/120s~1/60s, or 120Hz/60Hz **with Stable PD**   
    - Higher gain/damping requires smaller time step   


P28  
## Tracking Mocap with Root Forces/Torques   

![](./assets/10-10.png)

\\(\tau _j\\): joint torques   
\\(\text{ }\\) Apply \\(\tau _j\\) to “child” body   
\\(\text{ }\\) Apply \\(-\tau _j\\) to “parent” body    
\\(\text{ }\\) All forces/torques sum up to zero   

\\(f_0,\tau _0\\): root force / torque   

\\(\quad\quad\\) Apply \\(f _0\\) to the root body

\\(\quad\quad\\) Apply \\(\tau _0\\) to the root body   

\\(\quad\quad\\) Non-zero net force/torque on the character!    


> &#x2705; 当前系统仍存的问题。(1) 稳态误差，相位延迟 (2) 缺少对根结点的力。   
> &#x2705; 净外力能解决问题2，但会有“提线木偶”的artifacts.   



P30   
## Trajectory Optimization

[Witkin and Kass 1988 – Spacetime constraints]   

Find the trajectories:   

$$
\begin{align*}
 \text{Simulation trajectory } & : S_0,S_1,\dots ,S_T \\\\
 \text{Control trajectory } & : a_0,a_1,\dots ,a_{T-1}
\end{align*}
$$



that minimize the objective function   

$$
\min_{(S_t,a_t)} f(S_T)+\sum_{t=0}^{T-1} f(S_t,a_t)
$$

and satisfy the constraints:   

$$
\begin{align*}
M\dot{v}+C(x,v)   & =f+J^T\lambda & \text{Equations of motion} \\\\
 g(x,v) & \ge 0 & \text{constraints } \quad \quad\quad
\end{align*}
$$


> &#x2705; 解决方法：不直接学习目标轨迹，而是先对目标轨迹增加一个修正。  



P33 
## A very simple example   

Compute a target trajectory \\(\tilde{x} (t)\\) such that the simulated trajectory \\(x(t)\\) is a sine curve.    

$$
\min_ {(x_n,v_n,\tilde {x} _n)} \sum _ {n=0}^{N} (\sin (t_n)-x_n)^2+\sum _ {n=0}^{N} \tilde {x}^2_n 
$$

$$
\begin{align*}
 s.t. \quad & v _ {n+1}= v_ n+h (k _ p( \tilde {x} _n-x_n)-k _ dv_n) \\\\
  & v _ {n+1} = x _ n + hv _ {n+1}
\end{align*}
$$

![](./assets/10-11.png)


> &#x2705; 仍以方块移动到目标高度为例。   
> &#x2705; 目标函数：目标项＋正则项    
> &#x2705; 约束：半隐式积分的运动方程      


P34   
## A very simple example
 

|||
|--|--|
|Hard constraints: | ![](./assets/10-12.png) |
| Soft constraints:  |![](./assets/10-013.png) |


> &#x2705; 以两种方式体现约束：   
> &#x2705;（1）Hard：必须满足，难解，不稳定。    
> &#x2705;（2）Soft：尽可能满足，易求解。   



P35   
## A very simple example

Collocation methods:   

Assume the optimization variables {\\(x_n, v_n, \tilde{x}_n\\)} are values of a set of parametric curves    
 - typically polynomials or splines    


Optimize the parameters of the curves \\(\theta\\) instead     
 - with smaller number of variables than the original problem    


> &#x2705; 参数量太大，难以优化。  
> &#x2705; 解决方法：假设参数符合特定的曲线，只学习曲线的参数，再生成完整的参数。   



P37  
## A very simple example   

How to solve this optimization problem?    
Gradient-based approaches:    
 - Gradient descent   
 - Newton’s methods   
 - Quasi-Newton methods   
 - ……   


P39   
## Trajectory Optimization for Tracking Control  

![](./assets/10-14.png)

find a target trajectory    

![](./assets/10-15.png)


P40  
## Problem with Gradient-Based Methods

 - The optimization problem is usually **highly nonlinear**, gradients are unreliable    
 - The system is a black box with unknow dynamics, gradients are not available   


![](./assets/10-16.png)


P42   
## Derivative-Free Optimization   

 - Iterative methods
    - Goal: find the variables 𝒙 that optimize \\(f(x)\\)   
    - Determining an initial guess of \\(x\\)   
    - Repeat:   
      - Propose a set of candidate variables {\\(x_i\\)} according to \\(x\\)   
      - Evaluate the objective function \\(f_i=f(x_i)\\)   
      - Update the estimation for \\(x\\)   

 - Examples:   
    - Bayesian optimization, Evolution strategies (e.g. CMA-ES), Stochastic optimization, Sequential Monte Carlo methods, ……   


> &#x2705; 启发式方法或随机采样方法，不需要梯度。   
> &#x2705; 缺点：慢、不精确。   


P43  
## CMA-ES   

 - Covariance matrix adaptation evolution strategy (CMA-ES)   
    - A widely adopted derivative-free method in character animation   

![](./assets/10-17.png)


Goal: find the variables 𝒙 that optimize \\(f(x)\\) 
 - Initialize Gaussian distribution \\(x\sim \mathcal{N} (\mu ,\Sigma )\\)   
 - Repeat:   
    - sample candidate variables {\\(x_i\\)} \\( \sim \mathcal{N} (\mu ,\Sigma )\\)   
    - Evaluate the objective function \\(f_i=f(x_i)\\)   
      - Involve simulation and generate simulation trajectories   
    - Sort {\\(f_i\\)} and keep the top \\(N\\) elite samples   
    - Update \\(\mu ,\Sigma \\) according to the elite samples    



> &#x2705; 优点：稳定，无梯度，可用于黑盒系统。  



P44  
## CMA-ES   

[Wampler and Popović 2009 - Optimal Gait and Form for Animal Locomotion]    


P45    

[Al Borno et al. 2013 - Trajectory Optimization for Full-Body Movements with Complex Contacts]   


> &#x2705; 只优化目标轨迹，不优化仿真轨迹。  


P46  
## SAMCON   

 - **SA**mpling-based **M**otion **CON**trol [Liu et al. 2010, 2015]   
    - Motion Clip → Open-loop control trajectory   
    - A sequential Monte-Carlo method   

![](./assets/10-18.png)


> &#x2705; CMA-ES的缺点：   
> &#x2705;（1）每次都从头到尾做仿真，计算量大。   
> &#x2705;（2）如果仿真轨迹长，则难收敛。   
> &#x2705; 改进方法：每次采样，只考虑下面一帧。   



P47  
## SAMCON   

![](./assets/10-19.png)


> &#x2705; 把轨迹分割开，每次优化一小段。  



P48  
## Sampling & Simulation

![](./assets/10-20.png)


> &#x2705; 在目标轨迹上增加偏移，跟踪偏移之后的轨迹。  
> &#x2705; 偏移量未知，因此以高斯分布对偏移量采样。  
> &#x2705; 高斯分布可由其它分布代替。  



P49  
## Sample Selection


![](./assets/10-21.png)


> &#x2705; 对每个偏移量做一次仿真，生成新的状态，保留其中与当目标接近的N个。   



P50  
## SAMCON Iterations

![](./assets/10-22.png)


> &#x2705; 从上一步N个中随机选择出发点，以及随机的偏移量，再做仿真与筛选。  



P51  
## Constructed Open-loop Control Trajectory

![](./assets/10-23.png)

> &#x2705; 最终找到一组最接近的。   
> &#x2705; 原理：只选一个容易掉入局部最优，因此保留多个。   
> &#x2705; 蒙特卡罗＋动态规划    
> &#x2705; 优点：穿膜问题也能被修正掉，可还原动捕数据，可根据环境影响而自动调整。  


P54  
## Feedforward Control


![](./assets/10-24.png)


> &#x2705; 前馈控制，要求每一步的起始状态都是在获取轨迹过程中能得到的状态。  
> &#x2705; 如果对起始状态加一点挠动，状态会偏离很远。  


P56  
## Feedback Control


![](./assets/10-025.png)


> &#x2705; 解决方法：引入反馈策略。根据当前偏差，自动计算出更正，把更正叠加到控制轨迹上。   



P57  
## Feedback Control

![](./assets/10-026.png)   


P58  
## Feedback Control

![](./assets/10-027.png)   


P62  
## Static Balance   

What is balance?   

![](./assets/10-28.png)   


> &#x2705; Static Balance：在不发生移动的情况下，通过简单的控制策略，保证角色不摔倒。  
> &#x2705; 平衡：质心在支撑面内。  


P64  
## Static Balance   

What is balance?   

![](./assets/10-29.png)   


> &#x2705; 人的质心：每一段的质心的加权平均。  
> &#x2705; 人的支撑面：两脚之内。   


P66 
## Static Balance   


A simple strategy to maintain balance:   

 - Keep projected CoM close to the center of support polygon **while tracking a standing pose**   

 - Use **PD control** to compute feedback torque   


![](./assets/10-30.png)   


> &#x2705; 力矩1：让角色保持某个姿势。  
> &#x2705; 力矩2：让质心与目标质心位置接近。  



P68  
## Static Balance

 - Apply the feedback torque at **ankles** (ankle strategy) or **hips** (hip strategy)   


P69   
## Jacobian Transpose Control

![](./assets/10-32.png)   

Can we use joint torques \\(\tau _i\\) to mimic the effect of a force \\(f\\) applied at \\(x\\)   

 - Note that the **desired force** \\(f\\) is not actually applied   
 - Also called **“virtual force”**   


> &#x2705; 实现 static balance，除了PD控制还有其它方法。  
> &#x2705; 通过施下 \\(\tau _1 ，\tau _2，\tau _3\\) 来达到给 \\(x\\) 施加 \\(f\\) 的效果！  




P73  
## Jacobian Transpose Control  

> &#x2705; 从做功的角度。  

Make \\(f\\) and \\(\tau _i\\) done the same power    

$$
P=f^T\dot{x}=\tau  ^T\dot{\theta } 
$$

Forward kinematics \\(x=g(\dot{\theta } )\Rightarrow \dot{x}=J \dot{\theta } \\)   

$$
f^T J\dot{\theta } = \tau  ^T\dot{\theta } 
$$

$$
J=\frac{\partial g}{\partial \theta } 
$$

P76  
## Jacobian Transpose Control

$$
\tau =J^Tf
$$

$$
\Downarrow 
$$

$$
\tau _i=(x-p_i)\times f
$$


P77  
## Static Balance

A simple strategy to maintain balance:   
 - Keep projected CoM close to the center of support polygon **while tracking a standing pose**    

 - Use PD control to compute feedback **virtual force**    

$$
f=k_p(\bar{c} -c)-k_d\dot{c}
$$


> &#x2705; P66 中在 Hips 上加力矩的方式只能进行简单的控制。  
> &#x2705; 可以通过虚力实现相似的效果。  



P78   
## Static Balance   

 - Assuming \\(f\\) **is applied to the CoM**, compute necessary joint torques using Jacobian transpose control to achieve it   

 - Usually using the joints in the legs   


> &#x2705; C 不一定是投影距离，还可以描述高度距离，实现站起蹲下的效果。 


P79   
## Static Balance
A fancier strategy:   

 - Mocap tracking as an objective function   
 - Controlling both the CoM position/**momentum** and the **angular** momentum   
 - Solve a **one-step** optimization problem to compute joint torques   
 
![](./assets/10-34.png)   





---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/