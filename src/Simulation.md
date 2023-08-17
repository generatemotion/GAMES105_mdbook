# Lecture 08


P5  
## Outline   

 - Simulation Basis   
    - Numerical Integration: Euler methods   
 - Equations of Rigid Bodies   
    - Rigid Body Kinematics   
    - Newton-Euler equations   
 - Articulated Rigid Bodies   
    - Joints and constraints   
 - Contact Models   
    - Penalty-based contact   
    - Constraint-based contact      

<https://www.cs.cmu.edu/~baraff/sigcourse/>

P57  
## Kinematics vs. Dynamics

![](/assets/08-01.png)


P92   
## A System with Two Links

![](/assets/08-02.png)


P94  
## A System with Two Links

![](/assets/08-03.png)


$$
M\dot{v} +C(x,v)=f
$$


P96   
## A System with Two Links and a Joint

![](/assets/08-04.png)

$$
M\dot{v} +C(x,v)=f+f_J
$$

P98   
## Constraints  


![](/assets/08-05.png)


P99 

![](/assets/08-5.png)


P100  
## Constraint Force

![](/assets/08-06.png)

\\(\ast \\) Constraint is passive No energy gain or loss!!!   

$$
f_c\cdot v=0
$$

P101   

![](/assets/08-07.png)


P102   
## Equation of Motion with Constraints

![](/assets/08-08.png)

$$
\begin{align*}
 M\dot{v} & =f+J^T\lambda  \\\\
  Jv&=0
\end{align*}
$$

$$
\begin{align*}
 M\frac{v_{n+1}-v_n}{h}  & =f+J^T\lambda  \\\\
  Jv_{n+1}&=0
\end{align*}
$$


P104   
## Numerical Solution   


$$
Jv_{n+1}=\alpha \frac{C-g(x_n)}{h} 
$$

Correction of numerical errors   
𝛼: error reduction parameter (ERP)    


P105   
## Numerical Solution   


![](/assets/08-09.png)


P106   
## Joint Constraint

![](/assets/08-10.png)

$$
x_1+R_1r_1=x_J=x_2+R_2r_2
$$

对\\(dt\\)求导：

$$
v_1+\omega _1\times r_1=v_2+\omega _2\times r_2
$$

P107   
## Joint Constraint

$$
\begin{bmatrix}
 I_3 & -[r_1] _ \times  & -I_3 & [r_2] _ \times 
\end{bmatrix}\begin{bmatrix}
v_1 \\\\
w_1 \\\\
v_2 \\\\
w_2
\end{bmatrix}=0
$$

$$
Jv=0
$$


P108   
## Simulation of a Rigid Body System   

$$
\begin{align*}
 M\dot{v} +C(x,v)& =f+J^T\lambda  \\\\
  Jv&=0
\end{align*}
$$


P110   
## Different Types of Joints

![](/assets/08-11.png)


P111   
## A System with Many Links Joints   


![](/assets/08-12.png)


P112  
## Contacts

![](/assets/08-13.png)

P115  
## Penalty-based Contact Model   


![](/assets/08-14.png)

$$
f_n=-k_pd-k_dv_{c,\perp }
$$


P116  
## Frictional Contact  

![](/assets/08-15.png)


P117   
## Frictional Contact   

$$
\begin{align*}
 f_n&=-k_pd-k_dv_{c,\perp }\\\\
f_t&=-\mu f_n\frac{v_{c,\parallel }}{||v_{c,\parallel }||} 
\end{align*}
$$


P119  
## Contact as a Constraint

![](/assets/08-17.png)

$$
x_c  =x+r_c \quad\quad\quad\quad\quad\quad
$$

$$
v_c  =v+\omega \times r_c=J_c \begin{bmatrix}
 v\\\\
w
\end{bmatrix}
$$

$$
v_{c,\perp } =v+\omega \times r_c=J_{c,\perp  }\begin{bmatrix}
v \\\\
\omega 
\end{bmatrix}
$$

P121   
## Contact as a Constraint

![](/assets/08-19.png)


P122
## Contact as a Linear Complementary Problem

$$
v_c\perp \lambda =0
$$

(Mixed) Linear Complementary Problem (LCP)   



To solve an LCP:   
e.g. Lemke's algorithm – a simplex algorithm   


P123   
## Contact as a Linear Complementary Problem

How to deal the friction?   

David Baraff. SIGGRAPH ’94    
Fast contact force computation for nonpenetrating rigid bodies.    


P124  
## Simulation of a Rigid Body System


![](/assets/08-18.png)   



---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/