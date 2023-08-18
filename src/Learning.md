# Lecture 11

P2  
## Outline   

 - Walking and Dynamic Balance   

 - Simplified Models   
     - ZMP (Zero-Moment Point)   
     - Inverted Pendulum   
     - SIMBICON   


P3  
## Walking

![](/assets/11-01.png)

![](/assets/11-02.png)

phases of a walking gait cycle   
Pirker and Katzenschlager 2017.    
**Gait disorders in adults and the elderly**.   


P4   
## Walking

![](/assets/11-04.png)

Walking: move without loss of contact, or flight phases   

P5  
## Walking   

![](/assets/11-05.png)

Running   


P7  
## Walking with Static Balance  

![](/assets/11-6.png)

![](/assets/11-7.png) 


P8   
## Walking with Static Balance   


![](/assets/11-08.png)
![](/assets/11-09.png)

P9   
## Walking with Static Balance  

![](/assets/11-10.png)

![](/assets/11-11.png)

P12  
## Zero-Moment Point (ZMP)

![](/assets/11-12.png)   

P13   
## Recall: A System of Links and Joints

![](/assets/11-13.png)   

$$
M\dot{v} +C(x,v)=f+f_J
$$


P16  
## Zero-Moment Point (ZMP)  

![](/assets/11-14.png)   

![](/assets/11-15.png)   


P18   
## Zero-Moment Point (ZMP)

Assuming the ground is flat and level    
so \\(p_i\\) - \\(p\\)  is always in the horizontal plane   


![](/assets/11-16.png)   


P19  
## Zero-Moment Point (ZMP)

![](/assets/11-1.png)   


P20   
## Zero-Moment Point (ZMP)


![](/assets/11-17.png)   


P21  
## Zero-Moment Point (ZMP)

![](/assets/11-19.png)   

![](/assets/11-20.png)   


![](/assets/11-11-1.png)   

Can we find \\(p\\) such that \\(\tau _{GRF}^{xz}=0\\) ?     


P22   
## Zero-Moment Point (ZMP)

![](/assets/11-18.png)   


P23  
## Zero-Moment Point (ZMP)

![](/assets/11-19.png)     

$$
\begin{align*}
f_{GRF}  & =\sum _{i}^{} f_i \\\\
 \tau _{GRF} & =\tau _{GRF}^y=\sum _{i}^{}(p_i-p)\times f_i^{xz}
\end{align*}
$$

P25  
## Zero-Moment Point (ZMP)   

The position of \\(p\\) is not known, but we assume   

$$
\tau _{GRF}^{xz}=0
$$

SO

$$
\tau _{GRF}=\tau _{GRF}^y
$$


P27  
## Zero-Moment Point (ZMP)

![](/assets/11-20.png)   

The foot should not move in a **stance phase**   

Static Equilibrium:   

$$
f_{\text{ankle}} + f_{\text{GRF}} + mg = 0  
$$

The moment around a reference point \\(o\\):    

$$
(u-o) \times f_{\text{ankle}} + (p-o) \times f_{\text{GRF}} + (x-o)\times mg + \tau _{GRF}^{y} + \tau _{\text{ankle}} = 0
$$


P28   
## Zero-Moment Point (ZMP)   

Horizontal components (moment projected onto \\(xz\\) plane):       

$$
((u-o) \times f_{\text{ankle}})^{xz} +( (p-o) \times f_{\text{GRF}} ) ^{xz}+ (x-o)\times mg + \tau _{\text{ankle}}^{xz} = 0
$$


P29   
## Zero-Moment Point (ZMP)

We can solve this equation to find \\(p\\)   


P31   
## Zero-Moment Point (ZMP)   

\\(p\\) is **called Zero-Moment Point (ZMP)** because it makes   

$$
\tau _{GRF}^{xz}=0
$$

and the horizontal moment   

$$
((u-o) \times f_{\text{ankle}})^{xz} +( (p-o) \times f_{\text{GRF}} ) ^{xz}+ (x-o)\times mg + \tau _{\text{ankle}}^{xz} = 0
$$

Only when 𝑝 is within the support polygon!    


P34   
## Zero-Moment Point (ZMP)   

If the solution of   

$$
((u-o) \times f_{\text{ankle}})^{xz} +( (p-o) \times f_{\text{GRF}} ) ^{xz}+ (x-o)\times mg + \tau _{\text{ankle}}^{xz} = 0
$$

\\(p\\) is outside the support polygon   

\\(p\\) could NOT be the center of pressure, because all the GRFs 
are applied within the polygon, so that    

$$
\tau _{GRF}^{xz}\ne 0
$$

Or, if \\({p}' \\) is the real center of pressure, we have    

$$
((u-o) \times f_{\text{ankle}})^{xz} +( ({p}'-o) \times f_{\text{GRF}} ) ^{xz}+ (x-o)\times mg + \tau _{\text{ankle}}^{xz} \ne 0
$$


P35   

the foot will rotate…    


P36   
## Zero-Moment Point (ZMP)  

The existence of ZMP is an indication of dynamic balance We can achieve balanced walking by controlling ZMP But how?    


P37   
## Simplified Models   

 - Simplify humanoid / biped robot into an abstract model   
    - Often consists of a CoM and a massless mechanism   
    - Need to map the state of the robot to the abstract model   
 - Plan the control and movement of the model   
    - Optimization   
    - Dynamic programming   
    - Optimal control   
    - MPC   
 - Track the planned motion of the abstract model   
    - Inverse Kinematics   
    - Inverse Dynamics   

![](/assets/11-24.png) 

![](/assets/11-22.png)   

![](/assets/11-23.png)   

  
P38  
## Example: ZMP-Guided Control   


![](/assets/11-26-1.png)  

![](/assets/11-25.png)   

![](/assets/11-26.png)  


P39   
## Example: ZMP-Guided Control


![](/assets/11-27.png)   


P41   
## Walking == Falling + Step Planning   


P43  
## Inverted Pendulum Model (IPM)

![](/assets/11-27-1.png)   

![](/assets/11-27-2.png)   

Inverted pendulum on a cart   


P45   
## Inverted Pendulum Model (IPM)   

 - Step Plan with IPM

![](/assets/11-28.png)  


P46   
## Inverted Pendulum Model (IPM)

 - Step Plan with IPM   
    - Map CoM of the character and the stance foot as IPM   
    - Plan the position of the next foot step so that the mass point rests at the top of the pendulum   
    - Create foot trajectory based on the step plan   
    - Compute target poses using IK   

![](/assets/11-29.png)  



P47   
## Inverted Pendulum Model (IPM)    

 - Step Plan with IPM

![](/assets/11-30.png)  


P49   
## SIMBICON   

 - SIMBICON (SIMple BIped Locomotion CONtrol)   
    - Yin et al. 2007   
 
![](/assets/11-31.png)  



P50   
## SIMBICON   

 - Step 1: develop a cyclical base motion   
    - PD controllers track target angles   
    - FSM (Finite State Machine) or mocap   


![](/assets/11-32.png)  



P51   
## SIMBICON   

 - Step 2:    
    - control torso and swing-hip wrt world frame   

![](/assets/11-33.png)  


P52  
## SIMBICON  

 - Step 3: COM feedback   

![](/assets/11-34.png)  


P53  
## SIMBICON   

 - Step 3: COM feedback    

![](/assets/11-35.png)  

P54   
## SIMBICON   
 
![](/assets/11-36.png)  


P55   
## Outline   

 - How to generalize to other motion?    

![](/assets/11-37.png)  


---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/
