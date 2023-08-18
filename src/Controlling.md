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

![](/assets/10-01.png)

![](/assets/10-02.png)


P4  
## Problems with PD Control   

PD control computes torques based on **errors**   

 - Steady state error   

This arm never reaches the target angle under gravity   

![](/assets/10-03.png)  

$$
\tau =k_p(\bar{q} -q)-k_d\dot{q} 
$$


P5   
## Problems with PD Control   

PD control computes torques based on **errors**   

 - Steady state error   
 - Motion falls behind the reference   

![](/assets/10-04.png)


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

![](/assets/10-05.png)

$$
\begin{matrix}
f=-k_px-k_dv \quad\quad\quad\\\\
h: \text{ simulation time step}
\end{matrix}
$$



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



P14  
## Stability of PD Control   

$$
A=\begin{bmatrix}
1-k_dh  & -k_ph\\\\
 h(1-k_dh) & 1-k_ph^2
\end{bmatrix}
$$


![](/assets/10-06.png)


P19   
## Stability of PD Control

\\(\lambda _1,\lambda _2 \in  \mathbb{C}  \\) are eigenvalues of \\(A\\)   

if \\(|\lambda _1|> 1\\)   

The system is unstable!    

Condition of stability: \\(|\lambda _1|\le  1 \text{ for all } \lambda _i\\)   



P20
## Stability of PD Control

![](/assets/10-07.png)


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

![](/assets/10-08.png)


P25  
## Stable PD Control   

$$
\tau _{\mathrm{int} }=-K_p(q^n+\dot{q}^n \Delta t-\bar{q} ^{n+1})-K_d(\dot{q} ^n+\ddot{q} ^n \Delta t)
$$


![](/assets/10-09.png)


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

![](/assets/10-10.png)

\\(\tau _j\\): joint torques   
Apply \\(\tau _j\\) to “child” body   
Apply \\(-\tau _j\\) to “parent” body    
All forces/torques sum up to zero   

\\(f_0,\tau _0\\): root force / torque   

Apply \\(f _0\\) to the root body

Apply \\(\tau _0\\) to the root body   

Non-zero net force/torque on the character!    



P30   
## Trajectory Optimization

[Witkin and Kass 1988 – Spacetime constraints]   

Find the trajectories:   

$$
\begin{align*}
 \text{Simulation trajectory }: & S_0,S_1,\dots ,S_T \\\\
 \text{Control trajectory }: & a_0,a_1,\dots ,a_{T-1}
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

![](/assets/10-11.png)


P34   
## A very simple example
 

|||
|--|--|
|Hard constraints: | ![](/assets/10-12.png) |
| Soft constraints:  |![](/assets/10-013.png) |


P35   
## A very simple example

Collocation methods:   

Assume the optimization variables {\\(x_n, v_n, \tilde{x}_n\\)} are values of a set of parametric curves    
 - typically polynomials or splines    


Optimize the parameters of the curves \\(\theta\\) instead     
 - with smaller number of variables than the original problem    



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

![](/assets/10-14.png)

find a target trajectory    

![](/assets/10-15.png)


P40  
## Problem with Gradient-Based Methods

 - The optimization problem is usually highly nonlinear, gradients are unreliable    
 - The system is a black box with unknow dynamics, gradients are not available   


![](/assets/10-16.png)


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


P43  
## CMA-ES   

 - Covariance matrix adaptation evolution strategy (CMA-ES)   
    - A widely adopted derivative-free method in character animation   

![](/assets/10-17.png)


Goal: find the variables 𝒙 that optimize \\(f(x)\\) 
 - Initialize Gaussian distribution \\(x\sim \mathcal{N} (\mu ,\Sigma )\\)   
 - Repeat:   
    - sample candidate variables {\\(x_i\\)} \\( \sim \mathcal{N} (\mu ,\Sigma )\\)   
    - Evaluate the objective function \\(f_i=f(x_i)\\)   
      - Involve simulation and generate simulation trajectories   
    - Sort {\\(f_i\\)} and keep the top \\(N\\) elite samples   
    - Update \\(\mu ,\Sigma \\) according to the elite samples    



P44  
## CMA-ES   

[Wampler and Popović 2009 - Optimal Gait and Form for Animal Locomotion]    


P45    

[Al Borno et al. 2013 - Trajectory Optimization for Full-Body Movements with Complex Contacts]   


P46  
## SAMCON   

 - **SA**mpling-based **M**otion **CON**trol [Liu et al. 2010, 2015]   
    - Motion Clip → Open-loop control trajectory   
    - A sequential Monte-Carlo method   

![](/assets/10-18.png)


P47  
## SAMCON   

![](/assets/10-19.png)


P48  
## Sampling & Simulation

![](/assets/10-20.png)


P49  
## Sample Selection


![](/assets/10-21.png)


P50  
## SAMCON Iterations

![](/assets/10-22.png)


P51  
## Constructed Open-loop Control Trajectory

![](/assets/10-23.png)

P54  
## Feedforward Control


![](/assets/10-24.png)


P56  
## Feedback Control


![](/assets/10-025.png)


P57  
## Feedback Control

![](/assets/10-026.png)   


P58  
## Feedback Control

![](/assets/10-027.png)   


P62  
## Static Balance   

What is balance?   

![](/assets/10-28.png)   



P64  
## Static Balance   

What is balance?   

![](/assets/10-29.png)   


P66 
## Static Balance   


A simple strategy to maintain balance:   

 - Keep projected CoM close to the center of support polygon **while tracking a standing pose**   

 - Use **PD control** to compute feedback torque   


![](/assets/10-30.png)   


P68  
## Static Balance

 - Apply the feedback torque at **ankles** (ankle strategy) or **hips** (hip strategy)   


P69   
## Jacobian Transpose Control

![](/assets/10-31.png)   

Can we use joint torques \\(\tau _i\\) to mimic the effect of a force \\(f\\) applied at \\(x\\)   

 - Note that the **desired force** \\(f\\) is not actually applied   
 - Also called **“virtual force”**   


P70   
## Jacobian Transpose Control  

Make \\(f\\) and \\(\tau _i\\) done the same work    



P73  
## Jacobian Transpose Control  

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




![](/assets/10-32.png)   



---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/