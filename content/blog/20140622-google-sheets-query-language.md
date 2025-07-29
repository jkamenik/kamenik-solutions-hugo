---
title: 'Google Sheets Query Language'
date: 2014-06-22
lastmod: 2014-06-22

# Keywords help in classifying content
keywords:
  - Google Sheets Query Language
  - Google
  - Google Sheets
  - Query Language
---

A while back, my wife and I started keeping a budget. We need something very easy that shows us where we are every moment. Also, to ensure that it is not something we "forget" it must be something that we manually enter.

I created a Google Form in order to allow us to capture the receipts. The form dumps into a Google Spreadsheet. I then use a Pivot Table and the Google Query Language to create a Chart. In this post I will cover the entire process.

<!--more-->

## Step 1: Create a form

1. Create a google form
2. Add the following fields
3. "Company" - text- required
4. "Date" - date - required (don't include time)
5. "Amount" - text - required (add a "number" validation)
6. "Category" - list - required. We added the following
7. Other / Unknown
8. Baby Supplies
9. Car
10. Entertainment
11. Gas
12. Groceries
13. Home
14. Medical
15. Pet Supplies
16. Restaurants / Fast Food
17. "Comment" - paragraph
18. Choose response destination
19. Choose a "New Spreadsheet"
20. Send the form to yourself and anyone else that needs to enter receipts

At this point you have a Form which submits to a Spreadsheet. I recommend bookmarking the link in your smart-phone so that it is easy and quick to add receipts right after your purchases.

## Step 2: Pivot

Form usually records into a sheet called "Form Responses" which I assume here.

1. Select "Form Responses"
2. Select Data -> Pivot table report...
3. Rows - Add "Category"
4. Values - Add "Amount”

Now you should have a two column table. On the left are the categories. On the right is the sum of all the values of that category.

## Step 3: Google Query

In order to chart the budget vs the actual spending we need to create another table.

1. Insert a sheet named Budget.
2. Label the columns: Category, Budget, Actual, Query
3. Copy all the categories to column A
4. Add the budgeted amount to column B
5. Add the following to column C
6. `=if(isna(C2), 0, C2)`
7. Add the following query to column D
8. ` =QUERY('Pivot Table'!A:B, "select B where A='"&A2&"'","")`
9. `#NA` means that are no receipts for the category and can safely be ignored.
10. Copy and paste cell C2 and D2 to the rest of the cells in the column
11. Google will change the internal references (A2, and C2) to the correct cell name, so you don't have to.

The Google Query Language is defined [here](https://developers.google.com/chart/interactive/docs/querylanguage). It is a good read to see all the power of this language, but I am only going to explain the parts that we need.

### Query

`QUERY` takes three arguments: range of values, query string, and optional headers. I am going to explain them in reverse.

The headers are guessed if nothing is provided. This would cause the query to take two cells, which is not the behavior I wanted. By adding "" it removes the header.

The query string tells google what data we are selecting into the cell. In our simple example it is a direct value select using a conditional. This is because the column order may not be the same in both sheets. "select B" means to choose the "B" from whatever rows match the query. "where A='"&A2&"'" means to limit the rows returned to those where the value of cell A matches the value of A2 in this sheet. The "&" is the string concat operator.

The range of values tells Google what it is allowed to look at. We use the 'Sheet'!Col:Col form in order to select data from another sheet. We only provide the columns A and B because we want to look at all rows.

### ISNA

Charts cannot deal with non-number columns. Since the query can produce a non-number output (`#N/A`) we need to add an additional level of processing.

`isna` takes a cell and returns if that cell is `#N/A`.

`if` take a boolean, a true value, and a false value. If the first argument is true then the true value is returned. If the first argument is false then the false value is returned.

## Step 4: Chart

Charts can only take numbers and they can only accept contiguous cells. A, B, and C are the columns that we want to chart.

1. Insert -> Chart
2. Data range: Budget!A1:C14
3. Use row 1 as headers
4. Chart type: Bar chart
5. Add a chart title

## Step 5: Publish

The point of this document is to know where your money is going quickly. In order to make it easy publish the document. This will make google convert the document into a HTML version which is easily viewed in your smart phone. The chart will even be convert to an image.

1. File -> Publish to the web...
2. Check "Automatically republish when changes are made"
3. Copy the link
4. Send to link to anyone that needs to be kept informed about the budget
