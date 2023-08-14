
P4   
## Welcome & Course Information   


 - Instructor: \\( \quad \quad \quad \\)Libin Liu (<http://libliu.info>)   
 - Website: \\( \quad \quad \quad \\) <https://games-105.github.io/>    
 - Lecture: \\( \quad \quad\quad  \\) Monday 8:00PM to 9:00PM (12 Weeks)    
 - Prerequisites: \\( \quad  \\) linear algebra, calculus,   
 \\( \quad \quad \quad \quad\quad \quad\\) programming skills (python),   
  \\( \quad \quad \quad \quad\quad \quad\\) probability theory, mechanics, ML, RL…   
 - Exercise:
     - Codebase: \\( \quad  \\)<https://github.com/GAMES-105/GAMES-105>    
     - **Submission**: \\( \quad  \\)<http://cn.ces-alpha.org/course/register/GAMES-105-Animation-2022/>   
     - **Register code**: \\( \quad  \\)**GAMES-FCA-2022**    
 - BBS: \\( \quad \quad \quad \quad \quad\\)<https://github.com/GAMES-105/GAMES-105/discussions>    
 - QQ Group: \\( \quad \quad  \quad\\)533469817     




P8   
## 3D Computer Graphics    

![](/assets/01-02.png)


P11   
## 3D Computer Animation

![](/assets/01-03.png)


P12   
## Why Do We Study Character Animation   


 - A character typically has 20+ joints, or 50-100+ parameters    
    - It is not super high-dimensional, so most animation can be created manually, by posing the character at keyframes    
    - **Labor-intensive, not for interactive applications**    

 ![](/assets/01-4.png)  

 - Character animation techniques   
    - Understanding the mechanism behind motions and behaviors   
    - Smart editing of animation/ Reuse animation / Generate new animation   
    - **“Compute-intensive”**     

 ![](/assets/01-05.png)  


P14  
## Character Animation Pipeline   

![](/assets/01-06.png)  


P16  
## Where does a Motion Come From   
 
![](/assets/01-07.png)  



P17
## Keyframe-based/Kinematic Approaches  


![](/assets/01-08.png)  



P19    
## Physics-based/Dynamic Approaches

![](/assets/01-09.png)  




P20   
## Character Animation Methods


![](/assets/01-10.png)  



P21   
## Character Animation Methods

low-level control   

![](/assets/01-11.png)  


P22   
## Character Animation Methods


high-level control

![](/assets/01-12.png)  


P25   
## Disney’s 12 Principles of Animation

![](/assets/01-13.png)  

[<http://the12principles.tumblr.com/>]



P27    
## Forward Kinematics

![](/assets/01-14.png)  

**Given** rotations of every joints    
**Compute** position of end-effectors    


P28   
## Inverse Kinematics   

![](/assets/01-15.png)  

**Given** position of end-effectors     
**Compute** rotations of every joints    


P29   
## Interpolation
 
![](/assets/01-16.png)  



P35   
## Motion Retargeting   

![](/assets/01-17.png)  

**Given** motions of a source character   
**Compute** motions for target characters with   
  - different skeleton sizes
  - different number of bones
  - different topologies
  - ……   


P37   
## Motion Graphs / State Machines

![](/assets/01-18.png)  

P38   
## Motion Graphs / State Machines

![](/assets/01-19.png)  

P39  
## Motion Graphs / State Machines

![](/assets/01-20.png)   

[Heck and Gleicher 2007, Parametric Motion Graphs]  

P40   
## Motion Graphs / State Machines

**Character Animation in Two-Player Adversarial Games**   
KEVIN WAMPLER,ERIK ANDERSEN, EVAN HERBST, YONGJOON LEE, and ZORAN POPOVIC Univoersity of Washington     


**Near-optimal Character Animation with Continuous Control**   
Adrien Treuille  \\(\quad\\)   Yongjoon Lee   \\(\quad\\)  Zoran Popovic    
University of Washington    


P43  
## Complex Motion Graphs


![](/assets/01-21.png)  


P46   
## Learning-based Approaches


![](/assets/01-22.png)  

P50   
## Cross-Modal Motion Synthesis

 - Audio-driven animation   
    - Music to dance    
    - Co-speech gesture   
    - ……   

[Ao et al. 2022. Rhythmic Gesticulator. SIGGRAPH Asia 2022]    


P51   
## Cross-Modal Motion Synthesis   


 - Natural language to animation   
    - Descriptions to actions   
    - Scripts to performance   
    - ……   


![](/assets/01-23.png)  



P53  
## Character Animation Methods  


![](/assets/01-24.png)  


P56  
## Character Animation Methods   


![](/assets/01-25.png)  


P58  
## Kinematic Approaches


![](/assets/01-26.png)  


P59   
## Physics-based Character Animation


![](/assets/01-27.png)  


P60 

## Ragdoll Simulation


![](/assets/01-28.png)  


P62  
## Physics-based Character Animation


![](/assets/01-29.png)  


P64   
## Motion Reconstruction with Sparse Sensors

![](/assets/01-30.png)  

P65  
## Motion Reconstruction with Sparse Sensors

[DeepMotion: Virtual Reality Tracking]   

P66

[Ye et al. 2022: Neural3Points]   


P67   
[Yang et al. 2022: Learning to Use Chopsticks]




P68   
## Character Animation Methods

![](/assets/01-31.png)  


P69  
## Physics-based/Dynamic Approaches   


![](/assets/01-32.png)  


P70   

## Physics-based/Dynamic Approaches   


![](/assets/01-33.png)  


P71   

## Force & Torque


![](/assets/01-34.png)  


P72   

## Proportional-Derivative (PD) Control  
  

![](/assets/01-35.png)  


P73   
## Tracking Controllers


![](/assets/01-36.png)  

P74   
## Tracking Controllers

[Hodgins and Wooten 1995, Animating Human Athletics]   



P77   
## Trajectory Crafting

NaturalMotion - Endorphin   



P80  
## Spacetime/Trajectory Optimization

![](/assets/01-037.png)  

[Liu et al 2010. SAMCON]


P81  
## Spacetime/Trajectory Optimization

[Wampler and Popović. 2009. Optimal gait and form for animal locomotion]    


P82   
## Spacetime/Trajectory Optimization

[Hamalainen et al. 2020, Visualizing Movement Control Optimization Landscapes]    



P84   
## Abstract Models   


![](/assets/01-38.png)  


P86   
## Abstract Models   

Inverted Pendulum Model

![](/assets/01-039.png)  

[Coros et al. 2010]



P88   
## Reinforcement Learning  

![](/assets/01-40.png)  

P90   

## DRL-based Tracking Controllers  

 
[Liu et al. 2016. ControlGraphs]    

[Liu et al. 2018]     

[Peng et al. 2018. DeepMimic]    


P91  
## Multi-skill Characters

State Machines of Tracking Controllers    



P92   

## Multi-skill Characters  

![](/assets/01-41.png)  

[Liu et al. 2017: Learning to Schedule Control Fragments]  



P95   
## Generative Control Policies


![](/assets/01-42.png)  



P96   
## Generative Control Policies


![](/assets/01-43.png)  



P100   
## Character Animation Methods  


![](/assets/01-44.png)  



P101  

## Character Animation Methods   

![](/assets/01-45.png)  

P103    
## About This Course    

 - What will not be covered   
    - How to use Maya/Motion Builder/Houdini/Unity/Unreal Engine…   
    - How to become an animator    

 - What will be covered   
    - Methods, theories, and techniques behind animation tools   
      - Kinematics of characters   
      - Physics-based simulation   
      - Motion control   

    - Ability to create an interactive character   



---------------------------------------
> 本文出自CaterpillarStudyGroup，转载请注明出处。
>
> https://caterpillarstudygroup.github.io/GAMES105_mdbook/