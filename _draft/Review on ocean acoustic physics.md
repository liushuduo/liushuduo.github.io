# Review on Acoustic Wave Equation

Recent research on array processing for ocean acoustics is concerned with exploiting to maximum advantage the combination of the complexities of the ocean environment, sophisticated acoustic models, array design and both narrow and broadband coherent processing techniques. Since the approach has much in common with matched filtering theory, it is termed **matched field processing (MFP)**. The performance of MFP heavily depends on the accuracy of model which is calculated by solving wave equation. General methods for solving wave equation are discussed in this review.

## Introduction to Wave Equation

The wave equation is a PDE that may constrain some scalar function $u=u(\boldsymbol{x}, t)$ of a time $t$ and spatial variables $\boldsymbol{x}=[x_1,\ldots,x_n]$. The equation is 
$$
\ddot{u}=c^2\nabla^2u\tag{1}
$$
where $\ddot{u}=\frac{\partial^2 u}{\partial t^2}$ and $\nabla^2$ is the ***Laplacian operator***. Wave equation is a **linear equation** so that any multiple of a solution is also a solution, and the sum of any two solution is again a solution. Hence, the wave equation can be analyzed as a linear combination of simple solutions that are sinusoidal waves.

## Physical Quantities in Acoustic

There are many physical quantities to describe acoustic propagation. Here common quantities are summarized with discussion of their relationship.

- **Density (kg/m^3):** $\rho=\rho_0+\rho'$ where $\rho_0$ is the ambient density and $\rho'$ is the infinitesimal acoustic density disturbance. 

- **Pressure (Pa N/m^2):** $p=p_0+p'$ where $p_0$ is the ambient pressure and $p'$ is the infinitesimal disturbance. $p'$ is also named *acoustic pressure*. $\tilde{p}$ is denoted for complex acoustic pressure. Sinusoidal $p'$ has magnitude $\mathcal{P}$.

> Acoustic processes are nearly *isentropy* (adiabatic and reversible). Pressure $p$ is function of $\rho$ and can be represented by a Taylor's expansion. The adiabatic state function is  
> $$
> p=p_0+(\frac{\partial p}{\partial \rho})_{\rho_0}\rho'+\frac{1}{2}(\frac{\partial^2p}{\partial\rho^2})_{\rho_0}\rho'^2+\ldots\tag{2}
> $$
> If $\rho'$ is small, only lowest order term need be retained. The *adiabatic bulk modulus* $K=\rho(\partial p/\partial\rho)_{\rho_0}$ 
> $$
> c^2\equiv(\frac{\partial p}{\partial\rho})_{\rho_0}=\frac{K}{\rho}
> $$
> If $\rho_0$ is constant, we have the linear state function:
> $$
> p'=p-p_0=\rho'c^2
> $$

- **Acoustic particle velocity (m/s):** $\boldsymbol{v}$. Designating $v$ for its norm, i.e., $v=\|\boldsymbol{v}\|_2$. $\tilde{v}$ for complex particle velocity. $\mathcal{V}$ for its magnitude.

> Using **conservation of mass**, we have the relation between density and particle velocity named *exact continuity equation*:
> $$
> \frac{\partial \rho}{\partial t}=-\nabla\cdot\rho\boldsymbol{v}\tag{3}
> $$

> Using **Newton's second law** we have the *Euler's equation* 
> $$
> \frac{\partial\boldsymbol{v}}{\partial t}+(\boldsymbol{v}\cdot\nabla)\boldsymbol{v}=-\frac{1}{\rho}\nabla p(\rho)\tag{4}
> $$

The three equation in citation blocks form the base of acoustic wave equation. To reduce the dimension of acoustic wave equation, we always separate time dependent factor $\mathrm{e}^{-j\omega t}$. All the physical processes are considered as sinusoidal processes. 

- **Velocity potential (m^2/s)**: $\phi$. $\boldsymbol{v}=\nabla\phi$.

- **Kinetic energy (J):** $E_k=\frac{1}{2}mv^2=\frac{1}{2}\rho_0V_0v^2$.

- **Potential energy (J):** $E_p=-\int_{V_0}^V p'\mathrm{d}V$. With linear state function, $E_p=\frac{1}{2}\frac{p'^2}{\rho_0c^2}V_0$.

- **Instantaneous energy density (J/m^3):** $\mathcal{E}_i=(E_k+E_p)/V_0=\frac{1}{2}\rho_0(v^2+\frac{p'^2}{\rho_0^2c^2})$. Considering the impedance relation of plane wave $p'/v=\rho_0c^2$. $\mathcal{E}_i=\rho_0 v^2=\frac{p'^2}{\rho_0c^2}=\frac{p'v}{c}$. 

- **Energy density (J/m^3):** $\mathcal{E}=\frac{1}{T}\int_0^T\mathcal{E}_i\mathrm{d}t$. For plane wave, $\mathcal{E}=\frac{1}{2}\rho_0\mathcal{V}^2=\frac{\mathcal{P}^2}{2\rho_0c^2}=\frac{\mathcal{PV}}{2c}$. For sinusoidal process, root-mean-square equals magnitude divided by $\sqrt{2}$. $\mathcal{E}=\rho_0 v_{rms}^2=\frac{p_{rms}v_{rms}}{c}$.

- **Instantaneous intensity (W/m^2):** $I(t)=pv$.

- **Intensity (W/m^2):** $I=\frac{1}{T}\int_0^TI(t)\mathrm{d}t$. For plane wave, $I=\frac{\mathcal{PV}}{2}$. For complex quantities, $I=\Re\{\tilde{p}^*\tilde{v}\}/2$.

- **Specific acoustic impedance:** $\tilde{z}=\tilde{p}/\tilde{v}$. For plane wave, $z=\rho_0c$.
- **Transmission loss (dB):** $TL=-10\log\frac{I(r,z)}{I_0}$, where $I_0$ is the intensity at 1-m distance from the source.

## Acoustic Wave Equation

The wave equation in an ideal fluid can be derived from hydrodynamics and the adiabatic relation between pressure and density. Equation (2) to (4) forms the base of acoustic wave equation, however, nonlinear wave equation. Some assumptions are needed to derive linear wave equation. For equation (3), we assume **ambient density $\rho_0$ is a sufficient weak function of time** and **disturbance $\rho'$ is very small**. Continuity function becomes linear  
$$
\frac{\partial \rho^{\prime}}{\partial t}=-\nabla \cdot\left(\rho_{0} \boldsymbol{v}\right)\tag{5}
$$
The ambient pressure $p_0$ is function of depth and density, e.g., $p_0=\rho_0 g z$ where $g$ is gravity acceleration.  With assumption $\rho'\ll1$ and $|(\boldsymbol{v}\cdot\nabla)\boldsymbol{v}|\ll|\partial\boldsymbol{v}/\partial t|$, (4) becomes
$$
\frac{\partial \boldsymbol{v}}{\partial t}=-\frac{1}{\rho_0}\nabla p'(\rho)\tag{6}
$$
With precedent discussion on state equation, we can obtain a **wave equation for pressure**. ***From now on, primes for pressure and density perturbations are omitted.***
$$
\rho \nabla\cdot(\frac{1}{\rho}\nabla p)-\frac{1}{c^2}\frac{\partial^2 p}{\partial t^2}=0
$$
 If density is **constant**, above formula can be replaced by the standard form of the wave equation:
$$
\nabla^2p-\frac{1}{c^2}\frac{\partial^2 p}{\partial t^2}=0
$$
**Wave equation for particle velocity: **
$$
\frac{1}{ \rho}\nabla(\rho c^2\nabla\cdot\bold{v})-\frac{\partial^2 \bold{v}}{\partial t^2}=0
$$
Under the assumption of constant density, velocity potential $\phi$ satisfies the wave equation:
$$
\nabla^2\phi-\frac{1}{c^2}\frac{\partial^2 \phi}{\partial t^2}=0
$$
Particle displacement is defined by $\boldsymbol{v}=\partial \boldsymbol{u}/\partial t$. Displacement potential $\psi$ is defined by $\boldsymbol{u}=\nabla\psi$. Consider inhomogeneous wave equation for displacement potential (with constant density $\nabla\cdot\rho=0$):
$$
\nabla^{2} \psi-c^{-2} \frac{\partial^{2} \psi}{\partial t^{2}}=f(\mathbf{r},t)
$$

where $f(\boldsymbol{r},t)$ represents the volume injection as a function of space and time. The wave equation for displacement potential is natural since underwater sound is produced by natural or artificial phenomena through forced mass injection.

### Computation Solution to Acoustic Wave Equation

It is relatively easy to solve wave equation (1), if $c$ is independent or approximately independent with the environment. And analytic solutions can be given in many cases. However, the ocean is a very complicated environment where sound speed $c$ is function of many factors such as depth $z$, temperature $T$, salinity $S$, etc. A empirical formula for sound speed is 
$$
c=1449.2+4.6 T-0.055 T^{2}+0.00029 T^{3}
+(1.34-0.01 T)(S-35)+0.016 z.
$$
If we assume $c$ varies only with **ocean depth**, the model is termed **range independent**. A model that also permits $c$ (ocean environment) horizontal variations is termed **range dependent**. In both case, analytic solutions cannot be given and computational methods are required. 

### The Helmholtz Equation

We have the time-domain inhomogeneous wave equation for displacement potential
$$
\nabla^{2} \psi-c^{-2} \frac{\partial^{2} \psi}{\partial t^{2}}=f(\mathbf{r}, t)
$$
Applying Fourier transform to the formula above we have frequency-domain wave equation, or *Helmholtz equation*.
$$
[\nabla^2+k^2(\bold{r})]\psi(\bold{r}, \omega)=f(\bold{r}, \omega)
$$
where $k(\bold{r})=\frac{\omega}{c(\bold{r})}$.

The *Green's function* in free field satisfies the inhomogeneous Helmholtz equation
$$
\left[\nabla^{2}+k^{2}\right] g_{\omega}\left(\mathbf{r}, \mathbf{r}_{0}\right)=-\delta\left(\mathbf{r}-\mathbf{r}_{0}\right)
$$



$$
p=\rho\frac{\partial \phi}{\partial t}\\
\boldsymbol{v}=-\nabla\phi
$$
