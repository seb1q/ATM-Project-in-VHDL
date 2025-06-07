# ATM-Project-in-VHDL
Project “ATM” – FPGA-based (Basys 3) VHDL implementation of a simplified ATM with 4-digit PIN authentication, menu-driven balance inquiry, cash withdrawal with greedy algorithm and limit checks, cash deposit by denomination, multiplexed 4×7-seg display, five buttons, and RAM. Modular FSM design.

Insturctions:
- download zip file
- make sure you have Xilinx Vivado installed
- run divizor_de_frecventa (Vivado Project File)
- connect your Basys 3 FPGA to your pc and hit run bitstream in Xilinx Vivado
- after bitstream is completed you can test the ATM

## How to Use the FPGA ATM

### 1. Entering Your PIN
1. **Activate PIN entry**  
   - Flip **SW0** to ON.  
   - The 4×7-segment display starts a rolling counter on the **units** digit.

2. **Select each digit**  
   - While **SW0 = ON**, the counter increments continuously.  
   - When it shows your desired digit, press **UP** to lock it in and move to the next position (units → tens → hundreds → thousands).  
   - If **SW0 = OFF**, the counter pauses.

3. **Submit PIN**  
   - After all four digits are locked, press **ENTER** (center) to submit and enter the main menu.  
   - **Note:** SW0 must remain ON while choosing digits.

### 2. Main Menu
After **ENTER**, the display shows one of four options:  
1. **Balance Inquiry**  
2. **Cash Withdrawal**  
3. **Cash Deposit**  
4. **Reserved** (not implemented)

- Press **UP** repeatedly to cycle through options.  
- Press **ENTER** to select the highlighted operation.  
- Press **DOWN** at any time to return to the main menu.

### 3. Balance Inquiry
- Select “Balance Inquiry” and press **ENTER**.  
- Your current balance is shown.  
- Press **DOWN** to return to the main menu.

### 4. Cash Withdrawal
1. **Start withdrawal**  
   - After selecting “Cash Withdrawal,” a rolling counter appears on the **units** digit (like PIN entry).

2. **Select amount**  
   - While **SW0 = ON**, the counter runs; press **UP** to lock each digit in sequence (units → tens → … → thousands).  
   - When you’ve set the final digit, press **ENTER** to confirm.

3. **Review banknotes**  
   - The display cycles through denominations **500**, **200**, **100**, **50**, **10**, **5**, **1**; the **first digit** shows how many of each note will be dispensed.

4. **Update balance**  
   - Press **LEFT** after reviewing to deduct the amount and return to the main menu.

### 5. Cash Deposit
1. **Start deposit**  
   - After selecting “Cash Deposit,” a rolling counter appears on the **units** digit.

2. **Select number of notes**  
   - For each denomination (**500**, **200**, **100**, **50**, **10**, **5**, **1**), the display shows the note value and a counter on the first digit.  
   - While **SW0 = ON**, the counter increments; press **ENTER** (center) to lock in the number of notes for that denomination and advance to the next.

3. **Review total**  
   - After the last denomination, the display shows the **total sum** of all deposited notes.

4. **Update balance**  
   - Press **LEFT** to add the deposit to your balance and return to the main menu.

---

**Button Summary**  
- **SW0 ON/OFF**: start/pause rolling counter  
- **UP**: lock digit & advance (PIN/amount) or cycle menu items  
- **ENTER**: confirm digit, menu selection, or note count  
- **DOWN**: return to main menu  
- **LEFT**: finalize transaction (update balance)


