# Tableau Lab 5: Level of Detail (LOD) Calculations

**Course:** Data Analytics & Visualization  
**Software:** Tableau Desktop Public Edition  
**Dataset:** Chapter_05_Loans.csv  
**Estimated Time:** 120-150 minutes  
**Difficulty:** Intermediate

---

## 📋 Table of Contents

1. [Learning Objectives](#learning-objectives)
2. [Prerequisites](#prerequisites)
3. [What You'll Learn](#what-youll-learn)
4. [Understanding Level of Detail](#understanding-level-of-detail)
5. [Part 1: Setup and Data Connection](#part-1-setup-and-data-connection)
6. [Part 2: FIXED Level of Detail Calculations](#part-2-fixed-level-of-detail-calculations)
7. [Part 3: INCLUDE Level of Detail Calculations](#part-3-include-level-of-detail-calculations)
8. [Part 4: EXCLUDE Level of Detail Calculations](#part-4-exclude-level-of-detail-calculations)
9. [Part 5: Building a Complete Dashboard](#part-5-building-a-complete-dashboard)
10. [Challenge Exercises](#challenge-exercises)
11. [Submission Requirements](#submission-requirements)
12. [Troubleshooting Guide](#troubleshooting-guide)

---

## 🎯 Learning Objectives

By the end of this lab, you will be able to:

- Understand what "level of detail" means in Tableau
- Identify when to use LOD calculations vs. regular calculations
- Create FIXED LOD calculations to analyze data at specific granularity
- Use INCLUDE LOD calculations to add dimensions to your analysis
- Apply EXCLUDE LOD calculations to remove dimensions from aggregations
- Combine multiple LOD calculations in a single visualization
- Build an interactive dashboard using LOD calculations

---

## 📚 Prerequisites

**Required Software:**
- **Tableau Desktop Public Edition** (free version)
  - Download: [https://public.tableau.com/app/discover](https://public.tableau.com/app/discover)
  - Make sure you have the latest version installed

**Required Dataset:**
- **Chapter_05_Loans.csv** (provided by your instructor)
  - This dataset contains loan information for members of a financial institution
  - Each row represents a monthly snapshot of a loan

**Basic Tableau Skills You Should Know:**
- How to connect to CSV files
- How to drag fields to Rows and Columns
- How to create basic bar charts and line graphs
- Basic understanding of dimensions vs. measures
- How to create simple calculated fields

**Official Documentation (Keep These Open!):**
- **Main Help:** [https://help.tableau.com/current/pro/desktop/en-us/default.htm](https://help.tableau.com/current/pro/desktop/en-us/default.htm)
- **LOD Calculations:** [https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod.htm](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod.htm)
- **Understanding LOD:** [https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_overview.htm](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_overview.htm)

---

## 🎓 What You'll Learn

**The Big Picture:**

Level of Detail (LOD) calculations are one of Tableau's most powerful features. They let you answer questions like:

- "Has this customer EVER had a problem?" (even if we're looking at just recent data)
- "How does this store compare to the company average?" (comparing different levels)
- "What's the average number of products per customer?" (aggregating at different levels)

Think of LOD calculations as giving you X-ray vision into your data - you can see through different layers of detail at the same time.

---

## 🔍 Understanding Level of Detail

Before we dive into creating LOD calculations, let's understand what "level of detail" means.

### Three Types of Detail in Tableau

**1. Data Level of Detail (Row-Level)**
- This is the most detailed level - what each individual row represents
- In our loans dataset: **one row = one monthly snapshot of one loan for one member**
- Example row: "On May 1, 2020, Member #5864 had a Gold Card with a balance of $2,292"

**2. View Level of Detail (Visualization-Level)**
- This is determined by the dimensions you put in your view
- Example: If you put "State" on Columns, the view level is "per state"
- Example: If you put "State" and "Portfolio" in your view, the level is "per state per portfolio"

**3. Calculated Level of Detail (LOD Calculations)**
- This is a custom level you define in a calculation
- You explicitly tell Tableau what level to calculate at
- This can be **different from** what's visible in your view!

### Why LOD Calculations Matter

**The Problem They Solve:**

Imagine you want to show average loan balance by state, but you ALSO want to show how many unique members each state has. The problem? Balance is measured monthly (many rows per member), but you want to count each member only once.

**Without LOD:** You'd get confusing or wrong results  
**With LOD:** You can precisely control what level each calculation works at

---

## Part 1: Setup and Data Connection

### Exercise 1.1: Connecting to the Loans Dataset

Let's get started by loading your data into Tableau.

**Step 1: Open Tableau Desktop Public Edition**

1. Launch Tableau Desktop Public Edition from your computer
2. You'll see the Start page with connection options on the left

**Step 2: Connect to the CSV File**

1. On the left side of the Start page, under "Connect," look for **"To a File"** section
2. Click on **"Text file"**
   - Note: CSV files are considered "text files" in Tableau
3. Navigate to where you saved **Chapter_05_Loans.csv**
4. Select the file and click **"Open"**

**Step 3: Verify Your Data Connection**

You should now see the **Data Source** page. Let's verify everything loaded correctly:

1. At the top, you should see "Chapter_05_Loans.csv" as your connection
2. Below that, you'll see a grid showing your data
3. Look at the column headers - you should see:
   - Date
   - Portfolio
   - Loan Type
   - Loan Number
   - Balance
   - Original Balance
   - Open Date
   - Member ID
   - Member Name
   - Credit Score
   - Age
   - State

**Step 4: Check Data Types**

This is important! Make sure Tableau interpreted your data types correctly:

1. Look at the icons above each column name:
   - **Calendar icon (📅)** = Date field (should be on "Date" and "Open Date")
   - **# icon** = Number field (should be on Balance, Credit Score, Age, etc.)
   - **Abc icon** = Text/String field (should be on Portfolio, Loan Type, Member Name, State)

2. If any data type is wrong, click the icon above the column name and select the correct type

**Important:** Member ID should be a **String (Abc)**, not a number, because we don't want to do math with ID numbers!

**Step 5: Examine Sample Data**

Take a moment to understand what you're looking at:

- Each row represents a **monthly snapshot** of a loan
- The same member can appear multiple times (different months or different loans)
- The same loan can appear multiple times (one row per month)

📖 **Reference:** [Connect to a Text File](https://help.tableau.com/current/pro/desktop/en-us/examples_text.htm)

---

### Exercise 1.2: Understanding Your Dataset

Before creating calculations, let's explore the data to understand it better.

**Step 1: Create Your First Worksheet**

1. At the bottom of the screen, click on **"Sheet 1"**
2. You're now in the worksheet view where you build visualizations
3. Rename this sheet:
   - Right-click on "Sheet 1" at the bottom
   - Select **"Rename Sheet"**
   - Type: **"Data Exploration"**

**Step 2: See the Data Pane**

On the left side, you'll see the **Data pane** with two sections:

**Tables** (if expanded)
- Shows your data source name

**Dimensions** (blue pills)
- Date fields
- Text fields (Portfolio, Loan Type, Member Name, State, etc.)

**Measures** (green pills)
- Number fields (Balance, Credit Score, Age, etc.)
- Generated measures (Latitude, Longitude, Number of Records)

**Step 3: Quick Data Check - How Many Records?**

Let's see how much data we're working with:

1. Find **"Number of Records"** under Measures (at the bottom)
2. Drag **"Number of Records"** to the **Text** card on the Marks shelf (center area)
3. You should see a large number appear - this is how many rows are in your dataset

**Step 4: Quick Data Check - How Many Unique Members?**

Now let's count unique members:

1. Find **"Member ID"** under Dimensions
2. Drag **"Member ID"** to the view (just drop it in the middle)
3. Tableau will create a text table showing all Member IDs
4. Notice the status bar at the bottom - it shows how many marks (unique Member IDs) are in the view

**Step 5: Understanding the Time Period**

1. Create a new sheet: Click the new worksheet icon (looks like a page with +)
2. Rename it to **"Timeline Check"**
3. Drag **"Date"** to Columns
4. Drag **"Number of Records"** to Rows
5. Right-click on "Date" in Columns → select **"Month"**

You should see a line chart showing the timeline of your data. This shows you which months have loan snapshots.

**What You Should Notice:**
- Data spans from January 2020 to September 2020 (9 months)
- Some months have more records than others
- This is monthly snapshot data

---

## Part 2: FIXED Level of Detail Calculations

FIXED LOD calculations work at a level of detail that YOU specify, regardless of what's in the view. Think of them as "locked" to a specific level.

### Concept: What is FIXED?

**The Syntax:**
```
{FIXED [Dimension1], [Dimension2] : AGG([Measure])}
```

**Translation:** "Calculate this aggregation at the level of these specific dimensions, no matter what's in my view"

**Real-World Analogy:**
Imagine you're a teacher with a grade book. A FIXED calculation is like saying: "For each student (fixed at student level), what was their lowest test score?" Even if you're looking at a class average view, you still want the individual student's lowest score.

---

### Exercise 2.1: Was a Member Ever At Risk?

**Business Question:** Management has determined that any member who has EVER had a credit score below 550 is considered "at risk" and eligible for special assistance. We need to identify all members who have ever been at risk, even if their current score is above 550.

**The Challenge:**

- Credit scores change month-to-month
- A member might have been at risk in January but recovered by June
- We want to mark ALL records for that member as "Ever At Risk" = TRUE

**Step 1: Create a New Worksheet**

1. Click the new worksheet icon at the bottom (or press Ctrl+M / Cmd+M)
2. Rename it to **"At Risk Analysis"**

**Step 2: Explore Credit Score History**

Let's first see how credit scores fluctuate:

1. Drag **"Member Name"** to Rows
2. Drag **"Date"** to Columns
3. Right-click "Date" → select **"Month"**
4. Drag **"Credit Score"** to Rows (place it to the RIGHT of Member Name)
5. Right-click on "Credit Score" (the green pill on Rows) → **Measure** → **Average**

You should see a table showing average credit score per member per month.

**Step 3: Filter to See Specific Examples**

Let's look at a few members to understand the problem:

1. Click on **"Member Name"** on Rows
2. Click the dropdown arrow → **"Show Filter"**
3. In the filter that appears on the right, search for and select these members:
   - Vicki Gray
   - Charles Marshall
   - Thomas Rodriguez
4. Click **OK**

**What You Should See:**

- Some members have credit scores that fluctuate above and below 550
- If we just check current score, we'd miss their risk history
- We need a calculation that "remembers" if they were EVER at risk

**Step 4: Create the LOD Calculation**

Now let's create our FIXED calculation:

1. Right-click in the empty space of the Data pane (left side)
2. Select **"Create Calculated Field..."**
3. Name it: **Member Ever At Risk?**
4. Type this formula exactly:

```
{FIXED [Member ID] : MIN([Credit Score])} < 550
```

**Let's Break Down This Formula:**

- `{FIXED [Member ID] : MIN([Credit Score])}` 
  - Fixed at Member ID level (one value per member)
  - Find the MINIMUM credit score for that member
  - This works across ALL months for that member

- `< 550`
  - Compare that minimum to the threshold
  - Returns TRUE if minimum < 550, FALSE otherwise

5. Click **OK** to save the calculation

**Step 5: Apply the Calculation**

1. Clear your current view:
   - Click **"Clear Sheet"** (icon looks like an eraser in the toolbar)

2. Start fresh:
   - Drag **"Member Name"** to Rows
   - Drag **"Date"** to Columns → change to **"Month"**
   - Drag **"Credit Score"** to Text on the Marks card
   - Drag **"Member Ever At Risk?"** to Color on the Marks card

**Step 6: Analyze the Results**

1. Add the same filter from before (Vicki Gray, Charles Marshall, Thomas Rodriguez)

**What You Should Notice:**

- Vicki Gray: All months show FALSE (never below 550)
- Charles Marshall: All months show TRUE (even months when score was above 550!)
- Thomas Rodriguez: All months show TRUE (was below 550 in some months)

**The Power of FIXED:**

The calculation evaluated EACH member's entire history (all months) and determined their minimum credit score. Then it applied that same TRUE/FALSE result to EVERY row for that member. This is the key feature of FIXED - it calculates at the member level but returns row-level results.

📖 **Reference:** [FIXED LOD](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_fixed.htm)

---

### Exercise 2.2: Latest Balance Per Member/Loan

**Business Question:** We want to identify which records represent the most recent balance for each member's each loan. This will help us create "current status" reports.

**The Challenge:**

- Each loan has multiple monthly snapshots
- Some loans have data through September, others only through July
- We can't just filter to September - we'd lose loans that ended earlier

**Step 1: Create a New Worksheet**

1. Create a new worksheet (Ctrl+M / Cmd+M)
2. Rename it to **"Latest Balance Identifier"**

**Step 2: Explore the Problem**

Let's look at a few specific members to understand:

1. Drag **"Member Name"** to Rows
2. Drag **"Loan Number"** to Rows (place it to the right of Member Name)
   - This creates a hierarchy: Member → Loan
3. Drag **"Date"** to Columns
4. Change **"Date"** to **"Month"** (right-click → Month)
5. Drag **"Balance"** to Text

6. Filter to specific members:
   - Show filter for Member Name
   - Select: Kelly (search), Joseph (search), Gerald (search)

**What You Should Notice:**

- Some members have multiple loans (Loan Number 1, 2, etc.)
- Each loan has data for different months
- The "latest" month is different for each loan

**Step 3: Create the FIXED Calculation**

1. Create a new calculated field
2. Name it: **Latest Date Per Member/Loan**
3. Formula:

```
{FIXED [Member ID], [Loan Number] : MAX([Date])} = [Date]
```

**Understanding This Formula:**

- `{FIXED [Member ID], [Loan Number] : MAX([Date])}`
  - Fixed at Member ID AND Loan Number level
  - Find the MAXIMUM (most recent) date for that specific loan
  - Note: We need BOTH dimensions because one member can have multiple loans

- `= [Date]`
  - Compare that maximum date to each row's date
  - Returns TRUE only for rows where the row's date matches the maximum
  - Returns FALSE for all historical rows

**Why Two Dimensions?**

If we only used `[Member ID]`, we'd get the latest date across ALL of their loans, not per loan. We need to be more specific.

4. Click **OK** to save

**Step 4: Apply and Test**

1. Drag **"Latest Date Per Member/Loan"** to Color on the Marks card

**What You Should See:**

- Most cells are orange/FALSE (historical records)
- A few cells per loan are blue/TRUE (the most recent record)
- Each loan has only ONE TRUE value (its latest month)

**Step 5: Create a Filter for Latest Only**

Now let's use this to show only current balances:

1. Create a new worksheet: **"Current Balances Only"**
2. Drag **"Latest Date Per Member/Loan"** to the Filters shelf
3. Check only **"True"**
4. Click **OK**

5. Now build your view:
   - Drag **"State"** to Rows
   - Drag **"Balance"** to Columns
   - Change Balance to **SUM**

This shows total current (latest) balance by state - automatically excluding old data!

**Real-World Application:**

This technique is incredibly useful for:
- "Current status" dashboards
- Comparing first vs. last transactions
- Filtering to most recent data when data arrives at different times
- Removing duplicate records (keeping first or last)

📖 **Reference:** [Understanding LOD Calculations](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_understanding.htm)

---

### Exercise 2.3: Overall Average Comparison

**Business Question:** For each state, how does the average number of loans per member compare to the overall company average? We want to see which states have members with more loans than average.

**Step 1: Create a New Worksheet**

1. New worksheet: **"State Loan Comparison"**

**Step 2: Create the Overall Average Calculation**

First, we need to calculate the true overall average:

1. Create a new calculated field
2. Name: **Overall Average Loans Per Member**
3. Formula:

```
{FIXED : AVG([Loan Number])}
```

**Understanding This Formula:**

- `{FIXED : ...}` 
  - Fixed with NO dimensions listed
  - This is called a "table-scoped" calculation
  - Calculates across the ENTIRE dataset
  
- `AVG([Loan Number])`
  - Average loan number
  - Since loan numbers increment (1, 2, 3), the maximum equals total loans
  - The average across all members = overall average

4. Click **OK**

**Step 3: Create State Average Calculation**

Now create the state-level average:

1. New calculated field
2. Name: **State Average Loans Per Member**
3. Formula:

```
{FIXED [State], [Member ID] : MAX([Loan Number])}
```

This calculates the number of loans per member per state.

4. Click **OK**

**Step 3: Create the Final Risk Flag**

1. Create a new calculated field
2. Name: **Member Ever At Risk?**
3. Formula:

```
[Lowest Credit Score per Member] < 550
```

**Understanding This Formula:**

- This is a boolean (True/False) field.
- Because it uses the FIXED LOD, the result is stored at the member level.
- Every row for a member who has ever had a score below 550 will be marked TRUE.

4. Click **OK**

**Step 4: Create the Comparison**

Now calculate the difference:

1. New calculated field
2. Name: **Difference from Overall Average**
3. Formula:

```
AVG([State Average Loans Per Member]) - AVG([Overall Average Loans Per Member])
```

4. Click **OK**

**Step 5: Build the Visualization**

1. Drag **"State"** to Rows
2. Drag **"Difference from Overall Average"** to Columns
3. Drag **"Difference from Overall Average"** to Color

You should see a bar chart showing which states are above or below average!

**Understanding the Results:**

- Positive numbers (blue): States where members have MORE loans than average
- Negative numbers (orange): States where members have FEWER loans than average
- Zero: Exactly at average

---

## Part 3: INCLUDE Level of Detail Calculations

INCLUDE LOD calculations add dimensions to your view level of detail. Think of them as saying: "Calculate this, but also consider this other dimension, even if I'm not showing it."

### Concept: What is INCLUDE?

**The Syntax:**
```
{INCLUDE [Dimension] : AGG([Measure])}
```

**Translation:** "Calculate at the view level PLUS this additional dimension"

**Real-World Analogy:**
Imagine you're showing average class test scores by grade level (9th, 10th, 11th, 12th). But for each grade, you want to calculate considering individual students first, even though students aren't visible in your view. INCLUDE lets you do this.

---

### Exercise 3.1: Average Loans Per Member by State

**Business Question:** What is the average number of loans per member for each state? This requires calculating at the member level first, then averaging those results at the state level.

**The Challenge:**

We can't just count loans and divide by members using regular aggregations, because the view level and calculation level need to be different.

**Step 1: Create a New Worksheet**

1. New worksheet: **"Loans Per Member Analysis"**

**Step 2: Start with a Simple View**

Let's see what we're working with:

1. Drag **"State"** to Rows
2. Drag **"Member ID"** to Rows (to the right of State)
   - This shows members within each state
3. Drag **"Loan Number"** to Text
4. Right-click on "Loan Number" → **Measure** → **Maximum**

You can see how many loans each member has.

**Step 3: Create the INCLUDE Calculation**

Now let's calculate loans per member, but at a level that includes members even when they're not in the view:

1. Create a new calculated field
2. Name: **Number of Loans Per Member**
3. Formula:

```
{INCLUDE [Member ID] : COUNTD([Loan Number])}
```

**Understanding This Formula:**

- `{INCLUDE [Member ID] : ...}`
  - Include Member ID in the calculation level
  - Even if Member ID isn't in the view, it's used for calculation
  
- `COUNTD([Loan Number])`
  - Count distinct loan numbers
  - Gives us how many unique loans per member

**Why INCLUDE Instead of FIXED?**

- FIXED would lock us to specific dimensions
- INCLUDE is more flexible - it works with whatever's already in the view PLUS the included dimension
- If we change our view (add Portfolio, for example), INCLUDE adapts automatically

4. Click **OK**

**Step 4: Build the State-Level View**

1. Clear your sheet
2. Drag **"State"** to Rows
3. Drag **"Number of Loans Per Member"** to Columns
4. Right-click on "Number of Loans Per Member" → **Measure** → **Average**

**What You Should See:**

A bar chart showing average loans per member by state!

**Step 5: Create a Geographic View**

Let's make this more visual:

1. Clear the sheet
2. Double-click on **"State"** in the Dimensions pane
   - Tableau automatically creates a map!
3. Drag **"Number of Loans Per Member"** to Color
4. Change to **Average** (right-click measure)

5. Format the colors:
   - Click on Color → **Edit Colors**
   - Choose a color palette (try "Orange-Blue Diverging")
   - Click **OK**

**What You Should See:**

A map where states are colored by average loans per member. Darker colors = more loans per member.

**Step 6: Verify Your Calculation**

Let's prove this is working correctly with a crosstab:

1. New worksheet: **"Verification Table"**
2. Drag **"State"** to Rows
3. Drag **"Member ID"** to Rows (to the right)
4. Drag **"Loan Number"** to Text
5. Change to **COUNTD** (Count Distinct)

6. Now add a summary:
   - Right-click on "Member ID" on Rows
   - Select **"Show Row Grand Totals"**

For one state, manually calculate: (sum of all loan counts) / (number of members)

Then compare to your INCLUDE calculation - they should match!

📖 **Reference:** [INCLUDE LOD](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_include.htm)

---

### Exercise 3.2: Alternative Approaches (Understanding Flexibility)

It's helpful to know there are often multiple ways to solve problems. Let's explore alternatives to understand when to use each.

**Alternative 1: Using FIXED Instead**

1. Create a new calculated field
2. Name: **Loans Per Member (FIXED Version)**
3. Formula:

```
{FIXED [State], [Member ID] : COUNTD([Loan Number])}
```

This achieves the same result but is less flexible. If you wanted to add Portfolio to your view, you'd need to update the calculation.

**Alternative 2: Using Regular Aggregations**

*   **Note:** For this specific problem (averaging a pre-calculated measure at a higher level), a reliable solution using only regular aggregations is not possible, which is why the INCLUDE LOD is the correct method. The complexity of trying to solve this without LODs demonstrates the power of the INCLUDE expression.

**When to Use Each Approach:**

- **INCLUDE**: Most flexible; adapts to view changes
- **FIXED**: When you want to lock to specific dimensions
- **Regular Aggregation**: When you want calculations that respond to filters normally (e.g., simple SUM, AVG, or COUNT)

---

## Part 4: EXCLUDE Level of Detail Calculations

EXCLUDE LOD calculations remove dimensions from your view level of detail. Think of them as saying: "Calculate this, but ignore this particular dimension."

### Concept: What is EXCLUDE?

**The Syntax:**
```
{EXCLUDE [Dimension] : AGG([Measure])}
```

**Translation:** "Calculate at the view level MINUS this dimension"

**Real-World Analogy:**
Imagine you're showing test scores by student and by test. But you want to compare each student's test score to the class average (which should NOT be broken down by student). EXCLUDE removes the student dimension to give you the class average.

---

### Exercise 4.1: Portfolio Average Credit Score Comparison

**Business Question:** For each loan type within each portfolio, how does the average credit score compare to the overall portfolio average? This helps identify which specific loan types attract higher or lower credit score customers.

**Step 1: Create a New Worksheet**

1. New worksheet: **"Credit Score Analysis"**

**Step 2: Build the Base View**

1. Drag **"Portfolio"** to Rows
2. Drag **"Loan Type"** to Rows (to the right of Portfolio)
3. Drag **"Credit Score"** to Text
4. Change to **Average**

You should see average credit score for each loan type.

**Step 3: Create the EXCLUDE Calculation**

Now let's calculate the portfolio average, excluding loan type:

1. Create a new calculated field
2. Name: **Average Credit Score Excluding Loan Type**
3. Formula:

```
{EXCLUDE [Loan Type] : AVG([Credit Score])}
```

**Understanding This Formula:**

- `{EXCLUDE [Loan Type] : ...}`
  - Remove Loan Type from the level of detail
  - Calculate at Portfolio level only
  
- `AVG([Credit Score])`
  - Average credit score
  - Now calculated per Portfolio, not per Loan Type

**Why This Matters:**

If you have Portfolio and Loan Type in your view:
- Normal AVG would calculate per Portfolio per Loan Type
- EXCLUDE removes Loan Type, so it calculates per Portfolio only

4. Click **OK**

**Step 4: Add to Your View**

1. Drag **"Average Credit Score Excluding Loan Type"** to your view
2. You'll need to add it as Text or Rows

**What You Should Notice:**

- The excluded average is the SAME for all loan types within a portfolio
- This is expected - it's the portfolio-level average
- Each loan type shows the same overall portfolio number

**Step 5: Create a Comparison Calculation**

Now let's see the difference:

1. Create a new calculated field
2. Name: **Difference from Portfolio Average**
3. Formula:

```
AVG([Credit Score]) - AVG([Average Credit Score Excluding Loan Type])
```

**Understanding This Formula:**

- `AVG([Credit Score])`
  - View-level average (per Portfolio per Loan Type)
  
- `AVG([Average Credit Score Excluding Loan Type])`
  - Portfolio-level average
  - We wrap it in AVG again because we're using it as a measure

- The difference shows how each loan type compares to its portfolio

4. Click **OK**

**Step 6: Visualize the Comparison**

1. Clear your sheet
2. Drag **"Portfolio"** to Rows
3. Drag **"Loan Type"** to Rows (right of Portfolio)
4. Drag **"Difference from Portfolio Average"** to Columns
5. Drag **"Difference from Portfolio Average"** to Color

6. Format for clarity:
   - Right-click on the axis → **"Edit Axis"**
   - Check **"Include zero"**
   - Click **OK**

7. Add a reference line at zero:
   - Click **Analytics** tab (top of left pane)
   - Drag **"Reference Line"** to the view
   - Drop it on "Table"
   - Set Value to **0**
   - Click **OK**

**What You Should See:**

- Bars showing positive values: Loan types with HIGHER than portfolio average credit scores
- Bars showing negative values: Loan types with LOWER than portfolio average credit scores
- This helps identify which products attract different credit quality customers

**Step 7: Add Context with Colors**

1. Click on Color card
2. Edit Colors
3. Choose "Orange-Blue Diverging"
4. Check "Stepped Color" and set to 3 steps
5. Click **OK**

Now it's very clear: Blue = above average, White = average, Orange = below average

📖 **Reference:** [EXCLUDE LOD](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_exclude.htm)

---

### Exercise 4.2: Understanding EXCLUDE vs. Regular Aggregation

Let's understand when EXCLUDE is necessary vs. when regular calculations work.

**Step 1: Create a Test Comparison**

1. New worksheet: **"Understanding EXCLUDE"**

**Step 2: Try Without EXCLUDE First**

1. Drag **"Portfolio"** to Rows
2. Drag **"Loan Type"** to Rows
3. Drag **"Credit Score"** to Text
4. Change to **Average** - this is the loan type average

5. Try to add another Average Credit Score:
   - Drag **"Credit Score"** to Text again
   - Change to **Average**
   - What happens? You get the same number!

**The Problem:**

When you use regular AVG in a view with Portfolio and Loan Type, Tableau calculates at that level (Portfolio + Loan Type). You can't easily get the Portfolio-only average.

**Step 3: The EXCLUDE Solution**

1. Drag your **"Average Credit Score Excluding Loan Type"** calculation to Text

Now you can see BOTH levels of detail at once!

**Key Insight:**

EXCLUDE lets you show multiple levels of aggregation in the same view, which is impossible with regular calculations alone.

---

## Part 5: Building a Complete Dashboard

### Exercise 5.0: Creating the Latest Snapshot Filter

Before building the dashboard, we need a filter to ensure we are only looking at the most recent data for each loan. Since the data is monthly snapshots, we must filter out the older records.

**Step 1: Create the Latest Date Filter Field**

1. Create a new calculated field
2. Name: **Latest Date Per Member/Loan**
3. Formula:

```
[Date] = {FIXED [Loan Number] : MAX([Date])}
```

**Understanding This Formula:**

- `{FIXED [Loan Number] : MAX([Date])}` finds the latest date for every unique loan number in the dataset.
- The outer expression `[Date] = ...` checks if the date of the current row is equal to the latest date found for that specific loan.
- This calculation returns `TRUE` for the most recent snapshot of each loan and `FALSE` for all previous snapshots.

4. Click **OK**

---

## Part 5: Building a Complete Dashboard

Now let's combine everything you've learned into a comprehensive dashboard.

### Exercise 5.1: Risk Assessment Dashboard

**Goal:** Create a dashboard that shows member risk status, current balances, and credit score analysis.

**Step 1: Create Worksheet - Risk by State**

1. New worksheet: **"Risk by State"**
2. Drag **"State"** to Rows
3. Drag **"Member Ever At Risk?"** to Columns
4. Change to **COUNTD([Member ID])**
   - This counts unique members
5. Drag **"Member Ever At Risk?"** to Color
6. Format:
   - Edit axis to show better labels
   - Edit colors: TRUE = Red, FALSE = Green

**Step 2: Create Worksheet - Current Balance by Portfolio**

1. New worksheet: **"Current Balance Distribution"**
2. Add filter: **"Latest Date Per Member/Loan"** = TRUE
3. Drag **"Portfolio"** to Rows
4. Drag **"Balance"** to Columns
5. Change to **SUM**
6. Sort descending (click sort icon in toolbar)

**Step 3: Create Worksheet - Loans Per Member Map**

1. New worksheet: **"Geographic Distribution"**
2. Double-click **"State"**
3. Drag **"Number of Loans Per Member"** to Color
4. Change to **Average**
5. Format colors appropriately

**Step 4: Create Worksheet - Credit Score Comparison**

1. Use your existing **"Credit Score Analysis"** worksheet
2. Make sure it shows the difference from portfolio average

**Step 5: Build the Dashboard**

1. Click **"Dashboard"** tab at bottom
2. Click **"New Dashboard"** icon (or press Ctrl+D / Cmd+D)
3. On the left, set size:
   - Select **"Automatic"** or **"Desktop Browser"** from dropdown

4. Drag your worksheets to the dashboard:
   - Drag **"Risk by State"** to the top
   - Drag **"Current Balance Distribution"** below it
   - Drag **"Geographic Distribution"** to the right
   - Drag **"Credit Score Analysis"** at the bottom

5. Add a title:
   - Double-click on "Dashboard 1" at top
   - Type: **"Loan Portfolio Risk Assessment"**
   - Click **OK**

6. Add interactivity:
   - For **"Geographic Distribution"**, click the dropdown arrow
   - Select **"Use as Filter"**
   - Now clicking states will filter other views!

**Step 6: Add Explanatory Text**

1. From the left sidebar, drag **"Text"** object to your dashboard
2. Place it at the very top
3. Double-click to edit
4. Type:

```
Dashboard Purpose: This dashboard uses Level of Detail calculations to analyze member risk, 
current balances, and credit score patterns. Click on states in the map to filter other views.

Key Insights:
• Red bars indicate members who have EVER been at risk (credit score < 550)
• Current balances show only the most recent snapshot for each loan
• Credit scores show how each loan type compares to portfolio average
```

5. Click **OK**

**Step 7: Format for Polish**

1. Remove unnecessary titles:
   - For each worksheet in the dashboard, click the dropdown
   - Uncheck **"Title"** if it's redundant

2. Adjust colors for consistency:
   - Make sure risk colors are intuitive (Red = Risk, Green = Safe)
   - Use consistent color schemes across views

3. Add tooltips:
   - For each worksheet, click **"Worksheet"** → **"Tooltip"**
   - Add helpful explanations

📖 **Reference:** [Build a Dashboard](https://help.tableau.com/current/pro/desktop/en-us/dashboards_create.htm)

---

## Challenge Exercises

Ready to test your skills? Try these on your own!

### Challenge 1: First-Time Borrowers

**Question:** Identify members who opened their first loan after January 1, 2019. Create a visualization showing how many first-time borrowers each state has.

**Hint:** Use a FIXED calculation to find MIN([Open Date]) per member, then compare to the threshold date.

**Expected Output:** A bar chart or map showing count of new borrowers by state.

---

### Challenge 2: High-Balance Portfolio Members

**Question:** For each portfolio, identify members whose total current balance (across all their loans) is in the top 25% for that portfolio. Show these members and their balances.

**Hints:** 
- Use Latest Date filter to get current balances only
- Use FIXED to calculate total balance per member
- Use EXCLUDE to find the 75th percentile per portfolio
- Compare member totals to portfolio percentile

**Expected Output:** A table showing Portfolio, Member Name, Total Balance, and a TRUE/FALSE indicator for top 25%.

---

### Challenge 3: Credit Score Improvement Tracker

**Question:** Calculate how many points each member's credit score has changed from their first record to their latest record. Show members with the biggest improvements.

**Hints:**
- Create two FIXED calculations: one for MIN(Date) and one for MAX(Date) per member
- Join these to get first and last credit scores
- Calculate the difference
- Filter to show only improvements (positive differences)

**Expected Output:** A ranked bar chart of members with largest credit score improvements.

---

### Challenge 4: Portfolio Performance Over Time

**Question:** For each month, show how each portfolio's average credit score compares to the overall company average credit score for that month.

**Hints:**
- Create a view with Date (Month) and Portfolio
- Calculate portfolio average per month
- Use EXCLUDE to calculate overall average per month (excluding portfolio)
- Show the difference

**Expected Output:** A line chart showing portfolio performance trends over time, with a reference line at 0.

---

## Submission Requirements

### What to Submit

**1. Tableau Workbook File (.twbx)**

Save your completed workbook:
1. Go to **File** → **Save As**
2. Choose **"Tableau Packaged Workbook (.twbx)"**
   - Note: Must be .twbx (packaged), not .twb
   - Packaged workbooks include the data
3. Name it: **LastName_FirstName_Lab5_LOD.twbx**
4. Save to your designated submission folder

**2. Documentation Document (PDF or Word)**

Create a document that includes:

**Part A: Screenshots**
- Screenshot of your **"Risk by State"** worksheet
- Screenshot of your **"Current Balance Distribution"** worksheet
- Screenshot of your **"Geographic Distribution"** map
- Screenshot of your final dashboard
- Screenshot of at least one challenge exercise (if attempted)

**Part B: Written Explanations**

Answer these questions (2-3 sentences each):

1. Explain in your own words: What is the difference between FIXED, INCLUDE, and EXCLUDE?

2. Why did we need a FIXED calculation for "Member Ever At Risk?" instead of just checking Credit Score < 550?

3. In the "Loans Per Member" analysis, why did we use INCLUDE instead of FIXED?

4. Describe one real-world business scenario (not from this lab) where you would use an LOD calculation.

5. What was the most challenging part of this lab? What helped you understand it?

**Part C: Key Insights**

Based on your dashboard, document 3-5 insights, such as:
- Which states have the highest percentage of at-risk members?
- Which portfolio has the highest average balance?
- Which loan types attract higher credit score customers?
- Any interesting patterns you noticed

**3. Naming Convention**

- Workbook: **LastName_FirstName_Lab5_LOD.twbx**
- Documentation: **LastName_FirstName_Lab5_Documentation.pdf**

---

## Troubleshooting Guide

### Common Errors and Solutions

**Error: "Cannot mix aggregate and non-aggregate arguments"**

**Cause:** You're trying to combine regular fields with LOD calculations incorrectly.

**Solution:** 
- Make sure your LOD calculation is complete with curly braces {}
- If comparing LOD to regular aggregation, wrap both in appropriate functions
- Example: `AVG([LOD Calculation]) - AVG([Regular Field])`

---

**Error: LOD calculation shows same value for every row**

**Cause:** This might actually be correct! If you're using FIXED or EXCLUDE, the same value might be intentional.

**Solution:**
- Check if this is expected behavior
- Verify you're using the right LOD type (FIXED vs. INCLUDE vs. EXCLUDE)
- Make sure you included the right dimensions

---

**Error: "Cannot use LOD in a calculated field"**

**Cause:** You're trying to nest LOD calculations in complex ways.

**Solution:**
- Create the LOD calculation as a separate field first
- Then reference that field in other calculations
- Don't try to put LOD expressions inside other LOD expressions

---

**Problem: Map shows only dots, not filled states**

**Cause:** Tableau didn't recognize State as a geographic field.

**Solution:**
1. Right-click on **"State"** in the Data pane
2. Select **Geographic Role** → **State/Province**
3. Make sure Country is set to **United States**

---

**Problem: "No results" or empty visualization**

**Cause:** Filters might be too restrictive, or data type issues.

**Solution:**
1. Check all filters - temporarily remove them to see if data appears
2. Verify data types are correct (Member ID should be String)
3. Check for typos in calculation formulas
4. Use **"View Data"** (click on a mark → View Data) to see what's being calculated

---

**Problem: Count of members seems wrong**

**Cause:** Might be counting multiple times due to monthly snapshots.

**Solution:**
- Always use **COUNTD([Member ID])** (Count Distinct)
- Never use **COUNT** for counting unique members in this dataset
- Remember: each member appears once per month per loan

---

**Problem: Calculations are very slow**

**Cause:** LOD calculations on large datasets can be computationally expensive.

**Solution:**
1. Consider using data extracts instead of live connections
   - Go to Data → Extract Data
   - Save as .hyper file
   - Extracts are much faster

2. Simplify complex nested calculations if possible

3. Close other worksheets while working (they recalculate automatically)

---

**Problem: Can't add LOD calculation to view**

**Cause:** LOD calculations return row-level results and need to be aggregated.

**Solution:**
- When dragging LOD calculation to the view, Tableau will ask how to aggregate it
- Choose appropriate aggregation: AVG, SUM, MIN, MAX, etc.
- For TRUE/FALSE LOD calculations, you might want to COUNT or use as a dimension

---

### Getting Help

**If you're stuck:**

1. **Check the official Tableau documentation:**
   - [LOD Overview](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_overview.htm)
   - [LOD Examples](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_examples.htm)

2. **Use Tableau's built-in help:**
   - Press F1 while in Tableau
   - Right-click on any element → "Describe" to see how it's calculated

3. **Verify your formula syntax:**
   - LOD calculations must have curly braces: `{}`
   - Dimensions must be in square brackets: `[Dimension]`
   - Aggregation is required: `AVG()`, `SUM()`, `COUNT()`, etc.

4. **Contact your instructor:**
   - Include screenshots of the error
   - Share your formula that's causing issues
   - Describe what you were trying to accomplish

---

## Additional Resources

**Official Tableau Resources:**

- **Main Help:** [https://help.tableau.com/current/pro/desktop/en-us/default.htm](https://help.tableau.com/current/pro/desktop/en-us/default.htm)
- **LOD Calculations:** [https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod.htm](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod.htm)
- **LOD Examples:** [https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_examples.htm](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod_examples.htm)
- **Functions Reference:** [https://help.tableau.com/current/pro/desktop/en-us/functions.htm](https://help.tableau.com/current/pro/desktop/en-us/functions.htm)

**Video Tutorials:**
- Search "Tableau LOD Calculations Tutorial" on YouTube
- Tableau's official channel has great explanations

**Practice Datasets:**
- After completing this lab, try LOD calculations on Sample - Superstore
- Look for patterns in your own data where LOD would be useful

---

## Glossary of Terms

**Level of Detail (LOD):** The granularity at which data is analyzed. Can refer to data level (row-level), view level (determined by dimensions in view), or calculated level (defined by LOD expressions).

**FIXED:** An LOD expression that calculates at a specific level of detail, regardless of the view level.

**INCLUDE:** An LOD expression that adds dimensions to the view level of detail for calculation purposes.

**EXCLUDE:** An LOD expression that removes dimensions from the view level of detail for calculation purposes.

**Aggregation:** A calculation that combines multiple values into a single value (SUM, AVG, COUNT, MIN, MAX, etc.).

**Dimension:** A categorical field that defines the level of detail in a view (text fields, dates, geographic fields).

**Measure:** A quantitative field that can be aggregated (numbers that you can sum, average, etc.).

**Granularity:** The level of detail in data; finer granularity = more detailed (row-level), coarser granularity = more summarized (aggregated).

**Context Filter:** A special filter that is evaluated first and can affect LOD calculations.

**Table-Scoped:** A FIXED LOD expression with no dimensions specified, calculating across the entire dataset.

---

## Tips for Success

1. **Draw it out:** When confused about LOD, sketch out what level of detail you want vs. what's in your view

2. **Test incrementally:** Build complex calculations in stages - test each part before combining

3. **Use meaningful names:** Name your calculations clearly so you remember what they do later

4. **Check your math:** Always verify LOD results with a crosstab showing all the detail

5. **Think about the business question:** Start with "What am I trying to answer?" before jumping into formulas

6. **Practice, practice, practice:** LOD calculations become intuitive with repetition

7. **Learn from errors:** Each error message teaches you something about how Tableau works

---

## Congratulations!

You've completed Lab 5 on Level of Detail calculations! This is one of the most powerful features in Tableau, and mastering it opens up countless analytical possibilities.

**Key Takeaways:**

✅ You can calculate at different levels of detail simultaneously  
✅ FIXED locks calculations to specific dimensions  
✅ INCLUDE adds dimensions to your view level  
✅ EXCLUDE removes dimensions from your view level  
✅ LOD calculations enable complex comparisons and analyses  
✅ Real-world business questions often require LOD thinking

**Next Steps:**

- Experiment with LOD calculations on other datasets
- Try combining multiple LOD expressions in one visualization
- Look for opportunities to use LOD in your own projects
- Explore table calculations (the next advanced calculation type)

---

**Lab Created By:** Dr. Lee  
**Last Updated:** 2025  
**Questions?** Contact your instructor or visit office hours

**Good luck with your analysis!** 🎉📊
