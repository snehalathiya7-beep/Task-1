#!/usr/bin/env python3
"""
Simple CLI Calculator App
Author: Your Name
Description: A basic command-line calculator for simple arithmetic operations.
"""

import sys

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return "Error: Division by zero!"
    return a / b

def main():
    print("=== Simple CLI Calculator ===")
    print("Type 'exit' at any time to quit.\n")

    while True:
        try:
            # Read user input
            user_input = input("Enter expression (e.g., 5 + 3): ").strip()

            # Exit condition
            if user_input.lower() == "exit":
                print("Goodbye! ")
                sys.exit(0)

            # Split input
            parts = user_input.split()
            if len(parts) != 3:
                print("Invalid format. Use: <number> <operator> <number>")
                continue

            a, op, b = parts

            # Convert numbers
            try:
                a = float(a)
                b = float(b)
            except ValueError:
                print(" Invalid number. Please enter valid numeric values.")
                continue

            # Perform operation
            if op == "+":
                result = add(a, b)
            elif op == "-":
                result = subtract(a, b)
            elif op == "*":
                result = multiply(a, b)
            elif op == "/":
                result = divide(a, b)
            else:
                print(f" Unsupported operator: {op}")
                continue

            print(f" Result: {result}\n")

        except KeyboardInterrupt:
            print("\nGoodbye! 👋")
            sys.exit(0)

if __name__ == "__main__":
    main()
