#include <iostream>
#include <string>
#include <bitset>
#include <cstdlib>   // for rand() and srand()
#include <ctime>     // for time()

using namespace std;

// Function 1: Decimal to Binary
string decimalToBinary(int decimalNumber) {
    string binary = "";
    if (decimalNumber == 0) return "0";
    while (decimalNumber > 0) {
        binary = char((decimalNumber % 2) + '0') + binary;
        decimalNumber /= 2;
    }
    return binary;


// Function 2: Binary to Decimal
int binaryToDecimal(const string &binaryString) {
    int decimal = 0;
    for (char bit : binaryString) {
        if (bit == '0' || bit == '1') {
            decimal = decimal * 2 + (bit - '0');
        } else {
            return -1; // invalid binary
        }
    }
    return decimal;
}

// Function 3: Decimal to Hexadecimal
string decimalToHexadecimal(int decimalNumber) {
    if (decimalNumber == 0) return "0";
    string hexChars = "0123456789ABCDEF";
    string hex = "";
    while (decimalNumber > 0) {
        int remainder = decimalNumber % 16;
        hex = hexChars[remainder] + hex;
        decimalNumber /= 16;
    }
    return hex;
}

// Function 4: Hexadecimal to Decimal
int hexadecimalToDecimal(const string &hexString) {
    int decimal = 0;
    for (char c : hexString) {
        int value;
        if (c >= '0' && c <= '9') value = c - '0';
        else if (c >= 'A' && c <= 'F') value = c - 'A' + 10;
        else if (c >= 'a' && c <= 'f') value = c - 'a' + 10;
        else return -1; // invalid
        decimal = decimal * 16 + value;
    }
    return decimal;
}

// Demo function
void demoConversion() {
    int randomNumber = rand() % 100;  // between 0 and 99
    cout << "\nDemo Number: " << randomNumber << endl;
    cout << "Binary Equivalent: " << decimalToBinary(randomNumber) << endl;
}

// Display menu
void displayMenu() {
    cout << "\n==== Number Conversion Menu ====" << endl;
    cout << "1. Convert Decimal to Binary" << endl;
    cout << "2. Convert Binary to Decimal" << endl;
    cout << "3. Convert Decimal to Hexadecimal" << endl;
    cout << "4. Convert Hexadecimal to Decimal" << endl;
    cout << "5. Demo (Generate and convert random integers to binary)" << endl;
    cout << "6. Exit" << endl;
    cout << "Enter your choice (1-6): ";
}

int main() {
    srand(time(0)); // Seed random number generator
    int choice;

    do {
        displayMenu();
        cin >> choice;

        if (choice == 1) {
            int num;
            cout << "Enter a decimal number: ";
            cin >> num;
            cout << "Binary: " << decimalToBinary(num) << endl;
        }
        else if (choice == 2) {
            string binary;
            cout << "Enter a binary number: ";
            cin >> binary;
            int result = binaryToDecimal(binary);
            if (result == -1)
                cout << "Invalid binary number!" << endl;
            else
                cout << "Decimal: " << result << endl;
        }
        else if (choice == 3) {
            int num;
            cout << "Enter a decimal number: ";
            cin >> num;
            cout << "Hexadecimal: " << decimalToHexadecimal(num) << endl;
        }
        else if (choice == 4) {
            string hex;
            cout << "Enter a hexadecimal number: ";
            cin >> hex;
            int result = hexadecimalToDecimal(hex);
            if (result == -1)
                cout << "Invalid hexadecimal number!" << endl;
            else
                cout << "Decimal: " << result << endl;
        }
        else if (choice == 5) {
            demoConversion();
        }
        else if (choice == 6) {
            cout << "Exiting program. Goodbye!" << endl;
        }
        else {
            cout << "Invalid choice. Please try again." << endl;
        }

    } while (choice != 6);

    return 0;
}
