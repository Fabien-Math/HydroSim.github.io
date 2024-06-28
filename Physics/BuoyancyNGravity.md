---
sort: 3
---

# Buoyancy and gravity


## Buoyancy

To compute buoyancy and gravity for the Zephyr, I tried several methods with one goal, being the most efficient in terms of computational time. All of them are enounced below and the chosen one described in details. 

### First approach, considering the boat as a box

In this first approach, I consider each part of the boat as boxes, $$4.7x0.7x0.6$$ m for the hull and $$2.3x0.3x0.3$$ for a float. This approach was the most rapid but the less precise. The hull convex volume being $$1.287~m^3$$ and a float volume being $$0.127~m^3$$, there is $$35\%$$ error in the volume of the hull and $$39\%$$ for a float.

This approach clearly not the solution to balance between precision and time efficiency.

### Second approach, volume approximation

This volume approximation consists in subdividing the boat into multiple known volumes. Briefly I created a 3D mesh of the boat with tetrahedron, calculate the centre and the volume of each cell. For each cell, if it is under sea level, the Archimedes force is calculated. Otherwise, the cell is skipped for buoyancy.

In this method, each cell has a binary state; above water or underwater, it creates steps in the buoyancy force which is not desired. To avoid these steps and have a relatively good precision, the number of cells must be large. However, computational time get too high to run in real time, making this solution unexploitable.

### Third approach, another volume approximation

At this stage, I must find a way to make the buoyancy force continuous and decrease the number of cells.

To solve continuity, calculating the depth of water in each cell enables to calculate a continuous immersed volume and thus a continuous force. In the second approach, it added a lot of calculation to determine the immersed volume inside cells.

To decrease number of cells, I started to think to a clever way to subdivide the boat.  
The one I found was to split the boat in multiple vertical boxes ($$47 \times 7$$ of $$0.1 \times 0.1~m$$ in the [implementation part](../Unity_implementation/BuoyancyNGravity.md)).  

The third approach works by creating a uniform mesh under the boat at a constant depth, each point of this mesh is the starting point of a vertical virtual box which ends at the deck height. For each box, it computes its intersection volume with the hull. After having the volume, it calculates the real height of the box from the deck. It returns this calculated point as well as the volume of the box computed.

The water depth is simply calculated by finding the difference between the bottom-centred point of the boxes and the sea level. With this distance known, the immersed volume is determined by proportioning the heights of the filled boxes to the water depth.

$$V_{im} = \dfrac{\text{water depth}}{\text{box height}}$$

Where $$\text{water depth} = \text{sea level} - \text{box bottom-centred point}$$.

Immersed volume allows to calculate the buoyancy force

$$\displaystyle \vec{F_A} = \rho_{water} V_{im} \vec{g}$$

where $$\displaystyle \rho_{water} = 1026 kg.m^{-3}$$ is the average sea water density, $$\displaystyle V_{im}$$ is the immersed volume and $$\displaystyle \vec{g}$$ is the standard acceleration of gravity $$\displaystyle \vec{g} = \begin{pmatrix}0 \\0 \\-9.81\end{pmatrix}$$

This method enables a fairly good distribution of buoyancy forces with few cells. Additionally, the computed force is continuous.  
On average, it runs in $$\displaystyle 0.159~ms$$, which allows running the simulation up to $$6,287~FPS$$ (Frame Per Second) with *Python* using the *NumPy* library over $$\displaystyle 500,000$$ iterations.


The centre of buoyancy is calculated by the formula below:  

$\displaystyle \vec{OB} = \dfrac{1}{\vec{F_A}} \sum \vec{F_{A_{box}}} \cdot \vec{OM}$

Where $$\displaystyle \vec{OB}$$ is the buoyancy centre coordinates, $$\displaystyle \vec{F_A}$$ the total buoyancy force vector, $$\displaystyle \vec{F_A_{box}}$$ the boxes' buoyancy force vector and $$\displaystyle \vec{OM}$$ the gravity centre coordinates of the immersed volume of boxes.

Moment due to Archimedes forces is defined as follows:

$$\displaystyle \vec{M_{buoy}} = \vec{GB} \times \vec{F_A}$$

Where $$\displaystyle \vec{M_{buoy}}$$ the moment vector due to buoyancy $$\displaystyle \vec{GB}$$ the distance vector between centre of gravity and centre of buoyancy.


## Gravity

Gravity is calculated for each cell by the Newton's formula with density.

$$\displaystyle \vec{P} = \rho V \vec{g}$$

where $$\displaystyle \rho$$ and $$\displaystyle V$$ are respectively the density and the volume of the cell being treated and $$\displaystyle \vec{g}$$ is the standard acceleration of gravity $$\displaystyle \vec{g} = \begin{pmatrix}0 \\0 \\-9.81\end{pmatrix}$$.  

The centre of gravity is calculated by the formula below:  

$\displaystyle \vec{OG} = \dfrac{1}{\vec{P}} \sum \vec{P_{box}} \cdot \vec{OM}$

Where $$\displaystyle \vec{OG}$$ is the gravity centre coordinates, $$\displaystyle \vec{P}$$ the total gravity force vector, $$\displaystyle \vec{P_{box}}$$ the boxes' gravity force vector and $$\displaystyle \vec{OM}$$ the gravity centre coordinates of boxes.

There isn't moment due to gravity because moments are defined in the gravity centre of the boat.

### Improvement of the third approach

To enhance this third method, I have defined sub-boxes that improve the distribution of mass within the boat. For example, boxes overlapping compartments in the boat have been divided into two separate groups to assign densities to hull-boxes and compartment-boxes individually.

