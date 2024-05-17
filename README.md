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

**Note:** The pipe operator can be entered into R by using `Ctrl` `+` or `-`.

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
**Note:** The pipe operator can be entered into R by using `Ctrl` `Shift` `M`.

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

#### Functions
### Creating Functions in R

In R, functions are a fundamental way to create reusable pieces of code. Functions allow you to encapsulate code into a single unit that can be executed whenever needed, with different inputs.

#### Creating and Using Functions

- **Function Syntax:**
  - Functions in R are created using the `function` keyword.
  - A function can take one or more arguments and perform a series of operations on them.
  - The result of a function is returned using the `return()` function or by simply placing the result as the last line of the function.

**Example:**
```r
# Define a simple function to add two numbers
add_numbers <- function(a, b) {
  result <- a + b
  return(result)
}

# Call the function with arguments
sum <- add_numbers(3, 5)
print(sum) # Output: 8
```


**Functions with Default Arguments**
You can also define default values for function arguments. This is useful when you want to allow the function to be called with fewer arguments, using default values for some of them.
**Example**
```r
# Define a function with default arguments
greet <- function(name = "Guest") {
  message <- paste("Hello,", name)
  return(message)
}

# Call the function with and without an argument
greeting1 <- greet("Chris")
print(greeting1) # Output: "Hello, Alice"

greeting2 <- greet()
print(greeting2) # Output: "Hello, Guest"
```

### Using Help and Documentation in R

In R, accessing help and documentation is crucial for understanding functions, packages, and other aspects of the language. Here are some key ways to access help and documentation in R:

#### Built-in Help Functions

1. **Help for a Specific Function:**
   - You can access the documentation for a specific function using the `?` or `help()` function.
   - Example:
     ```r
     ?mean
     # or
     help(mean)
     ```

2. **Search for Help Topics:**
   - Use the `??` operator or `help.search()` function to search for help topics related to a keyword.
   - Example:
     ```r
     ??regression
     # or
     help.search("regression")
     ```

3. **List Available Packages:**
   - To see a list of all available packages and their documentation, use `help.start()`.
   - Example:
     ```r
     help.start()
     ```

#### Using Vignettes

- **Vignettes are long-form documentation that includes detailed examples and explanations of a package's functionality.**
  - To list all vignettes available in your installed packages, use the `vignette()` function.
  - Example:
    ```r
    vignette()
    ```
  - To view a specific vignette, use `vignette("vignette_name")`.
  - Example:
    ```r
    vignette("dplyr")
    ```

#### Online Resources

1. **CRAN Task Views:**
   - CRAN Task Views provide curated lists of packages grouped by topic.
   - Visit [CRAN Task Views](https://cran.r-project.org/web/views/) for more information.

2. **RDocumentation:**
   - [RDocumentation](https://www.rdocumentation.org/) is an online resource that provides comprehensive documentation for R functions and packages.

3. **Stack Overflow:**
   - [Stack Overflow](https://stackoverflow.com/questions/tagged/r) is a popular Q&A website where you can find answers to R-related questions or ask your own.

4. **Posit Resources:**
   - [Postit](https://posit.co/resources/) provides a wide range of resources including blogs, videos, and cheatsheets to help you grow your data science skills.

#### Example: Finding Help for `ggplot2`

```r
# Accessing the documentation for the ggplot2 package
library(ggplot2)
?ggplot

# Searching for vignettes related to ggplot2
vignette("ggplot2-specs")
```
# Training Session Exercise: Mapping Locations to SA2 Regions

In this exercise, we'll map locations from a data frame to SA2 regions using R. We'll break down the process into clear, manageable steps. By the end of this exercise, you'll be able to:

1. Load required libraries
2. Define a function to map locations
3. Create sample data frames
4. Use the function to map locations
5. Combine the mapped data
6. Update data in a data frame

## Part 1: Load Required Libraries

First, we need to load the necessary libraries.

```r
library(sf)
library(dplyr)
library(janitor)
```
## Part 2: Define a Function to Map Locations to SA2 Regions
Next, we'll define a function geomap_data that takes a data frame of locations and a path to a shapefile. The function will perform a spatial join to map the locations to SA2 regions.
```r
geomap_data <- function(location_df, shapefile_path) {
  # Read the shapefile
  shape_data <- st_read(shapefile_path)
  
  # Ensure the location data frame has the same CRS as the shapefile
  location_sf <- st_as_sf(location_df, coords = c("Longitude", "Latitude"), crs = st_crs(shape_data))
  
  # Perform a spatial join to find which SA2 region each location is in
  joined_data <- st_join(location_sf, shape_data, join = st_intersects)
  
  # Select relevant columns
  result <- joined_data %>% 
    select(Name, SA2_NAME21) %>% 
    clean_names()
  
  # Identify unmappable locations
  unmappable_locations <- result %>% 
    filter(is.na(sa2_name21))
  
  # Print unmappable locations
  if (nrow(unmappable_locations) > 0) {
    message("Unmappable locations: ")
    print(unmappable_locations)
  } else {
    message("All locations were successfully mapped.")
  }
  
  return(result)
}
```
## Part 3: Create Sample Data Frames
We'll create sample data frames for locations in Sydney and Brisbane.
```r
# Create a sample data frame with locations in Sydney
sydney_locations <- data.frame(
  Name = c("Sydney Opera House", "Bondi Beach"),
  Longitude = c(151.215256, 151.209296),
  Latitude = c(-33.856784, -33.852306)
)

# Create a sample data frame with locations in Brisbane
brisbane_locations <- data.frame(
  Name = c("South Bank Parklands", "Story Bridge"),
  Longitude = c(153.023511, 153.028095),
  Latitude = c(-27.481078, -27.467917)
)
```
## Part 4: Use the Function to Map Locations
Define the path to the shapefile and call the function with the sample data frames.
```r
# Define the path to the shapefile
shapefile <- "~/R Scripts/SA2_2021/SA2_2021_AUST_GDA2020.shp"

# Call the function with Sydney locations
sydney_locations_mapped <- geomap_data(sydney_locations, shapefile) %>% 
  st_drop_geometry()

# Call the function with Brisbane locations
brisbane_locations_mapped <- geomap_data(brisbane_locations, shapefile) %>% 
  st_drop_geometry()
```
## Part 5: Combine the Mapped Data
Combine the mapped data frames into one.
```r
# Combine the data
combined_data <- rbind(brisbane_locations_mapped, sydney_locations_mapped)
```
## Part 6: Update Data in a Data Frame
Finally, we'll update the latitude and longitude for Bondi Beach in the Sydney data frame.
```r
# Update the latitude and longitude for Bondi Beach
sydney_locations <- sydney_locations %>% 
  mutate(
    Longitude = ifelse(Name == "Bondi Beach", 151.2744092, Longitude),
    Latitude = ifelse(Name == "Bondi Beach", -33.8904123, Latitude)
  )
```
# Training Session Exercise: Using Git for Version Control

In this exercise, we'll practice using Git for version control. We'll break down the process into clear, manageable steps. By the end of this exercise, you'll be able to:

1. Initialize a Git repository
2. Clone a repository
3. Create and switch branches
4. Make changes and commit them
5. Push changes to a remote repository
6. Pull changes from a remote repository
7. Resolve merge conflicts

## Part 1: Initialize a Git Repository

First, we'll initialize a new Git repository.

```sh
# Create a new directory for your project
mkdir my_project
cd my_project

# Initialize a new Git repository
git init
```

## Part 2: Clone a Repository

Next, we'll clone an existing repository from a remote source.

```sh
# Clone a repository (replace <repository_url> with the actual URL)
git clone <repository_url>
```

## Part 3: Create and Switch Branches

We'll create a new branch and switch to it.

```sh
# Create a new branch named "feature_branch"
git branch feature_branch

# Switch to the new branch
git checkout feature_branch

# Alternatively, create and switch to a new branch in one command
git checkout -b feature_branch
```

## Part 4: Make Changes and Commit Them

Make some changes to your files, then stage and commit those changes.

```sh
# Stage your changes (replace <file_name> with the actual file name)
git add <file_name>

# Commit your changes with a message
git commit -m "Describe your changes here"
```

## Part 5: Push Changes to a Remote Repository

Push your changes to the remote repository.

```sh
# Push your changes to the remote repository (replace <branch_name> with the actual branch name)
git push origin <branch_name>
```

## Part 6: Pull Changes from a Remote Repository

Pull the latest changes from the remote repository.

```sh
# Pull changes from the remote repository
git pull origin <branch_name>
```

## Part 7: Resolve Merge Conflicts

If there are merge conflicts, resolve them and commit the changes.

```sh
# Check the status to see which files have conflicts
git status

# Edit the conflicted files to resolve conflicts

# Stage the resolved files
git add <file_name>

# Commit the resolution
git commit -m "Resolved merge conflict in <file_name>"
```

# Quick and Easy Cheat Sheet: Git and R

## Git Commands

### Basic Commands
- **Initialize a Git repository**
  ```sh
  git init
  ```

- **Clone a repository**
  ```sh
  git clone <repository_url>
  ```

### Branching
- **Create a new branch**
  ```sh
  git branch <branch_name>
  ```

- **Switch to a branch**
  ```sh
  git checkout <branch_name>
  ```

- **Create and switch to a new branch**
  ```sh
  git checkout -b <branch_name>
  ```

### Staging and Committing
- **Stage changes**
  ```sh
  git add <file_name>
  ```

- **Commit changes**
  ```sh
  git commit -m "commit message"
  ```

- **Stage and commit all changes**
  ```sh
  git commit -am "commit message"
  ```

### Pushing and Pulling
- **Push changes to the remote repository**
  ```sh
  git push origin <branch_name>
  ```

- **Pull changes from the remote repository**
  ```sh
  git pull origin <branch_name>
  ```

### Merging
- **Merge a branch into the current branch**
  ```sh
  git merge <branch_name>
  ```

### Checking Status and Log
- **Check the status of the repository**
  ```sh
  git status
  ```

- **View commit history**
  ```sh
  git log
  ```

## R Commands

### Basic Commands

- **Install a package**
  ```r
  install.packages("package_name")
  ```

- **Load a library**
  ```r
  library(package_name)
  ```

- **View column names of a data frame**
  ```r
  colnames(data_frame)
  ```

- **View the first few rows of a data frame**
  ```r
  head(data_frame)
  ```

- **Summarise a data frame**
  ```r
  summary(data_frame)
  ```

### Data Manipulation
- **Select columns**
  ```r
  data_frame <- data_frame %>% select(column1, column2)
  ```

- **Filter rows**
  ```r
  data_frame <- data_frame %>% filter(condition)
  ```

- **Mutate (add or modify columns)**
  ```r
  data_frame <- data_frame %>% mutate(new_column = expression)
  ```

- **Arrange rows**
  ```r
  data_frame <- data_frame %>% arrange(column)
  ```

### Working with Factors
- **Convert a column to a factor**
  ```r
  data_frame$column <- as.factor(data_frame$column)
  ```

### Functions
- **Define a function**
  ```r
  my_function <- function(arg1, arg2) {
    # function body
  }
  ```

### Data Import
- **Read a CSV file**
  ```r
  data_frame <- read.csv("file_path.csv")
  ```
### Data Export
- **Write a CSV file**
  ```r
  write.csv(dataset, "file_path.csv")
  ```
