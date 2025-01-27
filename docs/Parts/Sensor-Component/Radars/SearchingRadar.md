---
title: Searching Radar
sidebar_position: 1
---

# Searching Radar

## Description

    **Short Description:**

        A simple and inexpensive radar for detecting targets in a wide sector. Detects the presence of a target and its azimuth relative to the radar.

    **Expanded Description:**

        `Searching Radar` is a basic radar designed for early warning of approaching targets.  It scans a wide area and reports the presence of a target in its field of view and determines its azimuthal direction.  This radar is ideal for building early warning and general situational awareness systems. Its simplicity and low cost make it an excellent choice for the early stages of the game or for installation on the periphery of a base.
        It has a ‘Sensitivity’ parameter to adjust for different detection conditions.

---

## Features

    1. **Maximum Malleability:** 200
    2. **Energy consumption per hour (kwh):** Depends on current unit size

        :::info Formula
        `Consumption = 10 kwh * Malleability`.
        :::

---

## Parameters

    1. **FOV X** - Horizontal field of view (in degrees). 

        1. `Range: 1-360.
        2. `Starting value: 90 degrees.`.

    2. **FOV Y** - Vertical field of view (in degrees). 

        1. `Range: 1-180.`.
        2. `Starting value: 70 degrees.`.

    3. **Total effective detection range:**.  
    
        :::info Formula.
        `Range = BaseRange * (Malleability_root / Current_Malleability_root) * (Minimum_FOV / Average_FOV)`.
        ::: 

            ```
                ``BasicDistance`` for 1x1x1 size and 45x45 degree FOV = 1000 metres.
                ``Malleability_root` = the cube root of the Maximum Malleability (approximately 5.85 for 200).
                `Current_Malleability_root` = the cube root of the block's current Malleability.
                `Minimum_FOV` = 10 degrees (minimum FOV value).
                `Average_FOV` = the arithmetic mean between FOV X and FOV Y.
            ```

        :::tip Example.
        *Calculation example:* For a 2x2x2 block (Malleability 8) and FOV 30x30 degrees: ``Range = 1000 * (5.85 / 2) * (10 / 30) ≈ 975 metres``.
        ::: 
        
    4. **Sensitivity:** Radar target sensitivity level. 

        1. `Range: 1-100.
        2. `Starting value: 50.`

            * *1-30 (Low):* * Detection of large objects (ships, heavy equipment). Fewer false positives from interference.
            * *31-70 (Medium):* Detection of aerial targets (aeroplanes, helicopters). Balance between detection and jamming.
            * *71-100 (High):* Cartographic mode, detection of even small objects and terrain. High probability of false alarms from interference (birds, clouds).

---

### Component outputs and inputs

    ### Analogue

        * **Analogue input:**  
            ‘On/Off’

                1. Signal ON (RIGHT).
                    * Radar is active
                2. Signal OFF (False).
                    * Radar is inactive and does not consume energy.


    ### Arithmetic

        * ** Digital output:** 
            ‘Current Azimuth’

                1. * Outputs the current azimuth of the radar face in degrees (0-360)
                    *Updated if the radar is rotating.
            


    ### Electrical

        * **Electrical input:** 

            ‘Power’

                * Required to supply power to operate the radar.

        ** **Electrical Output:** 

            ‘Energy Transit’. 

                * For connection to a further electrical circuit.

    ### Composite

        * **Composite Output:**

            **Number Of Channels:** 32 

            
            <details>
                <summary>
                    Channel data
                </summary>
                    <div>
                            <details>
                                <summary>
                                    Target Detection [1-16] - [1-16]
                                </summary>
                                    <div>
                                        <div>Description: Each channel corresponds to a potential goal.</div> 
                                        <br/>
                                        

                                        <div>Data type: Logical</div>
                                        <br/>
                                        

                                        <div>Values:</div>
                                        <br/>
                                            <div>Maximum value: 1</div>
                                            <br/>
                                                <div>The target is detected in the radar field of view and corresponds to the target sequence number.</div> 
                                                <br/>
                                            <div>Minimum value: 0</div>
                                            <br/>
                                                <div>The target is not detected or tracked on this channel.</div>
                                                <br/>
                                        
                                        <div>Received channels: nan</div>
                                        <br/>
                                        

                                        
                                            

                                        <div>Channel [1]</div>
                                        <br/>
                                        <div>Channel [2]</div>
                                        <br/>
                                        <div>Channel [3]</div>
                                        <br/>
                                        <div>Channel [4]</div>
                                        <br/>
                                        <div>Channel [5]</div>
                                        <br/>
                                        <div>Channel [6]</div>
                                        <br/>
                                        <div>Channel [7]</div>
                                        <br/>
                                        <div>Channel [8]</div>
                                        <br/>
                                        <div>Channel [9]</div>
                                        <br/>
                                        <div>Channel [10]</div>
                                        <br/>
                                        <div>Channel [11]</div>
                                        <br/>
                                        <div>Channel [12]</div>
                                        <br/>
                                        <div>Channel [13]</div>
                                        <br/>
                                        <div>Channel [14]</div>
                                        <br/>
                                        <div>Channel [15]</div>
                                        <br/>
                                        <div>Channel [16]</div>
                                        <br/>
                                    
                                    </div>
 
                            </details>

                            <details>
                                <summary>
                                    Azimuth Of the Target [17-32] - [1-16]
                                </summary>
                                    <div>
                                        <div>Description: Each channel corresponds to the azimuth of the detected target associated with the target detection channel with the same serial number.</div>
                                        <br/>
                                        

                                        <div>Data type: Arithmetic</div>
                                        <br/>
                                        
                                        
                                        <div>Values:</div>
                                        <br/>
                                        

                                            <div>Maximum value: 360</div>
                                            <br/>
                                                <div>The azimuth of the target in degrees relative to the radar.</div>
                                                <br/>
                                            <div>Minimum value: 0</div>
                                            <br/>
                                                <div>If the target is not detected on the corresponding detection channel, the value is 0.</div>
                                                <br/>

                                        
                                        <div>Received channels: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16</ div>
                                        <br/>
                                        
                                            

                                        <div>Channel [17]</div>
                                        <br/>
                                        <div>Channel [18]</div>
                                        <br/>
                                        <div>Channel [19]</div>
                                        <br/>
                                        <div>Channel [20]</div>
                                        <br/>
                                        <div>Channel [21]</div>
                                        <br/>
                                        <div>Channel [22]</div>
                                        <br/>
                                        <div>Channel [23]</div>
                                        <br/>
                                        <div>Channel [24]</div>
                                        <br/>
                                        <div>Channel [25]</div>
                                        <br/>
                                        <div>Channel [26]</div>
                                        <br/>
                                        <div>Channel [27]</div>
                                        <br/>
                                        <div>Channel [28]</div>
                                        <br/>
                                        <div>Channel [29]</div>
                                        <br/>
                                        <div>Channel [30]</div>
                                        <br/>                               
                                        <div>Channel [31]</div>
                                        <br/>
                                        <div>Channel [32]</div>


                                    </div>
                            </details>
                    </div>
            </details>
