# OS
### 2A. FIRST COME FIRST SERVE 
SCHEDULING

```
#include<stdio.h> 
int main() 
{ 
int 
bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,t
emp; float 
avg_wt,avg_tat; 
printf("Enter number of process:"); 
scanf("%d",&n); 
printf("\nEnter Burst Time:\n"); 
for(i=0;i<n;i++) 
{ 
printf("p % d:",i+1); 
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
printf("\nProcess\t Burst Time \tWaiting 
Time\tTurnaround Time"); 
for(i=0;i<n;i++) 
{ 
tat[i]=bt[i]+wt[i]; 
total+=tat[i]; 
printf("\np%d\t\t %d\t\t 
%d\t\t\t%d",p[i],bt[i],wt[i],tat[i]); 
} 
avg_tat=(float)total/n; 
printf("\n\nAverage Waiting 
Time=%f",avg_wt); 
printf("\nAverage Turnaround 
Time=%f\n",avg_tat); 
}
```
![OS PROXY_20221129_124658_1](https://user-images.githubusercontent.com/94827772/204463707-675addb5-0630-4c64-812a-4003b449fa2c.png)

### 2B. SHORTEST JOB FIRST 
SHEDULING:
```
#include<stdio.h> 
int main() 
{ 
int 
bt[20],p[20],wt[20],tat[20],i,j,n,total=0,pos,t
emp; float 
avg_wt,avg_tat; 
printf("Enter number of process:"); 
scanf("%d",&n); 
printf("\nEnter Burst Time:\n"); 
for(i=0;i<n;i++) 
{ 
printf("p%d:",i+1); 
scanf("%d",&bt[i]); 
p[i]=i+1; //contains process number 
} 
//sorting burst time in ascending order using 
selection sort 
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
wt[0]=0; //waiting time for first process will 
be zero 
//calculate waiting time 
for(i=1;i<n;i++) 
{ 
wt[i]=0; 
for(j=0;j<i;j++) 
wt[i]+=bt[j]; 
total+=wt[i]; 
} 
avg_wt=(float)total/n; //average waiting 
time 
total=0; 
printf("\nProcess\t Burst Time \tWaiting 
Time\tTurnaround Time"); 
for(i=0;i<n;i++) 
{ 
tat[i]=bt[i]+wt[i]; //calculate turnaround 
time 
total+=tat[i]; 
printf("\np%d\t\t %d\t\t 
%d\t\t\t%d",p[i],bt[i],wt[i],tat[i]); 
} 
avg_tat=(float)total/n; //average turnaround 
time 
printf("\n\nAverage Waiting 
Time=%f",avg_wt); 
printf("\nAverage Turnaround 
Time=%f\n",avg_tat); 
}
```

