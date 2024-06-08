---
sort: 3
---

# Buoyancy

The goal of the method is to determine a discretization of the volume of the Zephyr to compute buoyancy.
                                   
It works by creating a uniform mesh under the boat at a constant depth, each point of this mesh is the starting point of a vertical virtual box which ends at the deck height. For each box, it computes its intersection volume with the hull with a stochastic method. After having the volume, it calculates the real height of the box from the deck. It returns this calculated point as well as the volume of the box computed.