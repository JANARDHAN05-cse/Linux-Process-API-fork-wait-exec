# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls
```
    #include <stdio.h>
    #include <unistd.h>

    int main() {
        pid_t pid, ppid;

        pid = getpid();     // Get current process ID
        ppid = getppid();   // Get parent process ID

        printf("Process ID: %d\n", pid);
        printf("Parent Process ID: %d\n", ppid);

        return 0;
    }
```
# OUTPUT
![WhatsApp Image 2025-05-21 at 11 43 04_fbb85b9c](https://github.com/user-attachments/assets/4c927e0e-595b-43df-a845-3df42d047fa4)



## C Program to create new process using Linux API system calls fork() and exit()
```
    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>

    int main() {
        pid_t pid;

        pid = fork();  // Create a new process

        if (pid < 0) {
            // Fork failed
            perror("fork failed");
            exit(1);
        } else if (pid == 0) {
            // Child process
            printf("Child Process:\n");
            printf("  PID: %d\n", getpid());
            printf("  Parent PID: %d\n", getppid());
            exit(0);  // Child exits
        } else {
            // Parent process
            printf("Parent Process:\n");
            printf("  PID: %d\n", getpid());
            printf("  Child PID: %d\n", pid);
            exit(0);  // Parent exits
        }
    }
```


# OUTPUT

![WhatsApp Image 2025-05-21 at 11 44 48_6a319995](https://github.com/user-attachments/assets/299c25dc-02b2-4a22-a013-c137c7a7d69b)


# C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family
```
    #include <stdio.h>
    #include <stdlib.h>
    #include <unistd.h>

    int main() {
        printf("Before executing ls -l\n");

        // execl(path, arg0, arg1, ..., NULL)
        execl("/bin/ls", "ls", "-l", NULL);

        // If execl() is successful, the lines below won't execute
        perror("execl failed");
        exit(1);
    }
```
# OUTPUT

![WhatsApp Image 2025-05-21 at 11 46 17_a5c6efd3](https://github.com/user-attachments/assets/fe8ecefe-637f-4c82-9225-2599d2540782)


# RESULT:
The programs are executed successfully.
