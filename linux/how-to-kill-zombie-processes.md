# How to Kill Zombie Processes

A **zombie** or a **defunct process** in Linux is a process that has been completed but its entry still remains in the process table due to lack of correspondence between the parent and child processes. Usually, a parent process keeps a check on the status of its child processes through the `wait()` function. When the child process has finished, the wait function signals the parent to completely exit the process from the memory. However, if the parent fails to call the wait function for any of its children, the child process remains alive in the system as a dead or zombie process. These zombie processes might accumulate, in large numbers, on your system and affect its performance. In that case, you will have to kill these zombies manually.

### Command Line  
The `top` command displays a detailed view of the processes running on your system along with the memory and CPU resources they are using. It also gives you information about any zombie processes running on your system. Open the **Terminal** by pressing **Ctrl+Alt+T** and then type `top`.

If you want further details about the zombie process, use the following command:  
`$ ps xa | grep defunct`  

### Killing a Zombie-Process

It is important to learn that zombies are dead and mostly completed processes that do not take memory or CPU resources. However, each of these processes has a unique process ID assigned to them which comes from a limited pool of PIDs reserved for your processor. If a large number of zombies gather, they will eat up most part of the PID pool and the new processes will not be able to launch due to lack of a process ID.

You can kill the parent process through the following command:  
`$ kill -9 PID`  ( **PID** is the ID of the zombie process )

After you have killed all the zombie processes and run the `top` command, you will find out that there are no zombie processes running on your system anymore.
