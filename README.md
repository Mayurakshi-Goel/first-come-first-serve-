# first-come-first-serve-
#include<conio.h>
#include<stdio.h>
void main(){
	int bt[25],wt[25],n,tat[25],i;
	double avgtat,avgwt,tempwt,temptat;
	tempwt=0;
	temptat=0;
	printf("Enter the number of processes (max 25): ");
	scanf("%d",&n);
	for(i=0;i<n;i++){
		printf("Enter the burst time for process number %d: ",i);
		scanf("%d",&bt[i]);
	}
	wt[0]=0;
	tat[0]=bt[0];
	for(i=1;i<n;i++){
		wt[i]=wt[i-1]+bt[i-1];
		tat[i]=wt[i]+bt[i];
	}
	for(i=0;i<n;i++){
		tempwt = tempwt + wt[i];
		temptat = temptat + tat[i];
	}
	avgwt=tempwt/n;
	avgtat=temptat/n;
	printf("\n\n\nTotal number of processes: %d",n);
	printf("\n\nProcess\tBurst Time\tWaiting time\tTurn around Time\n");
	for(i=0;i<n;i++){
		printf("%d\t%d\t\t%d\t\t%d\n",i,bt[i],wt[i],tat[i]);
	}
	
	printf("\nAverage waiting time: %lf\n",avgwt);
	printf("Average turn around time: %lf",avgtat);
}
