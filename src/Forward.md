
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
Q_4={\color{Red}R_4}
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

![](/assets/03-011.png)  

P37   
## Kinematics of a Chain: Summary

![](/assets/03-13.png)  

Forward kinematics:    

Given the rotations of all joints \\(R_i\\), find the coordinates of \\(x_0\\) in the global frame \\(x\\):    

![](/assets/03-14.png)  

     
P38    

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
| ![](/assets/03-025.png)  |![](/assets/03-023.png)  | knee, elbow <br>  \\({\color{Red}{1 \text{DoF}}}\\)  <br>  hinge joint <br>  revolute joint  |
|  |![](/assets/03-024.png) |hip, shoulder <br>  \\({\color{Red}{3 \text{DoF}}}\\) <br> ball-and-socket joint |

 
P51   
## Degrees of Freedom (DoF)
   
![](/assets/03-25.png)  

P52   
## 
Joint Limits



![](/assets/03-26.png)  

![](/assets/03-27.png)  

![](/assets/03-28.png)  












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

 - DoF of \\( \theta \\) is often much larger than that of \\(x \\). We cannot easily tune\\(\theta \\) to achieve a specific value of \\(x\\). 


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


![](/assets/03-33.png)  

P68   
## A simple solution to a two-joint IK problem

1. Rotate joint 1 such that   

$$
||l_{ox}||=||l_{02}||
$$

![](/assets/03-34.png)  







![](/assets/03-35.png)  

---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/