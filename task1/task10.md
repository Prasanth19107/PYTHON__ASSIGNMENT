# 1. Problem Statement
Develop a Python program to calculate traffic violation penalties for multiple offences based on vehicle category, offence type, and repeat-offence status. The program applies predefined fine rules, calculates the total penalty, and identifies whether the driver may face disqualification.
# 2. Algorithm
1. Start the program.
2. Enter the number of violations.
3. For each violation, enter the vehicle category, offence type, and whether it is a repeat offence.
4. Find the base fine using predefined rules.
5. Increase the fine for repeat offences.
6. Add each fine to the total penalty.
7. Check whether any offence triggers disqualification.
8. Display individual fines, total penalty, and disqualification status.
9. Stop.
# 3. Flowchart (Mermaid)
```mermaid
flowchart TD
    A([Start]) --> B[/Enter number of violations/]
    B --> C[/Enter vehicle, offence and repeat status/]
    C --> D[Find predefined fine]
    D --> E{Repeat offence?}
    E -- Yes --> F[Double the fine]
    E -- No --> G[Keep base fine]
    F --> H[Add fine to total]
    G --> H
    H --> I{More violations?}
    I -- Yes --> C
    I -- No --> J{Disqualification condition met?}
    J -- Yes --> K[Display disqualification warning]
    J -- No --> L[Display no disqualification]
    K --> M[/Display total penalty/]
    L --> M
    M --> N([Stop])
```
# 4. Source Code (Python)

fine_rules = {
    "bike": {"speeding": 1000, "signal": 500,
             "helmet": 500, "drunk": 10000},
    "car": {"speeding": 1500, "signal": 1000,
            "helmet": 500, "drunk": 10000},
    "truck": {"speeding": 2000, "signal": 1500,
              "helmet": 500, "drunk": 10000}
}

n = int(input("Enter number of violations: "))
total = 0
disqualified = False

for i in range(n):
    vehicle = input("Vehicle (bike/car/truck): ").lower()
    offence = input("Offence (speeding/signal/helmet/drunk): ").lower()
    repeat = input("Repeat offence? (yes/no): ").lower()

    fine = fine_rules[vehicle][offence]

    if repeat == "yes":
        fine *= 2

    total += fine

    if offence == "drunk":
        disqualified = True

    print("Fine:", fine)

print("Total penalty:", total)
if disqualified:
    print("Disqualification condition triggered")
else:
    print("No disqualification condition triggered")

# 5. Sample Input

Enter number of violations: 2

Vehicle (bike/car/truck): bike
Offence (speeding/signal/helmet/drunk): helmet
Repeat offence? (yes/no): no

Vehicle (bike/car/truck): car
Offence (speeding/signal/helmet/drunk): speeding
Repeat offence? (yes/no): yes
# 6. Sample Output
Fine: 500
Fine: 3000
Total penalty: 3500
No disqualification condition triggered
# 7. Screenshot

<img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/118db062-638f-400b-bfd3-f2f93dd4cfcc" />

