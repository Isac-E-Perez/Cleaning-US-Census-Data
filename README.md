# Cleaning US Census Data Project
### About: 

For this project, I implemented data analysis using R. I used the libraries readr, dplyr and tidyr which helped me to build the project. I analyze the data of US census to gain a better understanding and insight of the states' total population, demographic, gender and income.
 
### Note:

There is data from 10 different .csv of all 50 states.

### Results:

The goal of this project is to demonstrate that I have knowledge in how to clean and tidy datasets that were just collected and get them ready for data analysis.

I could see that all of the datasets have similar aspects in the save file name. I could take advantage of this when reading the files. It is easier to inspect datasets stored when the files have a data frame. I could read each file in *files* into a data frame using *lapply* and save the result to *df_list* 

```R
# load CSVs
files <- list.files(pattern = "states_.*csv")
df_files <- lapply(files, read_csv)
```

Afterwards, I could concatenate all of the data frames in *df_list* into one data frame called *us_census*.

```R
us_census <- bind_rows(df_files)
```

I inspected the datasets with the functions *names*, *str* and *head* to gain insight in what I wanted to gleam from the data and extract from it.

When inspecting *us_census* I noteiced a column *X1* (or on some computers, *...1*) that stores meaningless information. Therefore,  Idropped the *X1* column from *us_census* and saved the resulting data frame back to us_census and viewed the data to confirm the changes.

```R
# drop X1 column
us_census <- us_census %>%
select(-X1)
head(us_census)
```

I noticed that there are six columns representing the popuation percentage from different reaces. The columns include the percent symbol %. So I removed the percent symbol % from each of the race columns (Hispanic, White, Black, Native, Asian, and Pacific). Then I saved the resulting in teh data frame *us_census* and viewed to check the change.

```R
# remove % from race columns
us_census <- us_census %>%
mutate(Hispanic = gsub('\\%', '', Hispanic),
White = gsub('\\%', '', White),
Black = gsub('\\%', '', Black),
Native = gsub('\\%', '', Native),
Asian = gsub('\\%', '', Asian),
Pacific = gsub('\\%', '', Pacific))
head(us_census)
```

The Income column also includes a $ symbol along with the number representing median income for the state. Therefore, I removed the $ from the Income column, saved the results to *us_census* and viewed the data.

```R
# remove $ from Income column
us_census <- us_census %>%
mutate(Income = gsub('\\$', '', Income))
head(us_census)
```

The GenderPop column held both male and female population counts. I separate this column at the _ character to create two new columns: *male_pop* and *female_pop* and saved the results into the data frame *us_census*. I did this to it would be easier to read and analyze the data.


```R
# separate GenderPop column
us_census <- us_census %>%
separate(GenderPop, c("male_pop", "female_pop"), '_')
head(us_census)
```

Afterwards, I cleaned the male and female population coumns since the columns contained extra characters M and F, respectively.

```R
# clean male and female population columns
us_census <- us_census %>%
mutate(male_pop = gsub('\\M', '', male_pop), 
female_pop = gsub('\\F', '', female_pop))
head(us_census)
```

I then updated the data types of the columns. I noticed that now that the symbols are removed, a lot of the columns are now numeric but the data type for these columns are still *chr*, or characters. So, I converted all these columns into numeric data types.

```R
# update column data types
us_census <- us_census %>%
mutate(Hispanic = as.numeric(Hispanic),
White = as.numeric(White),
Black = as.numeric(Black),
Native = as.numeric(Native),
Asian = as.numeric(Asian),
Pacific = as.numeric(Pacific),
Income = as.numeric(Income),
male_pop = as.numeric(male_pop),
female_pop = as.numeric(female_pop))
head(us_census)
```

I then took a second look back to the colums Hispanic, White, Black, Native, Asian and Pacific. The columns represeted the population percentage for each race. To maake any desired calculations easier, the coumns should represent percentages in decimal form. Therefore, I updated the values of these cooumns to be in decimal form.

```R
# update values of race columns
us_census <- us_census %>%
mutate(Hispanic = Hispanic/100, 
White = White/100, 
Black = Black/100,
Native = Native/100,
Asian = Asian/100,
Pacific = Pacific/100)
head(us_census)
```

I then checked if duplicate rows are present in the dataset and viewed the results in a table to get a count of the duplicated rows.

```R
# check for duplicate rows
us_census %>% 
duplicated() %>%
table()
```

**TRUE means that there is duplicated data present**

```R
## FALSE    TRUE
##    52       9
```

The code told me that duplicates were present so since there are duplicates I updated the *us_ccensus* data frame with only unique/distinct rows.

```R
# remove duplicate rows
us_census <- us_census %>%
distinct()
```

Afterwards, I wanted to confirm that there were no more duplicated rows in *us_census*.

```R
# check for duplicate rows
us_census %>%
duplicated() %>%
table()
```

```R
## FALSE
##    52
```

I viewed the data frame one last time to ensure everything was cleaned and ready for analysis. Afterwards I concluded that yes, the data frame was cleaned and ready for future analysis when needed.
