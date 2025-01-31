# R Subsetting Bug: Unexpected Behavior When Subsetting with Non-Existent Values

This repository demonstrates a subtle bug related to subsetting data frames in R when using character vectors that contain values not present in the column being subsetted.  The unexpected behavior is that the rows corresponding to the missing values are not simply omitted, but rather the entire subsetting operation may behave unpredictably or return unexpected results.  The solution showcases the proper way to handle such cases.

## Bug Description
The provided `bug.R` script attempts to subset a data frame (`df`) using `subset()`. The character vector used for subsetting (`c("A", "D", "E")`) includes elements ("D", "E") that do not exist in `df$col1`.  The unexpected behavior is that, instead of returning only rows where `col1` is "A", the entire subset operation produces incorrect or empty results depending on the R version and settings.

## Solution
The `bugSolution.R` script provides a solution that correctly handles non-existent values during subsetting.  It explicitly checks for the presence of values in the column before subsetting.

## How to reproduce
1. Clone this repository.
2. Navigate to the directory containing `bug.R`
3. Run the script in R: `source("bug.R")`
4. Compare the output with the expected output from `bugSolution.R` (which should only include rows where `col1` equals "A").