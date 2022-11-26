# Assignment 2
*Idea*: Check that our software to integrate ODEs work

## Harmonic oscillator
**System**: A harmonic oscillator
$$\begin{cases}\frac{dx}{dt}= \; y \\ \frac{dy}{dt}= -x\end{cases}$$
***Exercise**:* The first integral is
$$H(x, y) = \frac{1}{2}(x^{2}+y^{2})$$
We know that the orbits are circles around the center, since $x^{2}+y*2 = cnt > 0$.

To find the tangent vector for a point (the sense of the orbits), we simply check a point in the $x$-axis:
$$P = \begin{pmatrix}x>0 \\ 0 \end{pmatrix}, \quad \begin{pmatrix}x' \\ y' \end{pmatrix}_{P}= \begin{pmatrix} 0 \\ -x \end{pmatrix}.$$
#### First part
1. In condition $\vec x = (1, 0)$, $t_{0}= 0$, $t_{max}=2\pi$ (16 digits of precision) -> check the final piont
2. Take $np = 50$ intermediate points and check them. All this forward in time (idir=1)
3. Repeat with idir=-1 (backward in time): From $t_{0} = 0$ to $t_{max}= -2\pi$.
4. Play with initial conditions and plot the output
5. Add in the code "Check of the first integral":
	1. Take an initial condition $(x_{0}, y_{0})$, compute $H(x_{0}, y_{0})$
	2. Along each point of the orbit, we should check that $H(x(t), y(t)) = H(x_{0}, y_{0})$

### Second part
1. Integrate the harmonic oscillator + variational equations (6 ODE)
	*Check*: 
	1. Take initial condition. 
	2. Integrate one period ($x_{1}, x_{2}, x_{3}, x_{4}, x_{5}, x_{6}$): the first two ocmponents were already checked in the previous part. To check the others 
	3. 
$$ \begin{pmatrix}x_{3} & x_{4} \\ x_{5} & x_{6} \end{pmatrix}= -1$$


	
	


