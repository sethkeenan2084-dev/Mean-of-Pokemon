# Open and read the CSV file
attack = []
defense = []
speed = []

with open('pokemon_data.csv', 'r', encoding='utf-8') as f:
    lines = f.readlines()

# Get column indices
header = lines[0].strip().split(',')
attack_idx = header.index('attack')
defense_idx = header.index('defense')
speed_idx = header.index('speed')

# Extract values
for line in lines[1:]:
    cols = line.strip().split(',')
    # Skip rows with missing values
    if cols[attack_idx] and cols[defense_idx] and cols[speed_idx]:
        attack.append(int(cols[attack_idx]))
        defense.append(int(cols[defense_idx]))
        speed.append(int(cols[speed_idx]))

def calc_mean(data):
    return sum(data) / len(data)

def calc_median(data):
    data_sorted = sorted(data)
    n = len(data_sorted)
    mid = n // 2
    if n % 2 == 0:
        return (data_sorted[mid - 1] + data_sorted[mid]) / 2
    else:
        return data_sorted[mid]

def calc_range(data):
    return max(data) - min(data)

def print_stats(name, data):
    print(f"{name} - Mean: {calc_mean(data)}, Median: {calc_median(data)}, Range: {calc_range(data)}")

print_stats('Attack', attack)
print_stats('Defense', defense)
print_stats('Speed', speed)

You can calculate the mean, median, and range for attack, defense, and speed without using any modules by manually reading the CSV file and implementing the calculations yourself. Here’s how you can do it:

Purpose of the Program
This program analyzes Pokémon stats from a CSV file (pokemon_data.csv).
It calculates and prints the mean, median, and range for the attack, defense, and speed attributes of all Pokémon listed in the file.

What the Program Does
Inputs:

Reads data from pokemon_data.csv (must be in the same folder as the script).
Process:

Extracts the attack, defense, and speed values for each Pokémon.
Calculates the mean (average), median (middle value), and range (max - min) for each stat.
Outputs:

Prints the mean, median, and range for attack, defense, and speed to the terminal.
Example output:

How to Use the Program
Place pokemon_data.csv in the same directory as Mean_of_pokemon.py.
Open a terminal in VS Code.
Run the script with:
View the results printed in the terminal.
No additional modules are required; only standard Python functions are used.
