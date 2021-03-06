# ExploreUNIXprogrammingwithC
  ExploreUNIXprogrammingwithC is prepared to introduce a basic technique in UNIX/Linux programming. We will go through examples and practices of the C programming language using some basic functions of UNIX. 

## Day#1:WarmUp - Basic of UNIX
  In this section, we will introduce the fundamental concept of UNIX, Shell, and some easy examples of script program.
### 1.1 What is UNIX/Linux?
  **UNIX** is an [_Operating System(OS)_](https://en.wikipedia.org/wiki/Operating_system) which derive from a original AT&T Unix developed in the 1970s at the Bell Labs research center. 
##### _Wait! What is OS?_
  In a simplest word, an Operating System(OS) is fundamental system software for running the software on the computer. For example, Windows, UNIX(Linux), macOS. OS has many functions in a computer system, but here, we give a brief review on  _program execution_, _block_, _preemptive multitasking_, and _system call_. 
1. Program execution

      We start with CPU. [Central Processing Unit(CPU)](https://g.co/kgs/SCsae3) fetches, decodes, and executes       an instruction from program memory(instruction's address is determined by [Program Counter(PC)](https://en.wikibooks.org/wiki/Microprocessor_Design/Program_Counter)). OS itself is also a           program([kernel](https://en.wikipedia.org/wiki/Kernel_(operating_system))). During OS execution, PC determines kernel.         To execute a new program (here we call a.out), a.out is copied from file to memory, then modify the PC to point to             a.out. The CPU will now execute a.out. In a case of only one CPU is used, during the a.out program's execution, the kernel             cannot be executed. Here, timer [interrupt](https://en.wikibooks.org/wiki/Operating_System_Design/Processes/Interrupt)         is used to make it possible to return after the a.out program is executed. 
      
      ![program execution](https://github.com/mengsay/ExploreUNIXwithC/blob/master/figures/day1/programexecution.png)

2. Block

      To temporarily suspend the execution of the program is called **block**. Let's see an example.
      
      ```
      % sleep 5; echo goodmorning
      ```
      
      Executing this command, after about 5 seconds, _goodmorning_ will be printed on the screen. It means, execution is blocked for 5 seconds. However, during that 5 seconds, what was CPU doing? The answer is "CPU was wexecuting another program".
      Meaning, when a [process](https://g.co/kgs/Ea4Efj) is blocked, OS make a [process switching](https://www.streetdirectory.com/travel_guide/137699/computers/process_switching.html) to execute another process.
      
3. Preemptive Multitask

      Recent OS(including UNIX) has **preemptive multitask** function. Preemptive multitasking is an execution method that makes it appear that multiple programs are running at the same time. In preemptive multitasking, the OS uses the timer interrupt function of the CPU to switch processes anywhere in the program execution without blocking. 
      
4. System Call

      A [system call](https://g.co/kgs/JmKw8D) is used to interact with the kernel. (It is different between system call and library function.)
 
      ![OS](https://github.com/mengsay/ExploreUNIXwithC/blob/master/figures/day1/systemcall.png)  
      
#### **UNIX and Linux**[1]

* UNIX is a type of OS, Linux or macOS is a type of UNIX
* Linux is only a kernel
* Linux + Application + Library = Linux distribution (e.g. Ubuntu)
* Advantage of Linux : many of Linux distributions are free, source code is public

#### **User Interface**

On UNIX, there are two main user interfaces: window and shell.
* window([GUI](https://www.geeksforgeeks.org/what-is-the-difference-between-gui-and-cui/))
* shell([CUI](https://www.geeksforgeeks.org/what-is-the-difference-between-gui-and-cui/)): operate computer by [command](https://g.co/kgs/ip3zRh) input from keyboard

### 1.2 Shell

Shell is a core software of CUI(character user interface). It interprets and executes user's input commands. It is also called a command interpreter.

![macOS:terminal(bash shell)](https://github.com/mengsay/ExploreUNIXwithC/blob/master/figures/day1/terminalscreen.png)

_macOS terminal (bash shell)_

![macOS:finder(GUI:file manager)](https://github.com/mengsay/ExploreUNIXwithC/blob/master/figures/day1/finderscreen.png)

_macOS Finder (file manager)_

#### Command

* Syntax:
```
% command [-options][arguments]
```
e.g.1:(without option) to display a list of filenames
```
% ls 
```
e.g.2:(with option) to display a list of filenames with their information
```
% ls -l
```
![ls command](https://github.com/mengsay/ExploreUNIXwithC/blob/master/figures/day1/ls.png)

#### Types of Commands

* Internal commands of the shell (e.g. cd, pwd, etc.)
* External commands(program) 
  * machine language program (executable binary file)
  * script file (text file. e.g. shell script, Ruby script)
  
#### Pipelins

In shell, an output of a command can be used as an input of another command using **pipelining**.

* Syntax:
```
% command1 | command2
```
e.g. Use the output of \[ls -l command(list of filenames)\] as input \[wc -l command(count line number)\]
```
% ls -l | wc -l
```

#### Shell Script: Example
##### How to run?
* Use "bash" command as an interpreter

or

* Use "chmod" command to make script file executable and use its filename as an external command

sample1Script: 
```
# email.sh
echo -n "Input your email : "
read email
echo "Application form has been sent to $email."
```

sample1Result①:
```
% bash email.sh
Input your email : sample1@email1.com
Application form has been sent to sample1@email1.com.
%
```
sample1Result②:
```
% chmod +x email.sh
% ./email.sh
Input your email : sample1@email2.com
Application form has been sent to sample1@email2.com.
%
```

sample2Script: 
```
# loop
echo -n "loop = "
read loop
i=1
while (($i <= $loop))
do
  echo -n "loop#$i "
  i=$(($i+1))
done
```

sample2Result①:
```
% bash loop
loop = 3
loop#1 loop#2 loop#3
%
```
sample2Result②:
```
% chmod +x loop
% ./loop
loop = 3
loop#1 loop#2 loop#3
%
```




## References
[\[1\]](https://www.amazon.co.jp/%E4%BE%8B%E8%A7%A3UNIX-Linux%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%9F%E3%83%B3%E3%82%B0%E6%95%99%E5%AE%A4-%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0%E3%82%B3%E3%83%BC%E3%83%AB%E3%82%92%E4%BD%BF%E3%81%84%E3%81%93%E3%81%AA%E3%81%99%E3%81%9F%E3%82%81%E3%81%AE12%E8%AC%9B-%E5%86%A8%E6%B0%B8%E5%92%8C%E4%BA%BA-ebook/dp/B07D38LMT4/ref=sr_1_4?__mk_ja_JP=%E3%82%AB%E3%82%BF%E3%82%AB%E3%83%8A&dchild=1&keywords=unix%2Flinux&qid=1587973525&sr=8-4) Kazuto Tominaga. Illustrative UNIX / Linux programming class 12 lessons for mastering system calls (p.4)
