Simple Calculator:

```C
#include <stdio.h>

int main() {
    double num1, num2, result;
    char operator;

    printf("Enter first number: ");
    scanf("%lf", &num1);

    printf("Enter operator (+, -, *, /): ");
    scanf(" %c", &operator);

    printf("Enter second number: ");
    scanf("%lf", &num2);

    switch (operator) {
        case '+':
            result = num1 + num2;
            break;
        case '-':
            result = num1 - num2;
            break;
        case '*':
            result = num1 * num2;
            break;
        case '/':
            if (num2 != 0) {
                result = num1 / num2;
            } else {
                printf("Error: Division by zero\n");
                return 1; // Exit with an error code
            }
            break;
        default:
            printf("Error: Invalid operator\n");
            return 1; // Exit with an error code
    }

    printf("Result: %.2lf\n", result);
    return 0;
}
```


Month Name to Number Converter:

```C
#include <stdio.h>

int main() {
    int day, month, year;

    // Input the numeric date
    printf("Enter numeric date (DD/MM/YYYY): ");
    scanf("%d/%d/%d", &day, &month, &year);

    // Display the original numeric date
    printf("\nOriginal Numeric Date: %02d/%02d/%d\n", day, month, year);

    // Convert month to text using switch-case
    char monthText[20];
    switch (month) {
        case 1:
            strcpy(monthText, "January");
            break;
        case 2:
            strcpy(monthText, "February");
            break;
        case 3:
            strcpy(monthText, "March");
            break;
        case 4:
            strcpy(monthText, "April");
            break;
        case 5:
            strcpy(monthText, "May");
            break;
        case 6:
            strcpy(monthText, "June");
            break;
        case 7:
            strcpy(monthText, "July");
            break;
        case 8:
            strcpy(monthText, "August");
            break;
        case 9:
            strcpy(monthText, "September");
            break;
        case 10:
            strcpy(monthText, "October");
            break;
        case 11:
            strcpy(monthText, "November");
            break;
        case 12:
            strcpy(monthText, "December");
            break;
        default:
            printf("Error: Invalid month\n");
            return 1; // Exit with an error code
    }

    // Display the converted date
    printf("Converted Date: %02d/%s/%d\n", day, monthText, year);

    return 0;
}
```


```C
#include <stdio.h>

int main() {
    int month;

    printf("Enter the month number (1-12): ");
    scanf("%d", &month);

    switch (month) {
        case 1:
        case 3:
        case 5:
        case 7:
        case 8:
        case 10:
        case 12:
            printf("Number of days: 31\n");
            break;
        case 4:
        case 6:
        case 9:
        case 11:
            printf("Number of days: 30\n");
            break;
        case 2:
            printf("Number of days: 28 or 29\n");
            break;
        default:
            printf("Invalid month\n");
            return 1;
    }

    return 0;
}

```