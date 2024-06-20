---
sort: 5
---

# Aerodynamics

## Sails


### File format

***file_format.txt***
```
# NUMBER_OF_WIND_ANGLE
181

# WIND_ANGLES
-90    -88    -86    ...    -2    0    2    ...    86    88    90

# NUMBER_OF_SPEEDS_SERIES
5

# WIND_SPEEDS
speed_0    speed_1    speed_2    speed_3    speed_4

# NUMBER_OF_FLAP_ANGLE
7

# FLAP_ANGLES
flap_angle_0    flap_angle_1    flap_angle_2    flap_angle_3    flap_angle_4    flap_angle_5    flap_angle_6

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



# Appendices

## Python script 1

```python
def write_file(datas, names, speeds, parameters, out_name, out_path = "./"):
    """
    ## Description
        Write the output file to be treated by the C# code in Unity.        
    
    ### Args:
        datas (dict): format : {sheet_name_0: {wind_speed_name_ 0: {cd: [], cl: []}, wind_speed_name_ 1: {cd: [], cl: []}, ...}, sheet_name_1:...}
        names (list): Format : [sheet_names, wind_speed_names]
        speeds (list): List of speeds
        parameters (list): Format : [NUMBER_OF_COEFFICIENTS_PER_SERIES, STARTING_FLAP_ANGLE, INCREMENT_FLAP_ANGLE, STARTING_WIND_ANGLE, INCREMENT_WIND_ANGLE]
        out_name (str): Output file name
        out_path (str): Output file path with '/' at the end
    """
    sheet_names = names[0]
    ws_names = names[1]

    with open(out_path + out_name + ".txt", "w") as f:
        # Write parameters
        f.write("# NUMBER_OF_COEFFICIENTS_PER_SERIES\n")
        f.write(f"{parameters[0]}\n\n")
        f.write("# NUMBER_OF_SPEEDS_SERIES\n")
        f.write(f"{len(ws_names)}\n\n")
        f.write("# NUMBER_OF_FLAP_ANGLES\n")
        f.write(f"{len(sheet_names)}\n\n")
        f.write("# STARTING_FLAP_ANGLE\n")
        f.write(f"{parameters[1]}\n\n")
        f.write("# INCREMENT_FLAP_ANGLE\n")
        f.write(f"{parameters[2]}\n\n")
        f.write("# STARTING_WIND_ANGLE\n")
        f.write(f"{parameters[3]}\n\n")
        f.write("# INCREMENT_WIND_ANGLE\n")
        f.write(f"{parameters[4]}\n")

        for i, ws_n in enumerate(ws_names):
            f.write(f"\n# SERIE_{i},{speeds[i]:.5f}\n# ")
            for j in range(len(sheet_names)):
                f.write(f"flap_angle_{j}\t")
            f.write("\n")
            for alpha in range(parameters[0]):
                for sheet_n in sheet_names:
                    for c in ['cd', 'cl']:
                        f.write(f"{datas[sheet_n][ws_n][c][alpha]}\t")
                f.write('\n')    
    print("File written with success")

```
