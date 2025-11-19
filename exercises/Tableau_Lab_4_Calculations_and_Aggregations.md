# Tableau Lab 4: Understanding Calculations and Aggregations

**Course:** Data Analytics & Visualization  
**Software:** Tableau Desktop Public Edition  
**Dataset:** Vacation_Rentals.csv  
**Estimated Time:** 90-120 minutes  
**Difficulty:** Beginner to Intermediate

---

## 📋 Table of Contents

1. [Learning Objectives](#learning-objectives)
2. [Prerequisites](#prerequisites)
3. [What You'll Learn](#what-youll-learn)
4. [Understanding Calculations vs. Aggregations](#understanding-calculations-vs-aggregations)
5. [Part 1: Setup and Data Connection](#part-1-setup-and-data-connection)
6. [Part 2: Row-Level Calculations](#part-2-row-level-calculations)
7. [Part 3: Aggregate Calculations](#part-3-aggregate-calculations)
8. [Part 4: Understanding Aggregation Types](#part-4-understanding-aggregation-types)
9. [Part 5: The Order Matters: Aggregate vs. Non-Aggregate](#part-5-the-order-matters-aggregate-vs-non-aggregate)
10. [Part 6: Building a Complete Analysis Dashboard](#part-6-building-a-complete-analysis-dashboard)
11. [Challenge Exercises](#challenge-exercises)
12. [Submission Requirements](#submission-requirements)
13. [Troubleshooting Guide](#troubleshooting-guide)

---

## 🎯 Learning Objectives

By the end of this lab, you will be able to:

- Understand the difference between row-level and aggregate calculations
- Create basic calculated fields in Tableau
- Apply different aggregation functions (SUM, AVG, COUNT, MIN, MAX)
- Recognize when Tableau automatically aggregates data
- Understand why the order of operations matters in calculations
- Build calculated fields that combine multiple measures
- Create meaningful business metrics from raw data
- Avoid common calculation pitfalls

---

## 📚 Prerequisites

**Required Software:**
- **Tableau Desktop Public Edition** (free version)
  - Download: [https://public.tableau.com/app/discover](https://public.tableau.com/app/discover)
  - Make sure you have the latest version installed

**Required Dataset:**
- **Vacation_Rentals.csv** (provided by your instructor)
  - This dataset contains rental information for vacation properties
  - Each row represents one rental reservation

**Basic Tableau Skills You Should Know:**
- How to connect to CSV files
- How to drag fields to Rows and Columns
- How to create basic visualizations
- Understanding of dimensions (blue pills) vs. measures (green pills)

**Official Documentation (Keep These Open!):**
- **Main Help:** [https://help.tableau.com/current/pro/desktop/en-us/default.htm](https://help.tableau.com/current/pro/desktop/en-us/default.htm)
- **Calculations Overview:** [https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields.htm](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields.htm)
- **Aggregation:** [https://help.tableau.com/current/pro/desktop/en-us/calculations_aggregation.htm](https://help.tableau.com/current/pro/desktop/en-us/calculations_aggregation.htm)
- **Aggregate Functions:** [https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_aggregate_create.htm](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_aggregate_create.htm)

---

## 🎓 What You'll Learn

**The Big Picture:**

Calculations are the heart of data analysis in Tableau. They let you create new insights from your existing data. In this lab, you'll learn TWO fundamental types of calculations:

1. **Row-Level Calculations** - Work on individual rows of data
   - Example: Calculating the number of nights for each rental
   - Example: Calculating the total cost for each reservation

2. **Aggregate Calculations** - Combine multiple rows into summary values
   - Example: Finding the total revenue across all rentals
   - Example: Calculating the average rental price per property

**Why This Matters:**

Understanding when to use each type of calculation is CRITICAL. Using the wrong type can give you completely incorrect results, even if your formula looks right!

---

## 🔍 Understanding Calculations vs. Aggregations

Before we dive in, let's understand the fundamental difference.

### What is a Row-Level Calculation?

**Definition:** A calculation that operates on each individual row of your data.

**Example from everyday life:**
Imagine you have a grocery receipt. For each item, you want to calculate: `Price × Quantity = Total`

- Item 1: Apples, $2 × 3 = $6
- Item 2: Bananas, $1 × 5 = $5
- Item 3: Oranges, $3 × 2 = $6

Each item gets its own calculation. This is row-level.

**In Tableau:** The formula `[Price] * [Quantity]` calculates once per row.

---

### What is an Aggregate Calculation?

**Definition:** A calculation that combines multiple rows into a single value.

**Example from everyday life:**
Using the same grocery receipt, you want to know your total spending:

`SUM(Item Totals) = $6 + $5 + $6 = $17`

You're combining (aggregating) all the individual items into ONE number. This is aggregation.

**In Tableau:** The formula `SUM([Price] * [Quantity])` first calculates each row, then sums them.

---

### The Critical Difference

Here's where it gets tricky and why ORDER MATTERS:

**Scenario:** You want to calculate the average price per item.

**WRONG Way (leads to incorrect results):**
```
AVG([Price]) / AVG([Quantity])
```
This averages prices separately from quantities, then divides.

**RIGHT Way:**
```
SUM([Price] * [Quantity]) / SUM([Quantity])
```
This multiplies first (row-level), then aggregates.

We'll explore this more in Part 5!

---

## Part 1: Setup and Data Connection

### Exercise 1.1: Connecting to the Vacation Rentals Dataset

Let's get started!

**Step 1: Open Tableau Desktop Public Edition**

1. Launch Tableau from your computer
2. You'll see the Start page with connection options

**Step 2: Connect to Your CSV File**

1. On the left side under "Connect," find the **"To a File"** section
2. Click on **"Text file"**
3. Navigate to where you saved **Vacation_Rentals.csv**
4. Select the file and click **"Open"**

**Step 3: Examine the Data Source Page**

You should now see the Data Source page. Let's verify everything:

1. At the top, you'll see "Vacation_Rentals.csv" as your connection
2. Below that is a preview of your data in a table

**Your data has these columns:**
- **Rental Property** - Name of the vacation rental (e.g., "112-Asbury Atoll")
- **First** - Guest's first name
- **Last** - Guest's last name
- **Start** - Rental start date
- **End** - Rental end date
- **Discount** - Discount amount in dollars
- **Rent** - Base rental price
- **Tax per Night** - Tax charged per night

**Step 4: Verify Data Types**

Look at the icons above each column name:

- **Abc (text icon)** should be on: Rental Property, First, Last
- **📅 (calendar icon)** should be on: Start, End
- **# (number icon)** should be on: Discount, Rent, Tax per Night

**If any data type is wrong:**
1. Click the icon above the column name
2. Select the correct data type

**Important:** Start and End should be recognized as dates. If they're not:
1. Click the Abc icon above "Start"
2. Select **"Date"**
3. Repeat for "End"

**Step 5: Understand Your Data**

Take a moment to look at the data:
- Each row = one rental reservation
- Same property can appear multiple times (different guests, different dates)
- Some rentals have discounts, some don't
- Rents and taxes vary by property and rental

📖 **Reference:** [Connect to a Text File](https://help.tableau.com/current/pro/desktop/en-us/examples_text.htm)

---

### Exercise 1.2: Initial Data Exploration

Before creating calculations, let's explore what we have.

**Step 1: Create Your First Worksheet**

1. At the bottom of the screen, click on **"Sheet 1"**
2. You're now in the worksheet view
3. Right-click on "Sheet 1" at the bottom
4. Select **"Rename Sheet"**
5. Name it: **"Data Overview"**

**Step 2: See Your Data Pane**

On the left, you'll see the **Data pane** with:

**Dimensions** (blue section):
- First
- Last
- Rental Property
- Start (date)
- End (date)

**Measures** (green section):
- Discount
- Rent
- Tax Per Night
- Latitude (generated)
- Longitude (generated)
- Number of Records (generated)

**Understanding Dimensions vs. Measures:**
- **Dimensions** = Categories, labels, dates (things you group by)
- **Measures** = Numbers you can calculate with (add, average, etc.)

**Step 3: How Many Rentals?**

Let's see how much data we have:

1. Find **"Number of Records"** at the bottom of Measures
2. Drag it to the **Text** card on the Marks shelf (center area)
3. You should see: **6**

This means we have 6 rental reservations in our dataset.

**Step 4: View the Raw Data**

To see all the details:
1. At the bottom of your worksheet, look for a small table icon
2. Click the dropdown next to "Data Overview"
3. Select **"View Data"**
4. A window will pop up showing all your rows

You can see all 6 rentals with their complete information. Close this window when done.

**Step 5: Quick Property Analysis**

Let's see which properties we have:

1. Clear your current view (click the eraser icon in toolbar)
2. Drag **"Rental Property"** to Rows
3. Drag **"Number of Records"** to Text

**What you should see:**
- 112-Asbury Atoll: 2 rentals
- 155-Beach Breeze: 2 rentals
- 207-Beach Breeze: 2 rentals

This tells us we have 3 different properties, each with 2 bookings.

---

## Part 2: Row-Level Calculations

Row-level calculations work on each individual row of data. They're perfect for creating new fields from existing data where you need a calculation for EACH record.

### Concept: What Are Row-Level Calculations?

**Key Characteristics:**
- Calculate once per row
- Don't use aggregation functions (no SUM, AVG, etc.)
- Can use basic math operators: `+`, `-`, `*`, `/`
- Can use row-level functions: `IF`, `CONTAINS`, `DATE`, etc.
- The result is a new field at the row level

**When to Use Row-Level Calculations:**
- Calculating a value specific to each transaction/row
- Transforming existing fields (e.g., converting units)
- Creating categories or flags based on row values

---

### Exercise 2.1: Calculating Number of Nights

**Business Question:** How many nights is each rental? We need to calculate the difference between check-in and check-out dates.

**Step 1: Create a New Worksheet**

1. Click the new worksheet icon at the bottom (or press Ctrl+M / Cmd+M)
2. Rename it: **"Nights Calculation"**

**Step 2: Create Your First Calculated Field**

1. Right-click in the empty space of the Data pane (left side)
2. Select **"Create Calculated Field..."**
3. A calculation editor window will open

**Understanding the Calculation Editor:**

The editor has three main parts:
- **Name box** at the top (where you name your field)
- **Formula box** in the middle (where you write your calculation)
- **Function reference** on the right (list of available functions)

**Step 3: Write the Calculation**

1. In the name box at top, type: **Number of Nights**

2. In the formula box, type:

```
DATEDIFF('day', [Start], [End])
```

**Understanding This Formula:**

- `DATEDIFF` = A function that calculates the difference between two dates
- `'day'` = We want the difference in days (could also be 'month', 'year', etc.)
- `[Start]` = The check-in date (field name in brackets)
- `[End]` = The check-out date

**How to Use the Function Reference:**

1. On the right side, you'll see a dropdown that says "All"
2. Change it to **"Date"** to see only date functions
3. Find **DATEDIFF** in the list
4. Click on it to see the syntax at the bottom

**Step 4: Validate Your Formula**

1. Look at the bottom of the calculation window
2. You should see: **"The calculation is valid"** ✓ in green
3. If you see an error in red, check your spelling and brackets

**Common Errors:**
- Forgetting brackets around field names
- Misspelling field names
- Wrong quote marks (use single quotes for 'day')

4. Click **OK** to save

**Step 5: See Your New Field**

1. Look in the Data pane on the left
2. Your new field **"Number of Nights"** appears under Measures
3. Notice it has a green color and an = sign (indicates it's calculated)

**Step 6: Use Your Calculation**

Let's see it in action:

1. Drag **"Rental Property"** to Rows
2. Drag **"Last"** (guest last name) to Rows (to the right of Rental Property)
3. Drag **"Number of Nights"** to Text

**What you should see:**

A table showing each rental and how many nights it was for:
- Some rentals are 7 nights
- Some are 14 nights
- Some are 6 nights

**Step 7: Verify Your Calculation**

Let's manually check one:
1. Look at the first row: Asbury Atoll, Slessor
2. The data shows Start: 2-Dec, End: 9-Dec
3. Count the days: Dec 2, 3, 4, 5, 6, 7, 8, 9 = 7 days
4. Your calculation should show 7 ✓

**Why is this Row-Level?**

Because it calculates separately for EACH booking. Each reservation gets its own number of nights calculated.

📖 **Reference:** [Create a Calculated Field](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_create.htm)

---

### Exercise 2.2: Calculating Gross Rent (Before Discount)

**Business Question:** What is the total rent charged before any discount is applied?

This is another row-level calculation because we need to calculate it for each reservation.

**Step 1: Create New Worksheet**

1. New worksheet: **"Gross Rent Calculation"**

**Step 2: Create the Calculation**

1. Right-click in Data pane → **"Create Calculated Field..."**
2. Name: **Gross Rent**
3. Formula:

```
[Rent] + ([Tax per Night] * [Number of Nights])
```

**Understanding This Formula:**

- `[Rent]` = The base rental price
- `[Tax per Night]` = Tax charged for one night
- `[Number of Nights]` = Our previously created field
- `* ` = Multiplication
- We multiply tax by nights, then add to base rent

**Why the Parentheses?**

Order of operations matters! Without parentheses:
```
[Rent] + [Tax per Night] * [Number of Nights]
```
Would calculate: Tax × Nights first, then add Rent ✓ (actually correct here)

But to be EXPLICIT and avoid confusion, use parentheses:
```
[Rent] + ([Tax per Night] * [Number of Nights])
```
This clearly shows: "multiply Tax by Nights, THEN add to Rent"

**Pro Tip:** When in doubt, use parentheses for clarity!

4. Verify the calculation is valid (green checkmark)
5. Click **OK**

**Step 3: Test Your Calculation**

1. Drag **"Rental Property"** to Rows
2. Drag **"Last"** to Rows (to the right)
3. Drag **"Gross Rent"** to Text

**Step 4: Manually Verify One Row**

Let's check Slessor at Asbury Atoll:
- Rent: $1,500
- Tax per Night: $15
- Number of Nights: 7
- Calculation: $1,500 + ($15 × 7) = $1,500 + $105 = $1,605 ✓

**Step 5: Format for Currency**

The numbers appear, but they don't look like money. Let's fix that:

1. Right-click on **"Gross Rent"** in the Data pane
2. Select **"Default Properties"** → **"Number Format"**
3. Choose **"Currency (Custom)"**
4. Set Decimal places to **0** (whole dollars)
5. Click **OK**

Now your numbers should show as: $1,605

**Why is this Row-Level?**

Each reservation has its own gross rent calculated individually. We're not combining multiple rentals yet.

---

### Exercise 2.3: Calculating Net Revenue (After Discount)

**Business Question:** What is the actual revenue after applying discounts?

**Step 1: Create New Worksheet**

1. New worksheet: **"Net Revenue Calculation"**

**Step 2: Create the Calculation**

1. Create Calculated Field
2. Name: **Net Revenue**
3. Formula:

```
[Gross Rent] - [Discount]
```

**Understanding This Formula:**

- `[Gross Rent]` = Our previously calculated field
- `[Discount]` = The discount amount
- We subtract discount from gross rent

**Building on Previous Calculations:**

Notice we're using `[Gross Rent]`, which is itself a calculated field! Tableau lets you nest calculations like this. The order is:

1. First, Tableau calculates `Number of Nights`
2. Then, it calculates `Gross Rent` (using Number of Nights)
3. Finally, it calculates `Net Revenue` (using Gross Rent)

4. Click **OK**

**Step 3: Apply Currency Format**

1. Right-click **"Net Revenue"** in Data pane
2. Default Properties → Number Format → Currency (Custom)
3. Set to 0 decimal places
4. Click **OK**

**Step 4: Compare All Three Calculations**

Let's see them side by side:

1. Clear your sheet
2. Drag **"Rental Property"** to Rows
3. Drag **"Last"** to Rows
4. Drag **"Gross Rent"** to Text
5. Drag **"Discount"** to Text (to the right of Gross Rent)
6. Drag **"Net Revenue"** to Text (to the right of Discount)

**What You Should See:**

A table showing:
- Gross Rent (total before discount)
- Discount (amount discounted)
- Net Revenue (final amount)

**Step 5: Verify the Math**

Check Slessor at Asbury Atoll:
- Gross Rent: $1,605
- Discount: $150
- Net Revenue: $1,605 - $150 = $1,455 ✓

**Key Insight:**

All three fields we created (Number of Nights, Gross Rent, Net Revenue) are ROW-LEVEL calculations. Each one calculates independently for each reservation.

📖 **Reference:** [Functions in Tableau](https://help.tableau.com/current/pro/desktop/en-us/functions.htm)

---

## Part 3: Aggregate Calculations

Now we move to a completely different type of calculation: AGGREGATE calculations. These combine multiple rows into summary values.

### Concept: What Are Aggregate Calculations?

**Key Characteristics:**
- Combine multiple rows into ONE value
- Use aggregation functions: SUM, AVG, COUNT, MIN, MAX, etc.
- Wrap fields in aggregation functions
- The result depends on what's in your view

**When to Use Aggregate Calculations:**
- Finding totals across multiple records
- Calculating averages
- Counting occurrences
- Finding minimums or maximums

---

### Exercise 3.1: Total Revenue Across All Rentals

**Business Question:** What is our total revenue across all vacation rentals?

**Step 1: Create New Worksheet**

1. New worksheet: **"Total Revenue"**

**Step 2: The Simple Way (Let Tableau Aggregate)**

First, let's see how Tableau automatically aggregates:

1. Drag **"Net Revenue"** to Text
2. Look at what appears in the view

**What You See:**

The pill on the Marks shelf says: **SUM(Net Revenue)**

Notice:
- Tableau automatically wrapped it in SUM
- The number shown is the TOTAL across all 6 rentals
- You didn't have to do anything - Tableau aggregated automatically!

**Understanding What Happened:**

When you drag a measure to a view without any dimensions, Tableau automatically aggregates it. By default, most measures use SUM.

**Step 3: Change the Aggregation**

Let's see what other aggregations do:

1. Right-click on **"SUM(Net Revenue)"** on the Marks shelf
2. Hover over **"Measure"**
3. You'll see options: Sum, Average, Median, Count, etc.

**Try These:**

**Average:**
1. Select **"Average"**
2. The pill changes to **AVG(Net Revenue)**
3. The number changes - this is now the average revenue per rental

**Count:**
1. Select **"Count"**
2. The pill changes to **CNT(Net Revenue)**
3. This counts how many rentals have a revenue value (should be 6)

**Minimum:**
1. Select **"Minimum"**
2. Shows the smallest revenue amount

**Maximum:**
1. Select **"Maximum"**
2. Shows the largest revenue amount

**Step 4: Return to Sum**

1. Right-click the pill → Measure → **Sum**
2. We're back to total revenue

**Why This Is Aggregate:**

We took 6 individual rental revenues and COMBINED them into one number. That's aggregation!

---

### Exercise 3.2: Creating an Aggregate Calculated Field

**Business Question:** What is the average revenue per night across all our rentals?

This requires both aggregation AND calculation.

**Step 1: Create New Worksheet**

1. New worksheet: **"Revenue Per Night"**

**Step 2: Create the Calculation**

1. Create Calculated Field
2. Name: **Average Revenue Per Night**
3. Formula:

```
SUM([Net Revenue]) / SUM([Number of Nights])
```

**Understanding This Formula:**

- `SUM([Net Revenue])` = Total revenue across all rentals
- `SUM([Number of Nights])` = Total nights across all rentals
- We divide total revenue by total nights

**Why We Need SUM:**

We want: (Total $ from all rentals) ÷ (Total nights from all rentals)

Not: (Average $ per rental) ÷ (Average nights per rental)

Those would give very different answers!

**Critical Concept - Aggregate vs. Non-Aggregate:**

This is CORRECT:
```
SUM([Net Revenue]) / SUM([Number of Nights])
```

This would be WRONG:
```
[Net Revenue] / [Number of Nights]
```

The second formula would calculate per row first, then try to aggregate, giving incorrect results. We'll explore this more in Part 5!

4. Click **OK**

**Step 3: Format as Currency**

1. Right-click **"Average Revenue Per Night"** in Data pane
2. Default Properties → Number Format → Currency
3. Keep 2 decimal places (we want cents for per-night rate)
4. Click **OK**

**Step 4: Display the Result**

1. Drag **"Average Revenue Per Night"** to Text

**What You Should See:**

A single number showing the average revenue per night across all properties and all rentals.

**Step 5: Verify Manually**

Let's calculate by hand:

1. Create a quick view with:
   - Drag **"SUM(Net Revenue)"** to Text
   - Note the total (should be around $8,400)

2. Create another with:
   - Drag **"SUM(Number of Nights)"** to Text
   - Note the total (should be around 55 nights)

3. Calculate: $8,400 ÷ 55 = approximately $152 per night

Does your **Average Revenue Per Night** match? ✓

**Why This Is Aggregate:**

We're using SUM functions, which combine multiple rows. The calculation happens at the aggregate level, not row-by-row.

📖 **Reference:** [Aggregate Calculations](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_aggregate_create.htm)

---

### Exercise 3.3: Revenue by Property (Aggregate with Dimensions)

**Business Question:** How much revenue does each property generate?

Now we'll use aggregation WITH dimensions to see breakdowns.

**Step 1: Create New Worksheet**

1. New worksheet: **"Revenue by Property"**

**Step 2: Build the View**

1. Drag **"Rental Property"** to Rows
2. Drag **"Net Revenue"** to Columns

**What Tableau Does Automatically:**

- It shows **SUM(Net Revenue)** for EACH property
- Each bar represents the total for that property
- This is aggregation at the property level

**Step 3: Add More Detail**

Let's see individual rentals too:

1. Drag **"Last"** (guest name) to Rows (to the right of Rental Property)

**What Changed:**

- Now you see each individual rental
- The SUM is still applied, but at a more detailed level
- Each guest's rental shows separately

**Step 4: Understanding Level of Detail**

The **view level of detail** is determined by the dimensions in your view:

- **Only Property** → Aggregate per property (3 values)
- **Property + Guest** → Aggregate per property per guest (6 values)

The aggregation (SUM) adapts to match your view's detail level!

**Step 5: Add a Grand Total**

Let's add a total across all properties:

1. Click **"Analysis"** in the top menu
2. Select **"Totals"** → **"Show Row Grand Totals"**

A "Grand Total" row appears at the bottom showing the sum across all properties.

**Step 6: Sort by Revenue**

Let's see which property generates most revenue:

1. Remove "Last" from Rows (drag it off)
2. Click the sort descending icon in the toolbar (or click the sort icon on the axis)

Now properties are ranked by revenue!

---

## Part 4: Understanding Aggregation Types

Tableau provides many aggregation functions. Let's explore the most common ones.

### Exercise 4.1: Exploring Different Aggregations

**Step 1: Create New Worksheet**

1. New worksheet: **"Aggregation Comparison"**

**Step 2: Create a Comparison Table**

We'll create a table showing different aggregations of the same field:

1. In Measures, find **Measure Names** (special field at bottom)
2. Drag **"Measure Names"** to Rows

3. Now we'll add Net Revenue multiple times with different aggregations:
   - This is a special technique for comparison

Actually, let's do this a simpler way:

1. Clear the sheet
2. Create a text table to compare

**Step 3: Build Comparison Manually**

We'll create calculated fields for each aggregation type to understand them:

**SUM - Total**
1. Create Calculated Field: **Total Revenue (Sum)**
2. Formula: `SUM([Net Revenue])`
3. This adds all revenues together

**AVG - Average**
1. Create Calculated Field: **Average Revenue (Mean)**
2. Formula: `AVG([Net Revenue])`
3. This calculates the mean

**COUNT - Count Records**
1. Create Calculated Field: **Count of Rentals**
2. Formula: `COUNT([Net Revenue])`
3. This counts how many non-null values exist

**COUNTD - Count Distinct**
1. Create Calculated Field: **Count Unique Properties**
2. Formula: `COUNTD([Rental Property])`
3. This counts unique property names

**MIN - Minimum**
1. Create Calculated Field: **Lowest Revenue**
2. Formula: `MIN([Net Revenue])`
3. This finds the smallest value

**MAX - Maximum**
1. Create Calculated Field: **Highest Revenue**
2. Formula: `MAX([Net Revenue])`
3. This finds the largest value

**Step 4: Display All Aggregations**

1. Create a text table:
   - Drag all your new calculated fields to Text
   - Stack them vertically

2. Format them:
   - Right-click each → Format
   - Set appropriate number formats

**What Each Aggregation Tells You:**

- **SUM**: Total revenue across all rentals
- **AVG**: Typical rental revenue
- **COUNT**: Number of rental records
- **COUNTD**: Number of unique properties
- **MIN**: Smallest single rental revenue
- **MAX**: Largest single rental revenue

### Common Aggregation Functions Reference

| Function | What It Does | Example Use |
|----------|--------------|-------------|
| **SUM** | Adds all values | Total sales, total quantity |
| **AVG** | Calculates mean | Average price, average score |
| **MEDIAN** | Finds middle value | Median income, median age |
| **COUNT** | Counts non-null records | Number of orders |
| **COUNTD** | Counts unique values | Number of customers |
| **MIN** | Finds smallest value | Lowest price, earliest date |
| **MAX** | Finds largest value | Highest price, latest date |
| **STDEV** | Standard deviation | Data spread, volatility |
| **VAR** | Variance | Data variability |
| **ATTR** | Returns value if all same | Single value aggregation |

📖 **Reference:** [List of Aggregations](https://help.tableau.com/current/pro/desktop/en-us/calculations_aggregation.htm)

---

## Part 5: The Order Matters: Aggregate vs. Non-Aggregate

This is one of the MOST IMPORTANT concepts in Tableau calculations. Getting this wrong leads to incorrect results!

### The Problem: When Does Calculation Happen?

**Two Different Approaches:**

**Approach 1: Aggregate First, Then Calculate**
```
SUM([Field A]) / SUM([Field B])
```

**Approach 2: Calculate First, Then Aggregate**
```
SUM([Field A] / [Field B])
```

**Are these the same?** NO! They can give VERY different results!

---

### Exercise 5.1: Demonstrating the Difference

**Scenario:** Calculate the average rent per night for each property.

**Step 1: Create New Worksheet**

1. New worksheet: **"Calculation Order Demo"**

**Step 2: Create METHOD 1 - Aggregate First**

1. Create Calculated Field
2. Name: **Avg Rate Method 1 (Correct)**
3. Formula:

```
SUM([Rent]) / SUM([Number of Nights])
```

This says:
- Add up all rent amounts
- Add up all nights
- Divide total rent by total nights

4. Click **OK**

**Step 3: Create METHOD 2 - Calculate First**

1. Create Calculated Field
2. Name: **Avg Rate Method 2 (Incorrect)**
3. Formula:

```
SUM([Rent] / [Number of Nights])
```

This says:
- For each row, calculate rent ÷ nights
- Add up all those individual calculations

4. Click **OK**

**Step 4: Compare the Results**

1. Drag **"Rental Property"** to Rows
2. Drag **"Avg Rate Method 1 (Correct)"** to Text
3. Drag **"Avg Rate Method 2 (Incorrect)"** to Text (next to Method 1)

**What You Should See:**

The numbers are DIFFERENT! Method 2 gives wrong results!

**Step 5: Understand WHY They're Different**

Let's trace through the math for one property manually.

**Example: 155-Beach Breeze**

This property has 2 rentals:
- Rental 1: Rent = $1,300, Nights = 7
- Rental 2: Rent = $1,400, Nights = 7

**Method 1 (CORRECT):**
```
SUM([Rent]) / SUM([Number of Nights])
= (1300 + 1400) / (7 + 7)
= 2700 / 14
= $192.86 per night ✓
```

**Method 2 (WRONG):**
```
SUM([Rent] / [Number of Nights])
= SUM(1300/7, 1400/7)
= SUM(185.71, 200.00)
= $385.71
```

Wait, what? Method 2 gave us $385.71 per night?? That's way too high!

**What Went Wrong:**

Method 2 calculated the rate for each rental separately ($185.71 and $200), then ADDED those rates together. That's nonsensical - you can't add rates!

**The Right Way:**

Method 1 calculated the total rent ($2,700) and total nights (14), then divided to get the true average rate ($192.86).

---

### Exercise 5.2: Real-World Example - Profit Margin

This example really drives home why order matters.

**Scenario:** Calculate overall profit margin.

**Business Terms:**
- **Profit** = Net Revenue - Original Rent
- **Profit Margin** = Profit / Net Revenue × 100%

**Step 1: Create Profit Calculation**

1. Create Calculated Field
2. Name: **Profit**
3. Formula:

```
[Net Revenue] - [Rent]
```

Note: This is row-level (no aggregation)

4. Click **OK**

**Step 2: Create CORRECT Profit Margin**

1. Create Calculated Field
2. Name: **Profit Margin (Correct)**
3. Formula:

```
SUM([Profit]) / SUM([Net Revenue])
```

4. Click **OK**

**Step 3: Create INCORRECT Profit Margin**

1. Create Calculated Field
2. Name: **Profit Margin (Incorrect)**
3. Formula:

```
AVG([Profit] / [Net Revenue])
```

4. Click **OK**

**Step 4: Compare**

1. New worksheet: **"Profit Margin Comparison"**
2. Drag **"Profit Margin (Correct)"** to Text
3. Format as Percentage
4. Drag **"Profit Margin (Incorrect)"** to Text
5. Format as Percentage

**What You Should See:**

Different percentages! The incorrect version gives misleading results.

**Why:**

- **Correct:** (Total Profit) ÷ (Total Revenue) = Overall margin
- **Incorrect:** Average of individual margins = Meaningless for business

**Real-World Impact:**

If you reported the wrong profit margin to your boss, you could make bad business decisions about pricing, discounts, or which properties to invest in!

---

### The Golden Rule

**When calculating ratios, rates, or percentages:**

✅ **DO:** Aggregate the numerator and denominator separately, then divide
```
SUM([Numerator]) / SUM([Denominator])
```

❌ **DON'T:** Calculate the ratio first, then aggregate
```
AVG([Numerator] / [Denominator])  ← Usually wrong!
SUM([Numerator] / [Denominator])  ← Usually wrong!
```

**Exceptions:**

Sometimes you DO want to calculate first, such as:
- When you want to sum individual subtotals
- When each row's calculation is meaningful on its own
- When explicitly modeling row-by-row effects

But for rates, ratios, and percentages: **aggregate first, calculate second!**

📖 **Reference:** [Understanding Calculations](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_understand.htm)

---

## Part 6: Building a Complete Analysis Dashboard

Now let's combine everything you've learned into a comprehensive dashboard.

### Exercise 6.1: Creating Multiple Analysis Views

**Goal:** Build 4 different views that we'll combine into a dashboard.

**View 1: Revenue by Property**

1. New worksheet: **"Property Revenue Bar"**
2. Drag **"Rental Property"** to Rows
3. Drag **"Net Revenue"** to Columns
4. Sort descending
5. Drag **"Net Revenue"** to Color
6. Format colors: Blue color scheme

**View 2: Occupancy Analysis**

1. New worksheet: **"Nights by Property"**
2. Drag **"Rental Property"** to Rows
3. Drag **"Number of Nights"** to Columns
4. Change to **SUM**
5. Add labels: Drag "SUM(Number of Nights)" to Label
6. Sort descending

**View 3: Discount Impact**

1. New worksheet: **"Discount Analysis"**
2. Drag **"Rental Property"** to Rows
3. Drag **"Gross Rent"** to Columns
4. Drag **"Net Revenue"** to Columns (next to Gross Rent)
5. This creates a side-by-side comparison
6. Add a reference line:
   - Right-click on axis → Add Reference Line
   - Set to average
   - This shows which properties are above/below average

**View 4: Guest Summary Table**

1. New worksheet: **"Guest Details"**
2. Drag **"Rental Property"** to Rows
3. Drag **"Last"** to Rows (guest name)
4. Drag these to Text (in order):
   - Start (date)
   - End (date)
   - Number of Nights
   - Gross Rent
   - Discount
   - Net Revenue
5. Format all currency fields

---

### Exercise 6.2: Building the Dashboard

**Step 1: Create a New Dashboard**

1. At the bottom, click the **"New Dashboard"** icon (looks like a grid)
2. Or press **Ctrl+D** / **Cmd+D**

**Step 2: Configure Dashboard Size**

On the left side, you'll see Dashboard pane:

1. Under "Size," select **"Desktop Browser (1000 x 800)"**
2. This ensures it fits on most screens

**Step 3: Add Worksheets**

From the Dashboard pane on the left, you'll see your worksheets listed:

1. Drag **"Property Revenue Bar"** to the top of the dashboard
2. Drag **"Nights by Property"** below it (or next to it)
3. Drag **"Discount Analysis"** to the bottom left
4. Drag **"Guest Details"** to the bottom right

Tableau will automatically tile them.

**Step 4: Add a Title**

1. From the left sidebar, drag **"Text"** object to the very top
2. Double-click it
3. Type:

```
Vacation Rental Analysis Dashboard
Comparing Revenue, Occupancy, and Discounts Across Properties
```

4. Format it:
   - Select the text
   - Make it bold
   - Increase font size to 14
   - Center align
5. Click **OK**

**Step 5: Add Interactivity**

Make the dashboard interactive:

1. Click on **"Property Revenue Bar"** view in your dashboard
2. Click the dropdown arrow that appears in the upper right
3. Select **"Use as Filter"**

Now clicking on a property bar will filter all other views!

**Step 6: Format for Polish**

1. For each worksheet in the dashboard:
   - Click dropdown arrow
   - Uncheck **"Title"** if redundant
   - Or edit title to be more concise

2. Adjust sizes:
   - Hover between views until you see resize arrows
   - Drag to adjust

3. Add borders:
   - Click on a view
   - Click **Format** → **Borders**
   - Add drop shadow or border lines

**Step 7: Add Explanatory Text**

1. Drag another **Text** object below your title
2. Add context:

```
Click on any property to filter all views. This dashboard shows:
• Total revenue and occupancy by property
• Impact of discounts on gross vs net revenue
• Individual guest rental details

Key Metrics:
• Total Revenue: [Add your calculated total]
• Average Nights per Rental: [Add your average]
• Average Revenue per Night: [Add your calculation]
```

**Step 8: Add a Legend**

If your views have colors:
1. The legend should automatically appear
2. If not, check "Show" for legends in worksheet dropdown

---

### Exercise 6.3: Creating a Summary Sheet

Let's create one master summary sheet with key metrics.

**Step 1: New Worksheet**

1. New worksheet: **"Key Metrics Summary"**

**Step 2: Create KPI Calculations**

Create these calculated fields:

**Total Properties**
```
COUNTD([Rental Property])
```

**Total Rentals**
```
COUNT([Last])
```

**Total Revenue**
```
SUM([Net Revenue])
```

**Total Nights Rented**
```
SUM([Number of Nights])
```

**Average Discount**
```
AVG([Discount])
```

**Average Revenue Per Rental**
```
SUM([Net Revenue]) / COUNT([Last])
```

**Step 3: Build the KPI View**

1. Drag all these metrics to Text
2. Stack them vertically
3. Format each appropriately (currency for money, numbers for counts)

**Step 4: Make it Visual**

1. Change Mark Type to **"Shape"**
2. Add **Measure Names** to Rows
3. Add **Measure Values** to Text
4. This creates a nice vertical list

5. Format:
   - Increase text size
   - Bold the numbers
   - Add labels

**Step 5: Add to Dashboard**

1. Go back to your dashboard
2. Add this "Key Metrics Summary" to the top or side
3. Make it prominent

📖 **Reference:** [Build a Dashboard](https://help.tableau.com/current/pro/desktop/en-us/dashboards_create.htm)

---

## Challenge Exercises

Test your skills with these challenges!

### Challenge 1: Effective Discount Rate

**Question:** Calculate the effective discount rate (Discount ÷ Gross Rent) for each property. Which property offers the highest average discount rate?

**Hints:**
- Create a calculated field: `[Discount] / [Gross Rent]`
- This is row-level
- Then aggregate by property
- Format as percentage

**Expected Output:** A bar chart showing average discount rate by property.

---

### Challenge 2: Revenue Per Square Foot

**Scenario:** Assume these property sizes:
- 112-Asbury Atoll: 1,200 sq ft
- 155-Beach Breeze: 1,000 sq ft
- 207-Beach Breeze: 1,500 sq ft

**Question:** Calculate revenue per square foot for each property.

**Hints:**
- Create a parameter for square footage
- Create a calculated field mapping properties to their sizes
- Calculate: Revenue / Square Feet
- Show per property

**Expected Output:** A table showing revenue per square foot.

---

### Challenge 3: Peak Season Analysis

**Question:** December 16-23 is considered "peak season" (holidays). Create a calculated field that identifies peak season rentals and compare average revenue for peak vs. non-peak.

**Hints:**
- Use IF statement: `IF [Start] >= #12/16/2020# THEN "Peak" ELSE "Off-Peak" END`
- Create a bar chart comparing average revenue
- Use color to distinguish peak vs. non-peak

**Expected Output:** Comparison visualization of peak vs. off-peak revenue.

---

### Challenge 4: Multi-Night Discount Analysis

**Question:** Do longer stays get better discounts per night? Calculate discount per night and compare for rentals of different lengths.

**Hints:**
- Calculate: `[Discount] / [Number of Nights]`
- Create bins or groups for night ranges (6-7 nights, 14+ nights)
- Compare average discount per night across groups

**Expected Output:** Chart showing relationship between stay length and discount per night.

---

## Submission Requirements

### What to Submit

**1. Tableau Workbook (.twbx)**

1. Save your work:
   - **File** → **Save As**
   - Choose **"Tableau Packaged Workbook (.twbx)"**
   - This includes your data
2. Name it: **LastName_FirstName_Lab4_Calculations.twbx**

**2. Documentation (PDF or Word)**

Create a document with:

**Part A: Screenshots**
- Screenshot of "Nights Calculation" worksheet
- Screenshot of "Gross Rent Calculation" worksheet
- Screenshot of "Revenue Per Night" worksheet
- Screenshot of "Calculation Order Demo" showing the difference
- Screenshot of your final dashboard
- Screenshot of at least one challenge (if attempted)

**Part B: Written Explanations**

Answer these questions (3-4 sentences each):

1. **Explain the difference between row-level and aggregate calculations.** Give an example of when you'd use each.

2. **Why does order matter?** Explain why `SUM([A]) / SUM([B])` is different from `SUM([A] / [B])`.

3. **Aggregation functions:** Name three aggregation functions and explain what each does.

4. **Calculated fields:** Describe the process of creating a calculated field in Tableau.

5. **Real-world application:** Describe a business scenario where you would need to use calculated fields and aggregations. What would you calculate?

**Part C: Key Findings**

Based on your analysis, document 3-5 insights:
- Which property generates the most revenue?
- What is the average revenue per night across all properties?
- Do longer stays receive larger discounts?
- Which property has the highest occupancy (total nights rented)?
- Any other interesting patterns?

**Part D: Calculation Documentation**

List all calculated fields you created:
- Field name
- Formula
- What it calculates
- Whether it's row-level or aggregate

**3. Naming Convention**
- Workbook: **LastName_FirstName_Lab4_Calculations.twbx**
- Documentation: **LastName_FirstName_Lab4_Documentation.pdf**

---

## Troubleshooting Guide

### Common Issues and Solutions

**Issue: "Cannot mix aggregate and non-aggregate arguments"**

**Cause:** You're trying to combine aggregated and non-aggregated fields incorrectly.

**Example of the Error:**
```
[Gross Rent] / SUM([Number of Nights])
```

**Solution:** Either aggregate both or neither:
```
SUM([Gross Rent]) / SUM([Number of Nights])  ← Correct
```
OR
```
[Gross Rent] / [Number of Nights]  ← Correct (row-level)
```

---

**Issue: Calculation is valid but gives weird results**

**Cause:** Probably an order-of-operations issue.

**Solution:**
1. Check if you should aggregate first or calculate first
2. Use parentheses to control order
3. Test with a small example manually
4. Create intermediate calculated fields to see step-by-step

---

**Issue: Numbers don't look right (scientific notation or too many decimals)**

**Cause:** Formatting hasn't been applied.

**Solution:**
1. Right-click field in Data pane
2. Default Properties → Number Format
3. Choose Currency, Number, Percentage, etc.
4. Set decimal places

---

**Issue: "The calculation contains errors"**

**Common Causes:**
- Misspelled field name
- Forgot brackets around field names `[Field Name]`
- Wrong quote marks (use single quotes for strings: `'text'`)
- Missing parenthesis
- Wrong function name

**Solution:**
1. Read the error message carefully (it tells you what's wrong)
2. Check spelling of field names
3. Verify all brackets are matched
4. Use the function reference on the right to verify syntax

---

**Issue: SUM doesn't make sense for my field**

**Cause:** The field might be better as a different aggregation.

**Solution:**
1. Right-click the field in the view
2. Measure → choose different aggregation
3. Or set Default Properties → Aggregation in Data pane

---

**Issue: Getting NULL or * in results**

**Cause:** 
- Missing data
- Aggregation returning multiple different values (for ATTR)

**Solution:**
- Check your data for NULLs
- Use different aggregation (MIN, MAX instead of ATTR)
- Filter out NULL values if appropriate

---

**Issue: My calculation worked in one sheet but not another**

**Cause:** The level of detail in your view affects how aggregations work.

**Solution:**
1. Check what dimensions are in each view
2. Aggregations calculate at the level defined by dimensions in view
3. You might need a Level of Detail (LOD) expression (covered in next lab)

---

### Getting Help

**Tableau's Built-In Help:**
1. Press **F1** while in Tableau
2. Right-click any element → **"Describe"** to see how it's calculated
3. Use the **Function Reference** in the calculation editor

**Official Tableau Resources:**
- [Calculation Functions](https://help.tableau.com/current/pro/desktop/en-us/functions.htm)
- [Calculation Syntax](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_formulas.htm)
- [Understanding Aggregation](https://help.tableau.com/current/pro/desktop/en-us/calculations_aggregation_understanding.htm)

**Contact Your Instructor:**
- Include screenshots of your error
- Share the formula causing issues
- Describe what you're trying to accomplish

---

## Key Formulas Reference

### Row-Level Calculations Created

```
Number of Nights
DATEDIFF('day', [Start], [End])
```

```
Gross Rent
[Rent] + ([Tax per Night] * [Number of Nights])
```

```
Net Revenue
[Gross Rent] - [Discount]
```

```
Profit
[Net Revenue] - [Rent]
```

### Aggregate Calculations Created

```
Average Revenue Per Night
SUM([Net Revenue]) / SUM([Number of Nights])
```

```
Profit Margin (Correct)
SUM([Profit]) / SUM([Net Revenue])
```

```
Total Revenue (Sum)
SUM([Net Revenue])
```

```
Average Revenue (Mean)
AVG([Net Revenue])
```

---

## Additional Learning Resources

**Official Tableau Documentation:**
- **Main Help:** [https://help.tableau.com/current/pro/desktop/en-us/default.htm](https://help.tableau.com/current/pro/desktop/en-us/default.htm)
- **Calculated Fields:** [https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields.htm](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields.htm)
- **Functions Reference:** [https://help.tableau.com/current/pro/desktop/en-us/functions.htm](https://help.tableau.com/current/pro/desktop/en-us/functions.htm)
- **Aggregation Guide:** [https://help.tableau.com/current/pro/desktop/en-us/calculations_aggregation.htm](https://help.tableau.com/current/pro/desktop/en-us/calculations_aggregation.htm)

**Video Tutorials:**
- Search "Tableau Calculated Fields Tutorial" on YouTube
- Tableau's official channel has excellent explanations

**Practice:**
- Apply these concepts to Sample - Superstore dataset
- Try creating calculations on your own data

---

## Glossary

**Aggregate Calculation:** A calculation that combines multiple rows of data into a single value using functions like SUM, AVG, COUNT.

**Aggregation:** The process of combining multiple data values into a summary value.

**Calculated Field:** A new field you create using a formula that operates on existing fields in your data.

**Dimension:** A categorical field that defines the structure of your data (what you group by).

**Formula:** The expression you write in a calculated field using operators and functions.

**Function:** A pre-built operation Tableau provides (like SUM, AVG, IF, DATEADD).

**Level of Detail:** The granularity at which calculations are performed, determined by the dimensions in your view.

**Measure:** A quantitative field containing numeric values that can be aggregated.

**Operator:** Symbols used in calculations (+, -, *, /, etc.).

**Row-Level Calculation:** A calculation that operates on each individual row of data before any aggregation.

**Syntax:** The rules for how to write formulas correctly in Tableau.

---

## Tips for Success

1. **Start Simple:** Build calculations step-by-step. Create intermediate fields if needed.

2. **Test Your Work:** Always verify calculations with manual math on a small example.

3. **Use Descriptive Names:** Name calculated fields clearly so you remember what they do.

4. **Comment Your Intent:** Use the description field in calculated fields to note what they do.

5. **Understand Before Aggregating:** Know whether you need row-level or aggregate calculations BEFORE you start.

6. **Watch for Automatic Aggregation:** Tableau adds SUM automatically - make sure that's what you want!

7. **Learn From Errors:** Error messages are helpful - read them carefully.

8. **Practice Order of Operations:** When in doubt about calculation order, use parentheses.

9. **Format Everything:** Apply number formats to make your work look professional.

10. **Build a Library:** Keep a document of useful calculations you can reference later.

---

## Congratulations!

You've completed Lab 4 on Calculations and Aggregations! This is foundational knowledge for data analysis in Tableau.

**Key Takeaways:**

✅ Row-level calculations work on individual records  
✅ Aggregate calculations combine multiple records  
✅ Order matters: aggregate first, then calculate (for ratios)  
✅ Tableau automatically aggregates measures  
✅ Different aggregations answer different questions  
✅ Always verify your calculations manually  

**Next Steps:**

- Practice on other datasets
- Experiment with more complex calculations
- Learn about Level of Detail (LOD) expressions (Lab 5)
- Explore table calculations
- Build real-world dashboards with calculated fields

---

**Lab Created By:** Dr. Lee  
**Last Updated:** 2025  
**Questions?** Contact your instructor or visit office hours

**Happy Calculating!** 🎉📊
