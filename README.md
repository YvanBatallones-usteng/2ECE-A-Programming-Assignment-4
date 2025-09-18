# 2ECEA Programming Assignment 4- DATA WRANGLING AND DATA VISUALIZATION

This repository contains solutions to programming exercises implemented in Python using Jupyter Notebook. The problems focus on **data manipulation and analysis** using the **Pandas** library.

## Contents

* **Problem 1: Data Filtering with Conditions**  
  A program that creates different DataFrames based on given conditions such as track, hometown, gender, and subject scores using the `board2.xlsx` dataset.

* **Problem 2: Data Visualization**  
  A program that visualizes how different features (track, gender, and hometown) contribute to the average grade using bar graphs.

## Files

* `2ECEA_PA4_Batallones.ipynb` — Jupyter Notebook containing solutions for Problem 1 and Problem 2.  
* `board2.xlsx` — Excel dataset used for data manipulation and analysis.  
* `instructions.png` — Screenshot of the given problem instructions.

## Example Usage

**Problem 1:**

```python
import pandas as pd

# Load the dataset into a DataFrame
df = pd.read_excel("board2.xlsx")

# Create a DataFrame for Instrumentation track, Luzon hometown, and Electronics > 70
instru = df.loc[
    (df["Electronics"] > 70) &
    (df["Track"] == "Instrumentation") &
    (df["Hometown"] == "Luzon"),
    ["Name", "GEAS", "Electronics"]
]
instru
````

**Sample Output:**

```text
   Name  GEAS  Electronics
3   S15    78           85
9   S42    81           90
```

**Problem 2:**

```python
import matplotlib.pyplot as plt

# Group by Track and compute mean of Average
avg_by_track = df.groupby("Track")["Average"].mean()

# Plot bar chart
plt.bar(avg_by_track.index, avg_by_track.values)
plt.title("Averages by Track")
plt.ylabel("Average Score")
plt.xlabel("Track")
plt.show()
```

**Sample Output:**

![A bar graph showing the average scores of students by track.](https://github.com/YvanBatallones-usteng/2ECE-A-Programming-Assignment-4/blob/5d03464fa7083e62f48995f57068495b78c44e6b/Bar_Graph.png)

## Author / Student Info

* **Name:** Yvan Reyan M. Batallones
* **Course:** 2ECE-A
* **Activity:** Programming Assignment 4 - DATA WRANGLING AND DATA VISUALIZATION

