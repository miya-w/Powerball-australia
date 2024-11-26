# Australian Powerball analysis 
![]()
#### Description
 The Australian Powerball Analysis project delves into historical Powerball lottery data to uncover patterns, trends, and insights.

#### Tools used 
1. Python
2. Jupyter


### How this help me to pick the number

The Australian Powerball Analysis project doesn't guarantee winning numbers but provides insights from historical data. It might help you save time when picking numbers by setting logical criteria, ex. selecting the most common or least common numbers.

### Will these calculated probabilities help me win the jackpot?

No, unfortunately not.

The Law of Large Numbers:
Using a coin as an example,
this fundamental principle of probability states that as the number of coin tosses increases, the proportion of heads and tails will approach 50-50. However, this does not mean that the exact number of heads and tails will always be equal.

A classic study by John Kerrich during World War II involved tossing a coin 10,000 times. The results showed that the ratio of heads to tails approached 50-50 over time, but deviations were always present at smaller intervals.

How Many Tosses to Reach 50-50?

Mathematically, ***there is no guarantee*** that the absolute counts of heads and tails will ever be perfectly equal. The probability of an exact tie decreases as the number of tosses increases due to the growing permutations of outcomes. However, the proportion (percentage) will get arbitrarily close to 50-50 as the number of tosses grows indefinitely.

 While probability theory can explain long-term trends in randomness, it cannot predict specific outcomes in the short term. Each draw is an independent event, and the odds of winning the jackpot remain astronomically. 

### ps. Australian Powerball Odds of Winning
| Division | Numbers Matched              | Odds of Winning        |
|----------|------------------------------|------------------------|
| 1        | 7 main numbers + the Powerball | 1 in 134,490,400      |
| 2        | 7 main numbers               | 1 in 7,078,443        |
| 3        | 6 main numbers + the Powerball | 1 in 686,176          |
| 4        | 6 main numbers               | 1 in 36,115           |
| 5        | 5 main numbers + the Powerball | 1 in 16,943          |
| 6        | 4 main numbers               | 1 in 1,173            |
| 7        | 5 main numbers               | 1 in 892              |
| 8        | 3 main numbers + the Powerball | 1 in 188             |
| 9        | 2 main numbers + the Powerball | 1 in 66              |


---
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
