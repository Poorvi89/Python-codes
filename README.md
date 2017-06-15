
# GRAY-SCOTT MODEL
The Gray Scott model follows some simple rules. Given two sets of virtual particles u and v: 
1. There's a constant feed rate of u particles into the system 
1. If two v particles meet a u particle, they 'convert' it into another v particle 
1. There's a constant kill rate that removes v particles 

The Gray-Scott partial differential equations are given as
```
\frac{\partial u}{\partial t} = D_u \nabla ^2 u - uv^2 + F(1-u)
\frac{\partial v}{\partial t} = D_v \nabla ^2 v + uv^2 - (F + k)v
```
1. Discretize the reaction-diffusion equations using forward-time central-space and assume that Δx=Δy=δ.
2. For your timestep, set Δt=(9/40) δ^2/max(Du,Dv)
3. Use Neumann boundary conditions on all sides of the domain with q_x=q_y=0.

The domain is defined by:
1. Grid of points with dimension 192x192 points
2. Domain is 5m x 5m
3. Final time is 8000 seconds.

# STOKES FLOW
To solve Stokes flow in a square cavity, using the vorticity-streamfunction formulation.
Stokes flow, also known as creeping flow, refers to flows that are dominated by viscous forces and not by the advective/convective forces.  The Stokes-flow assumption works well for flows that have very low Reynolds number, much smaller than 1: very slow, highly viscous or flows at microscopic length scales. 
Stokes flow allows us to simplify the Navier-Stokes equations, eliminating the non-linearity.  Let's run through a quick derivation of the vorticity-transport equation with Stokes-flow assumptions. 
We start with the Navier-Stokes equations for incompressible flow:
```
\frac{\partial u}{\partial t} + u \cdot \nabla u = -\frac{1}{\rho}\nabla p + \nu\nabla^2 u\ \ \ \ \ (1)

```
If we scale Equation (1) to make it non-dimensional, we can rewrite it as
```
Re \left(\frac{\partial u^*}{\partial t} + u^* \cdot \nabla u^* \right) = -\nabla p^* + \nabla^2 u^*\ \ \ \ \ (2)
```
Where u^∗ and p^∗ are the non-dimensional velocity and pressure, respectively.  
To obtain Stokes flow, we assume that the Reynolds number approaches zero.  Applying that assumption to Equation (2) and dropping the stars, yields
```
\begin{equation} 0 = - \nabla p + \nabla^2 u\ \ \ \ \ (3) \end{equation}
```
Now, we apply the curl operator on both sides of the equation:
```
\begin{equation} \nabla \times 0 = \nabla \times \left( - \nabla p + \nabla^2 u\right)\ \ \ \ \ (4) \end{equation}
```

The left-hand side remains zero, while the first term on the right-hand side is
```
\begin{equation} \nabla \times - \nabla p = 0\ \ \ \ \ (5) \end{equation}
```
we arrive at the simplified vorticity transport equation for Stokes flow:
```
\begin{equation} \nabla ^2 \omega = 0\ \ \ \ \ (7) \end{equation}
```
Define the stream function ψ, such that
```
\begin{equation} u = \frac{\partial \psi}{\partial y} \text{   and   } v = - \frac{\partial \psi}{\partial x}\ \ \ \ \ (8) \end{equation}

```
In 2D, we can write out the vorticity as
```
\begin{equation} \omega = \frac{\partial v}{\partial x} - \frac{\partial u}{\partial y}\ \ \ \ \ (9) \end{equation}

```
which, combined with the previous equation yields another familiar looking equation:

```
\begin{equation} \nabla^2 \psi = -\omega\ \ \ \ \ (10) \end{equation}

```
We have a system of two coupled equations that can describe the fluid flow in a lid-driven cavity at very low Reynolds numbers.  

```
\begin{equation} \nabla^2 \omega = 0\ \ \ \ \ (11) \end{equation}
\begin{equation} \nabla^2 \psi = -\omega\ \ \ \ \ (12) \end{equation}


```
Solve Stokes flow in a lid-driven cavity





