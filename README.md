# Ohms-Law-Calculator.26
Command-line Python tool that solves Ohm's Law for voltage, current or resistance.
# The programme should be able to calculate voltage, current, or resistace when given 2 of the variables.
#V= I*R; R = V/I; I =V/R
# Output e.g. Calculated voltage: 10V
# Rules: all values above 0, 2 decimals, a comma accepted as a decimal point.

#the funtion receives voltage(Volts) and resistance(Ohms), and it caluculates current(Amps)
def calculate_current(voltage, resistance):
  return voltage/resistance

#the funtion receives current(Amps) and resistance(Ohms), and it caluculates voltage(volts)
def calculate_voltage(current, resistance):
  return current*resistance

#the funtion receives voltage(Volts) and current(Amps), and it caluculates resistance(Ohms)
def calculate_resistance(voltage, current):
  return voltage/current

#Goal: one function that asks for a number and keeps asking until it gets a valid one. 
def get_number(prompt):
  while True:
     user_input = input(prompt)
     cleaned_input = user_input.replace(",",".")

     try:
          number= float(cleaned_input)
     except ValueError:
        print("Invalid input. Please enter a number.")
        continue

     if number <= 0 :
        print("Value should be greater than 0.")
        continue

     return number

#ne function that asks what to solve for and only returns "V", "I" or "R". It uses the same loop pattern as Stage 2, which is the point: you are reusing an idea, not learning a new one
def get_choice():
    print("The calculator needs either two values from resistance(R), voltage(V), and current(I). Below choose what you want to solve for and provide the values for the calculations")
  
    while True:
        user_input= input("What do you want to solve for between V, I , and R? ").strip().upper()

        if user_input in ("V", "R", "I"):
           return user_input

        print("Invalid choice. Please enter V, I, or R")
    

#connect the pieces so one full run works. 
def main():
  while True:
    choice = get_choice()

    if choice == "V":
       current = get_number("Enter current: ")
       resistance = get_number("Enter resistance: ")
 
       result= calculate_voltage(current, resistance)

       print("Formula: V = I*R ")
       print(f"Calculated voltage: {result:.2f} V")


    elif choice == "I":
        voltage = get_number("Enter voltage: ")
        resistance = get_number("Enter resistance: ")

        result = calculate_current(voltage, resistance)

        print("Formula: I = V/R")
        print(f'Calculated current: {result:.2f} A')

    elif choice == "R":
        voltage = get_number("Enter voltage: ")
        current = get_number("Enter current: ")

        result = calculate_resistance(voltage, current)

        print("Formula:  R= V/I")
        print(f'Calculated Resistance: {result:.2f} Ohms')

    user_input= input('Do you want to calculate again? y/n ')
    cleaned_user_input = user_input.strip().lower()

    if cleaned_user_input == "y":
          continue

    elif cleaned_user_input == "n":
        print("Goodbye!")
        break

if __name__ == "__main__":
    main()
