# Cleaning US Census Data Project
### About: 

For this project, I implemented data analysis using R. I used the libraries readr, dplyr and tidyr which helped me to build the project. I analyze the data of US census to gain a better understanding and insight of the states' total population, demographic, gender and income.
 
### Note:

There is data from 10 different .csv of all 50 states.

### Results:

The goal of this project is to demonstrate that I have knowledge in how to clean and tidy datasets that were just collected and get them ready for data analysis.

I could see that all of the datasets have similar aspects in the save file name. I could take advantage of this when reading the files. It is easier to inspect datasets stored when the files have a data frame. I could read each file in *files* into a data frame using *lapply* and save the result to *df_list* 

![1](https://user-images.githubusercontent.com/89553126/135869606-92b835ae-ce11-4858-a059-b7fac4770543.PNG)

Afterwards, I could concatenate all of the data frames in *df_list* into one data frame called *us_census*.

![2](https://user-images.githubusercontent.com/89553126/135870828-8913b8e6-60ae-46f7-b9d8-afc5d4caec45.PNG)

I inspected the datasets with the functions *names*, *str* and *head* to gain insight in what I wanted to gleam from the data and extract from it.

When inspecting *us_census* I noteiced a column *X1* (or on some computers, *...1*) that stores meaningless information. Therefore,  Idropped the *X1* column from *us_census* and saved the resulting data frame back to us_census and viewed the data to confirm the changes.

![3](https://user-images.githubusercontent.com/89553126/135871960-a54ab496-c8a0-421c-b05a-8689ca9e037e.PNG)

I noticed that there are six columns representing the popuation percentage from different reaces. The columns include the percent symbol %. So I removed the percent symbol % from each of the race columns (Hispanic, White, Black, Native, Asian, and Pacific). Then I saved the resulting in teh data frame *us_census* and viewed to check the change.

![4](https://user-images.githubusercontent.com/89553126/135872559-549e6830-7af4-4951-b59d-ce989dd80120.PNG)

The Income column also includes a $ symbol along with the number representing median income for the state. Therefore, I removed the $ from the Income column, saved the results to *us_census* and viewed the data.

![5](https://user-images.githubusercontent.com/89553126/135874590-5857c886-00c0-48ea-be23-3f63987e867a.PNG)

The GenderPop column held both male and female population counts. I separate this column at the _ character to create two new columns: *male_pop* and *female_pop* and saved the results into the data frame *us_census*. I did this to it would be easier to read and analyze the data.


![6](https://user-images.githubusercontent.com/89553126/135874919-7b785203-1fd6-4cbf-9e23-a667c2b71de2.PNG)

Afterwards, I cleaned the male and female population coumns since the columns contained extra characters M and F, respectively.

![7](https://user-images.githubusercontent.com/89553126/135875163-5bfade5f-b457-42ca-9260-54416ff06325.PNG)

I then updated the data types of the columns. I noticed that now that the symbols are removed, a lot of the columns are now numeric but the data type for these columns are still *chr*, or characters. So, I converted all these columns into numeric data types.

![8](https://user-images.githubusercontent.com/89553126/135875688-a1a432aa-1e51-4a32-b215-f30ab2be5728.PNG)

I then took a second look back to the colums Hispanic, White, Black, Native, Asian and Pacific. The columns represeted the population percentage for each race. To maake any desired calculations easier, the coumns should represent percentages in decimal form. Therefore, I updated the values of these cooumns to be in decimal form.

![9](https://user-images.githubusercontent.com/89553126/135876127-657ea070-e646-4aed-bfd8-324058bb1e52.PNG)

I then checked if duplicate rows are present in the dataset and viewed the results in a table to get a count of the duplicated rows.

![10](https://user-images.githubusercontent.com/89553126/135876510-db54bb62-562f-4c7e-8e8b-9e2d411a044c.PNG)

**TRUE means that there is duplicated data present**

![12](https://user-images.githubusercontent.com/89553126/135877016-536bdb29-2e1f-4aa4-99ba-c278b6748746.PNG)

The code told me that duplicates were present so since there are duplicates I updated the *us_ccensus* data frame with only unique/distinct rows.

![11](https://user-images.githubusercontent.com/89553126/135876749-78154b18-5dfd-4c96-8789-02a64410e594.PNG)

Afterwards, I wanted to confirm that there were no more duplicated rows in *us_census*.

![13](https://user-images.githubusercontent.com/89553126/135877350-8abb695f-e42d-400e-bc98-a66bc741d186.PNG)

![14](https://user-images.githubusercontent.com/89553126/135877430-f8df35e8-2e8f-4270-8079-8f688fd0252c.PNG)

I viewed the data frame one last time to ensure everything was cleaned and ready for analysis. Afterwards I concluded that yes, the data frame was cleaned and ready for future analysis when needed.
