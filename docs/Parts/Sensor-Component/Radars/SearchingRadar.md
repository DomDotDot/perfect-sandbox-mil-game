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

        1. `Range:` 1-360
        2. `Starting value:` 90

    2. **FOV Y** - Vertical field of view (in degrees). 

        1. `Range: 1-180.`
        2. `Starting value:` 70

    3. **Total effective detection range:**.  
    
        :::info Formula.
        `RangeKM = BaseRange * (Malleability_root / Current_Malleability_root) * (Minimum_FOV / Average_FOV)`.
        ::: 

            ```
                RanegKM = Range in kilometers
                BaseRange = 1 for every malleability 
                Malleability_root = the cube root of the Maximum Malleability (approximately 5.85 for 200).
                Current_Malleability_root = the cube root of the block's current Malleability.
                Minimum_FOV = Minimum FOV value of any radar is 1.
                Average_FOV = the arithmetic mean between FOV X and FOV Y.
            ```

        :::tip Example.
        *Calculation example:* For a 2x2x2 block (Malleability 8) and FOV 30x30 degrees: `RangeKM = 8 * (5.85 / 2) * (1 / 30) ≈ 0.78 kilometres`.
        ::: 

        :::tip Example.
        *Calculation example:* For a 2x2x2 block (Malleability 8) and FOV 1x1 degrees: `RangeKM = 8 * (5.85 / 2) * (1 / 1) ≈ 23.4 kilometres`.
        ::: 
        
    4. **Sensitivity:** Radar target sensitivity level. 

        1. `Range:` 1-100
        2. `Starting value:` 50

            * 1-30 (Low): Detection of large objects (ships, heavy equipment). Fewer false positives from interference.
            * 31-70 (Medium): Detection of aerial targets (aeroplanes, helicopters). Balance between detection and jamming.
            * 71-100 (High): Cartographic mode, detection of even small objects and terrain. High probability of false alarms from interference (birds, clouds).

---

### Component outputs and inputs

    ### Analogue

        * **Analogue input:**  
            `On/Off`

                1. [Bool]
                    * `Range:` 1
                    * `Description:` Radar is active.
                2. [Bool]
                    * `Range:` 0
                    * `Description:` Radar is inactive and does not consume energy.


    ### Arithmetic

        * **Digital output:** 
            `Current Azimuth`

                1. [Num]
                    * `Range:` 0-360
                    * `Description:` Outputs the current azimuth of the radar face in degrees. Updated if the radar is rotating.
                    
            


    ### Electrical

        * **Electrical input:** 
            `Electricity`

                * Required to supply power.


    ### Composite

        * **Composite Output:**
            `Radar Data`

                * `Architecture:` 32-bit
                * `Number Of Channels:` 32
                * `Occupied Channels:` 32
                * `Inbound channels:` 16
                * `Outbound channels:` 16
                * `Array:` [16][2]


            
            <details>
                <summary>
                    Channel data
                </summary>
                    <div>
                            <details>
                                <summary>
                                    Target Detection [1-16] - [nan-nan]
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

                                        <div>Channel list:</div>
                                        <br/>
      
                                        <div>Outbound [1] - Inbound [17]</div>
                                        <br/>
                                        <div>Outbound [2] - Inbound [18]</div>
                                        <br/>
                                        <div>Outbound [3] - Inbound [19]</div>
                                        <br/>
                                        <div>Outbound [4] - Inbound [20]</div>
                                        <br/>
                                        <div>Outbound [5] - Inbound [21]</div>
                                        <br/>
                                        <div>Outbound [6] - Inbound [22]</div>
                                        <br/>
                                        <div>Outbound [7] - Inbound [23]</div>
                                        <br/>
                                        <div>Outbound [8] - Inbound [24]</div>
                                        <br/>
                                        <div>Outbound [9] - Inbound [25]</div>
                                        <br/>
                                        <div>Outbound [10] - Inbound [26]</div>
                                        <br/>
                                        <div>Outbound [11] - Inbound [27]</div>
                                        <br/>
                                        <div>Outbound [12] - Inbound [28]</div>
                                        <br/>
                                        <div>Outbound [13] - Inbound [29]</div>
                                        <br/>
                                        <div>Outbound [14] - Inbound [30]</div>
                                        <br/>
                                        <div>Outbound [15] - Inbound [31]</div>
                                        <br/>
                                        <div>Outbound [16] - Inbound [32]</div>
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
                                        
                                        <div>Channel list:</div>
                                        <br/>
                                            
                                        <div>Inbound [17] - Outbound [1]</div>
                                        <br/>
                                        <div>Inbound [18] - Outbound [2]</div>
                                        <br/>
                                        <div>Inbound [19] - Outbound [3]</div>
                                        <br/>
                                        <div>Inbound [20] - Outbound [4]</div>
                                        <br/>
                                        <div>Inbound [21] - Outbound [5]</div>
                                        <br/>
                                        <div>Inbound [22] - Outbound [6]</div>
                                        <br/>
                                        <div>Inbound [23] - Outbound [7]</div>
                                        <br/>
                                        <div>Inbound [24] - Outbound [8]</div>
                                        <br/>
                                        <div>Inbound [25] - Outbound [9]</div>
                                        <br/>
                                        <div>Inbound [26] - Outbound [10]</div>
                                        <br/>
                                        <div>Inbound [27] - Outbound [11]</div>
                                        <br/>
                                        <div>Inbound [28] - Outbound [12]</div>
                                        <br/>
                                        <div>Inbound [29] - Outbound [13]</div>
                                        <br/>
                                        <div>Inbound [30] - Outbound [14]</div>
                                        <br/>                               
                                        <div>Inbound [31] - Outbound [15]</div>
                                        <br/>
                                        <div>Inbound [32] - Outbound [16]</div>


                                    </div>
                            </details>
                    </div>
            </details>
