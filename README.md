# Operating Systems Note Page (To-be Revised)



## To-Do

- [x] Install Ubuntu Virtual Machine

    - Ubuntu 16.04
    - Install Virtual Box and Virtual Box: Guest Additions

- [ ] ​

- [ ] Operating Systems HW Zero

    ​



## Bash/Shell Commands

    top                         : how many running processes  
    
    &                           : Backgrounds a process  
    
    JOBS                        : Lists all jobs  
    
    fg                          : Foreground a process  
                                        - _Keyboard I/O is enabled  
    
    bg                          : Background a process
                                        _Keyboard I/O is disabled
    
    cntrl + c                   : Stops a job
    
    -p                          : <Tag> Provides process id of a job
    
    vi mem.c                    : reads the file
    
    man Pthread_create          : manual for pthread
    
    pwd                         : present working directory
    
    echo $PATH                  : echo the path variable
    
    whereis pwd                 : location of the pwd command
    
    stdout
    
    stdin
    
    stderr 
    
    kill -9 <pid>
    
    wait(), waitpid()
    	waits for a child process to finish executing
    	not a sleep function
    	locking a parent process from proceeding until a child process exits
    	
    ps aux | ec -l
    
    more _pgDown
    
    less_pgUp       CTRL_F DOWN

## [ Key Combos, Linux Operations for processes ]

    Create
                - Create a new process
    
    Destroy
                - Terminate a process (CTRL+C)
    
    Wait
                - Wait for a process to complete/stop
    
    Misc Control
                - Suspend process (cntrl+z)
                - Resume process (fg, bg)

## [Bash]:
    sh                          :   file extension for bash files
    
    ./a0.sh                     :   ./ for current directory
    
    #                           :   - comment character in Bash
                                            #Q1 - How many processess
    
    chmod u+x a0.sh             : chmod user+execute_permission filename
    
    ./test.sh > output.txt      :   redirect standard out to a file
    
    cat output.txt              :   Prints out the output.txt contents to the terminal
    
    gedit &                     :   run gedit in th bacground
    
    vi 

## Memory Mapping (Address Translation):

>    #### Virtual Address Space :arrow_right: Physical Memory Location
>
>    `[OS  Does this for us]`

## PROCESSES VS THREADS

Both of them help us to speed things up

> - #### Processes:   
>
>   - [Google Chrome]
>     - Less likely to crash
>     -  Better job at isolation
>     - Memory is independent
>     - Heavy Weight (Initialization overhead)
>
> - ###### Threads:
>
>   - [Firefox]
>     - Crashes when a tab fails
>     - Sharing the same memory space with a parent process, less isolation
>     - Thread pool, sharing mem. (1..100 threads)
>     - Light Weight (Initialization overhead)



    (Synchronization)
        Coordinating who goes first, who goes next
        Operating system process scheduling
        Time Slice
            10sec
        Context Switches
    (Collisions)
    
    (ISOLATION)
        Isolating programs
    
    (Initialization overhead)
            The time it takes to get started

###### What would be the shared mem. for threads?
            Shared or independent?
            would each thread have its own stack or share a common stack?

|                   |                AKA                 | Multi Thread? | MultiProcess | Note                                                    |
| ----------------- | :--------------------------------: | :-----------: | :----------: | :------------------------------------------------------ |
| Code Segmentation |                                    |    Shared     | Not Shared*  |                                                         |
| Stack             |             Call Stack             |  Not Shared   |  Not Shared  | Can't share the stack<br />flow control for every stack |
| Heap              | Dynamic mem.<br /> (malloc & mmap) |    Shared     |  Not Shared  | Dynamic, Maybe not sure how much mem. you need          |
| Data Segment      |          Global Variables          |    Shared     |  Not Shared  |                                                         |

##### `Shared Library: .DLL and the linux equivelant, .SO`

# April 2nd, 2018

### *Context Switching*

Most bash scripts I have seen begin with 

```
#!/bin/bash
```



> did not include this in your sample, yet it still worked
>
> Why did it work? and/or why is this usually included if it is not needed

###### sh is also used

```bash
#!/bin/sh
```

### What is a fork used for? Such as in real-world application

> Often used to write shells

### What is CPU virtualization?

> Isolation; 

### How do you schedule processes manually

> turns out that you cant necessarily schedule manually; although we do have the ability to influence the OS through the `nice` command

What's an example of a process state that's blocked

> When a process is blocked by I/O

## Fork()

> Creates a new process - 
>
> CPU schedule is going to determine which is going to happen first

## Exec()

Supports for writing an eternal program


> ###### There are 6 types:
>
> `execl(), execlp(), execle(), execv(), execvp(), execvp(), execvpe`
>
> List of pointers (Terminated by null pointer)
>
> to strings provided as arguments... ( arg0, arg1, ... argn )
>
> > in "`wc -l <filename>` " 
> >
> > `wc` and `readme.txt or <filename>` are char*
> >
> > `-l` will count the number of lines in a file 
>
> ***Common use case:***
>
> > Write a new program which wraps a legacy one
> >
> > ### input :arrow_right: [BLACK BOX] :arrow_right: output
> >
> > Providing a new interface to an old system: Web services
> >
> > Legacy program thought of as a "Black  Box"

## Virtualizing the CPU

> How does the cpu support running so many jobs simultaneously?
>
> Through `Time Sharing`

> #### Direct :arrow_right: Kernel Mode
>
> #### LDE :arrow_right: User Mode



------



## <u>Linux</u> `time` <u>Command</u> 

> ***Example Use***:
>
> > `time ./pthread 100000000`
>
> `time`command will print the time spent in these different modes

> ## ***Limited Direct Execution CH6***
>
> Computer boot sequence OS with direct execution
>
> With direct execution:
>
> > How does the OS stop a program from running and switch to another to support time sharing?
> >
> > How do programs hare disks and perform I/O of they are given direct control?



> ## ***Control Trade-off***
>
> #### Too little Control
>
> > - No security
> > - No time sharing
>
> #### Too much Control
>
> > - Too much OS overhead
> > - Poor performance for compute & I/O
> > - Complex API (System calls), difficult to use



## CPU MODES

##### Utilize CPU privilege Rings (Intel x86)

> User mode: ring 3 - untrusted mode
>
> > Exception registers
> >
> > HALT instruction
> >
> > MMU instructions

### SYSTEM CALLS

> Implement restricted "OS" operations
>
> Kernel exposes key functions through an API
>
> > Device I/O ( )

```
Cooperative multitasking OSes
```

### Multitasking 

> ​	Preemptive multitasking (32 7 64 bit OSes) (initiates trap)
>
> ​	Save register values of the current processes to its kernel stack
>
>  	General Purpose regiters
>
> ​	PC: Program counter (Instruction Pointer)
>

## Context Switching



# Operating Systems April 4th 2018: Scheduling Algorithms and Metrics 

> In the fork code examples, why is both the child and parent executed?
>
> ​	because the child is a psudo "clone" of the child, allowing for multiple opportunities to evaluate the execution of the process



> If a time slice is longer than the amount of time a process needs to complete, doe the machine still wait for the timer interrupt to context switch?
>
> 	- Relinquish the CPU to the OS immediately when the task is complete



## <u>How can we minimize context switching (C/S) overhead?</u>

- Are processes using their full time slice?
  - The time slice should be selected carefully
- HW support (on the CPU) can minimize overhead
  - Ex. CPU should not flush mem page table cache
- Avoid having threads BLOCK

			Blocking induces a context switch

			When checking lock availability:
		
			Requesting a lock that is unavailable cause a C/S

Perform short lived busy waiting to check for LOCK availability

​		Helps avoid C/S

> There are three states to the CPU
>
> - Running  :arrow_right: Blocked (Acquire a lock)
> - Ready
> - Blocked

> ##### Preemptive multi-tasking -- is the timer interrupt the only method for the OS to regain control of the CPU?
>
> - What are CPU modes?
>   - User mode (Protected mode):arrow_left: Limited Direct Execution (LDE) (11)
>   - Unused (10)
>   - VM (01)
>   - Kernel 00 :arrow_left: (DE) Diret Execution more

## Scheduling Metrics

- **Metrics**: A standard measure to quantify to what degree a system possesses some property. Metrics provide repeatable techniques to quantify and compare systems.
- **Measurements** are the numbers derived from the application of metrics

### Scheduling Metric #1: **turn-around time**

> The time at which the job completes minus the time at which the job arrived in the system
>
> - T<sub>turnaround</sub> = T <sub>completion</sub> - T<sub>arrival</sub>
> - Turnaround time is different from execution time

###  <u>Scheduling Metric #2: fairness</u>

> Jains fairness index	
>
> Quantifies if jobs receive a fair share of **system resources**
>
> 1. n Processes
>
> 2. X<sub>i</sub> is the time share of each process
>
> 3. Worst case = 1/n
>
> 4. Best case = 1
>
>    > Consider n=3, worst case = .333, best case = 1
>    >
>    > With n = 3 and x<sub>1</sub> = .2, x<sub>2</sub> = .7, x<sub>3</sub> = .1, fairness = .62 

### Scheduling Metrics #3: Response Time

> Time from when job arrives until it starts execution
>
> > T<sub>response</sub> = T<sub></sub>

## <u>Schedulers, Scheduling Algorithms</u>

### FIFO: First in First out

> - Very simple, easy to implement
>
>  Consider: 
>
> > - 3sec x 10sec jobs, arrival: A B C

#### Convey Effect

Large job begins first, then multiple small jobs wont begin execution until the large job is completed

### Shortest Job First (SJF)

> Given that we now execution times in advance:
>
> - Run in order of duration, shortest to longest
> - Non preemptive scheduler
> - This is not realistic
> - Arrival: A, B, C

#### SJF: With Random Arrivals

- > If jobs arrive at anytime:
- > > A @ t=0sec, B @ t= 10sec, C@t=10sec

### STCF - Shortest Time to Completion First
- > Add preemption to the Shortest Job First Scheduler
- > - Also called preemptive shortest job first (PSJF)

##### STCF - (Practice Question #1)
> #### Consider: 
>
> - A<sub>len</sub> = 100 A<sub>Arrival</sub> = 0
> - B<sub>len</sub> = 10, B<sub>Arrival</sub> = 10, C<sub>Arrival</sub> = 10

### Round Robin

> - Run each job awhile, then switch to another distributing the CPU evenly (fairly)
> - Scheduling Quantum is called a **<u>time slice</u>**
> - Time Slice must be a multiple of timer interrupt period 
>

##### Round Robin Table

> | Process | Burst Time |
> | :-----: | :--------: |
> |   P1    |     12     |
> |   P2    |     8      |
> |   P3    |     4      |
> |   P4    |     10     |
> |   P5    |     5      |
>
> > ##### Round Robin scheduling algorithm Gantt chart
>
> | 0    | 5    | 10   | 14   | 19   | 24   | 29   | 32   | 37:arrow_right: 39 |
> | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------ |
> |      | P2   | P3   | P4   | P4   | P1   | P2   | P4   | P1                 |
>
> #### **Scheduling Quantum** = 5 sec

> **Round Robin** = really good for **response time**
>
> **Shortest Time to Completion** = Really good **Turn-Around time**
>

### Multi-Level Feedback Queue (MLFQ)

#### Objectives
> - Improve turnaround time:
>   - Run shorter jobs first
> - Minimize Response time
>   - Important for interactive jobs (UI)
>   - RR :arrow_right: UI
> - Achieve this without prior knowledge of job length
> - Multiple job queues
> - Adjust job priority based on observed behavior

#### Interactive Jobs

>
>   - Frequent I/O :arrow_right: Keep priority high
>   - Interactive jobs require fast response time (GUI/UI)
>   - Generally not CPU bound
>
#### Batch Jobs

>   - Require long periods of CPU utilization
>   - Keep priority low
>
>   MLFQ ISSUES
>
>   - **Starvation**
>     - Too many interactive jobs 
>   - **Preventing Gaming**
>   - **Improved time accounting:**
>     - Track total job execution time in the queue
>     - Each job receives a fixed time allotment
>     - When allotment is exhausted, job priority is lowered
>   - Duration is dependent on the CPU

#### Tuning

>   - Consider the trade offs:
>     - How many queues?
>     - What is a good time slice?
>     - How often should we "Boost priority of jobs?"
>     - What about different time slices to different queues
>

   #### MLFQ RULE SUMMARY: Multi Level Feedback Queues

> Adjust job priority based don observed behavior 
>
> Start a job at a high level priority where the time slice is smaller
>
> while when nearing the end, it will be moved to lower priority with larger time slices
>
> The refined set of MLFQ rules:
>
> 1. If Priority (A)  > Priority (B), A runs (B Doesn't)
> 2. If Priority (A)  = Priority (B), A & B run in RR.
> 3. When a job enters the sys it is placed at the highest priority
> 4. once a job uses up its time allotment at a given level
>
> Priority Boost
>
> ​	Too many interactive jobs will lead to job starvation  for batch jobs
>
> ​	To prevent this, we use priority boosts which work by resetting all job priorities at a time interval.

#### Preemptive Scheduler:

> Can stop another job to start another

Symmetric multiprocessing

Linux Completely Fair Scheduler
