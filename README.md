# OS
### 2A. FIRST COME FIRST SERVE 
SCHEDULING

```
#include<stdio.h>
int main(){
    int p[100],bt[100],wt[100],tat[100],i,j,n,pos,total=0;
    float avg_wt,avg_tat;
    scanf("%d",&n);
    printf("\nEnter the burst time\n");
    for(i=0;i<n;i++){
        printf("p%d: ",i+1);
        scanf("%d",&bt[i]);  
        p[i]=i+1;
    }
    wt[0]=0;
    for(i=1;i<n;i++){
        wt[i]=0;
        for(j=0;j<i;j++){
            wt[j]+=bt[j];
            total+=wt[j];
        }
    }
    avg_wt=(float)total/n;
    total =0;
    printf("\nProcess\t\tBurst_time\t\twait_time\t\ttut_time\n");
    for(i=0;i<n;i++){
        tat[i]=bt[i]+wt[i];
        total+=tat[i];
        printf("\t%d\t\t\t%d\t\t\t\t%d\t\t\t\t%d\n",p[i],bt[i],wt[i],tat[i]);
    }
    avg_tat=(float)total/n;
    printf("\nAverage Wait time: %f\n",avg_wt);
   printf("Average TT time: %f",avg_tat);
    
}
```
![OS PROXY_20221129_124658_1](https://user-images.githubusercontent.com/94827772/204463707-675addb5-0630-4c64-812a-4003b449fa2c.png)

### 2B. SHORTEST JOB FIRST 
SHEDULING:
```
#include<stdio.h> 
int main () 
{
    int bt[20], p[20], wt[20], tat[20], i, j, n, total = 0, pos, temp;
    float avg_wt, avg_tat;
    scanf ("Enter number of process: %d", &n);

    printf ("\nEnter Burst Time:\n");
    for (i = 0; i < n; i++)
    {
        printf ("p%d:", i + 1);
        scanf ("%d", &bt[i]);
        p[i] = i + 1;
    }

    for (i = 0; i < n; i++)
    {
        pos = i;
        for (j = i + 1; j < n; j++)
	    {
            if (bt[j] < bt[pos])
            pos = j;
        }
        temp = bt[i];
        bt[i] = bt[pos];
        bt[pos] = temp;
        temp = p[i];
        p[i] = p[pos];
        p[pos] = temp;
    }
    wt[0] = 0;
    for (i = 1; i < n; i++)
    {
        wt[i] = 0;
        for (j = 0; j < i; j++)
        wt[i] += bt[j];
        total += wt[i];
    }
    avg_wt = (float) total / n;	
    total = 0;
    printf ("\nProcess\t Burst Time \tWaiting Time\tTurnaround Time");
  
    for (i = 0; i < n; i++)
    {
        tat[i] = bt[i] + wt[i];	
        total += tat[i];
        printf ("\np%d\t\t %d\t\t %d\t\t\t%d", p[i], bt[i], wt[i], tat[i]);
    }

    avg_tat = (float) total / n;

    printf ("\n\nAverage Waiting Time=%f", avg_wt);
    printf ("\nAverage Turnaround Time=%f\n", avg_tat);
}

```
![OS PROXY_20221129_124933_1](https://user-images.githubusercontent.com/94827772/204464083-41753e74-767b-4c25-b4e8-33b4c519569f.png)

### 2C.PRIORITY SCHEDULING:
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
    printf(" enter priority of the process "); 
    for(i=0;i<n;i++) 
    { 
        p[i] = i; 
        printf("p%d ",i+1); 
        scanf("%d",&pri[i]); 
    } 
    for(i=0;i<n;i++) 
    for(k=i+1;k<n;k++) 
    if(pri[i] > pri[k]) 
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
    printf("\nProcess\t Burst Time \tPriority \tWaiting Time\tTurnaround Time"); 
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
![OS PROXY_20221129_125053_1](https://user-images.githubusercontent.com/94827772/204464343-9dddc2da-9072-43f1-87ca-41874928c6dc.png)


### 2D.ROUND ROBIN SCHEDULING:
```
#include<stdio.h> 
int main() 
{ 
    int st[10],bt[10],wt[10],tat[10],n,tq; int i,count=0,swt=0,stat=0,temp,sq=0; 
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
        if(st[i]>=0) 
        { 
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
    printf("%d\t\t %d\t\t %d\t\t %d\n",i+1,bt[i],wt[i],tat[i]); 
    printf("avg wt time=%f,avg turn around time=%f",awt,atat); 
}
```
![OS PROXY_20221129_125147_1](https://user-images.githubusercontent.com/94827772/204464496-17de748e-6f05-421d-9942-675c42c1f22f.png)

### 3A .INTER PROCESS COMMUNICATIONS:
```
#include <stdio.h> 
#include<stdlib.h> 
#include<string.h> 
#include<sys/types.h> 
#include<sys/wait.h> 
#include<unistd.h> 
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
{close(fd[1]); 
read(fd[0],a,5); 
printf("The string received from pipe is: %s",a); 
} 
return 0; 
}
```
![OS PROXY_20221129_125232_1](https://user-images.githubusercontent.com/94827772/204464602-983a5031-5ef9-44cf-a9d9-94d126233189.png)

### 3B. SYSTEM CALLS (READ & WRITE, CREATE 
&FORK, OPEN &CLOSE):
```
#include <stdio.h> 
#include<stdlib.h> 
#include<string.h> 
#include<sys/types.h> 
#include<sys/wait.h> 
#include<unistd.h> 
#include<sys/stat.h> 
#include<fcntl.h> 
int main() 
{ 
int n,i=0; 
int f1,f2; 
char c,strin[100]; 
f1=open("data",O_RDWR|O_CREAT|O_TRUN
C); 
while((c=getchar())!='\n') 
{ 
strin[i++]=c; 
} 
strin[i]='\0'; 
write(f1,strin,i); 
close(f1); 
f2=open("data",O_RDONLY); 
read(f2,strin,0); 
printf("\n%s\n",strin); 
close(f2); 
fork(); 
return 0; 
}
```
![OS PROXY_20221129_125327_1](https://user-images.githubusercontent.com/94827772/204464759-4d404039-de27-4b85-98e1-963ad153c720.png)

### 3C. IMPLEMENT BANKERS’ ALGORITHM 
FOR DEAD LOCKAVOIDANCE:
```
#include<stdio.h> 
int main () 
{ 
int allocated[15][15], max[15][15], need[15][15], 
avail[15], tres[15], work[15], flag[15]; 
int pno, rno, i, j, prc, 
count, t, total; count = 
0; 
//clrscr (); 
printf ("\n Enter number of 
process:"); 
scanf ("%d", &pno); 
printf ("\n Enter number 
of resources:"); 
scanf ("%d", &rno); 
for (i = 1; i <= pno; i++) 
{ 
flag[i] = 0; 
} 
printf ("\n Enter total numbers of 
each resources:"); 
for (i = 1; i <= rno; i++) 
scanf ("%d", &tres[i]); 
printf ("\n Enter Max resources for 
each process:"); 
for (i = 1; i <= pno; i++) 
{ 
printf ("\n for process %d:", 
i); 
for (j = 1; j <= rno; j++) 
scanf ("%d", &max[i][j]); 
} 
printf ("\n Enter allocated resources for each 
process:"); for (i = 1; i <= pno; i++) 
{
printf ("\n for process %d:", 
i); for (j = 1; j <= rno; j++) 
scanf ("%d", &allocated[i][j]); 
} 
printf ("\n available 
resources:\n"); 
for (j = 1; j <= rno; j++) 
{ 
avail[j] = 0; 
total = 0; 
for (i = 1; i <= pno; i++) 
{ 
total += allocated[i][j]; 
} 
avail[j] = 
tres[j] -
total; 
work[j] = 
avail[j]; 
printf (" %d \t", work[j]); 
} 
do 
{ 
for (i = 1; i <= pno; i++) 
{ 
for (j = 1; j <= rno; j++) 
{ 
need[i][j] = max[i][j] - allocated[i][j]; 
} 
} 
printf ("\n Allocated matrix Max need"); 
for (i = 1; i <= pno; i++) 
{ 
printf ("\n"); 
for (j = 1; j <= rno; j++) 
{ 
printf ("%4d", allocated[i][j]); 
} 
printf ("|"); 
for (j = 1; j <= rno; j++) 
{ 
printf ("%4d", max[i][j]); 
} 
printf ("|"); 
for (j = 1; j <= rno; j++) 
{ 
printf ("%4d", need[i][j]); 
} 
} 
prc = 0; 
for (i = 1; i <= pno; i++){ 
if (flag[i] == 0){ 
prc = i; 
for (j = 1; j <= rno; j++) 
{ 
prc = 0; break; 
} 
if (work[j] < need[i][j]) 
{ 
} 
} 
if (prc != 0) 
break; 
} 
if (prc != 0){ 
printf ("\n Process %d completed", 
i); 
count++; 
printf ("\n Available 
matrix:") 
for (j = 1; j <= rno; j++) 
{ 
work[j] += 
allocated[prc][ 
j]; 
allocated[prc][ 
j] = 0; 
max[prc][j] = 0; 
flag[prc] = 1; 
printf (" %d", work[j]); 
} 
} 
} 
while (count != pno && prc != 0); 
if (count == pno) 
printf ("\nThe system is in a safe 
state!!"); 
else 
printf ("\nThe system is in an unsafe 
state!!"); 
return 0; 
}
```
