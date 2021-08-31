---
title: "Advanced Data Science for Planners"
subtitle: 'Excercise 1.Data Types in R'
author: "Fang Fang"
knit: (function(input_file, encoding) {
  out_dir <- 'docs';
  rmarkdown::render(input_file,
 encoding=encoding,
 output_file=file.path(dirname(input_file), out_dir, 'index.html'))})
output: 
  html_document: 
    keep_md: yes
    toc: true
---

# Objectives

- Assign values to objects in R.

- Learn how to name objects properly in R.

- Understand different data types in R: vector, list, data frames, matrices...


In this session, we will have a brief overview of the R especially for those who are not very familiar with this language. I would recommend you to create a new script called lecture.r under a specific folder (e.g. exercise_1)  to try out the commands we introduced below.   

## 1. Basic operators

First, we start with some basic operators in R e.g. `+ - * /`. Try to type these commands below in your console window to get the results.


```r
2+3
3.14*4-52.6
9 %/% 4    #integer division
```

Another important operator is called *assignment operator*. We use an assignment operator to assign the value of an expression to a variable.

You have two options to assign a new variable. 1) the conventional assignment operator `=` which is very common in most programming languages, 2) `<-` which are specific to R. Throughout this course, we will only use `<-`. It assigns values on the right to objects on the left.  

The shortcut for `<-` is **Alt + - (Windows)** or **Option + - (Mac)**

Try out the commands below in your R console, or type in your code editor and click on run. We assign 4 to x, and 20 to y. Use the `print` function to print out these variables. If we assign a new value to y, it will override the previous value. 



```r
x <-  4   
y <- 20
print(x)
print(y)

y <- 227

print (y)   #Note R will overwrite value for y 
```

We can also create expressions using existing variables. We assign the value 4 to the variable `x` before, and we can further evaluate the square of `x` using the exponentiation `ˆ` operator below.


```r
x^2
```

How we usually name a variable in R? Please note

- R is case sensitive 

- Avoid existing function names e.g. if, else, mean...

- It’s also best to avoid dots, try *_* underscore instead. e.g. speed_limit<-60

- Name cannot start with a number e.g. 4_income is not valid. 


## 2. Basic Data Types in R

The commonly used data types in R are:

- Numeric: all the values are numbers or treated as numbers (for double precision floating point numbers). You can perform mathematical operations. For example, 12.3, -22.4, and 34.0 are all numeric data type. 

- Integer: values are integers. You can perform mathematical operations. For example, 12, 33,34 are all integer data type.

- Characters/string: values can be letters, texts or numbers, which will be treated as text. For example, "Tom" and "Austin" are all characters in R. 

- Logical: true or false values. 

- Dates: this data type will allowed you to perform time series analysis. For example, "2020-03-09" and "14:33:30" are date and time data types.


To check out the data type for a certain variable, you can use `typeof()`, or `class()`


### Question 1: 
Execute the commends below. What is the data type for x?

```r
x  <- 5
class(x)
```

Another function can help you to determine whether the variable is under numeric data type: `is.numeric()`. If yes, the variable is under numeric data type. 

Similarly we have `is.integer()`,`is.logical()`. 

For example, the example below examines x is an integer. 

```r
x <-5
is.integer(x)
class(x)
```


### Question 2: 
Execute the commands below. Is `y` an integer, logical or numeric data? 

```r
y <-5.0
is.integer(y)
is.numeric(y)
is.logical(y)
```

Logical data are just `TRUE` or `FALSE`. The example below examines `logicalvalue` is not a numeric data, it is a logical data. 


```r
logicalvalue <- TRUE
is.numeric(logicalvalue)
is.logical(logicalvalue)
```

Tip: If you want to assign an integer value, you need append an L suffix.For example


```r
x <- 55L
class(x)
```

Let's try out these character variables:


```r
test <- "This is just a test of character"
class(test)
```

### Question 3: 
Try out the commends below. What is the data type for `test2`? Numeric or character? 


```r
test2 <- "34.443"

class(test2)
```



## 3. Vectors

Vectors is the most common and basic data model in R.

Vectors have the following features:

- Composed by a series of values, which is a 1-dimensional array. 

- All of the elements must be the same type of data, you cannot mix data types in a single vector.

- Can be 1) numeric, 2) integer, 3) characters, or 4) logical, 5) complex

- Combine a series of values to a vector, you need the ` c()` function

Let's establish three different vectors: 

- First vector stores test scores for 5 students;

- Second vector stores students' university ID;

- Third vector stores students' name; 

         
Execute the commands below: 


```r
# test scores
scores <- c(30, 70, 100, 60)
print(scores)

# Set up students' ID  
ID<-c(637884982,093874618)
print(ID)

# assign students names here
name_list <-  c("Aaron", "Joe","Alex","Amanda")
print(name_list)
```


Let's try to examine their scores. Do all the four students get score above 50? We can use `scores>50` to answer the question. Execute the commends below. We assign the results into a new variable called eva_scores. 


```r
eva_scores <- scores>50
eva_scores
class(eva_scores)
```

### Question 4:

What is the data type for `eva_scores` ? 

How to subset vectors? To subset your vector, you can simply use a number, or an `index` to extract a certain value. The index means the position of the item in that vector. In R index starts with `1`. So executing `scores[2]` will return you the second item within `scores`. Please try the commends below. 


```r
scores <- c(30, 70, 100, 60)

scores[2]
```

You can also extract multiple items. The index `1:3` helps to extract from the first to the third item. If you are not extracting items in a row, use `c()` function to extract different items separately. 


```r
scores[1:3] # return the first 3 items
scores[c(2,4)] # return the second and fourth number. 
```

On the other hand,  you can drop an item using `-` in front of their index. For example, the commends below drops the second item in scores:


```r
scores[-2]
```

To further inspect your vectors, commonly used functions are:

- `length()`   get or set the length of vectors (including lists), how many values are there

- `str()`       structure of an object

- `names()`    names of the variable

- `rm()` 		  delete a vector from your current environment


```r
class(name_list)
length(ID)
str(ID)
```

As we mentioned before, we cannot mix data types in a single vector. Try out to mix numbers with letters in a single vector, see if you get any error messages


```r
scores <- c(30, 70, "a", 60)
class(scores)
```

It turns out that the `scores` vector is now a character type instead of numeric. This is called **implicit Coercion**, which coerce values to a different type in order to make it work. 

Note there is a certain order here for the implicit coercion: **Logical-> integer-> numeric->character**. Which means when mixing different types together, automatically logical values can be treated as any types on its right. However, integers can be converted automatically into numeric or character, but cannot be converted as logical under implicit coercion. In addition, logical values can be converted to numbers: `TRUE` is converted into 1 and `FALSE` turns into 0.


You can explicitly coerce one vector class to another using function start with `as.`. For example, to convert a variable into character, you can try `as.character`. This is called **Explicit Coercion**.

So it sounds like 77.8 should be numeric data type, but we converted it into character manually. So sometimes you need to use `class()` to double check the data type for certain variables. 


```r
convertbefore <- 77.8
class(convertbefore)
convertafter <- as.character(convertbefore)
class(convertafter)
print (convertafter)
```


## 4. Matrices

Vectors are 1-dimension array, matrices are 2-dimensional array. In other words, matrices have rows and columns. We can create a new matrix via `matrix()`. To check dimensions, please use the function: `dim()`. Please also note that matrices are structured column-wise. That means values are assigned by column first then rows. 

Try out these script in your console, and examine the output. Here we use matrix function to generate a matrix (4 rows and 3 columns). The values are from 1-12. Since matrix will populate  columns first, so the matrix will look like:

 Row number | first column  | Second column | Third column
------------- | -------------| -------------|-------------
1st row  | 1 |5|9
2nd row | 2 |6|10
3rd row |3|7|11
4th row |4|8|12



```r
# We specify we need the matrix with 4 rows and 3 columns
m <- matrix(1:12, nrow=4, ncol=3)
dim(m)
m
```

Within the matrix function,you can set `byrow=TRUE`, and the matrix is filled by rows. 

### Question 5:

Use the `matrix` function to generate the matrix below:

 Row number | first column  | Second column | Third column | Fourth column
------------- | -------------| -------------|-------------|-------------
1st row  | 10 |11|12|13
2nd row | 14 |15|16|17
3rd row |18|19|20|21



## 5. Data frame

A data frame is also a two-dimensional array structure, where each column contains values of one variable and each row contains one set of values. For a data frame, the column names cannot be empty, and each column should have same amount of items. Each column can store different types of data. A data frame is very similar to a tabular data in excel sheet. Usually when we read in any tables into R, we usually store them as a data frame. For this course, we will primarily work with vectors and data frames. 

Execute the commends below to examine the built-in data set (a data frame) in R called `iris`. 

```r
data(iris)
class(iris)
```


How to subset a data frame?  Here are some tips:

1) To subset a specific column:

Sometimes we just need to extract some certain variables or columns in a data set. We can use `$` to call a certain column. For example, the commends below extract column `Species`and assign it into a new data called `subset_iris`


```r
subset_iris <- iris$Species
```

2) To subset a specific value: 

Sometimes we need to extract just a certain value in a data frame. Again we will use item index to call specific values. Since data frames have two-dimensional structure, to locate a certain value we need two indexes: row number and column number. Take a look at the `iris` data in your R window. It has 150 rows and 5 columns. Let's try to extract the highlighted value `0.2` below: it locates on the first row and 4th column. 

![](images/iris.jpg)

So we can use `iris[1,4]` to return this value. Note row number goes first and followed by the column number. Use `,` to seperate these two numbers. 


```r
iris[1,4]
```


3) To subset rows

Sometimes we need subset some certain rows. Please note columns usually include column name, but no names are given for each row since rows are individual records (not variables). We can still use row index to call a specific row, just leave the column number blank and it will return us all the column values. For example, the command below returns us all the values on the 3rd row:


```r
iris[3,]
```


4) To subset rows using logical variable


Remember we can always use logical variable to subset certain rows. For example, how to extract records for setosa only? You want to set up a filter to see any record follows `iris$Species=="setosa"`. Note you need to use the equality operator which means always equal to, to identify whether this record is setosa. Try to execute the command below in your console window:


```r
iris$Species=="setosa"
```


What you get here? `iris$Species=="setosa"` will only return you a logical variable (T/F)! It will NOT tell you the original setosa data. But we can use this logical variables as `row numbers` for subsetting. Leave the column number blank so all the columns will be returned. Please try the commands below. You can always save the output as a new variable: for example, the subset will be saved as a new object called `subset_setosa` below. 


```r
subset_setosa <- iris[iris$Species=="setosa",]
# Or your can try the `subset` function
subset_setosa <- subset(iris, iris$Species=="setosa")
```

5) To subset rows based on multiple values

For example, how to extract records for both setosa and versicolor? Try the `%in%` operator to get the logical variable for multiple values. The `c()` will combine multiple values together. `%in%` operator in R will identify if an element belongs to this vector created by `c()`.
 

```r
subset_setosa_versicolor <- iris[iris$Species%in%c("setosa","versicolor"),]
```

6) To Subset rows based on a numeric column

Sometimes you need to subset your data based on some values of a numeric column. How about subset iris where Sepal.length is greater than 6?

We can still use the logical variable to subset the dataset. The `iris$Sepal.Length>6` will return a true or false variable. Leave the column number blank within the `[]` to subset the data. 


```r
subset_sepal <- iris[iris$Sepal.Length>6,]
# or try the subset function instead
subset_sepal <-subset(iris, iris$Sepal.Length>6)
```

### Question 6:

Try to use index numbers to extract the 3rd column from iris data instead of using `iris$Petal.Length`



## 6. Date and times

In social science field, there are lots of scenarios we have to analysis a certain pattern overtime. E.g is the mean household income declines each year from 1990-2020? Let's explore more about date and time in R. In fact date and time are different concepts. First let's install the `lubridata` package. 


```r
install.packages("lubridate")
```

Load the package then try out the scripts below. 


```r
library(lubridate)
# Below is the date of today
today()
# Below is the current time in 
# Year-Month-Date Hour-minute-second
now()
```


R has developed a special way to save dates and times.Usually dates are saved as Date class. For time we usually save them in POSIXct format. The POSIXct data class stores date/time as the number of seconds since January 1, 1970, while the POSIXlt class stores them as a list with elements for second, minute, hour, day, month, and year, among others. Unless you need the list nature of the POSIXlt class, the POSIXct class is the usual choice for storing dates in R (Copied from [Dates and Times in R](https://www.stat.berkeley.edu/~s133/dates.html)).

We can create a date/time variable from strings by specifying the format. For example, though visually `date_chr` and `date_POSIXct` are identical, but the data types are different. 


```r
date_chr <- c("2017-01-31")
date_POSIXct <- ymd(date_example)  # y: year, m: month, d: date

time_chr <- c("02/12/2015 08:01")
time_POSIXct <- mdy_hm(example2) # y: year, m: month, d: date , h: hour, m: minute
```

To extract a certain date/time component, you can use `month` or `year` to call this specific component. For example, let's extract month and year from `date_POSIXct`. 


```r
month_example <- month(date_POSIXct)
year_example <- year(date_POSIXct)
```


### Question 7: 

Try the command below to extract hour (it should be `8`) from `time_chr`. Does it work or not? Why?


```r
hour_example <- hour(time_chr)
```

Let's go back to the dataset called 'Beach_Water_Quality'. Load this dataset in R (Make sure you installed `tidyverse` package first):

```r
library(tidyverse)
water <- read_csv("data/Beach_Water_Quality.csv")
```


Examine all the columns in the dataset. According to the `measurement Timestamp` column these measures are posted since `10/01/2015 07:00:00 AM`. We are interested to get measurements from 2015-08-12 only. Currently the second column is a mix of data and time.We need to extract the date component from the column called `measurement Timestamp` in the dataset. Let's first examine the data type for this column:


```r
class(water$`Measurement Timestamp`)
```

This column is still under character category.We need to turn it into the POSIXlt format. We assign the updated result back into this `Measurement Timestamp` column.  


```r
water$`Measurement Timestamp` <- mdy_hms(water$`Measurement Timestamp`) 
```

Now we can extract the `date` component into a new column called `date`. The new column will be appended as the last column in the data set. 


```r
# Extract the "date" component as a new column 
water$date_component <- date(water$`Measurement Timestamp`)
```

![ ](images/date.jpg)



So this is what we need: a new column only includes the date info for each record. Next we can subset records for 2015-08-12 only. Let's try a new function `subset`. Within the function, the data set we need to extract from is `water`, and the values of interest is `2015-08-12`. The double equal sign `==` is the equality operator (always equal to).  It examines each value under the `date_component` column whether it equals `2015-08-12`. Execute the commands below. The result is assigned to a new data called `subset_water`: it turns out that on 2015-08-12 we have 136 records.  


```r
subset_water <- subset(water, date_component=='2015-08-12')
```


To learn more about date/time in R, click [here](https://r4ds.had.co.nz/dates-and-times.html#prerequisites-10). 

## 7. List

List is an R object which can mix different types of data e.g. numbers, letters, vectors matrix. For example, we can create a list below. Note the size for each vector are also different. 


```r
A_number = c(100, 200, 100) 
A_string = c("Data", "Science", "for", "Planners") 
logical_value = c(TRUE, FALSE, TRUE, TRUE, FALSE) 
A_list = list(A_number, A_string, logical_value, 3)   # Functions to construct a list

A_list
```

To subset a list, you must use double brackets to extract a certain value. 


```r
# Try out the script below. It only return the item as a list, 
# which the value is same as the vector called A_number. 

first <- A_list[1]
class(first)

# Here the double bracket will extract the first element. 

#Now it is a vector(numeric) instead of list. 

first_item <- A_list[[1]]
class(first_item)

# To extract the first element within the first item, 
A_list[[1]][1]
```

## 8. Factor

Another typically used data type in R is factor. Factors categorize the data value and store it as unique levels. The values can be both strings or integers. Usually we use factor to store variables with limited number of unique values. For example, especially working with data in the planing field, columns like gender or month are usually factors in R. Since in gender we usually have "Male" or "Female" as the unique values. For variable month, we have 12 unique values.  Factors can only contain a pre-defined set values, known as levels.  Levels are automatically sorted in alphabetical order.But you can modify an existing factor based on your need. 
To create or edit a factor,we can use `factor` function. Assume we need a new variable to store students gender. We simply create a vector called `sex`, but it is currently under character category. We can then convert this variable as a factor. Then we use `levels` to check out the unique values in alphabetical order.  


```r
sex <- c("M", "F", "M", "F","F")
sex <- factor(sex)
levels(sex) 
```



Since `M` and `F` are abbreviations/codes. We can rename them. You might need to install and load a package called "forcats" before executing the commands below. 


```r
library(forcats)
sex <- fct_recode(sex, "Male"="M", "Female"="F")
sex
```

Here is another example of factor variables. Let's record their school year in a new variable called `year` (freshman sophomore junior senior). We can reorder them in a more logical instead of default alphabetical order


```r
year <- factor(c("freshman","sophomore",
                 "junior","senior","junior","freshman",
                 "freshman","senior","freshman"))

levels(year)

#Let's reorder them

new_order_data <- factor(year,levels = 
                c("freshman", "sophomore", "junior", "senior"))

levels(new_order_data)
```



### Question 8

Examine the data type of the first column in the `Beach_Water_Quality` data set. Convert it into a factor data type. What are the unique values for this column? 



# Summary

The figure below gives you a better visualization of all the data types we mentioned above. 

![ ](images/data_type.jpg)
