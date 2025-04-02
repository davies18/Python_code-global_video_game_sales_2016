# Video Game Sales Analysis

## Table of Contents

-   [Short Description](#short-description)
-   [Getting Started](#getting-started)
    -   [Prerequisites](#prerequisites)
    -   [Installing](#installing)
-   [Running the Code](#running-the-code)
-   [Breakdown of the Code](#breakdown-of-the-code)
    -   [Explanation of Python Code](#explanation-of-python-code)
-   [Deployment](#deployment)
-   [Author](#author)
-   [License](#license)
-   [Acknowledgments](#acknowledgments)

## Short Description

This project analyzes video game sales data from a CSV file to determine if the average global sales were higher before or after 2005. It also creates a new column, 'Period', to categorize records as 'pre-2005' or 'post-2005' based on the release year. The analysis addresses missing values in the 'Year' column and calculates the average global sales for each period. This project was developed using Jupyter Notebook.

## Getting Started

### Prerequisites

-   Python 3.6 or later: Python is the programming language used for this analysis. The specified version ensures compatibility with the libraries used.
-   Pandas library (`pip install pandas`): Pandas is essential for data manipulation and analysis, providing data structures like DataFrames for efficient data handling.
-   NumPy library (`pip install numpy`): NumPy is used for numerical operations, particularly for creating the 'Period' column based on conditional logic.
-   Jupyter Notebook (optional, but recommended for interactive use): Jupyter Notebook allows for interactive coding and data exploration, making it easier to visualize and understand the data.

### Installing

1.  Clone the repository to your local machine:

    ```bash
    git clone [https://github.com/davies18/Python_code-global_video_game_sales_2016.git](https://www.google.com/search?q=https://github.com/davies18/Python_code-global_video_game_sales_2016.git)
    ```

    *Justification*: Cloning the repository ensures you have a local copy of all project files, including the Python script and data.

2.  Navigate to the project directory:

    ```bash
    cd Python_code-global_video_game_sales_2016
    ```

    *Justification*: This step moves you to the correct directory where the project files are located, allowing you to run the script.

3.  Install the required Python libraries:

    ```bash
    pip install pandas numpy
    ```

    *Justification*: Installing Pandas and NumPy ensures that your Python environment has the necessary tools for data manipulation and numerical operations used in the analysis.

4.  (Optional) to use Jupyter Notebook, make sure you have it installed. If not, install it via:

    ```bash
    pip install notebook
    ```

    *Justification*: Jupyter Notebook provides an interactive environment for running and testing the code.

## Running the Code

1.  Ensure you have the `vgsales.csv` file (or a similar CSV file with video game sales data) in the same directory as the `video_game_sales_analysis.py` script.
2.  **Using Python script:**

    ```bash
    python video_game_sales_analysis.py
    ```

    *Justification*: This command executes the Python script, which performs the data analysis and prints the results.

3.  **Using Jupyter Notebook (recommended):**

    -   Open Jupyter Notebook in your terminal: `jupyter notebook`
    -   Navigate to the project directory and open a new notebook or copy the python code into the notebook.
    -   Run the cells to execute the code.

    *Justification*: Jupyter Notebook provides an interactive environment for running and testing the code, allowing for step-by-step execution and visualization of results.

4.  The script/notebook will output the average global sales before and after 2005.

## Breakdown of the Code

### Explanation of Python Code

The python script `video_game_sales_analysis.py` performs the following actions:

1.  **Data Loading:**
    -   Uses Pandas to read the video game sales data from a CSV file into a DataFrame.

    ```python
    df = pd.read_csv(filepath)
    ```

    *Justification*: Pandas' `read_csv()` function efficiently reads CSV files into a DataFrame, a tabular data structure that simplifies data manipulation. Assigning the data to the variable `df` (short for DataFrame) allows for easy reference and manipulation throughout the script.

2.  **Missing Value Handling:**
    -   Identifies and fills missing values in the 'Year' column with the mode (most frequent value) of the column.
    -   This ensures that the analysis is not skewed by missing year data.

    ```python
    mode_year = df['Year'].mode()[0]
    df['Year'].fillna(mode_year, inplace=True)
    ```

    *Justification*: Missing year values would lead to incorrect calculations of average sales per period. Filling these values with the mode preserves the data's distribution without introducing bias from arbitrary values.

3.  **Data Type Conversion:**
    -   Converts the 'Year' column to integer data type for accurate calculations.

    ```python
    df['Year'] = df['Year'].astype(int)
    ```

    *Justification*: Converting the 'Year' column to integers ensures accurate comparison and categorization of years, which is essential for creating the 'Period' column and calculating average sales.

4.  **Creating the 'Period' Column:**
    -   Uses NumPy's `where` function to create a new 'Period' column.
    -   Records with 'Year' greater than or equal to 2005 are labeled 'post-2005', and those before are labeled 'pre-2005'.

    ```python
    df['Period'] = np.where(df['Year'] >= 2005, 'post-2005', 'pre-2005')
    ```

    *Justification*: The 'Period' column categorizes the data into the two periods of interest, enabling the calculation of average sales for each period. NumPy's `where` function efficiently applies the conditional logic to create this column.

5.  **Calculating Average Global Sales:**
    -   Calculates the average global sales for each period ('pre-2005' and 'post-2005') using Pandas' `mean()` function.

    ```python
    avg_sales_pre_2005 = df[df['Period'] == 'pre-2005']['Global_Sales'].mean()
    avg_sales_post_2005 = df[df['Period'] == 'post-2005']['Global_Sales'].mean()
    ```

    *Justification*: Calculating the average global sales for each period addresses the project's main objective, providing a quantitative measure of sales performance before and after 2005. Pandas' `mean()` function simplifies this calculation.

6.  **Output:**
    -   Prints the calculated average global sales for both periods.

    ```python
    print(f"Average Global Sales before 2005: {pre_2005_avg:.2f}")
    print(f"Average Global Sales after 2005: {post_2005_avg:.2f}")
    ```

    *Justification*: Printing the results provides a clear and immediate output of the analysis, allowing users to quickly understand the findings.

## Deployment

This script can be deployed as a part of a larger data analysis pipeline. You can integrate it into a web application or use it for batch processing of data.

## Author

-   OLOWONIRAN-DAVIES, DEWALADE


## License

This project is licensed under the MIT License - see the `LICENSE` file for details.

## Acknowledgments

-   This project was inspired by the need to analyze video game sales data and draw meaningful insights.
-   The use of Pandas and NumPy libraries was crucial for data manipulation and analysis.
-   The use of Jupyter notebook assisted in the interactive development of this project.
-   Special thanks to Durham College, Canada, and the coordinators of the Data Analysis Tools Analytics program.
-   Project 1, Group 5 (Dated 2025) members:
    -   OKPALEFE OGHENETEJIRI
    -   KADIKU FARUQUAT
    -   OWUSU KEITH
    -   KARRA AKHIL
-   The team effort was crucial in overcoming challenges and completing the project.
