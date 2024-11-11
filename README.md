#include <stdio.h>
int main() {
    int emp_id[5], basic_salary[5], hra[5], da[5], gross_salary[5], absent_days[5];
    float hra_percentage[5], da_percentage[5], daily_wage[5], net_salary[5], pf[5], tax[5], bonus[5], total_deductions[5];
    char emp_name[5][50];  // Array to store names of employees
    int i;
    const int total_working_days = 30;
    for (i = 0; i < 5; i++) {
        // Input employee details
        printf("Enter employee name: ");
        scanf(" %[^\n]s", emp_name[i]); 
        printf("Enter employee ID for %s: ", emp_name[i]);
        scanf("%d", &emp_id[i]);
        printf("Enter basic salary for employee %s: ", emp_name[i]);
        scanf("%d", &basic_salary[i]);
        printf("Enter HRA percentage for employee %s: ", emp_name[i]);
        scanf("%f", &hra_percentage[i]);
        printf("Enter DA percentage for employee %s: ", emp_name[i]);
        scanf("%f", &da_percentage[i]);
        printf("Enter number of absent days for employee %s: ", emp_name[i]);
        scanf("%d", &absent_days[i]);
        printf("Enter bonus amount for employee %s: ", emp_name[i]);
        scanf("%f", &bonus[i]);
        daily_wage[i] = basic_salary[i] / (float)total_working_days;
     hra[i] = (hra_percentage[i] / 100.0) * basic_salary[i];
        da[i] = (da_percentage[i] / 100.0) * basic_salary[i];
        gross_salary[i] = basic_salary[i] + hra[i] + da[i] + bonus[i];
        pf[i] = 0.12 * basic_salary[i]; // 12% PF deduction on basic salary
        tax[i] = 0.1 * gross_salary[i];  // 10% tax on gross salary
        float absence_deduction = absent_days[i] * daily_wage[i];
        total_deductions[i] = pf[i] + tax[i] + absence_deduction;
        net_salary[i] = gross_salary[i] - total_deductions[i];
    }
    printf("\nSalary Slip for Employees:\n");
    printf("----------------------------\n");
    for (i = 0; i < 5; i++) {
        printf("Employee Name: %s\n", emp_name[i]);
        printf("Employee ID: %d\n", emp_id[i]);
        printf("Basic Salary: %d\n", basic_salary[i]);
        printf("HRA (%.2f%%): %d\n", hra_percentage[i], hra[i]);
        printf("DA (%.2f%%): %d\n", da_percentage[i], da[i]);
        printf("Bonus: %.2f\n", bonus[i]);
        printf("Gross Salary (before deductions): %d\n", gross_salary[i]);
        printf("PF Deduction (12%%): %.2f\n", pf[i]);
        printf("Tax Deduction (10%%): %.2f\n", tax[i]);
        printf("Absent Days: %d\n", absent_days[i]);
        printf("Absence Deduction: %.2f\n", absent_days[i] * daily_wage[i]);
        printf("Total Deductions: %.2f\n", total_deductions[i]);
        printf("Net Salary (after deductions): %.2f\n", net_salary[i]);
        printf("----------------------------\n");
    }
    return 0;
}
