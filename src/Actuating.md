# Lecture 09

P2   
## Outline   

 - Simulating & Actuating Characters   
    - Joint torques   
 - PD (Proportional-Derivative) control   


P4   
## Recap: Dynamics of a Point Mass

![](/assets/09-01.png)



P10  
## Recap: Rigid Body Dynamics   

![](/assets/09-02.png)   


P11   
## Recap: Rigid Body Dynamics


$$
\begin{bmatrix}
 mI_3 & 0\\\\
 0 & I
\end{bmatrix}\begin{bmatrix}
\dot{v}  \\\\
\dot{\omega }
\end{bmatrix}+\begin{bmatrix}
 0\\\\
\omega \times I\omega 
\end{bmatrix}=\begin{bmatrix}
f \\\\
\tau 
\end{bmatrix}
$$


P12   
## Defining a Rigid Body


![](/assets/09-03.png)

Masses: \\(m,I\\)    
Kinematics:  \\(x,v,R,\omega \\)   

Geometry:    
• Box, Sphere, Capsule, Mesh, …    
• Collision detection   
• Compute \\(m,I\\)    



P14   
## Recap: Dynamics of Articulated Rigid Bodies   

![](/assets/09-04.png)  



P15  
## Recap: Dynamics of Articulated Rigid Bodies

$$
\begin{align*}
 M\dot{v} +C(x,v) & =f+J^T\lambda  \\\\
 Jv & =0
\end{align*}
$$


P16   
## Recap: Simulation of a Rigid Body System

![](/assets/09-05.png)


P17   
## Defining a Simulated Character  

![](/assets/09-06.png)

Rigid bodies:    
 - \\(m_i,I_i,x_i,R_i\\)     
 - Geometries    

Joints:   
 - Position   
 - Type   
 - Bodies   


P19   
## Simulating a Character   

![](/assets/09-07.png)


P22   
## Actuating a Rigid Body

![](/assets/09-08.png)


P23  
## Actuating a Rigid Body   

![](/assets/09-09.png)

![](/assets/09-10.png)


P24   
## Actuating a Rigid Body

![](/assets/09-11.png)

P26   
## Actuating Articulated Rigid Bodies

![](/assets/09-12.png)


P27  
## Actuating Articulated Rigid Bodies

![](/assets/09-13.png)


P29   
## Joint Torques  

What is a joint torque?   
How is a joint torque applied?   


P33  
## Joint Torques

$$
\sum_{i}^{} f_i=0
$$


![](/assets/09-014.png)

$$
\tau _1= \sum _ {i}^{} (r_1+r_i) \times f_i=r_1 \times \sum _ {i}^{}f_i + \sum _ {i}^{}r_i \times f_i
$$


P34  
## Joint Torques

$$
\tau _1= \sum _ {i}^{} r_i \times f_i
$$

![](/assets/09-15.png)

$$
\tau _1= \sum _ {i}^{} r_i \times f_i \quad \quad \quad \quad \tau _2= -\sum _ {i}^{} r_i \times f_i
$$


P36   
## Joint Torques
 
![](/assets/09-16.png)


P38  
## Joint Torques

Applying a joint torque \\( \tau\\):   
 - Add \\( \tau\\) to one attached body    
 - Add \\( -\tau\\) to the other attached body    

$$
M\begin{bmatrix}
 \dot{v}_1 \\\\
\dot{\omega }_1 \\\\
\dot{v}_2\\\\
\dot{\omega }_2 
\end{bmatrix} + \begin{bmatrix}
 0\\\\
\omega_1 \times I_1 \omega _1\\\\
0\\\\
\omega_2 \times I_2 \omega _2
\end{bmatrix}=\begin{bmatrix}
0 \\\\
\tau \\\\
0 \\\\
-\tau 
\end{bmatrix}+J^T\lambda 
$$

$$
Jv=0
$$


P40   
## Simulating + Controlling a Character

![](/assets/09-17.png)


P44   
## Forward Dynamics vs. Inverse Dynamics
  
![](/assets/09-18.png)





![](/assets/09-19.png)

---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/