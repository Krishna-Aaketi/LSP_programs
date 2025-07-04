## ------------------------Signals_Programs--------------------------------

### 1.Catch and handle the SIGINT signal.
```c
/* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
 * 1. Write a C program to catch and handle the SIGINT signal.           *
 * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */

#include <stdio.h>
#include <signal.h>
#include <stdlib.h>
#include <unistd.h>


void handle_sigint(int sig);

int main(void)
{
  signal(2, handle_sigint);
  while(1)
  {
    printf("Searching...\n");
    sleep(1);
  }
    return 0;
}

// Signal handler function
void handle_sigint(int sig)
{
    printf("\nReceived SIGINT\n");
    exit(0);
}
```
### 2.Send a custom signal to another process.
```c
/* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
 * 2. Implement a C program to send a custom signal to another process.  *
 * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */

#if 0
// Sender
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>
#include <unistd.h>


void send_signal(int sig);

int main(void)
{
  signal(SIGUSR1,send_signal);
  printf("PID =%d\n",getpid());
  while(1);
  return 0;
}

void send_signal(int sig)
{
    printf("\nReceived custom singal\n");
    exit(0);
}

#endif

#if 1
// Receiver
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>
#include <unistd.h>


int main(void)
{
  int sig;
  printf("Enter Process id\n");
  scanf("%d",&sig);
  if(kill(sig,SIGUSR1) == 0)
  {
    printf("signal is Sent\n");
  }
  else
  {
    printf("signal is not sent\n");
    return 0;
  }
  return 0;
}
#endif
```
### 3.Handle the SIGSEGV signal (segmentation fault)
```c
/* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
 * 7. Implement a program to handle the SIGSEGV signal (segmentation fault)  *
 * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */

#include<stdio.h>
#include<signal.h>
#include<stdlib.h>

void signal_handle(int sig);

int main(void)
{
  signal(SIGSEGV, signal_handle);
  char *str="Krishna";
  str[0]='R';
  return 0;
}

void signal_handle(int sig)
{
    printf("SIGSEGV\n");
    exit(7);
}

```
### 4.Handle the SIGABRT signal(Abort).
```c
/* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
 * 9. Write a program to handle the SIGABRT signal (abort).  *
 * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */

#include<stdio.h>
#include<signal.h>
#include<stdlib.h>

void signal_handle(int sig);

int main(void)
{
  signal(SIGABRT, signal_handle);
  abort();
  return 0;
}

void signal_handle(int sig)
{
    printf("Received SIGABRT\n");
    exit(7);
}
```
### 5.Handle the SIGQUIT signal
```c
/* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
 * 10. Implement a C program to handle the SIGQUIT signal    *
 * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */

#include<stdio.h>
#include<signal.h>
#include<stdlib.h>

void signal_handle(int sig);

int main(void)
{
  signal(SIGQUIT, signal_handle);
  while(1);
  return 0;
}

void signal_handle(int sig)
{
    printf("\nReceived SIGQUIT\n");
    exit(7);
}

```
### 6.Handle the SIGSTOP signal (terminal stop)
```c
/* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
 * 11.Write a program to handle the SIGSTOP signal (terminal stop)  *
 * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * */

#include<stdio.h>
#include<signal.h>
#include<stdlib.h>

void signal_handle(int sig);

int main(void)
{
  signal(SIGSTOP, signal_handle);
  while(1);
  return 0;
}

void signal_handle(int sig)
{
    printf("\nReceived SIGSTOP\n");
    exit(7);
}
```
