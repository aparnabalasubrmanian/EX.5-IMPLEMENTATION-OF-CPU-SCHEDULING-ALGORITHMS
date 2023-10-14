# EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS

AIM: To implement First-Come-First-Serve (FCFS) Scheduling

ALGORITHM:
```
1.Start the process
2.Get the number of processes to be inserted
3.Get the corresponding priority of processes
4.
Sort the processes according to the priority and allocate the one with highest priority
to execute first
5.If two process have same priority then FCFS scheduling algorithm is used
6.Calculate the total and average waiting time and turnaround time
7.Display the values
8.Stop the proce
```
PROGRAM:
```

#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp;
float avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst time:\n");
for(i=0;i<n;i++)
{
printf("p%d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1;
}
wt[0]=0;
for(i=1;i<n;i++)
{
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];
}
avg_wt=(float)total/n;
total=0;
printf("\nProcess\t Burst time \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i];
total+=tat[i];
printf("\np%d\t\t %d\t\t  %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
}
avg_tat=(float)total/n;
printf("\n\nAverage waiting time=%f",avg_wt);
printf("\nAverage turnaround time=%f",avg_tat);
}
```

OUTPUT:
file:///home/sec/Pictures/Screenshots/Screenshot%20from%202023-10-14%2013-33-48.png![image](https://github.com/aparnabalasubrmanian/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/123351172/85899886-4c02-427e-978c-59ee2205f450)


RESULT: First-Come-First-Serve Scheduling is implemented successfully.


AIM: To implement Shortest Job First (SJF) Preemptive Scheduling

ALGORITHM:
```
1. Start the process
2. Get the number of processes to be inserted
3. Sort the processes according to the burst tiine and allocate the one with shortest burst to
execute first
4. If two process have same burst length then FCFS scheduling algorithm is used
5. Calculate the total and average waiting time and turn around time
6. Display the values
7. Stop the process
```

PROGRAM:
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,temp;
float avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++)
{
printf("p%d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1;
}
for(i=0;i<n;i++)
{
pos=i;
for(j=i+1;j<n;j++)
{
if(bt[j]<bt[pos])
pos=j;
}
temp=bt[i];
bt[i]=bt[pos];
bt[pos]=temp;
temp=p[i];
p[i]=p[pos];
p[pos]=temp;
}
wt[0]=0;
for(i=1;i<n;i++)
{
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];
}
avg_wt=(float)total/n;
total=0;
printf("\nProcess\t Burst Time  \tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i];
total+=tat[i];
printf("\np%d\t\t %d\t\t  %d\t\t\t%d",p[i],bt[i],wt[i],tat[i]);
}
avg_tat=(float)total/n;
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
} 

```

OUTPUT:
file:///home/sec/Pictures/Screenshots/Screenshot%20from%202023-10-14%2014-28-22.png![image](https://github.com/aparnabalasubrmanian/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/123351172/638b4a97-3e01-4206-aaaa-4631e7485e12)


RESULT: Shortest Job First (SJF) preemptive scheduling is implemented successfully.


AIM: To implement Shortest Job First (SJF) Non-Preemptive Scheduling

ALGORITHM:
```
1.Start the process
2.Get the number of processes to be inserted
3.Get the corresponding priority of processes
4.
Sort the processes according to the priority and allocate the one with highest priority
to execute first
5.If two process have same priority then FCFS scheduling algorithm is used
6.Calculate the total and average waiting time and turnaround time
7.Display the values
8.Stop the process

PROGRAM:
```
#include<stdio.h>
int main()
{
int bt[20],p[20],wt[20],tat[20],pri[20],i,j,k,n,total=0,pos,temp;
float avg_wt,avg_tat;
printf("Enter number of process:");
scanf("%d",&n);
printf("\nEnter Burst Time:\n");
for(i=0;i<n;i++)
{
printf("p%d:",i+1);
scanf("%d",&bt[i]);
p[i]=i+1;
}
printf("enter priority of the process");
for(i=0;i<n;i++)
{
p[i]=i;
printf("Priority of process");
printf("p%d:",i+1);
scanf("%d",&pri[i]);
}
for(i=0;i<n;i++)
for(k=i+1;k<n;k++)
if(pri[i]>pri[k])
{
temp=p[i];
p[i]=p[k];
p[k]=temp;
temp=bt[i];
bt[i]=bt[k];
bt[k]=temp;
temp=pri[i];
pri[i]=pri[k];
pri[k]=temp;
}
wt[0]=0;
for(i=1;i<n;i++)
{
wt[i]=0;
for(j=0;j<i;j++)
wt[i]+=bt[j];
total+=wt[i];
}
avg_wt=(float)total/n;
total=0;
printf("\nProcess\t   Burst Time\tPriority\tWaiting Time\tTurnaround Time");
for(i=0;i<n;i++)
{
tat[i]=bt[i]+wt[i];
total+=tat[i];
printf("\np%d\t\t %d\t\t %d\t\t %d\t\t\t%d",p[i],bt[i],pri[i],wt[i],tat[i]);
}
avg_tat=(float)total/n;
printf("\n\nAverage Waiting Time=%f",avg_wt);
printf("\nAverage Turnaround Time=%f\n",avg_tat);
} 
```

OUTPUT:
file:///home/sec/Pictures/Screenshots/Screenshot%20from%202023-10-14%2020-47-27.png![image](https://github.com/aparnabalasubrmanian/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/123351172/08fdebb9-e966-45c0-90c7-047e5ed20286)



RESULT: Shortest Job First (SJF) Non-preemptive scheduling is implemented successfully.

AIM: To implement Round Robin (RR) Scheduling

ALGORITHM:
```
1.Start the process
2.Get the number of elements to be inserted
3.Get the value for burst time for individual processes
4.Get the value for time quantum
5.Make the CPU scheduler go around the ready queue allocating CPU to each process
for the time interval specified
6.Make the CPU scheduler pick the first process and set time to interrupt after quantum.
And after it's expiry dispatch the process
7.If the process has burst time less than the time quantum then the process is released by
the CPU
8.If the process has burst time greater than time quantum then it is interrupted by the OS
and the process is put to the tail of ready queue and the schedule selects next
process from head of the queue
9.Calculate the total and average waiting time and turnaround time
10.Display the results

PROGRAM:
#include<stdio.h>
main()
{
int st[10],bt[10],wt[10],tat[10],n,tq; int
i,count=0,swt=0,stat=0,temp,sq=0;
float awt,atat;
printf("enter the number of processes");
scanf("%d",&n);
printf("enter the burst time of each process /n");
for(i=0;i<n;i++)
{
printf(("p%d",i+1);
scanf("%d",&bt[i]);
st[i]=bt[i];
}
printf("enter the time quantum");
scanf("%d",&tq);
while(1)
{
for(i=0,count=0;i<n;i++)
{
temp=tq;
if(st[i]==0)
{
count++;
continue;
}
if(st[i]>tq)
st[i]=st[i]-tq;
else
if(st[i]>=0){
temp=st[i];
st[i]=0;
}
sq=sq+temp;
tat[i]=sq;
}
if(n==count)
break;
}
for(i=0;i<n;i++)
{
wt[i]=tat[i]-bt[i];
swt=swt+wt[i];
stat=stat+tat[i];
}
awt=(float)swt/n;
atat=(float)stat/n;
printf("process no\t burst time\t waiting time\t turnaround time\n");
for(i=0;i<n;i++)
printf("%d\t\t %d\t\t %d\t\t %d\n",i+1,bt[i],wt[i],tat[i]); printf("avg
wt time=%f,avg turn around time=%f",awt,atat);
}

OUTPUT:
file:///home/sec/Pictures/Screenshots/Screenshot%20from%202023-10-14%2022-46-21.png![image](https://github.com/aparnabalasubrmanian/EX.5-IMPLEMENTATION-OF-CPU-SCHEDULING-ALGORITHMS/assets/123351172/b4cadd7a-e7f9-4c11-94a5-ca174de52bc9)


RESULT: Round Robin (RR) Scheduling is implemented successfully.


AIM: To implement Priority Preemptive Scheduling

ALGORITHM:
```
1.Start the process
2.Get the number of elements to be inserted
3.Get the value for burst time for individual processes
4.Get the value for time quantum
5.Make the CPU scheduler go around the ready queue allocating CPU to each process
for the time interval specified
6.Make the CPU scheduler pick the first process and set time to interrupt after quantum.
And after it's expiry dispatch the process
7.If the process has burst time less than the time quantum then the process is released by
the CPU
8.If the process has burst time greater than time quantum then it is interrupted by the OS
and the process is put to the tail of ready queue and the schedule selects next
process from head of the queue
9.Calculate the total and average waiting time and turnaround time
10.Display the results
```
PROGRAM:
```
#include<stdio.h>
main()
{
int st[10],bt[10],wt[10],tat[10],n,tq; int
i,count=0,swt=0,stat=0,temp,sq=0;
float awt,atat;
printf("enter the number of processes");
scanf("%d",&n);
printf("enter the burst time of each process /n");
for(i=0;i<n;i++)
{
printf(("p%d",i+1);
scanf("%d",&bt[i]);
st[i]=bt[i];
}
printf("enter the time quantum");
scanf("%d",&tq);
while(1)
{
for(i=0,count=0;i<n;i++)
{
temp=tq;
if(st[i]==0)
{
count++;
continue;
}
if(st[i]>tq)
st[i]=st[i]-tq;
else
if(st[i]>=0){
temp=st[i];
st[i]=0;
}
sq=sq+temp;
tat[i]=sq;
}
if(n==count)
break;
}
for(i=0;i<n;i++)
{
wt[i]=tat[i]-bt[i];
swt=swt+wt[i];
stat=stat+tat[i];
}
awt=(float)swt/n;
atat=(float)stat/n;
printf("process no\t burst time\t waiting time\t turnaround time\n");
for(i=0;i<n;i++)
printf("%d\t\t %d\t\t %d\t\t %d\n",i+1,bt[i],wt[i],tat[i]); printf("avg
wt time=%f,avg turn around time=%f",awt,atat);
}

OUTPUT:


RESULT: Priority Preemptive scheduling is implemented successfully.


AIM: To implement Priority Non-Preemptive Scheduling

ALGORITHM:
```
1. Create a child process usingfork()
2. Create a simple pipe with C, we make use of the pipe() systemcall.
3. Create two file descriptor fd[0] is set up for reading, fd[1] is set up forwriting
4. Close the read end of parent process using close() and perform writeoperation
5. Close the write end of child process and performreading
6. Display thetext.
```

PROGRAM:
```
#include <stdio.h>
int main()
{
int fd[2],child; char a[10];
printf("\n Enter the string:");
scanf("%s",a);
pipe(fd);
child=fork();
if(!child)
{
close(fd[0]);
write(fd[1],a,5); wait(0);
}
else
{
close(fd[1]);read(fd[0],a,5);
printf("The string received from pipe is: %s",a);
}
return 0;
}
```

OUTPUT:


RESULT: Priority Non-preemptive scheduling is implemented successfully.

