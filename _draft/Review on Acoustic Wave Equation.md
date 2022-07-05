# Review on Acoustic Wave Equation

Recent research on array processing for ocean acoustics is concerned with exploiting to maximum advantage the combination of the complexities of the ocean environment, sophisticated acoustic models, array design and both narrow and broadband coherent processing techniques. Since the approach has much in common with matched filtering theory, it is termed **matched field processing (MFP)**. The performance of MFP heavily depends on the accuracy of model which is calculated by solving wave equation. General methods for solving wave equation are discussed in this review.

## Introduction to Wave Equation

The wave equation is a PDE that may constrain some scalar function $u=u(\boldsymbol{x}, t)$ of a time $t$ and spatial variables $\boldsymbol{x}=[x_1,\ldots,x_n]$. The equation is 
$$
\ddot{u}=c^2\nabla^2u\tag{1}
$$
where $\ddot{u}=\frac{\partial^2 u}{\partial t^2}$ and $\nabla^2$ is the *Laplacian operator*. Wave equation is a **linear equation** so that any multiple of a solution is also a solution, and the sum of any two solution is again a solution. Hence, the wave equation can be analyzed as a linear combination of simple solutions that are sinusoidal waves.

## Acoustic Wave Equation

### Computation Solution to Acoustic Wave Equation

It is relatively easy to solve wave equation (1), if $c$ is independent or approximately independent with the environment. And analytic solutions can be given in many cases. However, the ocean is a very complicated environment where sound speed $c$ is function of many factors such as depth $z$, temperature $T$, salinity $S$, etc. A empirical formula for sound speed is 
$$
c=1449.2+4.6 T-0.055 T^{2}+0.00029 T^{3}
+(1.34-0.01 T)(S-35)+0.016 z.
$$
If we assume $c$ varies only with **ocean depth**, the model is termed **range independent**. A model that also permits $c$ (ocean environment) horizontal variations is termed **range dependent**. In both case, analytic solutions cannot be given and computational methods are required. 

