#include <stdio.h>
#include <stdlib.h>

int add (int a, int b){
    return a + b;
}
int subtract (int a, int b){
    return a - b;
}
int multiply (int a, int b){
    return a * b;
}
float divide (int a, int b){
    return (float)a / b;
}
int main () {
    int a, b;
    char operation;

    while (1) {
        printf("Press 'q' at any time to exit.\n");
        while (1) {
            printf("First operand: ");
            if ((a = getchar()) == 'q') {
                printf("Exiting the program.\n");
                return 0;
            }
            ungetc(a, stdin);
            if (scanf("%d", &a) != 1) {
                printf("Error: Please enter a valid integer.\n");
                while (getchar() != '\n');
                continue;
            }
            break;
        }
        while (1) {
            printf("Second operand: ");
            if ((b = getchar()) == 'q') {
                printf("Exiting the program.\n");
                return 0;
            }
            ungetc(b, stdin);
            if (scanf("%d", &b) != 1) {
                printf("Error: Please enter a valid integer.\n");
                while (getchar() != '\n');
                continue;
            }
            break;
        }
        while (1) {
            printf("What is the operator (/,+,-,*)?: ");
            while (getchar() != '\n');
            operation = getchar();
            if (operation == 'q') {
                printf("Exiting the program.\n");
                return 0;
            }
            if (operation == '+' || operation == '-' || operation == '*' || operation == '/') {
                break;
            } else {
                printf("Error: Please enter a valid operator (+, -, *, /).\n");
            }
        }

        if (operation == '*') {
            printf("Product of %d and %d is: %d\n", a, b, multiply(a, b));
        } else if (operation == '-') {
            printf("Subtracting %d from %d gives: %d\n", a, b, subtract(a, b));
        } else if (operation == '+') {
            printf("Sum of %d and %d is: %d\n", a, b, add(a, b));
        } else if (operation == '/') {
            printf("Dividing %d by %d gives: %.2f\n", a, b, divide(a, b));
        }
    }
    return 0;
}
