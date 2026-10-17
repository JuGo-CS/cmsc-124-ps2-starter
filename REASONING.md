# Reasoning Before Execution

Write the rule behind each case before you commit your predictions. Replace
every placeholder line below with one to three sentences that name the rule
producing that case's value, type, length, and dimensions. One rule is enough.
After you run and find a miss, add a short correction entry under that case in a
later commit.

## P01
There is a double among the given values which results in an implicit coercion where all elements in the created vector were upgraded to double. This rule produces a flat vector of length 3 with no dimension containing the upgraded values [1,2,3.5].

## P02
There is a character string among the given values which results in an implicit coercion where all elements in the created vector were upgraded to character. This produces a flat character vector of length 3 with no dimension containing the string values ["1","2","TRUE"].

## P03
The shorter vector, which in this example is c(1L, 2L), was recycled to match the length of the longer vector before the element-wise addition happens. This integer addition results in an integer vector value of [11,22,31,42], a length of 4, and no dimension.

## P04
In R, since it uses 1-based indexing, the given expression extracts elements by their positional index (3rd and 1st index) in order. This positional subsetting produces a flat integer vector value of [third=9,first=8] with a length of 2 and no dimension.

## P05
With the given negative index, means that returning all values in the vector except the value at the given index position. Since the index -2L means return all values in the vector except the second element, it produces an integer vector value of [4,9] with a length of 2 and no dimension.

Correction: Based on my reasoning, the result has a length of 2, but I put length=1 in predictions.tsv. This was just a typo, sir.:>

## P06
Logical indexing filters the input vector by returning only values where the condition is passed (either TRUE or NA), which means that it returns the values that are NA or greater than 10. This results into an integer vector value of [NA_integer_,12] with a length of 2 and no dimension.

Correction: My predicted value is [NA_integer_,12] which is wrong because the missing values uses the general NA shorthand.

## P07
The factors conver the input text data into a categorical integer codes mapped to a unique levels attribute. This given conversion produces an underlying integer type value of factor[low,high,low];levels=[low,high] with a total length of 3 and no dimension.

## P08
Creates a list that is a generic vector that holds elements of different types and lengths. The total length of the ouput list is 2 which is based on the number of top-level components it contains, returning a list type, with a value of list{scores=[3,5],label=["A"]} with no dimension.

## P09
A data frame is like a list with vectors that have an equal length of a representing columns. This tabular structure produces a list type value of data.frame[2x2]{id=[1,2],passed=[TRUE,FALSE]} with a length of 2 columns and an explicit 2D dimension of 2x2.

## P10
The recycling of a vector to match the length of the longer matrix allows to proceed with the element-wise addition operation column by column. This results in an integer type matrix value of matrix[2x3](11,22,13,24,15,26) with a length of 6 and a dimension of 2x3.

## P11
The mean() function calculates the average of the given values, but since there is a missing value (NA_real_), it automatically returns NA_real_ as the resulting value. This summary output has a data type of double, a length of 1, and no dimension.

Correction: My predicted value is NA_real_ which is wrong because the missing values uses the general NA shorthand.

## P12
Using na.rm = TRUE will remove all missing values before calculating the average value of the remaining elements. This mathematical operation outputs a single double value of [9] with a length of 1 and no dimension.

## P13
The vector x first holds integer values but then the operation x[2] <- 2.5 results in implicitly converting the entire vector storage type to double. This in-place modification outputs a double vector value of [1,2.5,3] with a length of 3 and no dimension.

## P14
The ifelse operation maps over all values in scores where elements are changed to 0 if they are missing (NA_real_), and otherwise are doubled. This operation forces a double type vector value of [14,0,24,8], which is then capped down to [14,0,15,8] with a length of 4 and no dimension.

Correction: My predicted type for this given is integer, which was incorrect because of the `NA_real_` on the initial scores vector value which automatically upgrades the entire calculation to double precision.

## P15
The array function reshapes a flat vector sequence into multi-dimensional boundaries using the attribute dim while keeping its data type. This structural mapping produces an integer type value of array[2x2x2](1,2,3,4,5,6,7,8) with a length of 8 and a 3D dimension of 2x2x2.

## P16
Indexing a vector with a 0 index will return an empty vector with a length of zero while completely retaining the original data type. This specific subsetting produces an empty integer value of [] with a length of 0 and no dimension.