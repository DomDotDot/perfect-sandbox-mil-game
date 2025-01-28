# Tracking Radar

## Description

    **Short description:**

        Improved radar for accurate target tracking. Provides advanced data about each target, including distance, azimuth, and altitude.

    **Expanded description:**

        `The Tracking Radar` is an advanced version of the detection radar, designed not only to detect, but also to track targets in detail.  It provides all the functionality of the detection radar, but additionally provides information about the distance to the target, its azimuth and altitude relative to the radar, as well as the time since detection.  These enhanced data make `Tracking Radar` an ideal choice for air defense and interception systems, allowing for more effective targeting and coordination of actions.  With its average cost and balanced characteristics, it is a universal solution for protecting military bases and facilities.
        It has a `Sensitivity` parameter to adjust to different detection conditions.

---

## Features

    1. `Maximum Malleability:` 200
    2. `Energy consumption per hour (kw/h):` Depends on the current block size

        :::info Formula
        `Consumption = 15 kw/h * Malleability`
        :::

---

## Parameters

    1. **FOV X** - Horizontal field of view (in degrees). 

        1. `Range:` 1-360
        2. `Default value:` 90

    2. **FOV Y** - Vertical field of view (in degrees). 

        1. `Range:` 1-180
        2. `Default value:` 70

    3. **Total effective detection range:** 
    
        :::info Formula.
        `RangeKM = BaseRange * (Malleability_root / Current_Malleability_root) * (Minimum_FOV / Average_FOV)`.
        ::: 

            ```
                RangeKM = Range in kilometers
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

    4. **Sensitivity:** The level of sensitivity of the radar to targets.

        1. `Range:` 1-100
        2. `Default value:` 50

            * 1-30 (Low): Detection of large objects (ships, heavy machinery). Fewer false alarms from interference.
            * 31-70 (Medium): Detection of aerial targets (airplanes, helicopters). A balance between detection and interference.
            * 71-100 (High):  Cartographic mode, detection of even small objects and terrain. There is a high probability of false alarms from interference (birds, clouds).

---

# Component outputs and inputs

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

        * **Composite output:**
        `Radar data`

                * `Architecture:` 128-bit
                * `Number of Channels:` 128
                * `Occupied Channels:` 80
                * `Inbound channels:` 16
                * `Outbound channels:` 64
                * `Array:` [16][5]

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

                                            <div>Outgoing [1] - Incoming [17],[33],[49]</ div>
                                            <br/>
                                            <div>Outgoing [2] - Incoming [18],[34],[60]</ div>
                                            <br/>
                                            <div>Outgoing [3] - Incoming [19],[35],[51]</ div>
                                            <br/>
                                            <div>Outgoing [4] - Incoming [20],[36],[52]</ div>
                                            <br/>
                                            <div>Outgoing [5] - Incoming [21],[37],[53]</ div>
                                            <br/>
                                            <div>Outgoing [6] - Incoming [22],[38],[54]</ div>
                                            <br/>
                                            <div>Outgoing [7] - Incoming [23],[39],[55]</ div>
                                            <br/>
                                            <div>Outgoing [8] - Incoming [24],[40],[56]</ div>
                                            <br/>
                                            <div>Outgoing [9] - Incoming [25],[41],[57]</ div>
                                            <br/>
                                            <div>Outgoing [10] - Incoming [26],[42],[58]</ div>
                                            <br/>
                                            <div>Outgoing [11] - Incoming [27],[43],[59]</ div>
                                            <br/>
                                            <div>Outgoing [12] - Incoming [28],[44],[60]</ div>
                                            <br/>
                                            <div>Outgoing [13] - Incoming [29],[45],[61]</ div>
                                            <br/>
                                            <div>Outgoing [14] - Incoming [30],[46],[62]</ div>
                                            <br/>
                                            <div>Outgoing [15] - Incoming [31],[47],[63]</ div>
                                            <br/>
                                            <div>Outgoing [16] - Incoming [32],[48],[64]</ div>
                                            <br/>

                                    </div>

                            </details>

                            <details>
                                <summary>
                                    Distance to the Target [17-32] - [1-16]
                                </summary>
                                    <div>
                                        <div>Description: Each channel corresponds to the distance to the detected target associated with the target detection channel with the same sequence number.</div>
                                        <br/>


                                        <div>Data type: Arithmetic</div>
                                        <br/>


                                        <div>Values:</div>
                                        <br/>


                                            <div>Maximum value: Depends on the radar range</div>
                                            <br/>
                                                <div>The distance to the target in meters.</div>
                                                <br/>
                                            <div>Minimum value: 0</div>
                                            <br/>
                                                <div>If the target is not detected on the corresponding detection channel, the value is 0.</div>
                                                <br/>


                                        <div>Received channels: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16</ div>
                                        <br/>

                                        <div>Channel list:</div>
                                        <br/>

                                            <div>Incoming [17] - Outgoing [1]</div>
                                            <br/>
                                            <div>Incoming [18] - Outgoing [2]</div>
                                            <br/>
                                            <div>Incoming [19] - Outgoing [3]</div>
                                            <br/>
                                            <div>Incoming [20] - Outgoing [4]</div>
                                            <br/>
                                            <div>Incoming [21] - Outgoing [5]</div>
                                            <br/>
                                            <div>Incoming [22] - Outgoing [6]</div>
                                            <br/>
                                            <div>Incoming [23] - Outgoing [7]</div>
                                            <br/>
                                            <div>Incoming [24] - Outgoing [8]</div>
                                            <br/>
                                            <div>Incoming [25] - Outgoing [9]</div>
                                            <br/>
                                            <div>Incoming [26] - Outgoing [10]</div>
                                            <br/>
                                            <div>Incoming [27] - Outgoing [11]</div>
                                            <br/>
                                            <div>Incoming [28] - Outgoing [12]</div>
                                            <br/>
                                            <div>Incoming [29] - Outgoing [13]</div>
                                            <br/>
                                            <div>Incoming [30] - Outgoing [14]</div>
                                            <br/>
                                            <div>Incoming [31] - Outgoing [15]</div>
                                            <br/>
                                            <div>Incoming [32] - Outgoing [16]</div>
                                            <br/>

                                    </div>
                                    <details>
                                <summary>
                                    Azimuth Of the Target [33-48] - [1-16]
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

                                            <div>Incoming [33] - Outgoing [1]</div>
                                            <br/>
                                            <div>Incoming [34] - Outgoing [2]</div>
                                            <br/>
                                            <div>Incoming [35] - Outgoing [3]</div>
                                            <br/>
                                            <div>Incoming [36] - Outgoing [4]</div>
                                            <br/>
                                            <div>Incoming [37] - Outgoing [5]</div>
                                            <br/>
                                            <div>Incoming [38] - Outgoing [6]</div>
                                            <br/>
                                            <div>Incoming [39] - Outgoing [7]</div>
                                            <br/>
                                            <div>Incoming [40] - Outgoing [8]</div>
                                            <br/>
                                            <div>Incoming [41] - Outgoing [9]</div>
                                            <br/>
                                            <div>Incoming [42] - Outgoing [10]</div>
                                            <br/>
                                            <div>Incoming [43] - Outgoing [11]</div>
                                            <br/>
                                            <div>Incoming [44] - Outgoing [12]</div>
                                            <br/>
                                            <div>Incoming [45] - Outgoing [13]</div>
                                            <br/>
                                            <div>Incoming [46] - Outgoing [14]</div>
                                            <br/>
                                            <div>Incoming [47] - Outgoing [15]</div>
                                            <br/>
                                            <div>Incoming [48] - Outgoing [16]</div>
                                            <br/>

                                    </div>
                            </details>

                            <details>
                                <summary>
                                    Target Height [49-64] - [1-16]
                                </summary>
                                    <div>
                                        <div>Description: Each channel corresponds to the height of the detected target associated with the target detection channel with the same sequence number.</div>
                                        <br/>


                                        <div>Data type: Arithmetic</div>
                                        <br/>


                                        <div>Values:</div>
                                        <br/>


                                            <div>Maximum value: Depends on the height of the map</div>
                                            <br/>
                                                <div>The height of the target in meters relative to the radar level.</div>
                                                <br/>
                                            <div>Minimum value: Depends on the depth of the map (may be negative)</div>
                                            <br/>
                                                <div>If the target is not detected on the corresponding detection channel, the value is 0.</div>
                                                <br/>


                                        <div>Received channels: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16</ div>
                                        <br/>

                                        <div>Channel list:</div>
                                        <br/>

                                            <div>Incoming [49] - Outgoing [1]</div>
                                            <br/>
                                            <div>Incoming [50] - Outgoing [2]</div>
                                            <br/>
                                            <div>Incoming [51] - Outgoing [3]</div>
                                            <br/>
                                            <div>Incoming [52] - Outgoing [4]</div>
                                            <br/>
                                            <div>Incoming [53] - Outgoing [5]</div>
                                            <br/>
                                            <div>Incoming [54] - Outgoing [6]</div>
                                            <br/>
                                            <div>Incoming [55] - Outgoing [7]</div>
                                            <br/>
                                            <div>Incoming [56] - Outgoing [8]</div>
                                            <br/>
                                            <div>Incoming [57] - Outgoing [9]</div>
                                            <br/>
                                            <div>Incoming [58] - Outgoing [10]</div>
                                            <br/>
                                            <div>Incoming [59] - Outgoing [11]</div>
                                            <br/>
                                            <div>Incoming [60] - Outgoing [12]</div>
                                            <br/>
                                            <div>Incoming [61] - Outgoing [13]</div>
                                            <br/>
                                            <div>Incoming [62] - Outgoing [14]</div>
                                            <br/>
                                            <div>Incoming [63] - Outgoing [15]</div>
                                            <br/>
                                            <div>Incoming [64] - Outgoing [16]</div>
                                            <br/>

                                    </div>
                            </details>
                            <details>
                                <summary>
                                    Time since Detection[65-80] - [1-16]
                                </summary>
                                    <div>
                                        <div>Description: Each channel corresponds to the time after the target is detected, which is associated with a target detection channel with the same sequence number.</div>
                                        <br/>


                                        <div>Data type: Arithmetic</div>
                                        <br/>


                                        <div>Values:</div>
                                        <br/>


                                            <div>Maximum value: 60 </div>
                                            <br/>
                                                <div>The maximum time to memorize a goal in seconds. It is reset if the target has been detected again on the corresponding detection channel</div>
                                                <br/>
                                            <div>Minimum value: 0</div>
                                            <br/>
                                                <div>If the target is not detected on the corresponding detection channel, the value is 0.</div>
                                                <br/>


                                        <div>Received channels: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16</ div>
                                        <br/>

                                        <div>Channel list:</div>
                                        <br/>

                                            <div>Incoming [65] - Outgoing [1]</div>
                                            <br/>
                                            <div>Incoming [66] - Outgoing [2]</div>
                                            <br/>
                                            <div>Incoming [67] - Outgoing [3]</div>
                                            <br/>
                                            <div>Incoming [68] - Outgoing [4]</div>
                                            <br/>
                                            <div>Incoming [69] - Outgoing [5]</div>
                                            <br/>
                                            <div>Incoming [70] - Outgoing [6]</div>
                                            <br/>
                                            <div>Incoming [71] - Outgoing [7]</div>
                                            <br/>
                                            <div>Incoming [72] - Outgoing [8]</div>
                                            <br/>
                                            <div>Incoming [73] - Outgoing [9]</div>
                                            <br/>
                                            <div>Incoming [74] - Outgoing [10]</div>
                                            <br/>
                                            <div>Incoming [75] - Outgoing [11]</div>
                                            <br/>
                                            <div>Incoming [76] - Outgoing [12]</div>
                                            <br/>
                                            <div>Incoming [77] - Outgoing [13]</div>
                                            <br/>
                                            <div>Incoming [78] - Outgoing [14]</div>
                                            <br/>
                                            <div>Incoming [79] - Outgoing [15]</div>
                                            <br/>
                                            <div>Incoming [80] - Outgoing [16]</div>
                                            <br/>

                                    </div>
                            </details>

                    </div>
            </details>

---