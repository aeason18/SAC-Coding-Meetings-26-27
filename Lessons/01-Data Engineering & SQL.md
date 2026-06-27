# Lesson 1: Data Engineering & SQL

[Data](https://www.pro-football-reference.com/years/2024/passing.htm) <br>

## Lesson Summary
Today, you will add more data to your existing database and learn some basic SQL. <br>

Open Docker and start your container, then open TablePlus and navigate to the table you created in the last lesson. Before you add more data, you need to add a year to each row in your current dataset. Locate the SQL button in the top left of TablePlus. When you press it, a new tab called **SQL Query** should appear. To run something in SQL, you highlight the lines you want to run and press **Run Current**. Once you're in the tab, you can type out and run something like this to create a new column: <br>

```
ALTER TABLE your_table 
ADD season INT; 
```

In the above SQL, the first line tells the computer what table you want to alter, and the second line tells the computer that you want to add a column called **season** that contains ints. Next, to put data in the column, you can run this: <br>  

```
UPDATE qb_data
SET season = 2025;
```

Now, if you go back to your table and refresh (Ctrl + R), you should see your new column attached to the right side of your table. <br>

Once you are done with that, create a CSV using this [data](https://www.pro-football-reference.com/years/2024/passing.htm) as you did in the last lesson. right-click on your table in the **Tables** tab on the left, select import from CSV, and before you import, in the top right select **Match Columns by Name - Case insensitive**. If any columns are labeled as **Do not import** when they should NOT be, or are out of order, manually assign the columns. When finished with that, press import. The season column should have many new NULL values. To fix this, you can run this: <br>

```
UPDATE qb_data
SET season = 2024
WHERE season IS NULL;
```
Now refresh, you should have an extended table!

### Basic SQL
Let's go over some basic SQL you can use to navigate your table in TablePlus. If you wanted to find only a specific player's rows, you can run something like this: <br>

```
SELECT * 
FROM qb_data 
WHERE qb_data."Player" = 'Bryce Young';
```

If you wanted to get only players who meet a certain threshold, you can use something like this:  

```
SELECT * 
FROM qb_data 
WHERE qb_data."Yds" > 4500;
```
