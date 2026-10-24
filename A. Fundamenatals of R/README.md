# R Programming Fundamentals: Installation, Setup, and Core Concepts

## 1. R Installation and Setup

R is the programming language and computing environment. RStudio Desktop is an integrated development environment (IDE) for writing, running, and managing R code. Rtools is used on Windows when certain packages need to be compiled from source.

### 1.1. Windows Setup

#### Install R

1. Visit the official [CRAN website](https://cran.r-project.org/).
2. Select [Download R for Windows](https://cran.r-project.org/bin/windows/).
3. Open [base](https://cran.r-project.org/bin/windows/base/) and download the latest R installer.
4. Run the downloaded `.exe` file and follow the installation instructions.

#### Install Rtools

1. Visit the [CRAN Rtools page](https://cran.r-project.org/bin/windows/Rtools/).
2. Select the version compatible with your installed version of R.
3. Download and run the installer using the default settings.

Rtools is needed when compiling certain packages from source; it is not required for every package installation.

#### Install RStudio Desktop

1. Visit the official [Posit Downloads page](https://posit.co/downloads/).
2. Download RStudio Desktop for Windows.
3. Run the `.exe` installer and follow the installation instructions.

### 1.2. Linux Setup

The following commands apply to Ubuntu, Debian, and Linux Mint.

#### Install R and Development Tools

Open the terminal (`Ctrl + Alt + T`) and run:

```bash
sudo apt update
sudo apt install r-base r-base-dev build-essential -y
```

- `r-base`: Installs R.
- `r-base-dev`: Provides development files for building R packages.
- `build-essential`: Installs standard compilation tools, including GCC and Make.

Linux uses its native development toolchain rather than Windows Rtools.

Verify the installation:

```bash
R --version
```

#### Install RStudio Desktop

1. Visit the official [Posit Downloads page](https://posit.co/downloads/).
2. Download the Linux `.deb` installer for your distribution.
3. Open a terminal and navigate to the Downloads folder:

```bash
cd ~/Downloads
```

4. Install RStudio Desktop. If only the intended installer matches the pattern, run:

```bash
sudo apt install ./rstudio-*.deb
```

Launch RStudio from the applications menu or run:

```bash
rstudio
```

### 1.4. Run an R Script

Run it from the terminal:

```bash
Rscript script.R
```

### 1.5. Working Directory

```r
# View the current working directory
getwd()

# Change the working directory
setwd("/path/to/project")

# Check the working directory again
getwd()
```

Prefer project-based relative paths where practical instead of repeatedly hard-coding absolute paths.

### 1.6. Install and Load R Packages

Install a package:

```r
install.packages("dplyr")
```

Load an installed package:

```r
library(dplyr)
```

Check installed packages:

```r
installed.packages()

"ggplot2" %in% rownames(installed.packages())
```

## 2. Variables and Data Types

Variables are names used to store values in a program. Data types describe what kind of value is stored, such as a number, text, logical value, or collection of values. Understanding variables and data types is fundamental because almost every programming operation works with stored values.

### 2.1. Creating Variables

### R code:

```r
#| eval: false

name <- "Sajjad"

age <- 30

position <- 6219

is_high <- TRUE
```

R commonly uses `<-` for assignment, although `=` can also be used.

### 2.2. Naming Variables

Variable names should be descriptive and consistent.

### R code:

```r
#| eval: false

sample_name <- "Sample_01"

variant_position <- 6219

is_high_impact <- TRUE
```

### 2.3. Numeric Data

Numeric values are used for quantities such as positions, counts, lengths, and measurements.

### R code:

```r
#| eval: false

position <- 6219

frequency <- 0.25

count <- 100

position
frequency
count
```

### 2.4. Integer and Floating-Point Values

Integers are whole numbers, while floating-point values contain decimal values.

### R code:

```r
#| eval: false

integer_value <- 100L

decimal_value <- 100.5

class(integer_value)

class(decimal_value)
```

### 2.5. Character and String Data

Character or string values contain text.

### R code:

```r
#| eval: false

gene <- "BRCA1"

effect <- "Frameshift_variant"

ref <- "A"

alt <- "T"
```

### 2.6. Logical and Boolean Values

Logical values represent two states: true or false.

### R code:

```r
#| eval: false

is_high <- TRUE

is_coding <- FALSE

is_high

is_coding
```

### 2.7. Checking Data Types

### R code:

```r
#| eval: false

x <- 6219

class(x)

typeof(x)

is.numeric(x)

is.character(x)

is.logical(x)
```

### 2.8. Special Missing Values

Different languages represent missing or absent values differently.

### R code:

```r
#| eval: false

x <- NA

is.na(x)

y <- NULL

is.null(y)
```


### 2.9. Type Conversion

Values sometimes need to be converted from one data type to another.

### R code:

```r
#| eval: false

x <- "6219"

as.numeric(x)

as.integer(x)

as.character(6219)

as.logical(1)
```

### 2.10. Multiple Variables

### R code:

```r
#| eval: false

filename <- "sample_01"

position <- 6219

ref <- "A"

alt <- "T"

effect <- "Frameshift_variant"
```

### 2.11. Using Variables in Expressions

Variables can be used to perform calculations or construct new values.

### R code:

```r
#| eval: false

position <- 6219

position_end <- position + 100

position_end
```

### 2.12. Combining Text and Variables

### R code:

```r
#| eval: false

ref <- "A"

alt <- "T"

variant <- paste0(ref, ">", alt)

variant

df$variant <- paste0(df$ref, ">", df$alt)
```

### 2.13. Common Data Types

The basic types encountered frequently in data analysis include:

## 3. Operators

Operators are symbols or keywords used to perform calculations, comparisons, assignments, and logical operations. They are fundamental for writing expressions and controlling program behavior.

### 3.1. Arithmetic Operators

Arithmetic operators perform mathematical calculations.

### R code:

```r
#| eval: false

a <- 10
b <- 3

a + b
a - b
a * b
a / b
a ^ b
a %% b
a %/% b
```

### 3.2. Assignment Operators

Assignment operators store values in variables.

### R code:

```r
#| eval: false

x <- 10

y = 20

x
y
```

### 3.4. Logical Operators

Logical operators combine multiple conditions.

### R code:

```r
#| eval: false

x <- 10
y <- 20

x > 5 & y > 15

x > 15 | y > 15

!(x > 15)
```


- `&` for AND
- `|` for OR
- `!` for NOT

### 3.6. String Concatenation

String concatenation combines two or more strings.

### R code:

```r
#| eval: false

ref <- "A"
alt <- "T"

paste0(ref, ">", alt)
```

### 3.7. Membership Operators

Membership operators check whether a value belongs to a collection.

### R code:

```r
#| eval: false

impact <- "High"

impact %in% c(
    "High",
    "Moderate"
)
```

### 3.8. Operator Precedence

When an expression contains multiple operators, some operations are evaluated before others. Parentheses can be used to make the intended order explicit.

### R code:

```r
#| eval: false

result <- 10 + 5 * 2

result

result <- (10 + 5) * 2

result
```

### 3.9. Combining Operators

Multiple operators can be used together to create more useful expressions.

### R code:

```r
#| eval: false

position <- 6219
impact <- "High"

position > 5000 & impact == "High"
```

### 3.10. Increment and Decrement


### R code:

```r
#| eval: false

x <- 10

x <- x + 1

x

x <- x - 1

x
```

### 3.11. Pipe Operator |>

The pipe operator |> passes the result of one expression to the next function. It makes multi-step R code easier to read from left to right.

### R code:

```r
#| eval: false

x <- c(10, 20, 30, 40, 50)

x |> mean()

```

This is equivalent to:

```r
#| eval: false

mean(x)
```

The pipe can also be used for multiple steps:

```r

#| eval: false

x <- c(10, 20, 30, 40, 50)

x |>
    mean() |>
    round()
```

Read this as:

> Start with `x` → calculate the mean → round the result.

#### Pipe with dplyr:

The pipe is especially useful when working with data frames.

```r
#| eval: false

library(dplyr)

data |>
    filter(score > 80) |>
    select(name, score)
```

This can be read as:

> Start with `data` → keep rows where `score > 80` → select `name` and `score`.

Another example:

```r
#| eval: false

data |>
    filter(score > 80) |>
    arrange(score) |>
    select(name, score)
```

The steps happen from **top to bottom**:

1. Start with `data`
2. Filter scores greater than `80`
3. Sort by `score`
4. Select `name` and `score`

#### Pipe vs. Nested Functions:

##### Without a pipe:

```r
#| eval: false

select(
    arrange(
        filter(data, score > 80),
        score
    ),
    name,
    score
)
```

##### With a pipe:

```r
#| eval: false

data |>
    filter(score > 80) |>
    arrange(score) |>
    select(name, score)
```

The pipe version is often easier to read because the operations follow the same order as the analysis.

## 4. Input and Output:

Input and output are used to communicate with a program. **Input** provides information to a program, while **output** displays or returns information from a program.

### 4.1. Basic Output

### R code:

```r
#| eval: false

print("Hello from R")

cat("Hello from R\n")

x <- 100

print(x)

cat("Value:", x, "\n")
```

### 4.2. Printing Multiple Values

### R code:

```r
#| eval: false

name <- "Sample_01"
position <- 6219

print(name)
print(position)

cat(
    "Sample:",
    name,
    "Position:",
    position,
    "\n"
)
```

### 4.3. User Input

User input allows a program to receive information interactively.

### R code:

```r
#| eval: false

name <- readline(
    prompt = "Enter your name: "
)

cat(
    "Hello,",
    name,
    "\n"
)
```

### 4.4. Numeric Input

Input received from a user is often text and may need to be converted to a numeric value.

### R code:

```r
#| eval: false

position <- as.numeric(
    readline(
        prompt = "Enter position: "
    )
)

cat(
    "Position:",
    position,
    "\n"
)
```

### 4.5. Formatted Output

Formatted output makes program results easier to read.

### R code:

```r
#| eval: false

name <- "Sample_01"
position <- 6219

sprintf(
    "Sample: %s | Position: %d",
    name,
    position
)
```

### 4.6. Reading Command-Line Arguments

Command-line arguments allow values to be supplied when a script is started.

### R code:

```r
#| eval: false

args <- commandArgs(
    trailingOnly = TRUE
)

print(args)
```

Run the R script:


### 4.7. Input from a File

Programs can also receive input from files rather than directly from a user.

### R code:

```r
#| eval: false

data <- readLines(
    "data.txt"
)

print(data)
```

### 4.8. Output to a File

Output can be redirected or written to a file.

### R code:

```r
#| eval: false

writeLines(
    c(
        "Sample_01",
        "Sample_02",
        "Sample_03"
    ),
    "output.txt"
)
```

### 4.10. Pipes

A pipe `|` sends the output of one command as input to another command.

### 4.11. Checking Input Before Using It

Input can be checked before being processed.

### R code:

```r
#| eval: false

name <- readline(
    prompt = "Enter your name: "
)

if (name == "") {
    cat("No name was entered.\n")
} else {
    cat(
        "Hello,",
        name,
        "\n"
    )
}
```

## 5. Conditions

Conditions allow a program to make decisions based on whether an expression is `TRUE` or `FALSE`. They are fundamental for controlling which code is executed.

### 5.1. Basic `if` Condition

### R code:

```r
#| eval: false

x <- 10

if (x > 5) {
    print("x is greater than 5")
}
```

### 5.2. `if` and `else`

Use `else` when there are two possible outcomes.

### R code:

```r
#| eval: false

x <- 10

if (x > 5) {
    print("Greater than 5")
} else {
    print("5 or less")
}
```

### 5.3. Multiple Conditions

Multiple conditions can be checked using `else if` or `elif`.

### R code:

```r
#| eval: false

position <- 6219

if (position < 1000) {
    print("Low position")
} else if (position < 5000) {
    print("Medium position")
} else {
    print("High position")
}
```

### 5.4. Comparing Text Values

Conditions can compare character or string values.

### R code:

```r
#| eval: false

impact <- "High"

if (impact == "High") {
    print("High impact")
}
```

### 5.5. Using Multiple Conditions

Logical operators allow several conditions to be combined.

### R code:

```r
#| eval: false

position <- 6219
impact <- "High"

if (
    position > 5000 &
    impact == "High"
) {
    print("High-impact variant")
}
```

### 5.6. OR Conditions

An OR condition is true when at least one condition is true.

### R code:

```r
#| eval: false

impact <- "High"

if (
    impact == "High" |
    impact == "Moderate"
) {
    print("Important impact")
}
```

### 5.7. NOT Conditions

NOT reverses a logical condition.

### R code:

```r
#| eval: false

is_high <- TRUE

if (!is_high) {
    print("Not high impact")
}
```

### 5.8. Nested Conditions

A condition can contain another condition.

### R code:

```r
#| eval: false

position <- 6219
impact <- "High"

if (position > 5000) {

    if (impact == "High") {
        print("High-impact variant at a high position")
    }
}
```

### 5.9. Checking Membership

Membership conditions check whether a value belongs to a predefined set.

### R code:

```r
#| eval: false

impact <- "High"

if (impact %in% c(
    "High",
    "Moderate"
)) {
    print("Selected impact")
}
```

### 5.10. Conditional Expressions

Simple conditions can sometimes be written as a single expression.

### R code:

```r
#| eval: false

x <- 10

result <- ifelse(
    x > 5,
    "High",
    "Low"
)

result
```

### 5.11. Checking Missing Values

Missing values need special handling in conditions.

### R code:

```r
#| eval: false

x <- NA

if (is.na(x)) {
    print("Value is missing")
}
```

### 5.12. Practical Example

A condition can combine several basic concepts.

### R code:

```r
#| eval: false

position <- 6219
impact <- "High"

if (
    position >= 5000 &
    impact %in% c(
        "High",
        "Moderate"
    )
) {
    print("Variant meets the criteria")
} else {
    print("Variant does not meet the criteria")
}
```

## 6. Loops

Loops allow a program to repeatedly execute a block of code. They are useful when the same operation needs to be performed on multiple values, rows, files, or other objects.

### 6.1. `for` Loop

A `for` loop iterates over a sequence of values.

### R code:

```r
#| eval: false

for (i in 1:5) {
    print(i)
}
```

### 6.2. Loop Through a Vector or List

### R code:

```r
#| eval: false

samples <- c(
    "Sample_01",
    "Sample_02",
    "Sample_03"
)

for (sample in samples) {
    print(sample)
}
```

### 6.3. Loop With a Condition

A loop can perform different operations depending on a condition.

### R code:

```r
#| eval: false

for (i in 1:5) {

    if (i > 3) {
        print("Greater than 3")
    } else {
        print(i)
    }

}
```

### 6.4. `while` Loop

A `while` loop continues as long as a condition is true.

### R code:

```r
#| eval: false

i <- 1

while (i <= 5) {

    print(i)

    i <- i + 1
}
```

### 6.5. `repeat` Loop in R

R provides a `repeat` loop that continues indefinitely until `break` is used.

### R code:

```r
#| eval: false

i <- 1

repeat {

    print(i)

    i <- i + 1

    if (i > 5) {
        break
    }
}
```


### 6.6. `break`

`break` immediately stops a loop.

### R code:

```r
#| eval: false

for (i in 1:10) {

    if (i == 6) {
        break
    }

    print(i)
}
```

### 6.7. `next` / `continue`

These statements skip the current iteration and continue with the next one.

### R code:

```r
#| eval: false

for (i in 1:5) {

    if (i == 3) {
        next
    }

    print(i)
}
```

### 6.8. Nested Loops

A nested loop is a loop inside another loop.

### R code:

```r
#| eval: false

for (i in 1:3) {

    for (j in 1:3) {

        print(
            paste(i, j)
        )

    }
}
```

### 6.9. Loop Through Files


### R code:

```r
#| eval: false

files <- list.files(
    pattern = "\\.tsv$"
)

for (file in files) {

    print(
        paste(
            "Processing:",
            file
        )
    )
}
```

### 6.10. Loop Through File Contents

### R code:

```r
#| eval: false

lines <- readLines(
    "data.txt"
)

for (line in lines) {

    print(line)
}
```

### 6.11. Loop Through Columns

### R code:

```r
#| eval: false

for (column in names(df)) {

    print(column)
}
```

### 6.12. Loop Through Rows

Row-by-row processing is possible, although vectorized operations are generally preferred for large datasets.

### R code:

```r
#| eval: false

for (i in seq_len(nrow(df))) {

    print(
        df$Position[i]
    )
}
```

### 6.13. Practical Example

Process several positions and classify them.

### R code:

```r
#| eval: false

positions <- c(
    100,
    2500,
    6219,
    9000
)

for (position in positions) {

    if (position < 5000) {

        print(
            paste(
                position,
                "Low"
            )
        )

    } else {

        print(
            paste(
                position,
                "High"
            )
        )
    }
}
```

## 7. Functions

Functions are reusable blocks of code designed to perform a specific task. They help avoid repeating the same code and make programs easier to organize, test, and maintain.

A function generally has:

- A name
- Input arguments or parameters
- A block of code
- A return value or output

### 7.1. Creating a Basic Function

### R code:

```r
#| eval: false

hello <- function() {
    print("Hello from R")
}

hello()
```

### 7.2. Function With an Argument

Arguments allow a function to receive values.

### R code:

```r
#| eval: false

greet <- function(name) {
    print(
        paste(
            "Hello",
            name
        )
    )
}

greet("Sample_01")
```

### 7.3. Multiple Arguments

### R code:

```r
#| eval: false

variant <- function(
    chromosome,
    position,
    ref,
    alt
) {

    paste(
        chromosome,
        position,
        ref,
        alt,
        sep = ":"
    )
}

variant(
    "chr1",
    6219,
    "A",
    "T"
)
```

### 7.4. Returning a Value

Functions can calculate something and return the result.

### R code:

```r
#| eval: false

add_numbers <- function(
    a,
    b
) {

    result <- a + b

    return(result)
}

x <- add_numbers(
    10,
    20
)

print(x)
```

R also returns the last evaluated expression automatically.

```r
#| eval: false

add_numbers <- function(
    a,
    b
) {

    a + b
}

add_numbers(
    10,
    20
)
```

### 7.5. Default Arguments

Default arguments are used when the caller does not provide a value.

### R code:

```r
#| eval: false

greet <- function(
    name = "User"
) {

    paste(
        "Hello",
        name
    )
}

greet()

greet("Sample_01")
```

### 7.6. Function With a Condition

Functions can contain conditional operations.

### R code:

```r
#| eval: false

classify_position <- function(
    position
) {

    if (position < 5000) {

        return("Low")

    } else {

        return("High")
    }
}

classify_position(6219)
```

### 7.7. Function With Multiple Conditions

### R code:

```r
#| eval: false

classify_position <- function(
    position
) {

    if (position < 1000) {

        "Low"

    } else if (position < 5000) {

        "Medium"

    } else {

        "High"
    }
}

classify_position(6219)
```

### 7.8. Functions With Multiple Data Types

A function can receive different types of values.

### R code:

```r
#| eval: false

describe_variant <- function(
    gene,
    position,
    impact
) {

    paste(
        "Gene:",
        gene,
        "| Position:",
        position,
        "| Impact:",
        impact
    )
}

describe_variant(
    "BRCA1",
    6219,
    "High"
)
```

### 7.9. Local Variables

Variables created inside a function are generally intended for use within that function.

### R code:

```r
#| eval: false

calculate_position <- function(
    position
) {

    new_position <- position + 100

    new_position
}

calculate_position(6219)
```

### 7.10. Anonymous Functions

Anonymous functions are functions without a conventional reusable name.

### R code:

```r
#| eval: false

numbers <- c(
    1,
    2,
    3,
    4
)

lapply(
    numbers,
    function(x) x * 2
)
```

### 7.11. Using Functions Inside Loops

Functions become especially useful when the same operation needs to be repeated.

### R code:

```r
#| eval: false

square <- function(x) {
    x ^ 2
}

numbers <- 1:5

for (number in numbers) {

    print(
        square(number)
    )
}
```

### 7.12. Using Functions With Files

Functions can also be used to perform repeated file-processing tasks.

### R code:

```r
#| eval: false

count_lines <- function(
    file
) {

    length(
        readLines(
            file
        )
    )
}

count_lines(
    "data.txt"
)
```

### 7.13. Built-in Functions

All three environments provide many built-in functions and commands.

### R code:

```r
#| eval: false

length(
    c(10, 20, 30)
)

sum(
    c(10, 20, 30)
)

max(
    c(10, 20, 30)
)

min(
    c(10, 20, 30)
)
```

### 7.14. Function Documentation

Understanding how to find information about functions is an important programming skill.

### R code:

```r
#| eval: false

?mean

help(mean)

args(mean)
```

### 7.15. Practical Example: Variant Description Function

### R code:

```r
#| eval: false

describe_variant <- function(
    gene,
    position,
    ref,
    alt
) {

    paste0(
        gene,
        ":",
        position,
        " ",
        ref,
        ">",
        alt
    )
}

variants <- list(
    list(
        gene = "BRCA1",
        position = 6219,
        ref = "A",
        alt = "T"
    ),
    list(
        gene = "TP53",
        position = 7577,
        ref = "G",
        alt = "C"
    )
)

for (variant in variants) {

    print(
        describe_variant(
            variant$gene,
            variant$position,
            variant$ref,
            variant$alt
        )
    )
}
```

## 8. Data Structures


### 8.1. Vectors

A vector is a collection of values. Vectors are one of the most fundamental data structures in R.

### R code:

```r
#| eval: false

numbers <- c(
    10,
    20,
    30,
    40
)

numbers

numbers[1]

numbers[2:3]

length(numbers)
```

### 8.2. Character Vectors and Lists

### R code:

```r
#| eval: false

genes <- c(
    "BRCA1",
    "TP53",
    "EGFR"
)

genes[1]

genes[2:3]
```

### 8.3. Lists

R lists can contain different types of objects in a single structure.

### R code:

```r
#| eval: false

variant <- list(
    gene = "BRCA1",
    position = 6219,
    ref = "A",
    alt = "T",
    frequency = 0.25
)

variant

variant$gene

variant$position

variant[["ref"]]
```

### 8.4. Matrices

Matrices are two-dimensional structures containing values arranged in rows and columns.

### R code:

```r
#| eval: false

m <- matrix(
    c(
        1, 2, 3,
        4, 5, 6
    ),
    nrow = 2,
    byrow = TRUE
)

m

m[1, 2]

m[, 1]

m[1, ]
```

### 8.5. Arrays

R can use arrays for dimensions greater than two.

### R code:

```r
#| eval: false

x <- array(
    1:12,
    dim = c(2, 3, 2)
)

x

dim(x)
```

### 8.6. Data Frames

Data frames are tabular structures containing rows and columns. They are particularly important in data analysis.

### R code:

```r
#| eval: false

df <- data.frame(
    Gene = c(
        "BRCA1",
        "TP53",
        "EGFR"
    ),
    Position = c(
        6219,
        7577,
        5500
    ),
    REF = c(
        "A",
        "G",
        "C"
    ),
    ALT = c(
        "T",
        "C",
        "A"
    )
)

df
```

### 8.7. Factors and Categorical Data

R has a dedicated `factor` data structure for categorical variables.

### R code:

```r
#| eval: false

impact <- factor(
    c(
        "High",
        "Moderate",
        "Low",
        "High"
    )
)

impact

levels(impact)

as.character(impact)
```



### 8.8. Dictionaries / Key-Value Structures


### 8.9. Tuples


### 8.10. Sets

Sets store unique values.

### 8.11. Accessing and Modifying Elements

### R code:

```r
#| eval: false

numbers <- c(
    10,
    20,
    30
)

numbers[1] <- 100

numbers
```

### 8.12. Adding Elements

### R code:

```r
#| eval: false

numbers <- c(
    10,
    20,
    30
)

numbers <- c(
    numbers,
    40
)

numbers
```

### 8.13. Removing Elements

### R code:

```r
#| eval: false

numbers <- c(
    10,
    20,
    30,
    40
)

numbers <- numbers[
    -2
]

numbers
```

### 8.14. Checking Structure and Size

### R code:

```r
#| eval: false

numbers <- c(
    10,
    20,
    30
)

length(numbers)

str(numbers)

class(numbers)

typeof(numbers)
```

### 8.15. Practical Example: Store Variant Information

### R code:

```r
#| eval: false

variant <- list(
    Gene = "BRCA1",
    Position = 6219,
    REF = "A",
    ALT = "T",
    Impact = "High"
)

variant$Gene

variant$Position

variant$REF

variant$ALT

variant$Impact
```

## 9. Files, Directories and Paths

Files, directories, and paths are fundamental for working with data. Programs need to know where files are located, how to navigate directories, how to create paths, and how to check whether files or directories exist.

### 9.1. Current Working Directory

The current working directory is the directory from which the program is currently operating.

### R code:

```r
#| eval: false

# View current working directory
getwd()
```

### 9.2. Change Working Directory

### R code:

```r
#| eval: false

setwd("/path/to/project")

getwd()
```

A relative path can also be used:

```r
#| eval: false

setwd("data")

getwd()
```

### 9.3. Absolute and Relative Paths

An **absolute path** starts from the root of the filesystem.

Example:


A **relative path** is interpreted from the current working directory.

Example:


### R code:

```r
#| eval: false

absolute_path <- "/home/user/project/data/data.tsv"

relative_path <- "data/data.tsv"

absolute_path

relative_path
```

### 9.4. Parent and Child Directories

`..` refers to the parent directory, while `.` refers to the current directory.

### R code:

```r
#| eval: false

# Current directory
getwd()

# Parent directory
normalizePath("..")

# Current directory
normalizePath(".")
```

### 9.5. Listing Files and Directories

### R code:

```r
#| eval: false

# List files and directories
list.files()

# List only files
list.files(
    pattern = ".*"
)

# List recursively
list.files(
    recursive = TRUE
)
```

### 9.6. Checking Whether a File Exists

### R code:

```r
#| eval: false

file.exists(
    "data.tsv"
)
```

For multiple files:

```r
#| eval: false

files <- c(
    "data.tsv",
    "metadata.tsv",
    "results.tsv"
)

file.exists(files)
```

### 9.7. Checking Whether a Directory Exists

### R code:

```r
#| eval: false

dir.exists(
    "data"
)
```

### 9.8. Creating a Directory

### R code:

```r
#| eval: false

dir.create(
    "results"
)
```

Create nested directories:

```r
#| eval: false

dir.create(
    "results/tables",
    recursive = TRUE
)
```

### 9.9. Creating a File Path

Constructing paths programmatically is safer than manually joining strings.

### R code:

```r
#| eval: false

file_path <- file.path(
    "data",
    "results",
    "output.tsv"
)

file_path
```

### 9.10. File Extensions

### R code:

```r
#| eval: false

file <- "results/output.tsv"

tools::file_ext(file)
```

### 9.11. File Names Without Extensions

### R code:

```r
#| eval: false

file <- "results/output.tsv"

basename(
    tools::file_path_sans_ext(file)
)
```

### 9.12. Getting the Directory From a File Path

### R code:

```r
#| eval: false

file <- "data/results/output.tsv"

dirname(file)
```

### 9.13. Finding Files by Pattern

### R code:

```r
#| eval: false

# Find TSV files
list.files(
    pattern = "\\.tsv$"
)

# Find CSV files
list.files(
    pattern = "\\.csv$"
)
```

Recursively:

```r
#| eval: false

list.files(
    path = ".",
    pattern = "\\.tsv$",
    recursive = TRUE
)
```

### 9.14. File Information

### R code:

```r
#| eval: false

file.info(
    "data.tsv"
)
```

Specific information:

```r
#| eval: false

info <- file.info(
    "data.tsv"
)

info$size

info$mtime

info$isdir
```

### 9.15. Checking Read and Write Permissions

### R code:

```r
#| eval: false

file.access(
    "data.tsv",
    mode = 4
)

file.access(
    "data.tsv",
    mode = 2
)
```

Here:

- `4` checks read permission.
- `2` checks write permission.

### 9.16. Copying Files

### R code:

```r
#| eval: false

file.copy(
    "data.tsv",
    "backup_data.tsv"
)
```

### 9.17. Moving or Renaming Files

### R code:

```r
#| eval: false

file.rename(
    "data.tsv",
    "data_old.tsv"
)
```

### 9.18. Removing Files

### R code:

```r
#| eval: false

file.remove(
    "data_old.tsv"
)
```

### 9.19. Removing Directories

### R code:

```r
#| eval: false

unlink(
    "results",
    recursive = TRUE
)
```

### 9.20. Practical Project Directory Structure

A data-analysis project can be organized into separate directories.


### R code:

```r
#| eval: false

dir.create(
    "data/raw",
    recursive = TRUE
)

dir.create(
    "data/processed",
    recursive = TRUE
)

dir.create(
    "scripts",
    recursive = TRUE
)

dir.create(
    "results/tables",
    recursive = TRUE
)

dir.create(
    "results/figures",
    recursive = TRUE
)
```

### 9.21. Practical Example: Locate TSV Files

### R code:

```r
#| eval: false

files <- list.files(
    "data",
    pattern = "\\.tsv$",
    recursive = TRUE,
    full.names = TRUE
)

files
```

## 10. File Management

File management involves creating, copying, moving, renaming, organizing, inspecting, and removing files and directories. These operations are essential when working with large numbers of data files, analysis outputs, scripts, and project directories.

### 10.1. Check Whether a File Exists

### R code:

```r
#| eval: false

file.exists("data.tsv")
```

### 10.2. Check Whether a Directory Exists

### R code:

```r
#| eval: false

dir.exists("data")
```

### 10.3. Create a File

### R code:

```r
#| eval: false

file.create(
    "example.txt"
)
```

Write content to the file:

```r
#| eval: false

writeLines(
    "Hello from R",
    "example.txt"
)
```

### 10.4. Read a File

### R code:

```r
#| eval: false

content <- readLines(
    "example.txt"
)

print(content)
```

### 10.5. Append to a File

Appending adds new content without replacing the existing content.

### R code:

```r
#| eval: false

write(
    "Additional line",
    file = "example.txt",
    append = TRUE
)
```

### 10.6. Copy Files

### R code:

```r
#| eval: false

file.copy(
    "example.txt",
    "example_backup.txt"
)
```

Copy to another directory:

```r
#| eval: false

file.copy(
    "example.txt",
    "backup/example.txt",
    overwrite = TRUE
)
```

### 10.7. Move Files

### R code:

```r
#| eval: false

file.rename(
    "example.txt",
    "data/example.txt"
)
```

### 10.8. Rename Files

Renaming is a special case of moving a file to a new name.

### R code:

```r
#| eval: false

file.rename(
    "example.txt",
    "example_new.txt"
)
```

### 10.9. Delete Files

### R code:

```r
#| eval: false

file.remove(
    "example_new.txt"
)
```

### 10.10. Create Directories

### R code:

```r
#| eval: false

dir.create(
    "results"
)
```

Nested directories:

```r
#| eval: false

dir.create(
    "results/tables",
    recursive = TRUE
)
```

### 10.11. Delete Directories

### R code:

```r
#| eval: false

unlink(
    "results",
    recursive = TRUE
)
```

### 10.12. List Files

### R code:

```r
#| eval: false

list.files()
```

Only TSV files:

```r
#| eval: false

list.files(
    pattern = "\\.tsv$"
)
```

### 10.13. Find Files Recursively

### R code:

```r
#| eval: false

list.files(
    path = ".",
    pattern = "\\.tsv$",
    recursive = TRUE,
    full.names = TRUE
)
```

### 10.14. File Size

### R code:

```r
#| eval: false

file.info(
    "data.tsv"
)$size
```

### 10.15. Count Files

### R code:

```r
#| eval: false

length(
    list.files(
        "data"
    )
)
```

### 10.16. Organize Files by Extension

For example, separate TSV and CSV files into different directories.

### R code:

```r
#| eval: false

dir.create(
    "tsv_files",
    showWarnings = FALSE
)

files <- list.files(
    pattern = "\\.tsv$"
)

file.copy(
    files,
    "tsv_files",
    overwrite = TRUE
)
```

### 10.17. Batch Rename Files

Suppose files have names such as:


and need to become:


### R code:

```r
#| eval: false

files <- list.files(
    pattern = "_old\\.tsv$"
)

new_names <- sub(
    "_old\\.tsv$",
    ".tsv",
    files
)

file.rename(
    files,
    new_names
)
```

### 10.18. Compare Files

### R code:

```r
#| eval: false

identical(
    readLines("file1.txt"),
    readLines("file2.txt")
)
```

### 10.19. Search Inside Files

### R code:

```r
#| eval: false

lines <- readLines(
    "data.txt"
)

lines[
    grepl(
        "BRCA1",
        lines
    )
]
```

### 10.20. Process Multiple Data Files

### R code:

```r
#| eval: false

files <- list.files(
    "data",
    pattern = "\\.tsv$",
    full.names = TRUE
)

for (file in files) {

    print(
        paste(
            "Processing:",
            file
        )
    )
}
```

### 10.21. Backup Data Files

### R code:

```r
#| eval: false

dir.create(
    "backup",
    showWarnings = FALSE
)

files <- list.files(
    "data",
    full.names = TRUE
)

file.copy(
    files,
    "backup",
    recursive = TRUE
)
```

### 10.22. Check Before Deleting

Before deleting an important file, check that it exists and confirm the target.

### R code:

```r
#| eval: false

file <- "old_data.tsv"

if (file.exists(file)) {

    print(
        paste(
            "File found:",
            file
        )
    )

    file.remove(file)
}
```

### 10.23. Practical Data-File Management Workflow

A common workflow is:

1. Check whether the input directory exists.
2. Find the required files.
3. Create an output directory.
4. Process the files.
5. Save the results.
6. Back up important files.
7. Remove temporary files when appropriate.

### R code:

```r
#| eval: false

input_dir <- "data"

output_dir <- "results"

if (!dir.exists(output_dir)) {

    dir.create(
        output_dir,
        recursive = TRUE
    )
}

files <- list.files(
    input_dir,
    pattern = "\\.tsv$",
    full.names = TRUE
)

for (file in files) {

    print(
        paste(
            "Processing:",
            file
        )
    )
}
```
