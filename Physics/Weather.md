---
sort: 2
---

# Weather

To simulate the weather, I will consider a statistical approach defining multiple probability functions to predict the weather randomly based on the previous weather states.

To define these function, I will use the Hermite interpolation which interpolate a function by knowing the value and the derivative in all considerated point.

For that, let's define a new function $$\varphi$$: 
$$\begin{align}
  \varphi(0) &= 0//
  \varphi'(0) &= 0//
  \varphi(1) &= 1//
  \varphi'(1) &= 0//
  \varphi'(\sigma_x) = \sigma
\end{align}
$$
Where $$\sigma$$ is a parameter of the function.

$$\varphi$$ must be a monotonically non-decreasing function and its values between 0 and 1.
