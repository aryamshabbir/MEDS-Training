### **KEY TAKEAWAYS**

#### **From Digital Design and Computer Architecture Lectures By Onur Mutlu**

- #### **LECTURE 01:**

    1. **Course Overview:**
        - Objective: Understand how computers work "from the ground up" (transistors → gates → microprocessors).
        - Focus: Basics, principles, precedents, and tradeoffs in design

    2. **Key Concepts:**
        - Transformation Hierarchy:

        ![Computer Architecture Diagram](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/computer_architecture.png.png)
        
             

    3. **Computer Architecture Basics:**
        - The science and art of designing computing platforms.
        - Design Goals:
            - Highest Performance
            - Longest Battery Life
            - Best Average Performance

    4. **Transistors and Logic Gates:**
        - MOS Transistor:
            - nMOS: Closes circuit at high voltage.
            - pMOS: Closes circuit at low voltage.
            ![MOS Types](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/MOS_Types.png)
            
        - CMOS Transistors:
            - Combine n-type and p-type transistor.
            - NOT gate (inverter): Outputs inverse of input.
            - NAND Gate: Built using transistor networks (series and parallel).


    5. **Moore's Law and Innovation:**
        - Definition: Transistors count double every ~2 years.
        - Challenges: Heat dissipation, precision .manufacturing (e.g., EUV lithography).
- #### **LECTURE 02:**

    1. **Logic Circuit:**

        - Combinational Circuit(Memoryless)
        - Sequential Circuit(Has Memory)

        
    2. **Boolean ALgebra:**
     
        - Axioms:Identity,Complementarity,Distributive,De-Morgans.
        - Duality:Swap And/OR,1/0 to derive equivalent expression.
    3. **Standard Forms:**
    
        - Sum of Products(SOP):OR of minterms(AND combinations).
        - Product of Sums(POS):AND of maxterms(OR combinations).
    4. **Combinational Building Blocks:**

        - Decoder: *Input Pattern detector*
                    
            -  n input and 2^n outputs.
            -   used for address decoding.
            ![Decoder](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/Decoder.png)
            
        - Multiplexer: *Select one of the N inputs to connect it to the output*

            - based on the value of a log₂N-bit control signal.
            -   can implement lookup tables(LUTs) for arbitrary functions.
            

        - Full Adder:*Binary Addition similar to decimal addition*
           
           - Three inputs(A,B,Cin).
           - sum and carry outputs.
           
           ![Full_Adder](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/Full_Adder.png)

        - Programmable Logic Array(PLA):*Array of AND Gates followed by an array of OR Gate*
            
            - We program the connections from AND Gate output to OR Gate inputs to implement a desire logic function.
- #### **LECTURE 03:**

    1. **Advanced Combinantional Blocks:**

        - Comparator:

          - Check if N inputs values are exactly the same using XOR and AND Gates.
          
          ![Comparator](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/Comparator.png)

        - Tri-State Buffer:*Enables gating of different signals onto a wire*
            
            - Acts like a switch.
            - Output=input if enabled,else high impedance.
            - Enables shared buses(e.g, CPU-memeory communication).
            
            ![Tri-State-Buffer](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/Tri_Buffer.png)
            
    2. **Sequential Logic Circuits And Design:**
     
        - Basic Storage Elements:
            - S-R Latch:
                
                - Built from cross-coupled NAND/NOR gates.
                - S (Set): Drives output to 1.
                - R (Reset): Drives output to 0.
                - Avoid R=S=0: Causes metastability (Q and Q’ both 1).

                ![S-RLatch](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/SR_Latch.png)
            - Gated-D Latch:

                - Adds control via Write Enable (WE).
                - Transparent when WE=1 (output follows input).

                ![Gated-D-Latch](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/Gated-D-Latch.png)
                

            - D Flip-Flop:
              
                - Edge-triggered (captures input at clock edge).
                - Built from two latches (master-slave) to avoid transparency.
                - Rising-edge triggered: Updates output only on clock 0→1 transition.
                
                
            - Registers and Memory:

               - Register:Group of D flip-flops sharing a clock (e.g., 4-bit register).

               ![Register](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/Register.png)

               - Memory Arrays:

                   - Address decoder: Selects memory location.
                   - Multiplexer: Reads data from selected location.
                   - Example: 4x3 memory (4 addresses × 3 bits).
            - Finite State Machines:

                - Components:
                 
                  - States: Snapshots of system conditions
                  - Transitions: Rules for moving between states (based on inputs).
                  - Clock: Synchronizes state changes.

                   ![FSM](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/FSM.png)

                - Types:

                  - Moore FSM: Outputs depend only on current state
                  - Mealy FSM: Outputs depend on current state + inputs.
                - Design Steps:

                    - Define states and transitions (state diagram)
                    - Encode states (binary, output encoding).
                    - Implement combinational logic for next state/outputs.
    3. **Timings and synchronization:**

        - Synchronous Systems: Use a clock to coordinate state changes.
        - Asynchronous Systems: State changes occur immediately (e.g., combo locks).
    4. **Flip-Flop Types:**

        - Enabled: EN=1 allows updates.
        - Resettable: Sync/async reset to 0.
        - Settable: Forces output to 1.
- #### **LECTURE 04:**

    1. **Finite State Machine Overview:**

         - Purpose:Model systems with memory (outputs depend on current + past inputs).
         - Core Components:

              - States: Snapshots of system conditions 
              - Transitions: Rules to move between states (triggered by inputs/clock).
              - Clock: Synchronizes state changes in synchronous systems.
         - Types of State Machine:
          
             - Moore FSM
             - Mealy FSM
    2. **Differences B/W Moore and Mealy:**

          | Features  | Moore FSM | Mealy FSM |
          |-----------|-----------|-----------|
          |Output Dependence| Depends only on the current state| Depends on current state + inputs|
          |State Diagram| Outputs are labeled inside states (circles)|Outputs are labeled on transitions (arcs)|
          |Number of States| Typically requires more states for the same function|Often needs fewer states (inputs influence outputs directly)|
          |Glitch Risk|Lower (outputs stable until next state)|Higher (outputs may glitch if inputs change mid-cycle)|

          
- #### **LECTURE 05:**

    1. **HDL Basics and Methodologies:**

        - Purpose of HDLs:
        
            - HDLs enable easy description of hardware structures
            - HDLs enable seamless expression of parallelism inherent in hardware
        - Hierarchical Design:

            - Top-down: Start with top-level module and decompose into sub-modules until reaching leaf cells (e.g., logic gates).
            - Bottom-up: Build from primitive components (e.g., gates) into larger modules.
    2. **Verilog Module Structure:**

        - Module Definition:

        ```
               module example (input a, b, output y); 
                  assign y = a & b;  
               endmodule  

         ```
        ![Module](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/Module.png)

        - Multi-bit Signals: 
            
            - Use [MSB:LSB] notation (e.g., input [31:0] a for a 32-bit bus).
        - Manipulating Bits:

           - Bit Slicing
           - Concatenation
           - Duplication
    3. **Combinantional Logic Implementation:**

        - Behavioral vs. Structural:
            
             - Behavioral: High-level functional descriptions (e.g., assign y = (a == b) ? 1 : 0;).
             - Structural: Gate-level interconnections (e.g., instantiating AND/OR gates).
        - Operators:

            - Bitwise (&, |, ^), reduction (e.g., &a for AND of all bits), concatenation ({a, b}).
            - Conditional assignments (? : for multiplexers).
        - Number Representation in Verilog:

            - Format: N’Bxx
            - N: Number of bits (e.g., 8’b = 8-bit binary).
            - B: Base (b=binary, h=hex, d=decimal, o=octal).
            - xx: The actual value in the specified base.
    4. **Sequential Logic Implementation:**

        - Flip Flops and Latches:

            - Use always @(posedge clk) for synchronous logic (e.g., D flip-flops)
            - Non-blocking assignments (<=): Essential for sequential logic to avoid race conditions.

            ```
              always @(posedge clk) 
                 q <= d;  // Non-blocking assignment
            ```
            - Reset Mechanism:

                - Asynchronous: always @(posedge clk, negedge reset)
                - Synchronous: always @(posedge clk) with reset condition inside

    5. **Finite State Machine:**

        - Components:

            - State register: Stores current state (sequential).
            - Next-state logic: Combinational logic to determine next state
            - Output logic: Moore (output depends only on state) or Mealy (output depends on state + inputs).
            - Example: Divide By 3 counter
            ```
            parameter S0=0, S1=1, S2=2;
            always @(posedge clk) 
                  if (reset) state <= S0; 
                 else state <= nextstate; 
            ```
    6. **Blocking verses Non-Blocking:**

         - Use = for combinational logic (blocking).
         - Use <= for sequential logic (non-blocking).
         - Avoid Latches: Ensure all reg outputs are assigned in all branches of always blocks
    7. **Case Statements**

        - Useful for FSM and Multiplexers
        ```
        case (state) 
               S0: nextstate = S1; 
              default: nextstate = S0;
        endcase
        ```
    8. **Synthesis and Simulation:**

       -  Synthesis: Converts HDL to gate-level netlist 
       - Simulation: Verifies functionality before physical implementation
- #### **LECTURE 06:**

    1. **Circuit Delay ans its Variations:**

        - Delay is fundamentally caused by
        
            - Capacitance and resistance in a circuit
            - Finite speed of light 
        - Anything affecting these quantities can change delay

            - Rising (i.e., 0 -> 1) vs. falling (i.e., 1 -> 0) inputs
            - Different inputs have different delays
            - Changes in environment (e.g., temperature)
            - Aging of the circuit

            ![Delay](https://github.com/aryamshabbir/MEDS-Training/blob/main/png/Delay.png)

    2. **Combinational Circuit Timings:**
     
         - Delays are real
          
           - Propagation Delay (t_pd): Maximum time for output to stabilize after input change.
           - Contamination Delay (t_cd): Minimum time before output starts changing.
           - Both depend on gate delays, wire lengths, temperature, and voltage
        - Glitches:

          - Temporary incorrect outputs due to unequal path delays
          - Can be ignored if only steady-state output matters 
    3. **Sequential Circuit Timings:**

         - Flip Flop Constraints:

            - Setup Time : Input must be stable before the clock edge
            - Hold Time : Input must remain stable after the clock edge
            - Violations cause metastability (output stuck between 0/1)
        - Clock Period  must satisfy:

            - Setup Constraint: T_c > t_pcq (FF delay) + t_pd (combinational) + t_setup
            - Hold Constraint: t_ccq (FF delay) + t_cd (combinational) > t_hold.
        - Clock Skew:

            - Time differernce between two clock edges.
            - Effectively increases both t_setup and t_hold
    4. **Circuit Verification:**

        - Critical Path: Longest delay path limits max clock frequency
        - Tools (e.g., Vivado):

            - Automatically check timing constraints.
            - Report violations and suggest fixes (e.g., buffer insertion, logic optimization)
        - Fixing Violations:

             - Reduce combinational logic depth (pipeline).
             - Balance path delays.
            - Add buffers to fix hold violations.
    5. **Functional Verification:**

        - Testbenches:

           - Simple: Manually check outputs
           - Self-Checking: Compare outputs against expected values 
           - Golden Models: Use a reference design for automated comparison.



                       
                          
                    
                   
                
        


        
            

        
         

          
          


    
    


        
        
             
                  
                
             




    


                



         


