# Project creation
Start the project
1. Use the Windows key to bring up the search bar for Vivado.
2. Start Vivado.
3. Under Quick Start, choose Create Project.
4. Hit Next to use the assist at creating projects (Wizard).
5. Fill in the project name (lab2_board_demo) and file location.
6. Default is rtl project, which is what you want so just click Next.
7. Don't create a new file yet, just click Next.
8. No constraint file yet, so just click Next again.
9. Select the `Board` tab. Under `Name` find PYNQ-Z1.
10. Select PYNQ-Z1 in table below. Make sure that the Part is xc7z020clg400-1 or it may cause problems later.
11. Choose Finish.

    5. Force a constant value on an input line (signal)

    1) Select the signal -> right click -> force constant -> force value -> 1
   
   ![force constant](../lab1/rightclick_force_constant.png)

   ![right click](../lab1/rightclick_input_constant.png)

   # Setting up a constraints file

Download the constraints file at https://github.com/cs456s24/cs456s24/tree/main/lab2 
