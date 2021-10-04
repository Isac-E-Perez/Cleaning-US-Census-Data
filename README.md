# Cleaning US Census Data Project
### About: 

For this project, I implemented data analysis using R. I used the libraries readr, dplyr and tidyr which helped me to build the project. I analyze the data of US census to gain a better understanding and insight of the states' total population, demographic, gender and income.
 
### Note:

There is data from 10 different .csv of all 50 states.

### Results:

The goal of this project is to demonstrate that I have knowledge in how to clean and tidy datasets that were just collected.

I could see that all of the datasets have similar aspects in the save file name. I could take advantage of this when reading the files. It is easier to inspect datasets stored when the files have a data frame.I could read each file in *files* into a data frame using *lapply* and save the result to *df_list* 

![1](https://user-images.githubusercontent.com/89553126/135869606-92b835ae-ce11-4858-a059-b7fac4770543.PNG)

Afterwards, I could concatenate all of the data frames in *df_list* into one data frame called *us_census*.

![2](https://user-images.githubusercontent.com/89553126/135870828-8913b8e6-60ae-46f7-b9d8-afc5d4caec45.PNG)

I inspected the datasets with the functions *names*, *str* and *head* to gain insight in what I wanted to gleam from the data and extract from it.

When inspecting *us_census* I noteiced a column *X1* (or on some computers, *...1*) that stores meaningless information. Therefore,  Idropped the *X1* column from *us_census* and saved the resulting data frame back to us_census and viewed the data to confirm the changes.

![3](https://user-images.githubusercontent.com/89553126/135871960-a54ab496-c8a0-421c-b05a-8689ca9e037e.PNG)

