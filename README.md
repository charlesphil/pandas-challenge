# Pandas-Challenge: Charles Phil Week 4 Homework (PYMOLI)

## Three Trends

### Trend One: Gender Trends

![Trend One](Images\trend_1_1.png)

![Trend One](Images\trend_1_2.png)

The very first thing I noticed was that the player base that have purchased at least one item is largely male, accounting for 84% of all players. Additionally, the majority of players that buy more than one item are also largely male. That being said, it is interesting to note that while **total** purchases between genders is largely skewed toward males, the average amount spent per gender is actually higher by female players, at $4.47 compared to $4.07. It may be worthwhile to try to increase purchases made by female players if their average purchases stay high. The Other / Non-Disclosed category is unfortunatey too small to make any meaningful conclusion.

### Trend Two: Age Trends

![Trend Two](Images\trend_2_1.png)

![Trend Two](Images\trend_2_2.png)

When it comes to ages, the playerbase is as I would expect, with the majority of players being somewhere around 15-24 years old. The purchases are also as I would expect, with a total purchase value coming from that age range. That being said, it is curious to see an increase in the average purchase value per person in the 35-39 age bracket. It may be useful to try to target that age demographic if they continue to spend money for items at the same average amount.

### Trend Three: Item Trends

![Trend Two](Images\trend_3_1.png)

![Trend Two](Images\trend_3_2.png)

When it comes to the items, the most purchased items are actually quite different from the items that are most profitable. Excluding "Final Critic," "Oathbreaker," and "Fiery Glass Crusader," there are a number of items that are most frequently purchased that do not show up in the top 5 most profitable items. If the company were to increase the prices of the most purchased items, they would easily see a marked increase in profit just from the volume of purchases alone.

## Explanation of notebook

### Note on additional dependency

In my dependencies and setup cell, I imported numpy to use later on to make a quick array of numbers. Everything else in the first cell remains the same as the initial notebook file.

### Player Count

![Player Count](Images\player_count.png)

After importing the necessary modules, I found the number of unique players (based on their screen name, or "SN") and found the length of the unique array to get the count. I then displayed the count in a new summary data frame.

### Purchasing Analysis (Total)

![Purchasing Analysis](Images\purchasing_analysis.png)

Continuing on, I found the number of unique items by repeating what I did for unique players on the item column. Then I found the mean of all prices, counted the total number of purchases (which can be done on any column, as the number of purchases is equivalent to the number of rows in the dataset), and found the total sum of all purchases by adding up all prices from each purchase. I formatted the average and total prices prior to putting all values together in a summary data frame. 

### Gender Demographics

![Gender Demographics](Images\gender_demographics.png)

I initally went about this problem by first obtaining a sub data frame for each gender, and then counting the unique players in each and storing those values for later calculation. However, I wanted to experiment with some methods from the pandas library and changed my approach. I instead decided to drop all duplicates in the screen name column to have only a data frame that held the unique players and their purchase information. Because I am being asked to strictly find demographic information, I didn't have to worry about needing to use any of the item information. 

I then counted the number of values for each gender, renamed the resulting value counts column to "Gender," and actually set the output to a new data frame in itself. I then calculated the percentage by dividing by all unique players and multiplied that by 100 to then be formatted as a percentage. The result would then be stored into a new column in the new data frame.

### Purchasing Analysis (Gender)

![Gender Analysis](Images\gender_analysis.png)

I used a groupby method to group the dataset by gender. Within that, I counted each gender to obtain the total number of purchases made by each gender. Within each gender, I found the average price of each gender's purchases and mapped a format function on the column to get the result as a dollar. I did the same thing when I found the sum for each purchase value for each gender.

I created a loop function to go through each gender, as I needed to obtain a new data frame based on each gender and the group by screen names *within* those genders. The reason why this was necessary is because we needed to find the sum purchase values of only those players who identified as the corresponding gender, and then find the mean of the purchase values to store in a new data frame. The reason for creating the new data frame is to set the collected mean values up and categorize them by gender for later concatenation. 

To create the analysis table I concatenated all collected results and renamed the columns appropriately.

### Age Demographics

![Age Demographics](Images\age_demographics.png)

Using numpy, I created bins from 9.9 to 44.9 in increments of 5. I then find the minimum and maximum age values and attach those values in the appropriate spots to finish off the bin. After making the labels to match the bins, I cut the values into the unique players data frame I made from the gender demographics cell and counted the values. I then made the summary data frame and set the index values to be the age labels. After inserting the count into the summary data frame, I calculated the percentage out of the total number of unique players and mapped the result with the a formatting function to obtain the percentage.

### Purchasing Analysis (Age)

![Age Analysis](Images\age_analysis.png)

Much of the methods used in this cell are identical to the gender analysis cell. The difference here was to cut the age bins into our purchase data so that we can obtain a count of transactions based on age brackets. I find the mean and sum prices in the same manner as I did gender.

Similar to the gender analysis, I made a loop to obtain sub data frames based on the player's age bracket, and then grouped by the player screen names to obtain the sum and mean of each player's purchase values. I then concatenated and formatted the result in the same manner as the gender analysis table.

### Top Spenders

![Top Spenders](Images\top_spenders.png)

I needed to group by the players in order to get the number of purchases made by each player. The mean method would then show the mean value of purchases made by each player, and the sum method for total purchase value made by each player.

I then concatenate into the summary table and sort in descending order based on the total purchase value. I opted to format the dollar values after finishing the summary table because the sort would not have worked on string values had I formatted the values before sorting.

### Most Popular Items

![Popular Items](Images\popular_items.png)

I created a new data frame based on the Item ID, Item Name, and Price columns from the dataset. After grouping on the Item ID **and** Item Name, I was able to count how many times each item was bought and obtain the mean price of each item, along with the total value purchased. 

I concatenate and rename the columns appropriately into a summary table and sort in descending order on the count to sort by the most bought items. I format the price and values after sorting in order to have the summary table be ready to use again in the following cell.

### Most Profitable items

![Profitable Items](Images\profitable_items.png)

Using the pre-formatted summary table from the previous cell, I instead sort the values on the Total Purchase Value in descending order and store it in a new data frame. Then I format this newly sorted data frame.