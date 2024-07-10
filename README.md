#OBJECTIVE:
To understand the working of a scalar pipelined processor by simulating the different components of software level.
Assume that each piipeline stage takes 1 cycle.\\

##HOW TO RUN AND EXECUTE THE CODE IN WINDOWS:\\

STEP 1: Run by using following commands
COMMAND 1: g++ .\main.cpp
COMMAND 2: ./a.exe --dcache FILE_DIRECTORY_OF_DCACHE --icache FILE_DIRECTORY_OF_ICACHE --rf FILE_DIRECTORY_OF_RF
Then,
Both DCache.txt file,output.txt will contain the expected results.These files will be newly formed or overwritten if previously exists.If you want to pass these files names use flags --dcacheout and --out respectively.
FOR EXAMPLE:
g++ .\main.cpp
./a.exe --dcache .\input\DCache.txt --icache .\input\ICache.txt --rf .\input\RF.txt

OVERVIEW:

1. input

   1. ICache.txt
      This file contains the contexts of Instruction Cache.
   2. DCache.txt
      This file contains the contents of Data Cache.
   3. RF.txt
      This file contains the contents of Register File.

2. output

   1. DCache.txt
      This file contains of Data Cache reflecting all changes applied during execution.
   2. Output.txt
      This file contains of information like number of instructions executed, number of instructions of each type(Arithmetic,Logical,Shitf,Memory,Control and Halt Instructions),CPI(clock cycles per instruction),number of stalls,number of stalls of each type(Data and Control stalls).

3. main.cpp

OVERALL LOGIC:
We maintain a seperate queue called nop to keep track of the stalls; that is if there is a control hazard then we insert two NOP instructions in the queue and for data hazards or RAWs we insert accordingly.
while fetching instruction we will look at the queue, if queue id empty then we proceed to fetch from PC or if it's not empty then we pass the NOP instruction.
#   P i p e l i n e _ P r o c e s s o r 
 
 
