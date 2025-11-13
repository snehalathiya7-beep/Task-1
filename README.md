# Task-1
Python internship

# Calculator CLI App

def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return "Error: Cannot divide by zero!"
    return a / b

def calculator():
    print("=== Simple CLI Calculator ===")
    print("Operations: +  -  *  /")
    print("Type 'exit' to quit.\n")

    while True:
        user_input = input("Enter expression (e.g., 5 + 3): ").strip()

        if user_input.lower() == 'exit':
            print("Goodbye 👋")
            break

        try:
            parts = user_input.split()
            if len(parts) != 3:
                print("Invalid format! Use: number operator number")
                continue

            a = float(parts[0])
            op = parts[1]
            b = float(parts[2])

            if op == '+':
                result = add(a, b)
            elif op == '-':
                result = subtract(a, b)
            elif op == '*':
                result = multiply(a, b)
            elif op == '/':
                result = divide(a, b)
            else:
                result = "Invalid operator!"

            print(f"Result: {result}\n")

        except ValueError:
            print("Error: Please enter valid numbers.\n")

if __name__ == "__main__":
    calculator()