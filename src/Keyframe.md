# Lecture 04



P3   
## Outline

 - Character Kinematics (cont.)   
    - Motion Retargeting    
    - Full-body IK   

 - Keyframe Animation   
    - Interpolation and splines   


P4   

## Recap: Character Kinematics

![](/assets/04-01.png)  



P11   
## Recap: Forward Kinematics

![](/assets/04-02.png)  

$$
\begin{align*}
 Q_0= & R_0\\\\
 Q_1= & R_0R_1=Q_0R_1 \\\\
Q_2 = & R_0R_1R_2=Q_0R_2 
\end{align*}
$$


$$
\begin{align*}
 p_1= & p_0+Q_0l_1\\\\
 p_2= & p_0+Q_0l_1 +Q_1l_2\\\\
 = & p_1+Q_1l_2
\end{align*}
$$

$$
\begin{align*}
 R_1= & Q^{-1}_0Q_1\\\\
 R_2= & Q^{-1}_1Q_2
\end{align*}
$$

P15   

## T-Pose

![](/assets/04-3.png)  

P16   
## T-Pose? A-Pose?

![](/assets/04-04.png)  


P17   
## T-Pose? A-Pose?

![](/assets/04-05.png)  

P19   
## T-Pose? A-Pose?

![](/assets/04-06.png)  


P20   

![](/assets/04-07.png)  

P21   
![](/assets/04-08.png)  

P23   
## **Same motion** under different reference poses   

![](/assets/04-09.png)  


P29    
## **Retargeting** between reference poses

![](/assets/04-10.png)  


P31    
## Retargeting for a single object

![](/assets/04-11.png)  


P33   
## Retargeting for a single object

![](/assets/04-12.png)  


P37   
## Retargeting for a single object

![](/assets/04-13.png)  


P45    

## Retargeting for a chain of links

![](/assets/04-14.png)  

P49    
## Retargeting for a chain of links

![](/assets/04-15.png)  


P51   
## Retargeting for a chain of links

![](/assets/04-16.png)  


P52   
## **Retargeting** between reference poses


![](/assets/04-17.png)  


P53   
## Retargeting between reference poses

![](/assets/04-18.png)  

P54   
## Recap: Character Kinematics

![](/assets/04-19.png)  

P58   
## Cyclic Coordinate Descent (CCD) IK

![](/assets/04-20.png)  

Rotate joint 3 such that     

P80   
## Cyclic Coordinate Descent (CCD) IK   

![](/assets/04-21.png)  

Rotate joint 3 such that \\(l_{34}\\) points towards \\(\tilde{x} \\)    
Stretch link 2 such that \\((x-\tilde{x})\perp l_{23} \\)   
Rotate joint 1 such that 𝒍14 points towards \\(\tilde{x} \\)   
……    


P90   
## Geometric Method for Jacobian Matrix

Can we parameterize a ball joint using axis-angle \\(\theta u\\) and compute Jacobian as   

$$
\begin{matrix}
 \frac{\partial f}{\partial \theta _i} =\theta u\times r_i & ???
\end{matrix}
$$

![](/assets/04-22.png)  

Jacobian for axis-angle representation has a rather complicated formulation…   

P95   
## Full-body IK

![](/assets/04-23.png)  

The kinematic chain passes the root joint…    

 - Apply IK to the chain   
 - Set root transformation based on the FK along the chain   
 - Revert joint rotations between the foot and the root   

P97   
## Full-body IK

![](/assets/04-24.png)  

Two constraints…    

 - Formulate optimization problems     
 - Consider one constraint each time, then fix the broken one    

P98   
## Character Rig

![](/assets/04-25.png)  

Created Multiple IK chains   

User activates several IK chains each time, the joints controlled by the other IK chains can move freely   


P101  

# Keyframe Animation and Interpolation


P106   
## Interpolation

 - Given a set of data pairs \\(D=\\){\\((x_i,y_i)\mid i=0,\dots ,N\\)} find a function \\(f(x)\\) such that    

P107   

## Interpolation  

![](/assets/04-26.png)  


P113   
## Linear Interpolation

$$
f(x)=(1-t)y_1+ty_2
$$

![](/assets/04-27.png)  



P114   
## Smoothness

![](/assets/04-28.png)  


P115   
## Nonlinear Interpolation?

$$
f(x)=?
$$


P119   
## Polynomial Interpolation

$$
f(x)=a_0+a_1x+a_2x^2+\dots +a_nx^n
$$

Data point set  \\(D=\\){\\((x_i,y_i)\mid i=0,\dots ,N\\)}

$$
\begin{bmatrix}  
  1 & x_0 & x^2_0&\cdots & x^n_0 \\\\  
  1 & x_1 & x^2_1&\cdots & x^n_1 \\\\ 
  \vdots & \vdots & \vdots& \ddots & \vdots \\\\  
  1 & x_N & x^2_N&\cdots & x^n_N  
\end{bmatrix} \begin{bmatrix}
 a_0\\\\
 a_1\\\\
\vdots \\\\
a_n
\end{bmatrix}=\begin{bmatrix}
y_0 \\\\
y_1 \\\\
 \vdots\\\\
y_N
\end{bmatrix}
$$

P122   
## Polynomial Interpolation   

 - Runge's phenomenon   
    - High-degree polynomial can oscillate at the edges of an interval   


P153   
## Interpolation of Rotations

![](/assets/04-29.png)  

P154   
## Rotation Representations

![](/assets/04-30.png)  


P157   
## SLERP for Quaternions

$$
q_t=\frac{\sin[(1-t)\theta ]}{\sin \theta } q_0 + \frac{\sin t \theta }{\sin \theta }q_1
$$

$$
\cos \theta = q_0 \cdot q_1
$$

![](/assets/04-31.png)  

Constant rotational speed, but only “linear” interpolation    



---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/