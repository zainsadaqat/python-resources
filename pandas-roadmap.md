# Pandas Roadmap

## Stage 1 Fundamentals of pandas
Learn the core pandas building blocks so you can load data and answer simple questions.

### Key concepts to cover

1. Series and DataFrame
2. Reading files with pd.read_csv and pd.read_excel
3. Inspecting data with .head .info .describe
4. Selecting rows and columns with .loc and .iloc
5. Boolean filtering and chaining simple conditions

### Mini exercises

1. Load a CSV and print first 10 rows
2. Show rows where Value > 20000
3. Select only Date and Car Model columns and show unique models

### Project worth doing: Sales explorer slice

1 Input: small sales CSV like Task4a_data.csv
2 Tasks
1 Build a script that prints total sales, top 3 models by sales, and rows for a chosen salesperson
2 Save a CSV with only rows where Value > X
3 Success criteria
1 Script runs without errors on the provided CSV
2 Outputs are human readable and correctly computed
3 Code is wrapped in functions not one long script

### Common mistakes and how to avoid them

1. Mistake: treating date column as string. Fix: convert with pd.to_datetime immediately.
2. Mistake: chained indexing leading to warnings. Fix: use .loc properly.

## Stage 2 Data cleaning and transformation

Make messy real world data reliable so analysis is trustworthy.

### Key concepts to cover

1. Handling missing values with .dropna .fillna
2. Changing types with .astype and safe conversions
3. Renaming columns and trimming whitespace
4. Removing duplicates and standardizing categorical values
5. Simple text cleaning with .str methods

### Mini exercises

1 Replace empty salesperson with "Unknown"
2 Convert Value to numeric and drop rows that cannot convert
3 Standardize "New/Used" values to Title case

### Project worth doing: Clean and normalize pipeline

1 Input: one messy CSV with inconsistent columns and missing values
2 Tasks
1 Write a clean_data(df) function that returns a cleaned DataFrame
2 Write unit checks inside the function that assert expected dtypes and no nulls in key columns
3 Output a cleaned CSV and a short summary report
3 Success criteria
1 clean_data runs on the raw CSV and passes assertions
2 Report contains counts of rows cleaned and summary stats

Assumptions and skeptic check
1 Assumption: data issues are fixable programmatically. Skeptic: some problems need human judgement. Add logging so you can review ambiguous rows.

## Stage 3 Aggregation and groupby

Master aggregation patterns needed for real summaries and business questions.

### Key concepts to cover

1. groupby basics, multi column groupby
2. aggregation with .agg and named aggregations
3. pivot_table and unstack for reshaping
4. value_counts and crosstab for quick counts

### Mini exercises

1. Group by Car Model and compute total Value and count of sales
2. Use pivot_table to get totals per Model per Salesperson

### Project worth doing: Sales summary report

1 Input: cleaned sales dataset
2 Tasks
1 Produce a summary table: for each model and month, show total value, average value, and number of sales
2 Save the table to Excel with each model on a sheet or one sheet with clear columns
3 Success criteria
1 Monthly model summary is correct for sample checks
2 Excel file opens and is easy to read

Logic test
1 Groupby can return confusing index shapes. Always reset_index if you need flat tables.

## Stage 4 Time series and trends

Be able to analyze trends over days, weeks, and months and build time based summaries.

Key concepts to cover
1 pd.to_datetime and setting a DatetimeIndex
2 resample for period aggregation like daily weekly monthly
3 rolling windows and moving averages
4 shift and pct_change for growth rates

Mini exercises
1 Convert Date to datetime and set it as index
2 Resample to monthly totals: df.resample('M')["Value"].sum()
3 Compute a 7 day rolling average of daily sales

Project worth doing: New vs Used trend dashboard script
1 Input: cleaned sales dataset with Date and New/Used
2 Tasks
1 Create a script that outputs a CSV with monthly totals for New and Used
2 Produce a PNG line chart showing monthly New and Used totals
3 Add a small textual summary: months with highest growth or decline
3 Success criteria
1 Chart shows two clear lines and matches CSV numbers
2 Summary text lists top 2 months for growth and bottom 2 for decline, computed correctly

Common pitfalls
1 Plotting raw dates without conversion leads to incorrect ordering. Always convert.
2 Sparse daily data can make day level noise. Aggregate to weeks or months before concluding trends.

Stage 5 Visualization and storytelling

Goal
1 Use visualizations to communicate insights. Not for decoration but for decisions.

Key concepts to cover
1 Built in df.plot and matplotlib basics
2 Seaborn for cleaner categorical plots
3 Annotating charts and saving high quality images
4 Combining text summaries with charts to tell a story

Mini exercises
1 Make a bar plot for top 5 salespeople by revenue
2 Make stacked area chart for model mix over months

Project worth doing: One page data story
1 Input: sales dataset
2 Tasks
1 Produce a single PNG that contains 3 charts: monthly revenue trend, model mix stacked area, top 5 salespeople bar chart
2 Produce a short text summary of 3 key findings in the PNG footer or as a separate TXT
3 Success criteria
1 PNG is publication ready with labels and title
2 Numbers in charts are traceable back to computed tables

Teaching tip
1 Teach chart interpretation not just chart creation. Ask students what decision each visualization supports.

Stage 6 Performance and scaling

Goal
1 Process larger datasets and write efficient pandas code.

Key concepts to cover
1 Understanding memory usage and dtypes
2 Use of categorical dtype for repeated strings
3 Processing by chunks with pd.read_csv(..., chunksize=)
4 Avoiding slow .apply where vectorized ops are available

Mini exercises
1 Load a big CSV in chunks and compute total revenue per model across chunks
2 Convert suitable columns to category and show memory improvement

Project worth doing: Efficient monthly aggregator
1 Input: a big simulated sales CSV with 1 million rows
2 Tasks
1 Build a chunked aggregator that computes monthly totals without loading entire file
2 Benchmark memory usage and time before and after dtype optimization
3 Success criteria
1 Aggregator completes on a machine with limited memory
2 Documented improvement in memory/time

Common mistakes
1 Premature optimization. First make it correct then optimize hotspots with a profiler.

Stage 7 Advanced pipelines and production readiness

Goal
1 Turn pandas work into reusable pipelines and shareable artifacts.

### Key concepts to cover

1. Modular code structure: functions, small scripts, notebooks for exploration
2. Automated checks and assertions inside pipeline
3. Exporting results: Excel, CSV, JSON, PNG
4. Basic version control and reproducibility tips
5. Optionally introduce Dask or SQL for very large data needs

Capstone project worth doing: Versere Cars analytics service
1 Input: full sales dataset
2 Tasks
1 Build a single repository with:
1 data cleaning module
2 aggregation module
3 plotting module
4 a CLI script that runs the analyses and saves reports
2 Include tests or assertions that validate key outputs
3 Produce a README that explains how to run and interpret results
3 Success criteria
1 Running the CLI produces the expected CSVs and PNGs
2 Code is modular, commented and has a README

Alternatives and skeptic view
1 Alternative: Learn pandas inside Jupyter notebooks for exploration then refactor to scripts for production
2 Skeptic: mastering pandas alone is not enough. Complement with SQL and basic statistics. Consider adding those later.

Final checklist to know you mastered pandas
1 You can clean and validate messy data reliably
2 You can aggregate and answer business questions with groupby and resample
3 You can produce publication ready visuals and export them
4 You can handle moderate sized datasets and optimize when needed
5 You can wrap analysis into reusable scripts or simple command line tools

If you want, I can do one of two concrete next actions right now
1 Produce a week by week curriculum with exact lessons and exercises for each stage, or
2 Create the Versere Cars Capstone repository scaffold with code stubs for each module so your student can fill them in
