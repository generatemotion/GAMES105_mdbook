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
\sum _ {i}^{}  f_i=0
$$

$$
\tau _1= \sum _ {i}^{} r_i \times f_i
$$


P35  
## Joint Torques


$$
\sum _ {i}^{}  f_i=0
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



P47   
## Fully-Actuated vs. Underactuated

|||
|--|--|
|![](/assets/09-20.png) | ![](/assets/09-21.png)|
|If #actuators ≥ #dofs, the system is **fully-actuated** | If #actuators < #dofs, the system is **underactuated** |



P48   
## Fully-Actuated vs. Underactuated

For any \\([x,v,\dot{v} ]\\), there exists an \\(f\\) that produces the motion

For many \\([x,v,\dot{v} ]\\) , there is no such \\(f\\) that produces the motion



P50  
## Feedforward vs. Feedback   

Feedforward control:   
$$
f,\tau =\pi (t)
$$


 - Apply predefined control signals **without considering the current state** of the system   
 - Assuming unchanging system.    
   Perturbations may lead to unpredicted results   


![](/assets/09-22.png)


P51  
## Feedforward vs. Feedback   

Feedforward control:   
$$
f,\tau =\pi (s_t,t)
$$


 - Adjust control signals based on the current state of the system
 - Certain perturbations are expected.    
   The feedback signal will be used to improves the performance at the next state.   

P56   
## Proportional-Derivative Control

![](/assets/09-23.png)


P57   
## Proportional-Derivative Control


![](/assets/09-24.png)


P60   
## Proportional-Derivative Control

![](/assets/09-25.png)

![](/assets/09-26.png)


P61   
## Proportional-Derivative Control

Increase stiffness \\(k_p\\) reduces the steady-state error, but can make the system too stiff and numerically unstable    


P62   
## Proportional-Integral-Derivative controller 

![](/assets/09-27.png)  
![](/assets/09-28.png)  


P63   
## PD Control for Characters

![](/assets/09-29.png)

![](/assets/09-30.png)



P64  
## PD Control for Characters


![](/assets/09-31.png)


P67  
## Tracking Controllers


![](/assets/09-32.png)   


P68  
## Full-body Tracking Controllers


![](/assets/09-33.png)   


P72   
## Full-body Tracking Controllers

Is PD control a **feedforward** control?   
a **feedback** control?   

P73  
## Tracking Mocap with Joint Torques   

\\(\tau _j\\): joint torques   
Apply \\(\tau _j\\) to “child” body    
Apply \\(-\tau _j\\) to “parent” body   
**All forces/torques sum up to zero**   



P74   
## Tracking Mocap with Root Forces/Torques

\\(f_0,\tau _0\\): root force / torque    
Apply \\(f_0\\) to the root body    
Apply \\(\tau _0\\) to the root body   
Non-zero net force/torque on the character!   


P76  
## Mixture Simulation and Mocap

![](/assets/09-34.png)




---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/