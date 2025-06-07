# ATM-Project-in-VHDL
Project “ATM” – FPGA-based (Basys 3) VHDL implementation of a simplified ATM with 4-digit PIN authentication, menu-driven balance inquiry, cash withdrawal with greedy algorithm and limit checks, cash deposit by denomination, multiplexed 4×7-seg display, five buttons, and RAM. Modular FSM design.

Insturctions:
- download zip file
- make sure you have Xilinx Vivado installed
- run divizor_de_frecventa (Vivado Project File)
- connect your Basys 3 FPGA to your pc and hit run bitstream in Xilinx Vivado
- after bitstream is completed you can test the ATM

How to use ATM:
## How to Use the FPGA ATM

### 1. Entering Your PIN
1. **Activate PIN entry**  
   - Flip **SW0** to ON.  
   - The 4×7-segment display will start a rolling counter on the **units** digit.

2. **Select each digit**  
   - While **SW0 = ON**, the counter increments continuously.  
   - When the display shows your desired digit in the current position, press **UP** to lock it in and advance to the next position (units → tens → hundreds → thousands).  
   - If **SW0 = OFF**, the counter pauses and no digit can be selected.

3. **Submit PIN**  
   - After locking in all four digits, press **ENTER** (center button) to submit your PIN and proceed to the main menu.  
   - **Note:** Keep SW0 high the entire time you’re choosing digits; lowering SW0 at any point will freeze the counter until you turn it back on.

### 2. Main Menu
After pressing **ENTER**, you’ll be redirected to a menu with four options:  
1. **Balance Inquiry**  
2. **Cash Withdrawal**  
3. **Cash Deposit**  
4. **Reserved** (not yet implemented)  

- To navigate through the menu, press **UP** to cycle options.  
- Press **ENTER**(center buton) to select your highlighted option.  
