---
title: "Lab 2 Homework"
author: "Maxen Hamelynck"
date: "2023-01-16"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---

## Instructions

Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!

1.  What is a vector in R?

Vectors are methods of organizing data into objects as sequences, strings, or simple lists

2.  What is a data matrix in R?

Matrices are stacks of vectors organized such that they appear as data tables; they're another method of organizing data.

3.  Below are data collected by three scientists (Jill, Steve, Susan in order) measuring temperatures of eight hot springs. Run this code chunk to create the vectors.\


```r
spring_1 <- c(36.25, 35.40, 35.30)
spring_2 <- c(35.15, 35.35, 33.35)
spring_3 <- c(30.70, 29.65, 29.20)
spring_4 <- c(39.70, 40.05, 38.65)
spring_5 <- c(31.85, 31.40, 29.30)
spring_6 <- c(30.20, 30.65, 29.75)
spring_7 <- c(32.90, 32.50, 32.80)
spring_8 <- c(36.80, 36.45, 33.15)
```

4.  Build a data matrix that has the springs as rows and the columns as scientists.


```r
temperatures <- c(spring_1, spring_2, spring_3, spring_4, spring_5, spring_6, spring_7, spring_8)
people <- c('Jill', 'Steve', 'Susan')
hotspring_matrix <- matrix(temperatures, nrow=8, byrow=T)
colnames(hotspring_matrix) <- people
hotspring_matrix
```

```
##       Jill Steve Susan
## [1,] 36.25 35.40 35.30
## [2,] 35.15 35.35 33.35
## [3,] 30.70 29.65 29.20
## [4,] 39.70 40.05 38.65
## [5,] 31.85 31.40 29.30
## [6,] 30.20 30.65 29.75
## [7,] 32.90 32.50 32.80
## [8,] 36.80 36.45 33.15
```

4.  The names of the springs are 1.Bluebell Spring, 2.Opal Spring, 3.Riverside Spring, 4.Too Hot Spring, 5.Mystery Spring, 6.Emerald Spring, 7.Black Spring, 8.Pearl Spring. Name the rows and columns in the data matrix. Start by making two new vectors with the names, then use `colnames()` and `rownames()` to name the columns and rows.

    
    ```r
    people <- c('Jill', 'Steve', 'Susan')
    colnames(hotspring_matrix) <- people
    
    springnames <-c('Bluebell Spring','Opal Spring','Riverside Spring', 'Too Hot Spring','Mystery Spring','Emerald Spring', 'Black Spring', 'Pearl Spring')
    rownames(hotspring_matrix) <- springnames
    
    hotspring_matrix
    ```
    
    ```
    ##                   Jill Steve Susan
    ## Bluebell Spring  36.25 35.40 35.30
    ## Opal Spring      35.15 35.35 33.35
    ## Riverside Spring 30.70 29.65 29.20
    ## Too Hot Spring   39.70 40.05 38.65
    ## Mystery Spring   31.85 31.40 29.30
    ## Emerald Spring   30.20 30.65 29.75
    ## Black Spring     32.90 32.50 32.80
    ## Pearl Spring     36.80 36.45 33.15
    ```

5.  Calculate the mean temperature of all eight springs.

    
    ```r
    mBluebell <- mean(hotspring_matrix[1:1,1:3])
    mOpal <- mean(hotspring_matrix[2:2, 1:3])
    mRiver <- mean(hotspring_matrix[3:3, 1:3])
    mHot <- mean(hotspring_matrix[4:4, 1:3])
    mMyster <- mean(hotspring_matrix[5:5,1:3])
    mEmerald <- mean(hotspring_matrix[6:6,1:3])
    mBlack <- mean(hotspring_matrix[7:7,1:3])
    mPearl <- mean(hotspring_matrix[8:8,1:3])
    
    mBluebell 
    ```
    
    ```
    ## [1] 35.65
    ```
    
    ```r
    mOpal 
    ```
    
    ```
    ## [1] 34.61667
    ```
    
    ```r
    mRiver 
    ```
    
    ```
    ## [1] 29.85
    ```
    
    ```r
    mHot 
    ```
    
    ```
    ## [1] 39.46667
    ```
    
    ```r
    mMyster 
    ```
    
    ```
    ## [1] 30.85
    ```
    
    ```r
    mEmerald 
    ```
    
    ```
    ## [1] 30.2
    ```
    
    ```r
    mBlack 
    ```
    
    ```
    ## [1] 32.73333
    ```
    
    ```r
    mPearl 
    ```
    
    ```
    ## [1] 35.46667
    ```
    
    ```r
    rowSums(hotspring_matrix)/3 
    ```
    
    ```
    ##  Bluebell Spring      Opal Spring Riverside Spring   Too Hot Spring 
    ##         35.65000         34.61667         29.85000         39.46667 
    ##   Mystery Spring   Emerald Spring     Black Spring     Pearl Spring 
    ##         30.85000         30.20000         32.73333         35.46667
    ```

6.  Add this as a new column in the data matrix.

    
    ```r
    Average_temperatures <- rowSums(hotspring_matrix)/3 
    averagehotspring_matrix <- cbind(hotspring_matrix, Average_temperatures)
    averagehotspring_matrix
    ```
    
    ```
    ##                   Jill Steve Susan Average_temperatures
    ## Bluebell Spring  36.25 35.40 35.30             35.65000
    ## Opal Spring      35.15 35.35 33.35             34.61667
    ## Riverside Spring 30.70 29.65 29.20             29.85000
    ## Too Hot Spring   39.70 40.05 38.65             39.46667
    ## Mystery Spring   31.85 31.40 29.30             30.85000
    ## Emerald Spring   30.20 30.65 29.75             30.20000
    ## Black Spring     32.90 32.50 32.80             32.73333
    ## Pearl Spring     36.80 36.45 33.15             35.46667
    ```

7.  Show Susan's value for Opal Spring only.

    
    ```r
    mean(hotspring_matrix[,3])
    ```
    
    ```
    ## [1] 32.6875
    ```

8.  Calculate the mean for Jill's column only.

    
    ```r
    mean(hotspring_matrix[,1])
    ```
    
    ```
    ## [1] 34.19375
    ```

9.  Use the data matrix to perform one calculation or operation of your interest.

    Calculating the integer mean of Steve's hotspring data from 'Too hot' to 'Pearl'

    And reexpressing the matrix only as integers greater than or equal to 31

    
    ```r
    partialcol2 <- hotspring_matrix[4:8, 2]
    partialcol2
    ```
    
    ```
    ## Too Hot Spring Mystery Spring Emerald Spring   Black Spring   Pearl Spring 
    ##          40.05          31.40          30.65          32.50          36.45
    ```
    
    ```r
    intpartialcol2 <- as.integer(partialcol2)
    intpartialcol2
    ```
    
    ```
    ## [1] 40 31 30 32 36
    ```
    
    ```r
    mean(intpartialcol2)
    ```
    
    ```
    ## [1] 33.8
    ```
    
    ```r
    inttemp <- as.logical(temperatures>=31)
    intmatrix <- matrix(inttemp, nrow=8, byrow=T)
    intmatrix
    ```
    
    ```
    ##       [,1]  [,2]  [,3]
    ## [1,]  TRUE  TRUE  TRUE
    ## [2,]  TRUE  TRUE  TRUE
    ## [3,] FALSE FALSE FALSE
    ## [4,]  TRUE  TRUE  TRUE
    ## [5,]  TRUE  TRUE FALSE
    ## [6,] FALSE FALSE FALSE
    ## [7,]  TRUE  TRUE  TRUE
    ## [8,]  TRUE  TRUE  TRUE
    ```

## Push your final code to GitHub!

Please be sure that you check the `keep md` file in the knit preferences.


