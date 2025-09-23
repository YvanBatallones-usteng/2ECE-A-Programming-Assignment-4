
# 2ECEA Programming Assignment 4 - Data Wrangling and Data Visualization

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

### Problem 1

**Code:**

```python
import pandas as pd

# Load the Excel dataset into a Pandas DataFrame
df = pd.read_excel("board2.xlsx")

# Apply multiple conditions to filter the dataset:
# 1. Electronics score must be greater than 70
# 2. Student must be from the Instrumentation track
# 3. Student’s hometown must be Luzon
# Then, only keep the columns: Name, GEAS, and Electronics
instru = df.loc[
    (df["Electronics"] > 70) &               # condition on Electronics score
    (df["Track"] == "Instrumentation") &     # condition on Track
    (df["Hometown"] == "Luzon"),             # condition on Hometown
    ["Name", "GEAS", "Electronics"]          # select only relevant columns
]

# Display the resulting filtered DataFrame
instru
```
The dataset is loaded into a DataFrame and filtered based on conditions. Only students in the Instrumentation track from Luzon with Electronics scores above 70 are selected, and their names, GEAS, and Electronics scores are displayed.

**Sample Output:**

```
   Name  GEAS  Electronics
3   S15    78           85
9   S42    81           90
```

### Problem 2

**Code:**

```python
import matplotlib.pyplot as plt

# Group the dataset by Track and calculate the mean of the "Average" column.
# This gives us the average score for each track.
avg_by_track = df.groupby("Track")["Average"].mean()

# Create a bar chart:
# - The x-axis shows the track names
# - The y-axis shows the average score per track
plt.bar(avg_by_track.index, avg_by_track.values)

# Add chart details for readability
plt.title("Averages by Track")       # chart title
plt.ylabel("Average Score")          # label for y-axis
plt.xlabel("Track")                  # label for x-axis

# Display the bar chart
plt.show()
```

The dataset is grouped by track, and the mean of the average scores is calculated for each group. These results are visualized in a bar chart, making it easy to compare overall performance across tracks.

**Sample Output:**

![A bar graph showing the average scores of students by track.](https://github.com/YvanBatallones-usteng/2ECE-A-Programming-Assignment-4/blob/5d03464fa7083e62f48995f57068495b78c44e6b/Bar_Graph.png)

---

## Author / Student Info

* **Name:** Yvan Reyan M. Batallones
* **Course:** 2ECE-A
* **Activity:** Programming Assignment 4 - Data Wrangling and Data Visualization

---
