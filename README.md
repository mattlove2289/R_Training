### Overview of R and GIT

#### R: A Statistical Computing and Graphics Language
R is a programming language and software environment designed for statistical computing and graphics. It is widely used among statisticians, data analysts, and researchers for data analysis and visualisation. R provides a wide variety of statistical techniques, powerful graphical capabilities, and is highly extensible with a vast ecosystem of packages available. R is open-source software, freely available under the GNU General Public License.

We use R for our ReSPOND dashboard and in the Data and Systems team for custom data requests. R is used for connecting to the Enterprise Data Warehouse, geomapping, and data manipulation. The main packages we use include `dplyr` for data manipulation, `sf` for handling spatial data, `tinygeocoder` for geocoding, and the `tidyverse` for a cohesive collection of R packages designed for data science.

#### GIT: Version Control for Collaborative Development
GIT is a distributed version control system used for tracking changes in source code during software development. It allows multiple developers to work on a project simultaneously without overwriting each other's changes. GIT helps in managing code versions, collaborating with team members, and maintaining a history of changes for the project.

In this training, we will learn how to use GIT for version control in our R projects. We will cover basic GIT commands, using GIT with RStudio, and best practices for managing code versions and collaborating with others.

### Training Session Overview

#### Objectives:
Understand the basics of R programming, learn how to work with different data structures in R, gain practical skills for data manipulation and analysis, and learn to use GIT for version control.

#### Topics Covered:
1. **Introduction to R and RStudio:** Overview of R and RStudio IDE, setting up the R environment, basic R syntax and commands.
2. **Variables and Data Types:** Creating and assigning variables, understanding different data types (numeric, character, logical).
3. **Vectors:** Creating and manipulating vectors, accessing vector elements, basic vector operations.
4. **Data Frames:** Creating data frames, accessing and modifying data frame elements, basic data frame operations using `dplyr`.
5. **Lists:** Creating and using lists, accessing list elements, modifying lists.
6. **Basic Data Manipulation:** Subsetting data, filtering, selecting, and mutating data, using pipes (`%>%`) for streamlined data operations.
7. **Creating Functions:** Writing custom functions in R, understanding function arguments and return values.
8. **Using Help and Documentation:** Accessing R documentation and help files, exploring additional resources for learning R.
9. **Introduction to GIT:** Basic GIT commands, using GIT for version control, integrating GIT with RStudio.

#### What You Will Learn:
- **Foundational Skills:** Basic R syntax and commands, how to create and work with different data structures in R (variables, vectors, data frames, and lists).
- **Data Manipulation:** Techniques for subsetting, filtering, and transforming data, using `dplyr` for efficient data manipulation.
- **Function Writing:** How to write and use custom functions in R.
- **Version Control with GIT:** Basic GIT commands and workflows, using GIT for version control in your R projects.
- **Resources and Documentation:** How to use R's help system and find additional resources for learning and troubleshooting.


### Overview of Variables and Data Types

#### Variables
- **Introduction to Variables:**
  - A variable is a container that stores a value or an object.
  - In R, you assign values to variables using the assignment operator `<-`.

- **Creating and Assigning Variables:**
  - Syntax: `variable_name <- value`
  - Example: `x <- 42`
  - Accessing the variable: `print(x)`

- **Key Points:**
  - Variable names should be descriptive and cannot start with a number.
  - Use `=` for assignment, but `<-` is the preferred operator in R.

#### Data Types
- **Numeric:**
  - Numeric data types are used for numbers. They can be integers or floating-point numbers.
  - Example: `num <- 42.5`

- **Character:**
  - Character data types are used for text. They are enclosed in quotes.
  - Example: `char <- "Hello, R"`

- **Logical:**
  - Logical data types represent boolean values: TRUE or FALSE.
  - Example: `flag <- TRUE`

- **Factor:**
  - Factors are used for categorical data and can be ordered or unordered.
  - Example: `factor_var <- factor(c("low", "medium", "high"))`

- **Complex:**
  - Complex data types are used for complex numbers.
  - Example: `complex_num <- 2+3i`

#### Vectors
- **Definition:**
  - Vectors are one-dimensional arrays that store data of the same type.
  - They are created using the `c()` function.

- **Example:**
  ```r
  numbers <- c(1, 2, 3, 4, 5)
  print(numbers)

  first_number <- numbers[1]
  print(first_number)
  ```

#### Data Frames
- **Definition:**
  - Data frames are two-dimensional structures organised by columns and rows.
  - They can store different types of data in each column.

- **Example:**
  ```r
  data <- data.frame(
    Name = c("Chris", "Maggie", "Van"),
    Age = c(21, 22, 23),
    Occupation = c("Telephone Nerd", "TikTok Addict", "Scientist")
  )
  print(data)

  ages <- data$Age
  print(ages)

  second_person_name <- data$Name[2]
  print(second_person_name)
  ```

#### Lists
- **Definition:**
  - Lists are collections of objects of different types and lengths.
  - They are created using the `list()` function.

- **Example:**
  ```r
  my_list <- list(
    name = "Amanda",
    age = 36,
    occupation = "Public Service",
    hobbies = c("Reading", "Hiking", "Cooking")
  )
  print(my_list)

  converted_list <- data.frame(my_list)

  occupation <- my_list$occupation
  print(occupation)

  first_hobby <- my_list$hobbies[1]
  print(first_hobby)
  ```

#### Key Points
- R automatically determines the data type of a variable based on the assigned value.
- You can check the data type of a variable using the `class()` function.
- Understanding data types is essential for data manipulation and analysis in R, as different types of data require different handling and operations.

### Basic Data Frame Operations Using `dplyr`

The `dplyr` package in R is a powerful tool for data manipulation. It provides a set of functions that make it easy to perform common data manipulation tasks such as selecting, filtering, arranging, and summarising data.

#### Introduction to `dplyr`

- **Installation and Loading:**
  - If you don't already have `dplyr` installed, you can install it using:
    ```r
    install.packages("dplyr")
    ```
  - Load the `dplyr` package using:
    ```r
    library(dplyr)
    ```

- **Key Functions:**
  - `select()`: Select specific columns from a data frame.
  - `filter()`: Filter rows based on conditions.
  - `arrange()`: Arrange rows by variables.
  - `mutate()`: Create or transform columns.
  - `summarise()`: Summarise data.
  - `group_by()`: Group data by one or more variables.
  - `left_join()`: Merge two data frames based on a common column, keeping all rows from the left data frame.
  - `rename()`: Rename columns in a data frame.

#### Examples

**Creating a Sample Data Frame:**
```r
library(dplyr)

data <- data.frame(
  Name = c("Chris", "Maggie", "Van", "Amanda"),
  Age = c(21, 22, 23, 36),
  Occupation = c("Telephone Nerd", "TikTok Addict", "Scientist", "Public Service")
)
print(data)
```
**Selecting Columns:**
```r
# Select the 'Name' and 'Age' columns
selected_data <- select(data, Name, Age)
print(selected_data)
```
**Piping:**

The pipe operator `%>%` from the `magrittr` package (which is loaded with `dplyr`) allows you to chain multiple operations together in a readable and concise way. The ReSPOND dashboard commonly uses the pipe operator. Using the example above, we can use it as follows:
```r
# Select the 'Name' and 'Age' columns
selected_data_pipe <- data %>%
  select(Name, Age)
print(selected_data_pipe)
```
**Note:** The pipe operator can be entered into R by using `Ctrl` + `Alt` + `M`.

**Filtering data:**
```r
# Filter rows where Age is greater than 22
filtered_data <- data %>%
  filter(Age > 22)
print(filtered_data)
```

**Arranging Rows:**
```r
# Arrange rows by Age in ascending order
arranged_data <- data %>% 
  arrange(Age)
print(arranged_data)

# Arrange rows by Age in descending order
arranged_data_desc <- data %>% 
  arrange(desc(Age))
print(arranged_data_desc)
```

**Mutating Columns:**
```r
# Add a new column 'Age_in_5_years' by mutating the 'Age' column
 mutated_data <- data %>% 
    mutate(Age_in_5_years = Age + 5)
 print(mutated_data)
 ```

**Summarising Data:**
```r
# Summarise the data to calculate the average age
  summary_data <- data %>% 
    summarise(avg_age = mean(Age))
print(summary_data)
```
**Left Join:**
```r
# Create another sample data frame to join with
data2 <- data.frame(
  Name = c("Chris", "Maggie", "Van", "Amanda"),
  Department = c("Data", "Systems", "Data", "Systems")
)
print(data2)

# Perform a left join on the 'Name' column
joined_data <- left_join(data, data2, by = "Name")
print(joined_data)
```

**Rename Columns:**
```r
# Rename the Name column to staff_name
data2 <- data2 %>% 
  rename(staff_name = Name)
```
**Left Join:**
In this example we will perform the 'left_join' on two columns on two different column names
```r
joined_data <- data %>% 
  left_join(data2, by = c("Name" = "staff_name"))
  print(joined_data)
```
You will also notice in the previous join example, a pipe operator was not used.

**Grouping Data:**
```r
# Group data by 'Department' and then summarise to calculate the average age for each group.
grouped_data <- joined_data %>%  
  group_by(Department) %>% 
  summarise(avg_age = mean(Age))
print(grouped_data)
```

- `left_join()`: Merge two data frames based on a common column, keeping all rows from the left data frame.

