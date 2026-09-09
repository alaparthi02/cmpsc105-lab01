# CMPSC 105 Data Exploration - Lab 01: Using Pandas

## Overview
Welcome to the lab! Today, we will establish our standard version control workflow using GitHub and take our first steps into data manipulation using the Python `pandas` library. 

## Part 1: The GitHub Workflow
In this course, our cadence for managing assignments relies on GitHub. Before we write any code, we need to set up your environment. Follow these steps:

1. **Fork the Repository:** Navigate to the provided lab repository link. In the top right corner, click the **Fork** button. This creates a personal copy of the repository under your own GitHub account.
2. **Clone the Repository:** Open your terminal in VS Code and clone your *forked* version of the repository to your local machine:
   ```bash
   git clone https://github.com/YOUR_USERNAME/cmpsc105-lab01.git
   ```
3. **Navigate and Open:** Open the folder in VS Code.
4. **Pushing Your Work:** Once you complete the lab, add, commit, and push your changes to your fork. In VS Code, this can be done by
- Clicking the Source Control icon in the left sidebar, 
- Staging your changes and writing a commit message
- Committing the changes by clicking the checkmark, and finally
- Pushing the changes to your forked repository by clicking the "..." menu and selecting "Push".

## Part 2: Setting up the Python Environment with `uv`
Before we run our analysis, we need an isolated environment to manage our dependencies. We use `uv`, an extremely fast Python package manager.

1. **Create the Virtual Environment:** In your terminal, ensure you are inside the `cmpsc105-lab01` directory, then run:
   ```bash
   uv venv
   ```
2. **Activate the Environment:** You must activate the environment so your terminal uses the isolated Python version.
   * On **macOS/Linux**:
     ```bash
     source .venv/bin/activate
     ```
   * On **Windows**:
     ```bash
     .venv\Scripts\activate
     ```
3. **Install Pandas:** With the environment active, install the required library:
   ```bash
   uv add pandas
   ```

## Part 3: Setting up Pandas and Reading Data
Pandas is an essential library for data analysis in Python. Your cloned repository contains a file named `"dining.csv"` that we've seen in lecture. This file contains data about dining hall usage, and we will use it to practice our data manipulation skills.

First, let's import the library and read the data into a DataFrame. Create a new Python file (e.g., `lab.py`) or use the provided starter notebook.

```python
import pandas as pd

# Load the dataset
# We refer to the file by its exact name: "dining.csv"
df = pd.read_csv("dining.csv")

# Display the first 5 rows to understand the structure
print(df.head())
```

*Debugging Tip:* If you encounter a `FileNotFoundError`, think through where `"dining.csv"` is located. Often, you just need to ensure you are working from the correct folder!

## Part 4: Data Manipulation
Now that the data is loaded, let's explore and manipulate it. 

**Task 1: Basic Exploration**
Write code to print out the total number of rows and columns in the dataset using `df.shape`. Also, use `df.info()` to see the data types of each column.

**Task 2: Filtering Data**
Let's subset our data. Filter the DataFrame to include only rows from one of the dining halls. Name the filtered DataFrame something other than `df`. Print the first 5 rows of your filtered DataFrame to verify that the filtering worked as expected.

**Task 3: Creating a New Column**
You can create new columns in your DataFrame based on existing data. For example, if our dataset contains columns for the number of breakfast, lunch, and dinner swipes with names `"breakfast"`, `"lunch"`, and `"dinner"`. You can create a new column that sums these values to get the total swipes.

```python
df["total_swipes"] = df["breakfast"] + df["lunch"] + df["dinner"]
```

Given this, create a new column in your filtered DataFrame called `"average_coffee"` that calculates the average coffee consumption per swipe. Print out the first 5 rows of your filtered DataFrame to verify that the new column has been calculated correctly.

**Task 4: Sorting Data**
Finally, sort your filtered DataFrame based on the new `"average_coffee"` column in descending order. For example, you can sort a DataFrame `df` by a column named `"COLUMN NAME"` in descending order using the following code:

```python
df = df.sort_values(by="COLUMN NAME", ascending=False)
```

Print the first 5 rows of the sorted DataFrame to see which day had the highest average coffee consumption per swipe.


## Part 5: Saving Your Output
After cleaning and manipulating your data, it's crucial to know how to save your results. We will save our filtered and modified DataFrame into a new CSV file.

```python
# Save the modified DataFrame to a new file
# index=False prevents pandas from writing row numbers as a new column
filtered_df.to_csv("modified_dining.csv", index=False)
```

## Part 5: Submission and Exercise
Once you have successfully saved `"modified_dining.csv"`, commit and push your final code and the new CSV file to your GitHub fork.

Before you finish, add a short text file (`evaluation.md`) to your repository and answer the following metacognitive questions:
1. What was the most challenging part of this lab for you, and how did you overcome it?
2. Which dining hall did you choose to analyze?
3. For your chosen dining hall, which day had the highest coffee consumption per swipe?
4. How would you determine which day had the lowest coffee consumption per swipe for your dining hall?

Commit and push this repo file to complete the lab!