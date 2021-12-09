# OS-Practical-Exam-Set-3-Ramanujan-collegeUjjawal-kumar

**SET-3 OS-Practical-Exam**

**Ques1:Implement Round robin scheduling algorithm with quanta 3. Compute waiting time, 
turnaround time.**

**Solution:**

*********Description About the Program*********

Round Robin is a CPU scheduling algorithm where each process is assigned a fixed time slot in a cyclic way.

@It is simple, easy to implement, and starvation-free as all processes get fair share of CPU time and implementation got easy. 

@One of the most commonly used technique in CPU scheduling as a core feature of the program.

@It is preemptive as processes are assigned CPU only for a fixed slice of time at most.

@The disadvantage of it is more overhead of context switching.

**How to compute times in Round Robin using a program?**

@Completion Time: Time at which process completes its execution.

@Turn Around Time: Time Difference between completion time and arrival time. Turn Around Time = Completion Time – Arrival Time

@Waiting Time(W.T): Time Difference between turn around time and burst time. 

@Waiting Time = Turn Around Time – Burst Time

**Sample Output**

![Screenshot_2021-12-09-10-36-06-614_ru iiec cxxdroid](https://user-images.githubusercontent.com/83595564/145340001-f5e7b947-7114-422f-8988-c8734c21f330.jpg)

 
 ![Screenshot_2021-12-09-10-35-52-618_ru iiec cxxdroid](https://user-images.githubusercontent.com/83595564/145339365-2f379d0a-f5e1-4fd2-8372-c40401c890d9.jpg)
 
In this post, we have assumed arrival times as 0, so turn around and completion times are same.

The tricky part is to compute waiting times. Once waiting times are computed, turn around times can be quickly computed.

1- Create an array rem_bt[] to keep track of remaining
   burst time of processes. This array is initially a 
   copy of bt[] (burst times array)
   
2- Create another array wt[] to store waiting times
   of processes. Initialize this array as 0.
   
3- Initialize time : t = 0

4- Keep traversing the all processes while all processes
   are not done. Do following for i'th process if it is
   not done yet.
    a- If rem_bt[i] > quantum
       (i)  t = t + quantum
       (ii) rem_bt[i] -= quantum;
    c- Else // Last cycle for this process
       (i)  t = t + rem_bt[i];
       (ii) wt[i] = t - bt[i]
       (ii) rem_bt[i] = 0; // This process is over
       
In this way we are able to find the Round robin Schedule for CPU time distribution. 


**Que2 : Write a program to demonstrate fork where parent and child run same codes and parent 
process should be executed first.**

**Solution:**

***Description About the program***

The fork() System Call

System call fork() is used to create processes. It takes no arguments and returns a process ID. The purpose of fork() is to

create a new process, which becomes the child process of the caller. After a new child process is created, both processes 

will execute the next instruction following the fork() system call. Therefore, we have to distinguish the parent from the

child. This can be done by testing the returned value of fork():

If fork() returns a negative value, the creation of a child process was unsuccessful.

fork() returns a zero to the newly created child process.

fork() returns a positive value, the process ID of the child process, to the parent. The returned process ID is of type

pid_t defined in sys/types.h. Normally, the process ID is an integer. Moreover, a process can use function getpid() to retrieve the process ID assigned to this process.

Therefore, after the system call to fork(), a simple test can tell which process is the child

As both process start at same time The **Fork** will call parent process **first** and the process executes first with parent id. 

**Sample output:**

![IMG_20211209_110709](https://user-images.githubusercontent.com/83595564/145342322-cd19e292-6d4b-4ad9-8234-6e80c7673f8e.jpg)

