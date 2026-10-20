# Reasoning Before Execution

Write the rule behind each case before you commit your predictions. Replace
every placeholder line below with one to three sentences that name the rule
producing that case's value, type, length, and dimensions. One rule is enough.
After you run and find a miss, add a short correction entry under that case in a
later commit.

## P01
A double among the given values causes implicit coercion, so every element in the created vector is upgraded to double. This produces a flat vector of length 3 with no dimension and the value [1,2,3.5].

## P02
A character string among the given values causes implicit coercion, so every element in the created vector is upgraded to character. This produces a flat character vector of length 3 with no dimension and the values ["1","2","TRUE"].

## P03
The shorter vector, c(1L, 2L), is recycled to match the length of the longer vector before the element-wise addition happens. This integer addition results in an integer vector with the value [11,22,31,42], a length of 4, and no dimension.

## P04
R uses 1-based indexing, so the given expression extracts elements at the 3rd and 1st positions, in that order. This positional subsetting produces a flat integer vector with the value [third=9,first=8], a length of 2, and no dimension.

## P05
A negative index excludes the specified position from the vector. Since -2L excludes only the second element, the result keeps every other element. It is an integer vector with the value [4,9], a length of 2, and no dimension.

Correction: I predicted length 1 in predictions.tsv, but R returned length 2. The negative index -2L excludes only the second element, which leaves two elements. My reasoning already said length 2, so I mistyped the table entry.

## P06
Logical indexing filters the input vector by returning only the values where the condition passes (either TRUE or NA), so it returns the values that are NA or greater than 10. This results in an integer vector with the value [NA_integer_,12], a length of 2, and no dimension.

Correction: I predicted the value [NA_integer_,12], but R printed [NA,12]. The grader writes typed missing constants such as NA_integer_ as plain NA inside vector brackets. I also misread the selector rule: at the missing position, is.na(x) is TRUE, and TRUE | NA evaluates to TRUE. The missing element is selected because the condition is TRUE, not because the condition is NA.

## P07
A factor converts the input text data into categorical integer codes mapped to a unique levels attribute. This produces an underlying integer type with the value factor[low,high,low];levels=[low,high], a length of 3, and no dimension.

## P08
list() creates a generic vector that holds elements of different types and lengths. The output list has a length of 2, based on the number of top-level components it contains. It has a list type, the value list{scores=[3,5],label=["A"]}, and no dimension.

## P09
A data frame is a list of equal-length columns. This tabular structure has the type list, the value of data.frame[2x2]{id=[1,2],passed=[TRUE,FALSE]}, a length of 2 columns, and a 2D dimension of 2x2.

## P10
The recycling of the vector to match the length of the matrix allows the element-wise addition to proceed. Matrix values are stored column by column, so the addition runs down the columns. This results in an integer matrix with the value matrix[2x3](11,22,13,24,15,26), a length of 6, and a dimension of 2x3.

## P11
The mean() function calculates the average of the given values, but since one of the values is missing (NA_real_), the result is also missing. This summary output has the type double, a length of 1, and no dimension, with the value NA_real_.

Correction: I predicted the value NA_real_, but R's canonical description was [NA]. The grader represents missing values as NA inside vector brackets, so the length-one result is written [NA].

## P12
Using na.rm = TRUE removes all missing values before calculating the average value of the remaining elements. This operation outputs a single double value of [9], a length of 1, and no dimension.

## P13
The vector x first holds integer values, but the subassignment x[2] <- 2.5 widens the entire vector from integer to double so the new value fits. The result is a double vector with the value of [1,2.5,3], a length of 3, and no dimension.

## P14
The ifelse operation maps over all values in scores where elements become 0 if they are missing (NA_real_), and are doubled otherwise. This produces a double type vector with the value [14,0,24,8], which is then capped down to [14,0,15,8], with a length of 4, and no dimension.

Correction: I predicted the type as integer, but R returned double. The literals 7, 12, and 4 are already doubles in R, not only the NA_real_ value, and scores * 2 is also a double. So the input vector and the ifelse() result are double, and the final vector is double.

## P15
array() attaches a dim attribute to the integer vector, which arranges its values in three dimensions while keeping the integer type. This produces the value array[2x2x2](1,2,3,4,5,6,7,8), a length of 8, and a dimension of 2x2x2.

## P16
Indexing a vector with 0 returns an empty vector and retains the original data type. This subsetting produces an empty integer vector with the value [], a length of 0, and no dimension.
