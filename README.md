# Binary-Calculator-in-C

    #include <stdio.h>
    
    int binaryToDecimal(int binary) {
        int decimal = 0, weight = 1, rem;  //This function converts the given binary number to decimal number.
        while (binary != 0) {
            rem = binary % 10;
            decimal = decimal+ rem * weight;
            binary = binary / 10;
            weight = weight * 2;
        }
        return decimal;
    }
    
    void decimalToBinary(int decimal) {
        int rem, a[32], i = 0;         
        if (decimal == 0) {      //This function convert the decimal number to the binary number again.
            printf("0");
            return;
        }
        while (decimal > 0) {
            rem = decimal % 2;
            decimal = decimal/ 2;
            a[i] = rem;
            i++;
        }
        for (int j = i - 1; j >= 0; j--) {
            printf("%d", a[j]);
        }
    }
    
    void binaryCalculator(int binary1, int binary2, char operator) {
        int num1 = binaryToDecimal(binary1);
        int num2 = binaryToDecimal(binary2);   //This function performs the operation that you want to perform on the binary number.
        int result;
    
        if (operator == '+') {
            result = num1 + num2;
        } else if (operator == '-') {
            result = num1 - num2;
        } else if (operator == '*') {
            result = num1 * num2;
        } else if (operator == '/') {
            if (num2 != 0) {
                result = num1 / num2;
            } else {
                printf("Error: Division by zero\n");
                return;
            }
        } else {
            printf("Invalid operator\n");
            return;
        }
    
        printf("Result in binary: ");
        decimalToBinary(result);
        printf("\n");
    }
    
    int main() {
        int binary1, binary2;
        char operator;
    
        printf("Enter first binary number: ");
        scanf("%d", &binary1);
        printf("Enter operator (+, -, *, /): ");
        scanf(" %c", &operator);
        printf("Enter second binary number: ");
        scanf("%d", &binary2);
    
        binaryCalculator(binary1, binary2, operator);
    
        return 0;
    }
