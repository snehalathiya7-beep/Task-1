# Task-1
Python internship

# Calculator CLI App

import sys

def add(x, y):
    """Returns the sum of two numbers."""
    return x + y

def subtract(x, y):
    """Returns the difference of two numbers."""
    return x - y

def multiply(x, y):
    """Returns the product of two numbers."""
    return x * y

def divide(x, y):
    """Returns the quotient of two numbers, handling division by zero."""
    if y == 0:
        raise ZeroDivisionError("Error: Cannot divide by zero.")
    return x / y

def calculator_cli():
    """
    The main function for the Command Line Interface Calculator.
    Continuously prompts the user for calculations until they type 'quit'.
    """
    print("Welcome to the CLI Calculator!")
    print("Available operations: +, -, *, /")
    print("Enter 'quit' to exit the application.")
    print("-" * 30)

    while True:
        try:
            # Prompt user for the expression
            user_input = input("Enter expression (e.g., 5 + 3 or quit): ").strip()

            if user_input.lower() == 'quit':
                print("Thank you for using the CLI Calculator. Goodbye!")
                sys.exit(0)

            # Split the input into components (operand1, operator, operand2)
            parts = user_input.split()

            if len(parts) != 3:
                print("Invalid input format. Please enter 'Number Operator Number' (e.g., 10 * 5).")
                continue

            num1_str, operator, num2_str = parts

            # Convert string inputs to floating-point numbers
            try:
                num1 = float(num1_str)
                num2 = float(num2_str)
            except ValueError:
                print("Invalid number input. Please ensure both operands are valid numbers.")
                continue

            result = None
            
            # Perform the calculation based on the operator
            if operator == '+':
                result = add(num1, num2)
            elif operator == '-':
                result = subtract(num1, num2)
            elif operator == '*':
                result = multiply(num1, num2)
            elif operator == '/':
                result = divide(num1, num2)
            else:
                print(f"Invalid operator: '{operator}'. Use +, -, *, or /.")
                continue

            # Print the result
            print(f"Result: {result}")

        except ZeroDivisionError as e:
            print(e)
        except Exception as e:
            # Catch any other unexpected errors
            print(f"An unexpected error occurred: {e}")
            print("Please try again.")
        
        print("-" * 30)


if __name__ == "__main__":
    calculator_cli()