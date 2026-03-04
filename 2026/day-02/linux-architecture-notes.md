1: What are the core components of Linux Architecture?
Hardware is the physical foundation including the central processing unit, memory, and storage devices.
The Kernel is the core software interface acting as a bridge between all running applications and the physical hardware.
System Libraries are special functions that allow applications to interact with the kernel without writing complex low-level code.
User Space is the environment where all regular user applications, graphical interfaces, and background services execute.
The Init system or systemd is the very first program loaded by the kernel to initialize the rest of the operating system.

2: How are Linux processes created and managed?
A process is simply an executing instance of a program that has been loaded into the system memory.
New processes are typically created using the fork system call which creates an exact duplicate of an existing parent process.
The exec system call is then used by the new child process to replace its memory space with a completely new program.
The kernel assigns a unique Process ID to every running process to accurately track and manage its resource usage.
The kernel scheduler automatically allocates CPU time slices to each process to ensure smooth multitasking across the entire system.

3: What are the different Linux process states?
Running state means the process is currently executing on the CPU or waiting in the active queue to run.
Sleeping state occurs when a process pauses execution to wait for a specific event or resource like user input or disk access.
Stopped state happens when a running process receives a specific system signal to suspend its execution temporarily.
Zombie state refers to a process that has completed its task but still holds an entry in the process table waiting for its parent to acknowledge it.
Orphan state occurs when a parent process terminates before its child process, leaving the child to be safely adopted by the init system.

 4: What is systemd and why does it matter?
systemd is the modern initialization system and primary service manager used by most major Linux distributions today.
It dramatically improves system boot times by starting necessary services concurrently instead of one by one.
It keeps track of services using unit files making it incredibly easy to configure exactly how and when applications should start.
It handles the automatic restarting of crashed services ensuring high availability and reliability for critical applications.
It centralizes all system logging through the journalctl utility making troubleshooting and debugging much more efficient for engineers.

5: What are 5 Linux commands I would use daily for process management?
top displays a dynamic and interactive real-time view of all running system processes and current resource usage.
ps aux lists every currently running process across the entire system along with detailed user and memory information.
kill sends a specific signal to a target process ID to either terminate it gracefully or shut it down forcefully.
systemctl status helps quickly check whether a specific background service is actively running, failed, or currently inactive.
journalctl allows engineers to view, filter, and analyze system and service logs collected continuously by systemd.
