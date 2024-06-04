---
sort: 2
---

# Weather

To simulate the weather, I will consider a statistical approach defining multiple probability functions to predict the weather randomly based on the previous weather states.

To define these function, I could have use the Hermite interpolation which interpolate a function by knowing the value and the derivative in all considerated point.
To simplify the problem, I choose the Gompertz distribution [Link](https://en.wikipedia.org/wiki/Gompertz_distribution).  

This distribution is defined by two parameters $$\eta$$ and $$\beta$$, we will choose them to fit the correct distribution of pressure in the area considered.
