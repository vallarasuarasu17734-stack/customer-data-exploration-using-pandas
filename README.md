# Experiment 2 : Customer Data Exploration Using Pandas

## Aim
To create a sample customer dataset and perform data exploration, filtering, sorting, grouping, and basic statistical analytics using Pandas functions in Python.

## Algorithm

1. **Start** the program.
2. **Import Library**: Import the `pandas` library as `pd` for tabular data manipulation and analysis.
3. **Initialize Dataset**: Create a Python dictionary `data` containing customer attributes (`Customer_ID`, `Customer_Name`, `Region`, `Age`, `Annual_Income`, `Spending_Score`, `Loyalty_Years`).
4. **Construct DataFrame**: Convert the dictionary into a structured Pandas DataFrame `df` using `pd.DataFrame(data)` and print the dataset.
5. **Inspect Structure & Summary**:
   * Display dataset dimensions (`df.shape`), column names (`df.columns`), data types and null counts (`df.info()`), and descriptive statistics (`df.describe()`).
   * Display the first 3 records (`df.head(3)`) and last 3 records (`df.tail(3)`).
6. **Sort & Filter Records**:
   * Sort customers in descending order of `Annual_Income` using `df.sort_values()`.
   * Filter high-income customers where `Annual_Income > 70000`.
7. **Perform Group-Wise & Frequency Analysis**:
   * Group customers by `Region` and calculate regional averages for `Annual_Income` and `Spending_Score` using `df.groupby().mean()`.
   * Count customer distribution across each region using `df["Region"].value_counts()`.
8. **Compute Overall Metrics & Top Performer**:
   * Identify the customer record with the highest `Spending_Score` using `df["Spending_Score"].idxmax()` and `df.loc[]`.
   * Calculate overall mean `Annual_Income` and mean `Spending_Score`.
9. **Stop** the program.

## Functions and Methods Used

| Category | Function / Method | Purpose / Description |
| :--- | :--- | :--- |
| **Data Creation** | `pd.DataFrame()` | Converts a Python dictionary into a 2D labeled tabular DataFrame |
| **Structural Inspection** | `df.shape`, `df.columns` | Retrieves dimensions `(rows, columns)` and column labels |
| | `df.info()`, `df.describe()` | Summarizes column data types, memory usage, and descriptive statistics |
| | `df.head(n)`, `df.tail(n)` | Views the first `n` and last `n` rows of the dataset |
| **Sorting & Filtering** | `df.sort_values()` | Orders records by `Annual_Income` in descending order |
| | Boolean Indexing (`df[...]`) | Filters customers with `Annual_Income > 70000` |
| **Grouping & Aggregation** | `df.groupby().mean()` | Aggregates mean income and spending score per `Region` |
| | `df["Region"].value_counts()` | Counts occurrences of customers in each region |
| | `idxmax()`, `df.loc[]`, `.mean()` | Locates the top spender row and computes dataset-wide averages |

## Program
  #Customer Data Exploration using Pandas
    
    #Step 1: Create a sample customer dataset
    data = {
        "Customer_ID": [101, 102, 103, 104, 105, 106, 107, 108],
        "Customer_Name": ["Anita", "Rajesh", "Priya", "Vikram", "Divya", "Manoj", "Sita", "Amit"],
        "Region": ["North", "South", "East", "West", "North", "South", "East", "West"],
        "Age": [25, 32, 41, 29, 35, 45, 28, 40],
        "Annual_Income": [55000, 72000, 61000, 48000, 85000, 90000, 64000, 58000],
        "Spending_Score": [78, 62, 45, 88, 92, 55, 70, 60],
        "Loyalty_Years": [2, 5, 4, 3, 6, 7, 3, 4]
    }
    
    #Step 2: Convert to a Pandas DataFrame
    df = pd.DataFrame(data) 
    print("---- CUSTOMER DATASET ----")
    print(df)
    
    #Step 3: Basic exploration
    print("\nShape of Dataset:", df.shape)
    print("Columns:", df.columns.tolist())
    print("\n--- Dataset Info ---")
    print(df.info())
    print("\n--- Summary Statistics ---")
    print(df.describe())
     
    
    #Step 4: Display first and last few records
    print("\nFirst 3 Records:\n", df.head(3))
    print("\nLast 3 Records:\n", df.tail(3))
    
    #Step 5: Sort customers by Annual Income (descending)
    print("\nCustomers Sorted by Annual Income:\n",
          df.sort_values(by="Annual_Income", ascending=False))
    
    #Step 6: Filter high-income customers (Income > 70000)
    print("\nHigh Income Customers (Income > 70000):\n",
          df[df["Annual_Income"] > 70000][["Customer_Name", "Annual_Income"]])
          
    #Step 7: Group customers by Region and find average Income and Spending Score
    print("\nRegion-wise Average Income and Spending Score:")    
    print(df.groupby("Region")[["Annual_Income", "Spending_Score"]].mean())

    #Step 8: Count number of customers in each Region
    print("\nCustomer Count per Region:")
    print(df["Region"].value_counts())
     
    # Step 9: Identify customer with maximum Spending Score
    max_spender = df.loc[df["Spending_Score"].idxmax()]
    print("\nTop Spender Details:\n", max_spender)
     
    # Step 10: Compute overall averages
    print("\nAverage Annual Income:", df["Annual_Income"].mean()) 
    print("Average Spending Score:", df["Spending_Score"].mean())



## Output


    ---- CUSTOMER DATASET ----
    
        Customer_ID Customer_Name Region  Age  Annual_Income  Spending_Score  Loyalty_Years
    
        0          101         Anita  North   25          55000              78              2
        1          102        Rajesh  South   32          72000              62              5
        2          103         Priya   East   41          61000              45              4
        3          104        Vikram   West   29          48000              88              3
        4          105         Divya  North   35          85000              92              6
        5          106         Manoj  South   45          90000              55              7
        6          107          Sita   East   28          64000              70              3
        7          108          Amit   West   40          58000              60              4
     
    Shape of Dataset: (8, 7)
    
    Columns: ['Customer_ID', 'Customer_Name', 'Region', 'Age', 'Annual_Income', 'Spending_Score', 'Loyalty_Years']
     
    --- Dataset Info ---
    
    8 entries, 0 to 7; 7 columns; all columns have 8 non-null values.
    
    Dtypes: int64(5), object(2)
     
    --- Summary Statistics ---
    
           Customer_ID        Age  Annual_Income  Spending_Score  Loyalty_Years
    
        count       8.000000   8.000000       8.000000        8.000000       8.000000
        mean      104.500000  34.375000   66625.000000       68.750000       4.250000
        std         2.449490   7.089935   14676.876857       16.359794       1.669046
        min       101.000000  25.000000   48000.000000       45.000000       2.000000
        25%       102.750000  28.750000   57250.000000       58.750000       3.000000
        50%       104.500000  33.500000   62500.000000       66.000000       4.000000
        75%       106.250000  40.250000   75250.000000       80.500000       5.250000
        max       108.000000  45.000000   90000.000000       92.000000       7.000000
     
    First 3 Records: rows 0–2 (Anita, Rajesh, Priya).
    
    Last 3 Records: rows 5–7 (Manoj, Sita, Amit).
     
    
    Customers Sorted by Annual Income (descending):
    
    Manoj 90000; Divya 85000; Rajesh 72000; Sita 64000;
    
    Priya 61000; Amit 58000; Anita 55000; Vikram 48000.
     
    High Income Customers (Income > 70000):
    
    Rajesh 72000; Divya 85000; Manoj 90000.
     
    
    Region-wise Average Income and Spending Score:
    
    East 62500.0, 57.5
    
    North 70000.0, 85.0
    
    South 81000.0, 58.5
    
    West 53000.0, 74.0
     
    Customer Count per Region:
    
    North 2; South 2; East 2; West 2.
     
    Top Spender Details:
    
    Customer_ID 105; Customer_Name Divya; Region North; Age 35;
    
    Annual_Income 85000; Spending_Score 92; Loyalty_Years 6.
     
    Average Annual Income: 66625.0
    
    Average Spending Score: 68.75
 
## Result  
The program successfully creates a customer dataset using Pandas and performs exploratory analysis, sorting, filtering, regional grouping, and summary statistics.
