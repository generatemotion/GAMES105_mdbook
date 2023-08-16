# Lecture 05

P2   
## Outline   

 - Motion Capture     
    - History and modern mocap systems   

 - Motion Synthesis    
    - Motion retargeting    
    - Motion transition     
    - Motion graph    


P3  
## Motion Capture   


How to get motion data?   

P23   

![](/assets/05-01.png)  


P29   
## Motion Synthesis   

How to use motion data?   


P31    
## Using Motion Data

![](/assets/05-02.png)  


P32   

## Motion Retargeting   

 - Retarget a motion to drive a character with    
    - Different number of bones    
    - Different bone names   
    - Different reference pose   
    - Different bone ratios    
    - Different skeletal structure    
    - ……    

P34   
## Motion Retargeting   


 - A possible retargeting pipeline   
     - Map bone names   
     - Scale translations   
     - Copy or retarget joint rotations to fix reference pose   
     - Postprocessing with IK   
       - Foot-skating   
       - Self penetration    
     - ……

![](/assets/05-03.png)  

![](/assets/05-04.png)  


P38
## Motion Transition 

![](/assets/05-05.png)  


P39   
## Motion Transition    

![](/assets/05-06.png)  


P40   
## Motion Transition    

![](/assets/05-07.png)  


P44  
## Motion Transition 


![](/assets/05-08.png)  

P45   
## Motion Transition 

![](/assets/05-09.png)  


P46   
## Motion Transition

$$
p(t)=(1-\phi (t))p_0(i)+\phi (t)p_1(i)
$$

P55  
## “Facing Frame”    
    
 - A special coordinate system that moves horizontally with the character with one axis pointing to the “facing direction” of the character    


![](/assets/05-10.png)  

$$
\begin{align*}
 R & = \theta e_y \\\\
 t & = (t_x,0,t_z)
\end{align*}
$$

P56   
## “Facing Frame”  


 - A special coordinate system that moves horizontally with the character with one axis pointing to the “facing direction” of the character   

 - Possible definitions of \\(R\\)    
 - \\(R\\) is the **y-rotation** that aligns the z-axis of the global frame to the heading direction    
 - \\(R\\) is the **y-rotation** that aligns x-axis of the global frame to the average direction of the vectors between shoulders and hips    
 - Decomposition root rotation as \\(R_0=R_yR_{xz}\\)     


P58   
## Rotation Decomposition


![](/assets/05-11.png)  


P62   
## Motion Transition 

 - How to compute this transformation?    

![](/assets/05-12.png)  


P68   
## Path Fitting


![](/assets/05-13.png) 


P69   
## Motion Composition  


 - Computationally generating motions according to   
    - User control   
    - Objects in the same environment   
    - Movements of other characters   
    - ……   


P70  
## Motion Graphs


![](/assets/05-14.png)  


P71   
## Motion Graphs


![](/assets/05-15.png)  


P72  
## Segment Motion Data 


![](/assets/05-16.png) 


P73  
## Segment Motion Data 


![](/assets/05-17.png)  

 - Distance map   
    - Each pixel represents the difference between a pair of poses   
    - Local minima are potential transition point   


Lucas Kovar, Michael Gleicher, and Frédéric Pighin. 2002. **Motion graphs**.    
*ACM Trans. Graph*. 21, 3 (July 2002),  


P74   
## Motion Synthesis   


 - State-machines   
    - Nodes represent motion clips   
    - Edges represent potential transitions   
    - Transitions are triggered when necessary   
      - User input   
      - Clip end   
    - Check immediate connections for the next clip    
      - May need deeper search   

![](/assets/05-18.png) 



P75   
## Interactive Animation Pipeline


![](/assets/05-19.png)   



P78  
## Motion Matching?   


 - Clip → Pose   
 - Short clip →   
 “Raw” and long motion data   



---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/