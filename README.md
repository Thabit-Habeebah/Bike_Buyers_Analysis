# BIKE_ BUYERS_ANALYSIS

## Project Overview
This project shows welfare of a quite number of individuals as to the income they earn,their level of education,marital status,the number of cars and houses they own among others.

This analysis gives us an insight into the relationship between the number bike each individual purchase and the distance to and from their place of work,the average income base on their level of education and many others.

## Data Source and Content
The main source of ths data is Kaggle [Download Here] (https://www.kaggle.com/datasets)

This data contains the following columns:
   * Customer ID: This an identification number which is peculiar to each person.
   * Marital Status
   * Income : This indicates the income earned by each individual which ranges between #30,000 and #170,000.
   * Children: This contains the total number of children each individual has.
   * Education : This shows whether the indidvivual holds a Bachelor's degree, Graduate degree(Not Specified),just a college or high school student.
   * Occupation : It shows the occupation of each individual such as a manual or skilled labour,clerical staff,a manager or a professional in his field of work.
   * Home_Owner and Cars : It indicates whether such individual possesses a house and a car or not.
   * Commute Distance : It tells us the distance to and from his/her place of work.
   * Region : This contain information on th region each individual lived.
   * Age : The age ranges between 25 and 89.
   * Age_Range: This a calculated column created from the "Age" column so as to make categorization easier.
   * Income_ Range : This is also a calculated column created from "Income" column so as to make categorization and comparison easier.

## Tools Used

 * Microsoft Excel

   * For data loading and cleaning.

 * Structure Query Language (SQL)

    * For data querying and data cleaning.
 * Micosoft Power BI

     * For data visualization

##  Data Cleaning 
This involves the following steps;
  1. Data loading : This has to do with loading the dataset into excel for analysis.
  2. Removing duplicates : The very next thing to do after loading your data is to remove duplicates so as to make your analysis accurate.I used ALT+H+I+O to adjust the coulmns then AT+A+M to remove duplicate.
  3. Handling missing data: I made use of Power BI as well as SQL to fill in blank spaces.

## Exploratory Data Analysis 

The main aim of EDA is to gain a deeper understanding of the data. It answers questions like ;

1. The total number of regions taken into consideration ?
2. The total number of People that own a house ?
3. Is there any relationship between the distance to and from place of work and owning a car ?
4. The percentage of female to male
5. The total number of people that earn below #100,000 and also own a car
6. The percentage of people in each occupation and their age range

## Data Analysis

Some basic lines of code used in SQL for data querying 

1. Total number of region

```

SELECT Region, COUNT(Region) No_of_Region
FROM bike_buyers
GROUP BY Region

```

![image](https://github.com/user-attachments/assets/3e0df997-cf37-4140-a90c-8e9baea7a6d9)

2. Total number of females in each region

```

SELECT Region, COUNT(Gender) No_of_Females
FROM bike_buyers
WHERE Gender LIKE 'Female'
GROUP BY Region,Gender

```

![image](https://github.com/user-attachments/assets/ae1e7e57-cfeb-4c14-94f2-456b9e5a2079)

3. Calculated column

```

ALTER TABLE bike_buyers
ADD Income_Range VARCHAR(50)

UPDATE bike_buyers
SET Income_Range =
CASE 
WHEN Income BETWEEN 9000 AND 50000 THEN 'Low'
WHEN Income BETWEEN 51000 AND 100000 THEN 'Middle'
WHEN Income BETWEEN 101000 AND 150000 THEN 'High'
ELSE 'Very High'
END

```

4. Total number of people that own a house by age range

```

SELECT Age_Range,COUNT(Home_Owner) No_of_house_owner
FROM bike_buyers
WHERE Home_Owner LIKE 'Yes'
GROUP BY Age_Range

```

![image](https://github.com/user-attachments/assets/4cbb9753-9da2-4e33-acd3-42ad79820dc4)

4. Number of people that own a car by 

```

SELECT Income_Range, COUNT(Cars) No_of_car_owners
FROM bike_buyers
WHERE Cars > 0 
GROUP BY Income_Range

```

![image](https://github.com/user-attachments/assets/88185405-8b02-4d94-8fef-8728c94a442d)

##   Data Visualization

![Bike Buyers Dashboard 1_page-0001](https://github.com/user-attachments/assets/23a31200-32de-425d-b82f-d09c56466e90)


## Conclusion
From the analysis above, it has shown that the total number of people taken into consideraton is 985. Out of this 985, we have 487 females and 498 males both with an average age of 44 years. The total regions included are Europe, North America and Pacific with North America having the highest population which is 508
