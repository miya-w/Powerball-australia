# Australian Powerball analysis 
#### Description
 The Australian Powerball Analysis project delves into historical Powerball lottery data to uncover patterns, trends, and insights.

#### Tools used 
1. Python
2. Jupyter


### How this help me to pick the number
The Australian Powerball Analysis project doesn't guarantee winning numbers but you can use the logic to get the insights from historic date. It might help you to save your time.

### Will these calculated probabilities help me win the jackpot?

No, unfortunately not.

The Law of Large Numbers:
Using a coin as an example,
this fundamental principle of probability states that as the number of coin tosses increases, the proportion of heads and tails will approach 50-50. However, this does not mean that the exact number of heads and tails will always be equal.

A classic study by John Kerrich during World War II involved tossing a coin 10,000 times. The results showed that the ratio of heads to tails approached 50-50 over time, but deviations were always present at smaller intervals.

How Many Tosses to Reach 50-50?

Mathematically, ***there is no guarantee*** that the absolute counts of heads and tails will ever be perfectly equal. The probability of an exact tie decreases as the number of tosses increases due to the growing permutations of outcomes. However, the proportion (percentage) will get arbitrarily close to 50-50 as the number of tosses grows indefinitely.

 While probability theory can explain long-term trends in randomness, it cannot predict specific outcomes in the short term. Each draw is an independent event, and the odds of winning the jackpot remain astronomically. 


### How to Start python and Jupyter
```bash
# check python
python3 -V

# Start Python
python3 -m venv venv
source venv/bin/activate

# install jupyter
pip install jupyter 

# start jupyter
jupyter-notebook
```
#### Exit python even
```bash
deactivate
```


#### In jupyter:

```
# install pandas
!pip install pandas
```
```bash

import pandas as pd

file_path = ' the path of your csv file'
data = pd.read_csv(file_path)

```
### Calculate the most common and least common numbers in powerball history

```bash
from collections import Counter

# Combine columns #1 to #7 into a single series
combined_numbers = pd.concat([data[f'#{i}'] for i in range(1, 8)], axis=0)

# Count occurrences of each number for #1 to #7
number_counts = Counter(combined_numbers)

# Most common numbers between #1 and #7
most_common_numbers = number_counts.most_common()
most_common_number = most_common_numbers[0][0]
most_common_frequency = most_common_numbers[0][1]

print("Most common numbers between #1 and #7:")
print(f"Number: {most_common_number}, Frequency: {most_common_frequency}")

# Least common numbers between #1 and #7
least_common_numbers = [num for num, freq in number_counts.items() if freq == min(number_counts.values())]
print("Least common numbers between #1 and #7:")
print(f"Numbers: {least_common_numbers}, Frequency: {min(number_counts.values())}")

# Count occurrences of each number in PB
pb_counts = Counter(data['PB'])

# Most common number in PB
most_common_pb = pb_counts.most_common(1)[0]
print("Most common number in PB:")
print(f"Number: {most_common_pb[0]}, Frequency: {most_common_pb[1]}")

# Least common numbers in PB
least_common_pb = [num for num, freq in pb_counts.items() if freq == min(pb_counts.values())]
print("Least common numbers in PB:")
print(f"Numbers: {least_common_pb}, Frequency: {min(pb_counts.values())}")

```
results:
Most common numbers between #1 and #7:
Number: 17, Frequency: 82
Least common numbers between #1 and #7:
Numbers: [15, 26, 33], Frequency: 59
Most common number in PB:
Number: 2, Frequency: 27
Least common numbers in PB:
Numbers: [14], Frequency: 8

```bash
# list all the ranking of number
number_counts
```
result:
Counter({17: 82,
         7: 81,
         9: 80,
         3: 76,
         11: 76,
         20: 76,
         2: 74,
         6: 73,
         10: 72,
         16: 72,
         18: 72,
         12: 71,
         23: 71,
         25: 71,
         32: 71,
         19: 70,
         30: 70,
         4: 69,
         14: 69,
         28: 69,
         22: 68,
         35: 68,
         5: 67,
         27: 67,
         21: 66,
         24: 66,
         8: 64,
         34: 63,
         13: 62,
         1: 61,
         29: 61,
         31: 60,
         15: 59,
         26: 59,
         33: 59})

```bash
pb_counts
```
Counter({2: 27,
         4: 24,
         6: 23,
         15: 21,
         19: 21,
         7: 20,
         10: 20,
         3: 20,
         20: 18,
         9: 18,
         11: 18,
         18: 17,
         13: 16,
         17: 15,
         1: 13,
         16: 12,
         5: 12,
         8: 12,
         12: 10,
         14: 8})

#### Calculate the most difference in 2024 with the history
```bash
from datetime import datetime

def calculate_count_difference(data, date_column, number_columns, year):
    """
    Calculate the count difference for each number based on the whole sheet and the last year.

    Args:
        data (pd.DataFrame): The dataframe containing the data.
        date_column (str): The name of the column containing dates.
        number_columns (list): A list of column names (#1 to #7) containing numbers.
        year (int): The year to calculate the counts for the last year.

    Returns:
        dict: A dictionary with numbers as keys and the count difference as values.
    """
    # Convert the date column to datetime
    data[date_column] = pd.to_datetime(data[date_column], format='%d/%m/%y')
    
    # Filter rows for the given year
    last_year_data = data[data[date_column].dt.year == year]
    
    # Combine numbers from all columns (#1 to #7) for the whole sheet
    whole_sheet_numbers = pd.concat([data[col] for col in number_columns], axis=0)
    whole_sheet_counts = Counter(whole_sheet_numbers)
    
    # Combine numbers from all columns (#1 to #7) for the last year
    last_year_numbers = pd.concat([last_year_data[col] for col in number_columns], axis=0)
    last_year_counts = Counter(last_year_numbers)
    
    # Calculate the difference for each number
    count_difference = {
        number: whole_sheet_counts[number] - last_year_counts[number]
        for number in whole_sheet_counts
    }
    
    # Sort by count_difference values
    sorted_count_difference = sorted(count_difference.items(), key=lambda x: x[1], reverse=True)
    
    return sorted_count_difference


year = 2024
count_difference = calculate_count_difference(
    data=data,
    date_column='Date',
    number_columns=['#1', '#2', '#3', '#4', '#5', '#6', '#7'],
    year=year
)

print("Count Difference:")
print(count_difference)

pb_difference = calculate_count_difference(
    data=data,
    date_column='Date',
    number_columns=['PB'],
    year=year
)
print("PB Difference:")
print(pb_difference)


top7_diff = [k for k, v in count_difference[:7]]
pb_top_diff = [k for k, v in pb_difference[:1]]
print()
print(f"5. #1 ~ #7: {top7_diff}. PB: {pb_top_diff}")

```
Output:
Count Difference:
[(17, 76), (7, 71), (11, 68), (3, 66), (9, 66), (2, 65), (14, 64), (19, 64), (23, 64), (28, 63), (16, 62), (20, 62), (10, 61), (27, 61), (25, 61), (22, 60), (35, 60), (4, 59), (18, 59), (32, 59), (6, 58), (30, 58), (21, 57), (24, 57), (12, 56), (29, 56), (5, 55), (13, 55), (8, 55), (1, 53), (26, 53), (15, 51), (31, 51), (34, 50), (33, 50)]
PB Difference:
[(2, 21), (19, 21), (3, 19), (6, 18), (15, 18), (7, 17), (4, 17), (20, 16), (10, 16), (18, 15), (9, 15), (13, 15), (11, 15), (17, 13), (5, 12), (8, 12), (1, 11), (12, 10), (16, 9), (14, 8)]

5. #1 ~ #7: [17, 7, 11, 3, 9, 2, 14]. PB: [2]






Resources
---
- [the Lott - Powerball](https://www.thelott.com/powerball/results)
- [Powerball Statistics](https://australia.national-lottery.com/powerball/statistics)
- [Data Download - Powerball Results](https://gnetwork.com.au/powerball-results/)
- [jupyter](https://jupyter.org/)
