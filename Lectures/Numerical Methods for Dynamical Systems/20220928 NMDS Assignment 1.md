# Assignment 1
$$F: \begin{pmatrix}x  \\ y\end{pmatrix} \longrightarrow \begin{pmatrix}x + a\sin(x+y)  \\ x+y\end{pmatrix}$$with $a = 0.7$.

In principle, with the plot of Sol_assig1, we can find an approximation of the 3 periodic point if we zoom in the 3 islands area. Same if we zoom in in the 4 islands.

### Steps
3. Find a good approximation of a 3-periodic point -> it's not just zooming in.
6. Mercè wants an explanation like we were explaining it to a friend.


Comment on step 3:

We have
$$F^{3}\begin{pmatrix}x  \\ y\end{pmatrix} = \begin{pmatrix}x  \\ y\end{pmatrix} \Leftrightarrow G(\vec x) = H(\vec x) - \vec x = 0 $$where $F^{3}= H$.

**Newton**
Start with an approximation from the plot (zooming in), then solve a code that solves  $D G(\vec x_{n})\Delta \vec x_{n} = -G(\vec x)$, so that we have a new approximation and we check again.
$\vec x_{n+1}= \vec x_{n}+ \Delta \vec x_{n}$, where $D G(\vec x_{n})\Delta \vec x_{n} = -G(\vec x)$
$\vec x_{n}$ approx

**Goal**
$\Delta \vec x_{n}$ s.t. $\begin{pmatrix}0 \\ 0\end{pmatrix} = G \begin{pmatrix}x_{n}+\Delta x_{n} \\ y_{n} + \Delta y_{n}\end{pmatrix} = G \begin{pmatrix}x_{n} \\ y_{n}\end{pmatrix} + DG \begin{pmatrix}x_{n} \\ y_{n}\end{pmatrix}\begin{pmatrix}\Delta x_{n} \\ \Delta y_{n}\end{pmatrix}$


How to compute $DG$? Either the explicit expression of $F^3$ and take the derivative or appy the chain rule $DF^{3}(\vec x) = DF(F^{2}(\vec x)) DF(F(\vec x)) DF(\vec x)$
you only need a routine to compute $DF$ and one to compute $F$

The code needs to be part of the pdf. 

By next Wednesday


$$DF\begin{pmatrix}x  \\ y\end{pmatrix} = \begin{pmatrix}1 + a\cos(x+y) & a\cos(x+y)  \\ 1 & 1\end{pmatrix}$$
