# Lecture 03



P3   
## Outline   

 - Character Kinematics   
    - Skeleton and forward Kinematics   

 - Inverse Kinematics   
    - IK as a optimization problem   
    - Optimization approaches   
      - Cyclic Coordinate Descent (CCD)   
      - Jacobian and gradient descent method   
      - Jacobian inverse method   


P4   

## Character Kinematics    


kinematics /ˌkɪnɪˈmætɪks/
n. the study of the motion of bodies without reference to mass or force   
-- Collins English Dictionary    

P8   
## Skeleton

![](/assets/03-01.png)  

P9   
## Skeleton

![](/assets/03-02.png)  



P14    
## Kinematics of a Chain

![](/assets/03-03.png)  

$$
\begin{matrix}
 Q_0=I\\\\
 Q_1=I\\\\
 Q_2=I\\\\
 Q_3=I\\\\
Q_4=I
\end{matrix}
$$


P15    
## Kinematics of a Chain


![](/assets/03-04.png)  

$$
\begin{matrix}
 Q_0=I\quad\\\\\
 Q_1=I\quad\\\\\
 Q_2=I\quad\\\\\
 Q_3=I\quad\\\\\
Q_4={\color{Red}{R_4}}
\end{matrix}
$$


P16   

## Kinematics of a Chain

![](/assets/03-05.png) 

$$
\begin{matrix}
 Q_0=I\quad\\quad\\\\\
 Q_1=I\quad\\quad\\\\\
 Q_2=I\quad\\quad\\\\\
 Q_3={\color{Red}{R_3}}\quad\\\\\
Q_4={\color{Red}{R_3}}R_4
\end{matrix}
$$


P17    
## Kinematics of a Chain

![](/assets/03-06.png) 

$$
\begin{matrix}
 Q_0=I\quad \quad\quad   \\\\
 Q_1=I\quad \quad\quad   \\\\
 Q_2={\color{Red}{R_2}}\quad\\quad \\\\
 Q_3={\color{Red}{R_2}}R_3\quad \\\\
Q_4={\color{Red}{R_2}}R_3R_4
\end{matrix}
$$


P18   
## Kinematics of a Chain

![](/assets/03-07.png)  

$$
\begin{matrix}
 Q_0=I\quad \quad \quad \quad \\\\
 Q_1={\color{Red}{R_1}}\quad \quad \quad \\\\
 Q_2={\color{Red}{R_1}}R_2\quad \quad \\\\
 Q_3={\color{Red}{R_1}}R_2R_3\quad \\\\
Q_4={\color{Red}{R_1}}R_2R_3R_4
\end{matrix}
$$

P19   
## Kinematics of a Chain

![](/assets/03-08.png)  

$$
\begin{matrix}
 Q_0={\color{Red}{R_0}}\quad \quad\quad\quad \\\\
 Q_1={\color{Red}{R_0}}R_1 \quad\quad\quad \\\\
 Q_2={\color{Red}{R_0}}R_1R_2\quad \quad \\\\
 Q_3={\color{Red}{R_0}}R_1R_2R_3\quad \\\\
Q_4={\color{Red}{R_0}}R_1R_2R_3R_4
\end{matrix}
$$

P20   

## Kinematics of a Chain

![](/assets/03-09-1.png)  



P21   
## Kinematics of a Chain   

![](/assets/03-10-1.png)  



P23   
## Kinematics of a Chain   

![](/assets/03-11.png)  


P31   
## Kinematics of a Chain   

![](/assets/03-011.png)


P37   
## Kinematics of a Chain: Summary

![](/assets/03-13.png)  

Forward kinematics:    

Given the rotations of all joints \\(R_i\\), find the coordinates of \\(x_0\\) in the global frame \\(x\\):    

![](/assets/03-14.png)  

     
P38    
Forward kinematics:    

Given the rotations of all joints \\(R_i\\), find the coordinates of \\(x_0\\) in the global frame \\(x\\):    

![](/assets/03-15.png)  

P39   
## Kinematics of a Chain: Summary

Forward kinematics:    

Given the rotations of all joints \\(R_i\\), find the coordinates of \\(x_0\\) relative to the local frame of \\(Q_k\\):    

![](/assets/03-16.png)  

P40    
## Kinematics of a Chain: Summary

![](/assets/03-17.png)  


P41   
## Kinematics of a Character

![](/assets/03-18.png)  

P43    
## Root Location

![](/assets/03-19.png)  

P45   
## Types of Joints

![](/assets/03-20.png)  

P46   
## Types of Joints

|||
|---|---|
| ![](/assets/03-026.png) |knee, elbow  <br>  <br> hinge joint   <br> revolute joint  |
| ![](/assets/03-022.png) | hip, shoulder  <br>  <br>ball-and-socket joint   |



P47   
## Degrees of Freedom (DoF)   

 - Number of independent parameters that define the configuration or state of a mechanical system     

$$
\begin{matrix}
\text{DoF }=6 \\\\
(p,R) \in \mathbb{R} ^3\times so(3)
\end{matrix}
$$

P50   
## Degrees of Freedom (DoF)  

||||
|---|---|---|
| ![](/assets/03-025-2.png)  |![](/assets/03-023.png)  | knee, elbow <br>  \\({\color{Red}{1 \text{DoF}}}\\)  <br>  hinge joint <br>  revolute joint  |
| ![](/assets/03-025-1.png)  |![](/assets/03-024.png) |hip, shoulder <br>  \\({\color{Red}{3 \text{DoF}}}\\) <br> ball-and-socket joint |

 
P51   
## Degrees of Freedom (DoF)
   
![](/assets/03-25.png)  

P52   
## 
Joint Limits


||||
|---|---|---|
| ![](/assets/03-025-2.png)  |![](/assets/03-26.png)    | knee, elbow <br>  \\({\color{Red}{1 \text{DoF}}}\\)  <br> \\(\theta_{\min }\le \theta\le  \theta_{\max } \\) <br> hinge joint <br>  revolute joint  |
| ![](/assets/03-025-1.png)  |![](/assets/03-27.png) |hip, shoulder <br>  \\({\color{Red}{3 \text{DoF}}}\\) <br> \\(\theta_{\min }\preceq  \theta \preceq  \theta_{\max } \\) <br> ball-and-socket joint |


P55  

## Forward Kinematics   

$$
(t_0,R_0,R_1,R_2\dots \dots ) 
$$

$$
\text{root } \mid \text{ internal joints}
$$

joints are typically in the order that every joint precedes its offspring   

for \\(i\\) in joint_list:    

$$
\begin{align*}
 p_i= & i^,\text{ s parent joint} \\\\
  Q_i=& Q_{pi}R_i \\\\
 x_i= & x_{pi} + Q_{pi}l_i
\end{align*}
$$











P57   
## Forward Kinematics
Q2: how should we allow stretchable bones?    


P58   
## Example: motion data in a file

 - HIERARCHY: defining **T-pose of** the character   
 - MOTION: root position and Euler angles of each joints   


See: <https://research.cs.wisc.edu/graphics/Courses/cs-838-1999/Jeff/BVH.html>

![](/assets/03-30-1.png)  

![](/assets/03-31-1.png)  


P59   
## Inverse Kinematics

A. Aristidou, J. Lasenby, Y. Chrysanthou, and A. Shamir. 2018.    
**Inverse Kinematics Techniques in Computer Graphics: A Survey.**    
Computer Graphics Forum    

P61   
## Forward and Inverse Problems   

For a system that can be described by a set of **parameters** \\(\theta \\), and a **property** 𝒙 of the system given by    

$$
x=f(\theta )
$$

Forward problem:     

 - Given \\(\theta \\), we need to compute \\(x \\)    

 - Easy to compute since \\(f\\) is known, the result is unique    

 - DoF of \\( \theta \\) is often much larger than that of \\(x \\). We cannot easily tune \\(\theta \\) to achieve a specific value of \\(x\\). 


Inverse problem:    

 - Given \\(x \\), we need to find a set of valid parameters \\(\theta \\) such that\\(x=f(\theta) \\)   
 
 - Often need to solve a difficult **nonlinear** equation, which can have **multiple** solutions   

 - \\(x\\) is typically meaningful and can be set in intuitive ways   


P62   
## Inverse Kinematics

![](/assets/03-32.png)  

Given the position of the end-effector \\(x\\), Compute the joint rotations \\(R_i\\)    

P64   
## Solutions of IK Problems

![](/assets/03-33.png)  

P67   
## A simple solution to a two-joint IK problem

1. Rotate joint 1 such that    


![](/assets/03-34.png)  

P68   
## A simple solution to a two-joint IK problem

1. Rotate joint 1 such that   

$$
||l_{ox}||=||l_{02}||
$$

![](/assets/03-35.png)  


P70   
## A simple solution to a two-joint IK problem   

![](/assets/03-36.png)  

1. Rotate joint 1 such that   

$$
||l_{ox}||=||l_{02}||
$$

2. Rotate joint 0 such that   

$$
l_{ox}=l_{02}
$$

P71   
## A simple solution to a two-joint IK problem

![](/assets/03-37.png)  

1. Rotate joint 1 such that 

$$
||l_{ox}||=||l_{02}||
$$

2. Rotate joint 0 such that

$$
l_{ox}=l_{02}
$$

3. Rotate joint 0 around \\(l_{ox}\\) if necessary 

P72   

![](/assets/03-38.png)  

$$
x=f(\theta )
$$

$$
Q=Q(\theta )
$$

P74   
## IK as an Optimization Problem

![](/assets/03-39.png)  

Find \\(\theta \\) such that      

$$
\tilde{x} -f(\theta )=0
$$

P75  
## IK as an Optimization Problem  

Find \\(\theta \\)  to optimize   

$$
\min_{\theta } \frac{1}{2} ||f(\theta )-\tilde{x} ||^2_2
$$

P88   
## Cyclic Coordinate Descent (CCD)   

Update parameters along each axis of the coordinate system   

Iterate cyclically through all axes    

![](/assets/03-40.png)  


P90   
## Cyclic Coordinate Descent (CCD) IK  

Rotate joint 3 such that \\(𝒍_{34}\\) points towards \\(\tilde{x}\\)   

![](/assets/03-41.png)  

P92   
## Cyclic Coordinate Descent (CCD) IK   

Rotate joint 3 such that \\(𝒍_{34}\\) points towards \\(\tilde{x}\\)   

Rotate joint 2 such that \\(𝒍_{24}\\) points towards \\(\tilde{x}\\)   


![](/assets/03-42.png)  



P93   
## Cyclic Coordinate Descent (CCD) IK

Rotate joint 3 such that \\(𝒍_{34}\\) points towards \\(\tilde{x}\\)   

Rotate joint 2 such that \\(𝒍_{24}\\) points towards \\(\tilde{x}\\)  

![](/assets/03-43.png)  


P94   

## Cyclic Coordinate Descent (CCD) IK

Rotate joint 3 such that \\(𝒍_{34}\\) points towards \\(\tilde{x}\\)   

Rotate joint 2 such that \\(𝒍_{24}\\) points towards \\(\tilde{x}\\)  

Rotate joint 1 such that \\(𝒍_{14}\\) points towards \\(\tilde{x}\\)   

![](/assets/03-44.png) 

P95   
## Cyclic Coordinate Descent (CCD) IK

Rotate joint 3 such that \\(𝒍_{34}\\) points towards \\(\tilde{x}\\)   

Rotate joint 2 such that \\(𝒍_{24}\\) points towards \\(\tilde{x}\\)   

Rotate joint 1 such that \\(𝒍_{14}\\) points towards \\(\tilde{x}\\)   

Rotate joint 0 such that \\(𝒍_{14}\\) points towards \\(\tilde{x}\\)   

![](/assets/03-45.png)  


P96   

## Cyclic Coordinate Descent (CCD) IK  

Rotate joint 3 such that \\(𝒍_{34}\\) points towards \\(\tilde{x}\\)   

Rotate joint 2 such that \\(𝒍_{24}\\) points towards \\(\tilde{x}\\)   

Rotate joint 1 such that \\(𝒍_{14}\\) points towards \\(\tilde{x}\\)   

Rotate joint 0 such that \\(𝒍_{14}\\) points towards \\(\tilde{x}\\)   

Rotate joint 3 such that \\({l}'_{34}\\) points towards \\(\tilde{x}\\)   

……    

![](/assets/03-46.png)  


P97   
## Cyclic Coordinate Descent (CCD) IK

Iteratively rotation each joint to make the end-effector align with vector between the joint and the target    

Easy to implement, very fast    

The “first” joint moves more than the others May take **many iterations** to **converge** Result can be sensitive to the **initial solution**    


P105   

## Gradient Descent   

$$
\begin{align*}
 \nabla_\theta F(\theta ^i)= & (\frac{\partial f}{\partial \theta }(\theta ^i))^T(f(\theta ^i)-\tilde{x})\\\\
 = & J^T \Delta   
\end{align*}
$$

P106   
## Jacobian Transpose   

$$
\theta ^{i+1}=\theta ^i-\alpha J^T\Delta
$$

$$
J= \frac{\partial f}{\partial \theta }=(\frac{\partial f}{\partial \theta_0 }\frac{\partial f}{\partial \theta_1 }\dots \frac{\partial f}{\partial \theta_n } ) 
$$


P121   
## Jacobian Transpose / Gradient Descent   

First-order approach, convergence can be slow Need to re-compute Jacobian at each iteration   

P124    

## Example: Quadratic Programming   

$$
\min_{\theta } F(\theta )=\frac{1}{2} \theta ^TA\theta +b^T\theta 
$$

where \\(A\\) is positive definite:   

$$
A=A^T,\theta ^TA\theta \ge 0 \text{ for any } \theta 
$$



P126   



$$
\begin{matrix}
 \text{Gradient}: \nabla_\theta  F(\theta )=A\theta +b \\\\
 \text{Optimality condition}: \nabla_\theta  F(\theta ^\ast )=0\\\\
 {\color{Blue} \Downarrow } \\\\
\theta ^\ast =-A^{-1}b
\end{matrix}
$$


P127    
## Gauss-Newton Method   

$$
F(\theta )=\frac{1}{2} ||f(\theta )-\tilde{x} ||^2_2
$$

![](/assets/03-47.png)   

Consider the first-order approximation of \\(f(\theta)\\) at \\(\theta^0\\)    


$$
\begin{align*}
  f(\theta)\approx & f(\theta^0) + \frac{\partial f}{\partial \theta} (\theta^0)(\theta-\theta^0) \\\\
 = & f(\theta^0)+J(\theta-\theta^0)
\end{align*}
$$

P128    

\begin{align*}
  f(\theta)\approx  & \frac{1}{2}||f(\theta^0)+J(\theta -\theta ^0)-\tilde{x}||^2_2    \\\\
 = &\frac{1}{2} (\theta -\theta ^0)^TJ^TJ(\theta -\theta ^0)\\\\
 & +(\theta -\theta ^0)^TJ^T(f(\theta ^0)-\tilde{x})+c 
\end{align*}

P129   
## Gauss-Newton Method   

$$
\begin{matrix}
 f(\theta)\approx  \frac{1}{2}||f(\theta^0)+J(\theta -\theta ^0)-\tilde{x}||^2_2 \\\\
 \Downarrow \\\\
(\nabla F (\theta ))^T=J^TJ(\theta-\theta^0)+J^T(f(\theta^0)-\tilde{x} )=0
\end{matrix}
$$

first-order optimality condition    


P133   
## Gauss-Newton Method

$$
J^TJ(\theta-\theta^0)=-J^T\Delta 
$$


\\(J^TJ\\) is \\({\color{Red} {\text{NOT}}}\\) invertible, but \\(JJ^T\\) can be invertible      


P134   
## Jacobian Inverse Method
 
![](/assets/03-042.png)  


P135   
## Jacobian Inverse Method


![](/assets/03-047.png)  

$$
J(\theta-\theta^0)=\tilde{x} -f(\theta^0)
$$

P137   

$$
\begin{align*}
 \theta = & \theta ^0-J^+\Delta \\\\
 = & \theta ^0-J^T(JJ^T)^{-1}\Delta
\end{align*}
$$

(Moore-Penrose) Pseudoinverse   


P138   

## Gauss-Newton Method

$$
F(\theta )=\frac{1}{2} ||f(\theta )-\tilde{x} ||^2_2
$$

![](/assets/03-47.png)  

$$
J^TJ(\theta-\theta^0)=-J^T\Delta 
$$

If \\(J^TJ\\) is invertible, we have   

$$
\theta = \theta^0 - (J^TJ)^{-1}J^T\Delta
$$

but when can \\(J^TJ\\) be invertible?   

P141   
## Gauss-Newton Method

![](/assets/03-49.png)  

P143   
## Jacobian Inverse Method

![](/assets/03-50.png)     

P145   

Usually faster than gradient descent/Jacobian transpose method.   

Any problem? \\(JJ^T/J^TJ\\) can be (near) singular!    



P147   

## Damped Jacobian Inverse Method

$$
J^\ast =J^T(JJ^T+\lambda I)^{-1}
$$

$$
J^\ast =(J^TJ+\lambda I)^{-1}J^T
$$

P148   
Also called Levenberg-Marquardt algorithm    

P149   
## Damped Jacobian Inverse Method

Using the minimal rotations to reach the target    

P150  
## Damped Jacobian Inverse Method  

![](/assets/03-51.png)  

P152   
## Character IK


![](/assets/03-052.png)  

P156   
## Outline   

 - Character Kinematics   
    - Skeleton and forward Kinematics   

 - Inverse Kinematics   
    - IK as a optimization problem   
    - Optimization approaches   
      - Cyclic Coordinate Descent (CCD)   
      - Jacobian and gradient descent method   
      - Jacobian inverse method   

Andreas Aristidou and Joan Lasenby. 2011.   
**FABRIK: A fast, iterative solver for the Inverse Kinematics problem.**   
*Graphical Models*   


 

---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/