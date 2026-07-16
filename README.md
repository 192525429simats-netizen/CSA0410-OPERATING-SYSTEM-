#include <stdio.h>

int main() {
    int n, bt[10], rt[10], pr[10], ct[10], wt[10], tat[10];
    int i, time = 0, completed = 0, min, p;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    for(i = 0; i < n; i++) {
        printf("P%d Burst Time & Priority: ", i + 1);
        scanf("%d%d", &bt[i], &pr[i]);
        rt[i] = bt[i];
    }

    while(completed < n) {
        min = 999;
        p = -1;

        for(i = 0; i < n; i++) {
            if(rt[i] > 0 && pr[i] < min) {
                min = pr[i];
                p = i;
            }
        }

        rt[p]--;
        time++;

        if(rt[p] == 0) {
            completed++;
            ct[p] = time;
            tat[p] = ct[p];
            wt[p] = tat[p] - bt[p];
        }
    }

    printf("\nP\tBT\tPR\tWT\tTAT\n");
    for(i = 0; i < n; i++)
        printf("P%d\t%d\t%d\t%d\t%d\n", i + 1, bt[i], pr[i], wt[i], tat[i]);

    return 0;
}
