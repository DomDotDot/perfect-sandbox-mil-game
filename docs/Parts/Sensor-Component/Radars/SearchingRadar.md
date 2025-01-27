---
title: Searching Radar
sidebar_position: 1
---

## Searching Radar

## Description

    **Short Description:**

        A simple and inexpensive radar for detecting targets in a wide sector. Detects the presence of a target and its azimuth relative to the radar.

    **Expanded Description:**

        ‘Detection Radar’ is a basic radar designed for early warning of approaching targets.  It scans a wide area and reports the presence of a target in its field of view and determines its azimuthal direction.  This radar is ideal for building early warning and general situational awareness systems. Its simplicity and low cost make it an excellent choice for the early stages of the game or for installation on the periphery of a base.
        It has a ‘Sensitivity’ parameter to adjust for different detection conditions.

---

## Features

    1. **Maximum Traction:** 200
    2. **Energy consumption per hour (kwh):** Depends on current unit size

        :::info Formula
        `Consumption = 10 kwh * draught rate`.
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
        `Range = BaseRange * (Tightness_root / Current_Tightness_root) * (Minimum_FOV / Average_FOV)`.
        ::: 

            ```
                ``BasicDistance`` for 1x1x1 size and 45x45 degree FOV = 1000 metres.
                ``Toughness_root` = the cube root of the Maximum Toughness (approximately 5.85 for 200).
                `Current_FOV_root` = the cube root of the block's current pull.
                `Minimum_FOV` = 10 degrees (minimum FOV value).
                `Average_FOV` = the arithmetic mean between FOV X and FOV Y.
            ```

        :::tip Example.
        *Calculation example:* For a 2x2x2 block (pull 8) and FOV 30x30 degrees: ``Range = 1000 * (5.85 / 2) * (10 / 30) ≈ 975 metres``.
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
