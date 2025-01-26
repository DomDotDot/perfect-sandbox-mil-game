---
title: Electricity Laws
sidebar_position: 1
---

# Electricity Logic
1. The electrical system in the game is modelled on the basic principles of electricity, but with simplifications for game balance and convenience.
    1. Operating Principles: 
     Electricity in the game is based on the following key concepts: voltage, current, power, resistance.
        1. Voltage (Volts - V):
            1. Definition: Electrical voltage is the potential difference between two points in an electrical circuit that creates the ‘pressure’ for electric current to move.
            2. Presence in a circuit: Voltage is present in a circuit even if the circuit is open (no current flows).
            3. Regulation: Voltage is regulated by `Transformer' blocks (step up and step down).
            4. Effect on current: The higher the voltage, the more current can be ‘pushed’ through the circuit (all other things being equal).
            5. Necessity for operation: The presence of voltage is necessary for an electrical circuit to function. Without voltage, electricity will not function.
            :::tip
            Analogy
            Voltage can be compared to the pressure of water in a water pipe.
            :::
        2. current (Amps - A):
            1. Definition : Electric current is the directed movement of electric charges (electrons) through a conductor.
            2. Occurrence : Current occurs only in a closed electrical circuit in the presence of voltage.
            3. Current strength is the amount of electric charge flowing through the cross section of a conductor per unit time.
            4. Effect of load: The strength of current in a circuit increases with the number of electrical devices (load) connected and switched on.
            5. Calculation: The current in a circuit is calculated as the division of potential Power by voltage 
            :::info
            Power Formula:
            (Current = Potential Power / Voltage)
            :::

            :::tip
            Analogy
            Current can be compared to the amount of water flowing through a pipe per unit time.
            :::
        3. power (Watts - W):
            1. Definition: Electrical power is the amount of energy consumed or produced by an electrical device per unit of time.
            2. Calculation: Power is calculated as the product of voltage by amperage 
            :::info
            Power Formula:
            (Power = Voltage * Current).
            :::
            Types of power:
                1. Generated Power: The total power produced by power sources (e.g. turbines).
                2. Potential power: The power required to power all connected devices in a circuit at full load. This is the maximum power that the circuit can demand.
                3. Maximum Cable Power: The maximum power that an electrical cable can safely carry. Exceeding this value will result in overheating and damage to the cable.
        4. Resistance (Ohms - ohms):
            1. Definition: Electrical resistance is the property of a material or circuit element to prevent the passage of electric current.
            2- Artificial Resistance (Resistors): Resistors are used to artificially limit the current in a circuit to protect sensitive appliances from overloading.
            3- Automatic Resistance (In Appliances): Electrical appliances have their own internal resistance that is automatically accounted for in an electrical circuit.
            4. Natural resistance (of wires): The resistance of wires depends on their physical characteristics.
                :::note
                Increasing resistance:
                    Greater length of wire
                    Small wire thickness
                :::
                ::::note
                Decrease in resistance:
                    Small wire length
                    Large wire thickness
                :::
    2. Closed circuit: An electrical circuit functions only if it is closed. That is, there should be a continuous path for the current from the voltage source to the consumers and back again.
    3. Wiring:
        ‘Seamless Wiring": The game implements a “seamless wiring” system to simplify wiring over short distances. Within 100 herds, electrical devices can be connected to each other directly via logical electrical I/O, with no obvious wiring. This reduces visual noise and simplifies construction.
        Wires for long distances: To transmit power over distances greater than 100 herds, special wires must be used for phase and zero. These wires are created from copper blocks and physically connect electrical devices. This separation of wiring provides realism in long distance transmissions and gives the player control over the distribution of power over large areas.
    4. Circuit Shorting: Improper shorting of a circuit, such as up to a step-down transformer or in the middle of a phase, will cause a short circuit and failure of the electrical system at that location.
2. Electrical appliances and power
    1. Electrical appliances: These are units that require electrical energy to operate. These include motors, lamps, radars, guns, and other functional devices.
    2. Power Parameters of Appliances: Every electrical appliance has three key power parameters:
        1. Minimum Power: The minimum power (in watts) required to start the appliance. If the power delivered to the appliance is below the minimum wattage, the appliance will not operate.
        2. Critical Power: The power at which the appliance starts to operate at its maximum capacity and gradually deteriorates. Operation at critical power is not recommended for long-term use.
        3. Maximum Power: The maximum power that the appliance can withstand. Exceeding the maximum power will result in immediate destruction/short-circuiting of the appliance and will render it unusable.
    3. Power Consumption: Under normal conditions, an electrical appliance consumes exactly as much power as it needs to operate efficiently at the moment. However, if there is insufficient power in the electrical network, the power supplied to the appliance may be reduced, affecting its performance.
    4. Effect of voltage on appliances: Appliances designed for a certain voltage can be damaged if the mains voltage does not match their requirements. Transformers are necessary to harmonise the voltage between different parts of the electrical network and protect appliances from overvoltage or undervoltage.
    5. Power and performance: Power (and therefore voltage) affects the speed and efficiency of electrical appliances.
    :::tip.
    Example (Electric Motor):
        1. Standard operation (100% efficiency): A motor rated at 200 volts operates at 1.0 efficiency (standard performance) when supplied with 200 volts.
        2. Minimum power (efficiency ≈ 0): If voltage is supplied below the minimum value, the motor may not rotate or may rotate very slowly and inefficiently (efficiency approaches zero).
        3. maximum power (efficiency 2.0, but destruction): When the voltage is briefly increased to the maximum value, the motor may operate at higher output (e.g., efficiency 2.0), but this will cause it to overheat and destroy soon.
    :::
3. Batteries and Circuit Protection
    1. Batteries: Batteries are designed to store electrical energy. When needed, they can release the stored energy very quickly, providing a short burst of power.
    2. Risk of overloading: A sudden surge of power from batteries can overload the wires, especially if they are designed for a lower maximum power. This can cause the wires to explode.
    3. Shields: Shields (fuse boxes) are used to protect the electrical circuit from overloads and short circuits. Shields are installed at key points in the circuit and break the circuit when power exceeds the allowable capacity, preventing damage to cables and appliances.
4. Electrical circuit hierarchy
    In order to create a reliable and efficient electrical circuit in the game, it is recommended that the following hierarchy be followed:
        1. Power Generator (Turbine, Solar Panel, etc.): The source of electricity generation.
        2. Batteries (Optional): Storage of excess energy for later use.
        3. Shields (Fuses): Protection against overloads and short circuits at the start of the circuit.
        4. Step-up Transformer: Increasing voltage to transmit power over longer distances with less losses.
        5. Step-down transformer: Lowering the voltage to the required level for supplying power to appliances.
        6. Shields (Fuses): Additional protection on the section of the circuit upstream of the consumers.
        7. Electrical appliances (Motors, Lighting, Logic, etc.): Power Consumers.


    :::tip
        Example of a simple electrical circuit:
        Turbine -> Battery -> Shield -> Step-up transformer -> Long range wire -> Step-down transformer -> Shield -> Spotlight
    :::
