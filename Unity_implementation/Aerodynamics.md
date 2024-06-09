---
sort: 5
---

# Aerodynamics

## Sails


### File format

***file_format.txt***
```
# NUMBER_OF_COEFFICIENTS_PER_SERIES
181

# NUMBER_OF_SPEEDS_SERIES
5

# NUMBER_OF_FLAP_ANGLES
7

# STARTING_ANGLE
0

# INCREMENT
2

# SERIE_0,speed_0
# flap_angle_0    flap_angle_1  flap_angle_2  flap_angle_3  flap_angle_4  flap_angle_5  flap_angle_6
cd_0_0  cl_0_0  cd_1_0  cl_1_0  cd_2_0  cl_2_0  cd_3_0  cl_3_0  cd_4_0  cl_4_0  cd_5_0  cl_5_0  cd_6_0  cl_6_0
...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...
cd_0_180  cl_0_180  cd_1_180  cl_1_180  cd_2_180  cl_2_180  cd_3_180  cl_3_180  cd_4_180  cl_4_180  cd_5_180  cl_5_180  cd_6_180  cl_6_180

...
# SERIE_i,speed_i
# flap_angle_0    flap_angle_1  flap_angle_2  flap_angle_3  flap_angle_4  flap_angle_5  flap_angle_6
...

# SERIE_7,speed_7
# flap_angle_0    flap_angle_1  flap_angle_2  flap_angle_3  flap_angle_4  flap_angle_5  flap_angle_6
cd_0_0  cl_0_0  cd_1_0  cl_1_0  cd_2_0  cl_2_0  cd_3_0  cl_3_0  cd_4_0  cl_4_0  cd_5_0  cl_5_0  cd_6_0  cl_6_0
...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...
cd_0_180  cl_0_180  cd_1_180  cl_1_180  cd_2_180  cl_2_180  cd_3_180  cl_3_180  cd_4_180  cl_4_180  cd_5_180  cl_5_180  cd_6_180  cl_6_180
```

```warning
Make sure to respect the spacing betwen lines! Else, the file will be read incorrectly!  
cx_i_j is for the i-th flap angle and for the j-th angle, 'x' equal 'd' or 'l'.
```


This file can be generated using the [python script 1](#python-script-1)


## Other consideration

Neglect about everything else than sails ^^' with why. 