### SYNCHRONOUS-UP-COUNTER

NAME: P.VIGNESHWARAN

REF NO: 24900068

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**

/* write all the steps invloved */

Design: Implemented a 4-bit synchronous up counter that increments on every clock cycle and resets on the reset signal.

Testbench: Applied reset and observed the counter value.

Validation: Verified the functionality using a functional table to ensure correct counting behavior.





**PROGRAM**

/* Program for flipflops and verify its truth table in quartus using Verilog programming. 
module ripple (
    input clk,     // Clock input
    input reset,   // Reset input (active high)
    output [3:0] q // 4-bit output
);
    // Internal signals for flip-flops
    reg [3:0] q_int;
    // Assign internal register to output
    assign q = q_int;

   always @(posedge clk or posedge reset) begin
        if (reset) 
            q_int[0] <= 1'b0; // Reset the first bit to 0
        else 
            q_int[0] <= ~q_int[0]; // Toggle the first bit on clock edge
    end
    // Generate the other flip-flops based on the output of the previous one
    genvar i;
    generate
        for (i = 1; i < 4; i = i + 1) begin : ripple
            always @(posedge q_int[i-1] or posedge reset) begin
                if (reset) 
                    q_int[i] <= 1'b0; // Reset the bit to 0
                else 
                    q_int[i] <= ~q_int[i]; // Toggle the bit on clock edge of previous stage
            end
        end
    endgenerate
endmodule

Developed by: RegisterNumber:
*/

**RTL LOGIC UP COUNTER**
![ex-11 1](https://github.com/user-attachments/assets/c987d6b0-dfcf-4a53-a280-a9ed8bd4378c)


**TIMING DIAGRAM FOR IP COUNTER**
![ex-11 2](https://github.com/user-attachments/assets/50eddd5a-dfb0-4c42-a062-0df47fe08ab9)


**TRUTH TABLE**
![count-sequence-synchronous-counter](https://github.com/user-attachments/assets/d914f0c5-9832-4af3-b1d5-89d331c1a106)



**RESULTS**
 Implementing 4 bit synchronous up counter and validate functionality is done successfully.

