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

# NUMBER_OF_WIND_SPEED
5

# WIND_SPEEDS
speed_0 speed_1 speed_2 speed_3 speed_4

# NUMBER_OF_FLAP_ANGLE
7

# FLAP_ANGLES
flap_angle_0    flap_angle_1    flap_angle_2    flap_angle_3    flap_angle_4    flap_angle_5    flap_angle_6

# SERIE_0, WIND_SPEED_speed_0
# flap_angle_0  flap_angle_1    flap_angle_2    flap_angle_3    flap_angle_4    flap_angle_5    flap_angle_6
cd_0_0  cl_0_0  cd_1_0  cl_1_0  cd_2_0  cl_2_0  cd_3_0  cl_3_0  cd_4_0  cl_4_0  cd_5_0  cl_5_0  cd_6_0  cl_6_0
...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...     ...
cd_0_180  cl_0_180  cd_1_180  cl_1_180  cd_2_180  cl_2_180  cd_3_180  cl_3_180  cd_4_180  cl_4_180  cd_5_180  cl_5_180  cd_6_180  cl_6_180

...
# SERIE_i,speed_i
# flap_angle_0  flap_angle_1    flap_angle_2    flap_angle_3    flap_angle_4    flap_angle_5    flap_angle_6
...

# SERIE_7,speed_7
# flap_angle_0  flap_angle_1    flap_angle_2    flap_angle_3    flap_angle_4    flap_angle_5    flap_angle_6
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
def write_file(datas, names, speeds, angles, flap_angles, out_name, out_path = "./"):
    """
    ## Description
        Write the output file to be treated by the C# code in Unity.        
    
    ### Args:
        datas (dict): format : {sheet_name_0: {wind_speed_name_ 0: {cd: [], cl: []}, wind_speed_name_ 1: {cd: [], cl: []}, ...}, sheet_name_1:...}
        names (list): Format : [sheet_names, wind_speed_names]
        speeds (list): Ascending sorted list of wind speeds
        angles (list): Ascending sorted list of wind angles
        flap_angles (list): Ascending sorted list of flap angles
        out_name (str): Output file name
        out_path (str): Output file path with '/' at the end
    """

    sheet_names = names[0]
    ws_names = names[1]

    with open(out_path + out_name + ".txt", "w") as f:
        # Write parameters
        f.write("# NUMBER_OF_WIND_ANGLE\n")
        f.write(f"{len(angles)}\n\n")
        f.write("# WIND_ANGLES\n")
        for a in angles:
            f.write(f"{a:.2f}\t")
        f.write("\n\n")
        f.write("# NUMBER_OF_WIND_SPEED\n")
        f.write(f"{len(speeds)}\n\n")
        f.write("# WIND_SPEEDS\n")
        for s in speeds:
            f.write(f"{s:.2f}\t")
        f.write("\n\n")
        f.write("# NUMBER_OF_FLAP_ANGLE\n")
        f.write(f"{len(flap_angles)}\n\n")
        f.write("# FLAP_ANGLES\n")
        for fa in flap_angles:
            f.write(f"{fa:.2f}\t")
        f.write(f"\n")

        for i, ws_n in enumerate(ws_names):
            f.write(f"\n# SERIE_{i}, WIND_SPEED_{speeds[i]:.5f}\n# ")
            for fa in flap_angles:
                f.write(f"flap_{fa:.1f}_deg\t")
            f.write("\n")
            for alpha in range(len(angles)):
                for sheet_n in sheet_names:
                    for c in ['cd', 'cl']:
                        f.write(f"{datas[sheet_n][ws_n][c][alpha]}\t")
                f.write('\n')
    
    print("File written with success")
```
