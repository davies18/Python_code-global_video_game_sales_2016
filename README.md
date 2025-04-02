# Python_code-global_video_game_sales_2016

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

-   Python 3.6 or later
-   Pandas library (`pip install pandas`)
-   NumPy library (`pip install numpy`)
-   Jupyter Notebook (optional, but recommended for interactive use)

### Installing

1.  Clone the repository to your local machine:

    ```bash
    git clone <https://github.com/davies18/Python_code-global_video_game_sales_2016/tree/main>
    ```

2.  Navigate to the project directory:

    ```bash
    cd <https://github.com/davies18/Python_code-global_video_game_sales_2016/blob/main/Python_Code_Video_Game_Sales.html>
    ```

3.  Install the required Python libraries:

    ```bash
    pip install pandas numpy
    ```

4.  (Optional) to use Jupyter Notebook, make sure you have it installed. If not, install it via:

    ```bash
    pip install notebook
    ```

## Running the Code

1.  Ensure you have the `vgsales.csv` file (or a similar CSV file with video game sales data) in the same directory as the `video_game_sales_analysis.py` script.
2.  **Using Python script:**

    ```bash
    python video_game_sales_analysis.py
    ```

3.  **Using Jupyter Notebook (recommended):**

    -   Open Jupyter Notebook in your terminal: `jupyter notebook`
    -   Navigate to the project directory and open a new notebook or copy the python code into the notebook.
    -   Run the cells to execute the code.

4.  The script/notebook will output the average global sales before and after 2005.

## Breakdown of the Code

### Explanation of Python Code

The python script `video_game_sales_analysis.py` performs the following actions:

1.  **Data Loading:**
    -   Uses Pandas to read the video game sales data from a CSV file into a DataFrame.

    ```python
    df = pd.read_csv(filepath)
    ```

2.  **Missing Value Handling:**
    -   Calculated the modal year.
    -   We use the mode(2009) to fill the missing values because it preserves the dominant trend in the data, mean might.
    -   Reassigning the updated values back to the Year column

    ```python
    raw_df["Year"].value_counts()
    ```

3.  **Data Type Conversion:**
    -   Converts the 'Year' column to integer data type for accurate calculations.

    ```python
    df['Year'] = df['Year'].astype(int)
    ```

4.  **Creating the 'Period' Column:**
    -   Uses NumPy's `where` function to create a new 'Period' column.
    -   Records with 'Year' greater than or equal to 2005 are labeled 'post-2005', and those before are labeled 'pre-2005'.

    ```python
    df['Period'] = np.where(df['Year'] >= 2005, 'post-2005', 'pre-2005')
    ```

5.  **Calculating Average Global Sales:**
    -   Calculates the average global sales for each period ('pre-2005' and 'post-2005') using Pandas' `mean()` function.

    ```python
    avg_sales_pre_2005 = df[df['Period'] == 'pre-2005']['Global_Sales'].mean()
    avg_sales_post_2005 = df[df['Period'] == 'post-2005']['Global_Sales'].mean()
    ```

6.  **Output:**
    -   Prints the calculated average global sales for both periods.

    ```python
    print(f"Average Global Sales before 2005: {pre_2005_avg:.2f}")
    print(f"Average Global Sales after 2005: {post_2005_avg:.2f}")
    ```

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
-   Special thanks to Durham College, Canada, and the coordinators of the Data Analysis Tools Analytics module.
-   Project 1, Group 5 (2025) members:
    -   Author
    -   OKPALEFE OGHENETEJIRI
    -   KADIKU FARUQUAT
    -   OWUSU KEITH
    -   KARRA AKHIL
-   The team effort was crucial in overcoming challenges and completing the project.
