# Programming Assignment 4: Data Wrangling and Data Visualization
> [!NOTE]
> 💡 Also called as "Data Munching" involves manipulation and transformation of data frames in preparation for data analytics.

## 📖 Intended Learning Outcomes
1. To identify the codes and functions needed in cleaning and visualizing data
2. To be able to apply and use the different codes and functions in creating a Python program that will
be used in data wrangling and data visualization

## ❓ Instructions and Problems
>[!IMPORTANT]
>Download the ECE Board Exam 2 dataset found on this link: [ECEBoardExamDataset](bit.ly/ECEBoardExamDataset) 

Write a Python script/code in the Jupyter Notebook to do the given problems. You may submit your Jupyter
notebook in the dedicated submission bin.

### 🔩 ECE Board Exam Problem
sing data wrangling and data visualization technique with
storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

#### 🔧 Problem 1: Data Wrangling
Create the following data frames based on the format provided:

Example: Vis = [“Name”, “Gender”, “Track”, “Math<70”]; hometown is constant as **Visayas**

Output:

![image](https://github.com/user-attachments/assets/ba6930c6-76c1-44e3-8baf-7007ea45601a)

a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as
**Instrumentation** and hometown **Luzon**

b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is
constant as **Mindanao** and gender **Female**


#### 🔧 Problem 2: Data Visualization
Create a visualization that shows how the different features contributes to average grade. Does
chosen track in college, gender, or hometown contributes to a higher average score?

## 💿 Utilized IDE
> [!NOTE]
> Jupyter Notebook is used to solve the problem. You can use this IDE using [Anaconda Navigator](https://www.anaconda.com)

## 💻 Code Summary and Outcome

It is essential to import the pandas library as it will be required for data wrangling and visualization
```python
import pandas as pd
```
After downloading the "boards2.xlsx" file, it will be put inside the boards variable
> [!IMPORTANT]
> The boards2.xlsx can be downloaded inside this [link](bit.ly/ECEBoardExamDataset)

```python
boards = pd.read_excel("board2.xlsx")
boards
```
The result will be displayed as:

![image](https://github.com/user-attachments/assets/abf10c00-ff6b-4464-b3a7-1fde15992d5b)

### 📚 Problem 1 Solution:

To display a dataframe wherein the Name, GEAS, and Electronics grade more than 70 are displayed; With people who only lives at Luzon and has a track of Instrumentation. The .loc() function is going to be used, 
with multiple AND conditions and only a specific columns that are going to be shown.

```python
Instru = boards.loc[(boards['Hometown'] == 'Luzon') & (boards['Track'] == 'Instrumentation') & (boards['Electronics'] > 70), ['Name','GEAS','Electronics']]
Instru
```

The result will be displayed as:

![image](https://github.com/user-attachments/assets/204acd88-5fc3-4542-871e-a4b65fe039a7)

To display a dataframe wherein the Name, Track, Electronics, and Average greater or equal to 55 are displayed; With people who only lives at Mindanao and are female. The .loc() function is going to be used, 
with multiple AND conditions and only a specific columns that are going to be shown. The additional key named "Average" is going to be added with the .mean() function that is going to be utilized.
The .mean() function will only compute for the mean of each row (4 subjects) because its set at axis=1 and it will be rounded by 2 using the round() function.

```python
boards['Average'] = round(boards[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1),2)
Mindy = boards.loc[(boards['Hometown'] == 'Mindanao') & (boards['Gender'] == 'Female') & (boards['Average'] >= 55), ['Name','Track','Electronics', 'Average']]
Mindy
```

The result will be displayed as:

![image](https://github.com/user-attachments/assets/6361d0b0-6b70-4a17-82f4-95914f4172aa)

### 📚 Problem 2 Solution:

It is essential to import the matplotlib.pyplot library as it will be required for making different graphs

```python
import mathplotlib.pyplot as plt
```

Displaying different tracks, genders, and hometowns through bar graph for better interpretation of data with figure size modification settings. The average is going to be used as measurement for the comparison

**First: 3 Hometowns and their average**

```python
plt.figure(figsize=(10,4))
plt.bar(boards['Hometown'],boards['Average'])
```

The result will be displayed as:

![image](https://github.com/user-attachments/assets/f05331be-af1d-4d30-a54a-fd2782da6f93)

It was shown that Luzon has the highest average grade with Mindanao being the lowest

**Second: 3 Tracks and their average**

```python
plt.figure(figsize=(10,4))
plt.bar(boards['Track'],boards['Average'])
```
The result will be displayed as:

![image](https://github.com/user-attachments/assets/df40eb9a-1f63-4981-9fbd-16ca93af1a77)

It was shown that Microelectronics has the highest average grade with Instrumentation being the lowest

**Third: 2 Genders and their average**

```python
plt.figure(figsize=(10,4))
plt.bar(boards['Gender'],boards['Average'])
```

The result will be displayed as:

![image](https://github.com/user-attachments/assets/3ee54f22-05e9-471d-9e99-46abcd096c1b)

It was shown that Females perform well and has higher average grade than Males

With these data wrangling and visualization, the students will be able to learn how to organize, visualize, and interpret data using python

## 🛠 Author
#### Name: Kyle Adrienne S. Hizon
#### Section: 2ECE-A

## 🔑 Version History

- 1.02
  - Revised the supplemental files

- 1.01
  - Readme file completed

- 1.00
  - Added the supplemental files
  - Repository has been established




















