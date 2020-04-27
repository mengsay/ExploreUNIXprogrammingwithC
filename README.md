# ExploreUNIXwithC
  ExploreUNIXwithC is prepared to introduce a basic technique in UNIX/Linux programming. We will go through examples and practices of C programming language using some basic functions of UNIX. 

## Day#1:Basic of UNIX
  In this section we will introduce: fundermental concept of UNIX, Shell, and some easy example of Script Language.
### 1.1 What is UNIX/Linux?
  **UNIX** is an [_Operating System(OS)_](https://en.wikipedia.org/wiki/Operating_system) which derive from a original AT&T Unix developed in the 1970s at the Bell Labs research center. 
##### _Wait! What is OS?_
  In a simplest word, an Operating System(OS) is a fundermental system software for running the software on the computer. For example, Windows, UNIX(Linux), macOS. OS has many functions in a computer system, but here, we give a brief review on:  _program execution_, _block_, _preemptive multitask_, _system call_. 
1. Program execution

      We start with CPU. [Central Processing Unit(CPU)](https://g.co/kgs/SCsae3) fetches, decodes and executes       an instruction from program memory(instruction's address is determined by [Program Counter(PC)](https://en.wikibooks.org/wiki/Microprocessor_Design/Program_Counter)). OS itself is also a           program([kernel](https://en.wikipedia.org/wiki/Kernel_(operating_system))). During OS execution, PC determines kernel.         To execute a new program (here we call a.out), a.out is copied from file to memory, then modify the PC to point to             a.out. The CPU will now execute a.out. In a case of only one CPU is used, during a.out program's execution, kernel             cannot be executed. Here, timer [interrupt](https://en.wikibooks.org/wiki/Operating_System_Design/Processes/Interrupt)         is used to make it possible to return after a.out program is executed. 
      
      ![program execution](https://github.com/mengsay/ExploreUNIXwithC/blob/master/figures/day1/programexecution.png)

2. Block

      To temporarily suspend the execution of the program is called **block**. Let's see an example.
      
      ```
      % sleep 5; echo goodmorning
      ```
      
      Executing this command, after about 5 seconds, _goodmorning_ will be printed on the screen. It means, execution is blocked for 5 seconds. However, during that 5 seconds, what was CPU doing? The answer is "CPU was wexecuting another program".
      Meaning, when a [process](https://g.co/kgs/Ea4Efj) is blocked, OS make a [process switching](https://www.streetdirectory.com/travel_guide/137699/computers/process_switching.html) to execute another process.
      
3. Preemptive Multitask

      Recent OS(including UNIX) has **preemptive multitask** function. 

### 1.2 Shell

### 1.3 Script Language
