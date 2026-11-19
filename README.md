# Experiment 3 : Retail Sales and Profit Analysis Using Pandas

## Aim
To create a sample retail dataset, identify and handle missing values (`NaN`/`None`) and duplicate records, and compute summary statistics using Pandas in Python.

## Algorithm

1. **Start** the program.
2. **Import Library**: Import the `pandas` library as `pd` for tabular data cleaning and analysis.
3. **Initialize Raw Retail Dataset**: Create a Python dictionary `data` containing retail records (`Order_ID`, `Product`, `Region`, `Sales`, `Discount`, `Profit`) with deliberate missing (`None`) entries and duplicate rows.
4. **Construct DataFrame & Inspect**:
   * Convert `data` into a Pandas DataFrame `df` using `pd.DataFrame(data)`.
   * Print the original dataset and its initial dimensions (`df.shape`).
5. **Detect Missing Values**:
   * Count missing entries per column using `df.isnull().sum()`.
6. **Impute Missing Values**:
   * Replace missing numerical values in `Sales`, `Discount`, and `Profit` with their respective column means using `.fillna(df[col].mean())`.
   * Replace missing categorical values in `Region` with the column mode (most frequent category) using `.fillna(df["Region"].mode()[0])`.
7. **Remove Duplicate Records**:
   * Drop exact duplicate rows from `df` using `df.drop_duplicates()`.
8. **Display Cleaned Dataset & Summary Statistics**:
   * Print the cleaned DataFrame, updated dimensions (`df.shape`), and descriptive statistical metrics (`df.describe()`).
9. **Stop** the program.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Creation & Inspection** | `pd.DataFrame()` | Converts a Python dictionary into a labeled 2D tabular DataFrame |
| | `df.shape` | Returns the `(rows, columns)` dimensions before and after cleaning |
| | `df.isnull().sum()` | Counts the number of missing (`NaN`/`None`) values in each column |
| **Missing Value Imputation** | `df[col].fillna()` | Replaces missing values with a specified replacement value |
| | `df[col].mean()` | Calculates the arithmetic mean for numerical column imputation |
| | `df[col].mode()[0]` | Retrieves the most frequent category for categorical column imputation |
| **Deduplication & Summary** | `df.drop_duplicates()` | Identifies and removes duplicate rows from the DataFrame |
| | `df.describe()` | Generates count, mean, standard deviation, min, quartiles, and max for numerical features |

## Program

#Cleaning and Preparing Retail Data using Pandas

#Step 1: Create a sample retail dataset

#Step 2: Check for missing values

#Step 3: Fill missing numeric values with column mean

#Step 4: Fill missing Region with mode (most frequent value)

#Step 5: Remove duplicate records

#Step 6: Display summary statistics



## Output
import json
import io
import contextlib
import warnings

warnings.filterwarnings("ignore")

def make_md_cell(text):
    lines = [line + "\n" for line in text.split("\n")]
    if lines:
        lines[-1] = lines[-1].rstrip("\n")
    return {
        "cell_type": "markdown",
        "metadata": {},
        "source": lines
    }

def make_code_cell(code, exec_count, ns):
    lines = [line + "\n" for line in code.split("\n")]
    if lines:
        lines[-1] = lines[-1].rstrip("\n")
    
    buf = io.StringIO()
    with contextlib.redirect_stdout(buf):
        exec(code, ns)
    out_text = buf.getvalue()
    
    outputs = []
    if out_text:
        out_lines = [line + "\n" for line in out_text.split("\n")]
        if out_lines and out_lines[-1] == "\n":
            out_lines.pop()
        outputs.append({
            "name": "stdout",
            "output_type": "stream",
            "text": out_lines
        })
        
    return {
        "cell_type": "code",
        "execution_count": exec_count,
        "metadata": {},
        "outputs": outputs,
        "source": lines
    }

ns = {}

md1 = """# Retail Sales and Profit Analysis Using Pandas

## Aim
To create a sample retail dataset, identify and handle missing values and duplicates using Pandas.  

## Algorithm  
1. Import the Pandas library.  
2. Create a DataFrame with columns - `Order_ID`, `Product`, `Region`, `Sales`, `Discount`, and `Profit`.  
3. Introduce some missing and duplicate rows manually.  
4. Use `isnull()` and `sum()` to check missing values.  
5. Replace missing values using `fillna()` and `mean()` (and `mode()` for categorical columns).  
6. Remove duplicates using `drop_duplicates()`.  
7. Display the cleaned dataset with its shape."""  

code1 = """# Cleaning and Preparing Retail Data using default values    
import pandas as pd    

# Step 1: Create a sample retail dataset  
data = {  
    "Order_ID": [101, 102, 103, 104, 105, 105, 106, 107],  
    "Product": ["Laptop", "Tablet", "Phone", "Printer", "Monitor", "Monitor", "Tablet", "Laptop"],  
    "Region": ["East", "West", "North", "South", "East", "East", "West", None],  
    "Sales": [55000, 32000, None, 18000, 24000, 24000, 32000, 55000],  
    "Discount": [5, None, 10, 8, 5, 5, None, 8],  
    "Profit": [8000, 5000, 4000, None, 3000, 3000, 5000, 8000]  
}

df = pd.DataFrame(data)  
print("---- Original Retail Dataset ----")  
print(df)
print("\\nDataset Shape:", df.shape)"""  

code2 = """# Step 2: Check for missing values  
print("Missing Values per Column:\\n", df.isnull().sum())"""  

code3 = """# Step 3: Fill missing numeric values with column mean  
df["Sales"] = df["Sales"].fillna(df["Sales"].mean())  
df["Discount"] = df["Discount"].fillna(df["Discount"].mean())  
df["Profit"] = df["Profit"].fillna(df["Profit"].mean())  

# Step 4: Fill missing Region with mode (most frequent value)  
df["Region"] = df["Region"].fillna(df["Region"].mode()[0])  

print("Missing values handled successfully.")"""  

code4 = """# Step 5: Remove duplicate records  
df.drop_duplicates(inplace=True)   

print("---- Cleaned Retail Dataset ----")  
print(df)  
print("\\nDataset Shape after Cleaning:", df.shape)"""  

code5 = """# Step 6: Display summary statistics  
print("Summary Statistics:\\n", df.describe())"""  

md2 = """## Result  
The program successfully created a retail dataset, identified and handled missing values, and removed duplicates using Pandas."""  

cells = [
    make_md_cell(md1),
    make_code_cell(code1, 1, ns),  
    make_code_cell(code2, 2, ns),  
    make_code_cell(code3, 3, ns),  
    make_code_cell(code4, 4, ns),  
    make_code_cell(code5, 5, ns),  
    make_md_cell(md2)  
]  

notebook = {  
    "cells": cells,  
    "metadata": {  
        "kernelspec": {  
            "display_name": "Python 3",  
            "language": "python",  
            "name": "python3"  
        },
        "language_info": {  
            "name": "python",  
            "version": "3.10.0"  
        }  
    },
    "nbformat": 4,  
    "nbformat_minor": 4  
}

filename = "retail_sales_profit_analysis_pandas.ipynb"  
with open(filename, "w", encoding="utf-8") as f:  
    json.dump(notebook, f, indent=2)   

print("Generated:", filename)  

## Result
The program successfully creates a retail dataset, identifies missing entries and duplicate rows, imputes missing values using mean and mode strategies, removes duplicates, and outputs a clean dataset ready for downstream analysis.

