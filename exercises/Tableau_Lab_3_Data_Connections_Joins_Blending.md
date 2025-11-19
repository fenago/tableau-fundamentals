# Tableau Lab 3: Connecting and Combining Data Sources

**Course:** Data Analytics & Visualization  
**Software:** Tableau Desktop Public Edition  
**Datasets:** Hospital Visits, Hospital Goals  
**Estimated Time:** 120-150 minutes  
**Difficulty:** Beginner to Intermediate

---

## 📋 Table of Contents

1. [Learning Objectives](#learning-objectives)
2. [Prerequisites](#prerequisites)
3. [What You'll Learn](#what-youll-learn)
4. [Understanding Data Connections](#understanding-data-connections)
5. [Part 1: Download and Setup](#part-1-download-and-setup)
6. [Part 2: Single Data Source Connection](#part-2-single-data-source-connection)
7. [Part 3: Understanding Joins](#part-3-understanding-joins)
8. [Part 4: Data Blending](#part-4-data-blending)
9. [Part 5: Joins vs. Blending - When to Use Each](#part-5-joins-vs-blending---when-to-use-each)
10. [Part 6: Building a Complete Hospital Performance Dashboard](#part-6-building-a-complete-hospital-performance-dashboard)
11. [Challenge Exercises](#challenge-exercises)
12. [Submission Requirements](#submission-requirements)
13. [Troubleshooting Guide](#troubleshooting-guide)

---

## 🎯 Learning Objectives

By the end of this lab, you will be able to:

- Connect to multiple data sources (CSV and Excel files)
- Understand the difference between joins and data blending
- Create joins between tables from the same data source
- Use data blending to combine data from different sources
- Recognize when to use joins vs. blending
- Build visualizations using multiple data sources
- Create a performance dashboard comparing actual vs. goal metrics
- Troubleshoot common data connection issues

---

## 📚 Prerequisites

**Required Software:**
- **Tableau Desktop Public Edition** (free version)
  - Download: [https://public.tableau.com/app/discover](https://public.tableau.com/app/discover)
  - Make sure you have the latest version installed

**Required Datasets (You'll download these):**
- **Hospital Visits.csv** - Patient visit data
- **Hospital Goals.csv** - Revenue goals by department
- **Hospital Goals.xlsx** - Same goals data in Excel format

**Basic Tableau Skills You Should Know:**
- How to connect to a CSV file
- How to drag fields to create basic visualizations
- Understanding of dimensions vs. measures
- Basic calculated fields (from Lab 4)

**Official Documentation (Keep These Open!):**
- **Main Help:** [https://help.tableau.com/current/pro/desktop/en-us/default.htm](https://help.tableau.com/current/pro/desktop/en-us/default.htm)
- **Join Your Data:** [https://help.tableau.com/current/pro/desktop/en-us/joining_tables.htm](https://help.tableau.com/current/pro/desktop/en-us/joining_tables.htm)
- **Blend Your Data:** [https://help.tableau.com/current/pro/desktop/en-us/multiple_connections.htm](https://help.tableau.com/current/pro/desktop/en-us/multiple_connections.htm)
- **Data Source Page:** [https://help.tableau.com/current/pro/desktop/en-us/datasource_prepare.htm](https://help.tableau.com/current/pro/desktop/en-us/datasource_prepare.htm)

---

## 🎓 What You'll Learn

**The Big Picture:**

In real-world analytics, data is rarely in one perfect table. You'll often need to:
- Combine data from multiple Excel files
- Match transaction data with reference tables
- Merge data from different systems
- Compare actual performance against goals/targets

This lab teaches you TWO main ways to combine data in Tableau:

1. **JOINS** - Merge tables from the same source (like database tables or sheets in one Excel file)
2. **DATA BLENDING** - Combine data from completely different sources (separate files, databases, etc.)

**Real-World Example:**

You're analyzing hospital performance:
- **Visits data** (CSV file): Daily patient visits, revenue, doctors, departments
- **Goals data** (Excel file): Annual revenue targets by department

You need to answer: "Is each department meeting its revenue goals?"

To answer this, you'll need to combine both datasets!

---

## 🔍 Understanding Data Connections

Before we start, let's understand key concepts.

### What is a Data Source?

A **data source** in Tableau is how you connect to your data. Each file or database connection you make becomes a separate data source.

**Examples:**
- One CSV file = One data source
- One Excel file (even with multiple sheets) = One data source
- One database connection = One data source

### What is a Data Connection?

A **data connection** is the link Tableau makes to your file or database. You can have:
- **Single connection**: One file
- **Multiple connections**: Multiple files in the same data source

### Joins vs. Blending: The Key Difference

| Aspect | JOINS | DATA BLENDING |
|--------|-------|---------------|
| **Where** | Same data source | Different data sources |
| **When** | On Data Source page | On worksheet/view |
| **How** | Merges at row level | Aggregates then combines |
| **Example** | Two sheets in same Excel file | CSV file + Excel file |
| **Icon** | Physical tables joined | Orange chain link (🔗) |

**Think of it this way:**
- **JOINS** = Getting married (fully combined, can't easily separate)
- **BLENDING** = Dating (staying independent, meeting for specific occasions)

We'll explore both in detail!

---

## Part 1: Download and Setup

### Exercise 1.1: Downloading Your Data Files

You need to download three files for this lab.

**Step 1: Create a Lab Folder**

1. On your computer, create a folder called: **Tableau_Lab_3**
2. Location suggestion:
   - Windows: `Documents\Tableau_Labs\Lab_3`
   - Mac: `Documents/Tableau_Labs/Lab_3`

**Step 2: Download Hospital Visits Data**

1. Open your web browser
2. Navigate to: 

```
https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2003/Hospital%20Visits.csv
```

3. The file should download automatically
4. Move the file to your **Tableau_Lab_3** folder

**What this file contains:**
- Patient visit records
- Doctor names
- Hospital branches (East, Central, South)
- Departments (ER, Surgery, Labs, etc.)
- Revenue per visit
- Patient risk profiles
- Dates of admission and discharge

**Step 3: Download Hospital Goals (CSV Version)**

1. In your browser, navigate to:

```
https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2003/Hospital%20Goals.csv
```

2. Download and save to your **Tableau_Lab_3** folder

**What this file contains:**
- Department names
- Annual revenue goals for each department

**Step 4: Download Hospital Goals (Excel Version)**

1. In your browser, navigate to:

```
https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2003/Hospital%20Goals.xlsx
```

2. Download and save to your **Tableau_Lab_3** folder

**Why both CSV and Excel?**
We'll use these to demonstrate different connection methods. They contain the same data, just in different formats.

**Step 5: Verify Your Downloads**

Your **Tableau_Lab_3** folder should now contain:
- ✓ Hospital Visits.csv
- ✓ Hospital Goals.csv
- ✓ Hospital Goals.xlsx

**Important:** Don't open these files in Excel yet - let Tableau connect to them directly!

---

### Exercise 1.2: Understanding Your Data

Before connecting, let's understand what we're working with.

**Hospital Visits Dataset Structure:**

Each row represents one patient visit. Key fields:
- **Row_ID**: Unique identifier for each visit
- **Date of Admit**: When patient was admitted
- **Date of Discharge**: When patient left (blank if still admitted)
- **Doctor**: Doctor's name
- **Hospital Branch**: East, Central, or South location
- **Department Type**: General, Specialty, or Labs
- **Department**: Specific department (ER, Surgery, Cardiology, etc.)
- **Patient ID**: Unique patient identifier
- **Patient Name**: Patient's name
- **Patient Risk Profile**: High or Low risk
- **Revenue**: Money generated from this visit
- **Minutes to Service**: Wait time
- **Number of Patient Visits**: Always 1 (one row = one visit)

**Hospital Goals Dataset Structure:**

Each row represents one department's annual goal:
- **Department**: Department name (matches departments in Visits data)
- **Goal**: Annual revenue target

**The Analysis Question:**

We want to compare **actual revenue** (from Visits) against **goal revenue** (from Goals) for each department. This requires combining both datasets!

---

## Part 2: Single Data Source Connection

Let's start with the basics: connecting to a single data source.

### Exercise 2.1: Connecting to Hospital Visits

**Step 1: Open Tableau Desktop Public Edition**

1. Launch Tableau from your computer
2. You'll see the Start page

**Step 2: Connect to CSV File**

1. On the left side, under "Connect," find **"To a File"**
2. Click **"Text file"**
3. Navigate to your **Tableau_Lab_3** folder
4. Select **Hospital Visits.csv**
5. Click **"Open"**

**Step 3: Explore the Data Source Page**

You should now see the **Data Source** page. This is where you prepare your data before analyzing it.

**Key Areas of the Data Source Page:**

1. **Left Pane (Connections):**
   - Shows your data source: "Hospital Visits.csv"
   - You can add more connections here

2. **Canvas (Center):**
   - Shows tables/sheets you're using
   - This is where you'll create joins later
   - Currently shows "Hospital Visits" table

3. **Data Grid (Bottom):**
   - Preview of your data (first 1,000 rows)
   - Shows all columns and some sample values

4. **Metadata Grid Toggle:**
   - Click this to see column names, data types, and other metadata
   - Useful for checking data types at a glance

**Step 4: Verify Data Types**

Look at the icons above each column in the data grid:

**Expected Data Types:**
- **Abc (Text)**: Doctor, Hospital Branch, Department Type, Department, Patient Name, Patient Risk Profile
- **📅 (Date)**: Date of Admit, Date of Discharge
- **# (Number)**: Row_ID, Patient ID, Revenue, Minutes to Service, Number of Patient Visits

**If any data type is wrong:**
1. Click the icon above the column name
2. Select the correct data type

**Common Issues:**
- If "Date of Admit" shows as Abc (text), change it to Date
- If "Revenue" shows as Abc (text), change it to Number (decimal)

**Step 5: Rename the Data Source**

Let's give this data source a clear name:

1. At the top left, you'll see "Hospital Visits (Hospital Visits.csv)"
2. Right-click on this name
3. Select **"Rename"**
4. Type: **Hospital Visits - Primary**
5. Press Enter

This makes it easier to identify, especially when we add more sources!

📖 **Reference:** [Connect to a File](https://help.tableau.com/current/pro/desktop/en-us/examples_text.htm)

---

### Exercise 2.2: Exploring the Visits Data

Let's create a quick visualization to understand our data.

**Step 1: Go to a Worksheet**

1. At the bottom of the screen, click **"Sheet 1"**
2. You're now in the worksheet view
3. Rename the sheet:
   - Right-click "Sheet 1"
   - Select "Rename"
   - Type: **"Revenue Overview"**

**Step 2: Build a Simple View**

Let's see revenue by department:

1. From the Data pane (left side), drag **"Department"** to Rows
2. Drag **"Revenue"** to Columns
3. Tableau automatically aggregates to SUM(Revenue)

**What You Should See:**

A horizontal bar chart showing total revenue for each department:
- General Surgery (largest)
- ER
- Cardiology
- Gastroenterology
- ICU
- Neurology
- And others...

**Step 3: Sort the View**

1. Click the sort descending icon in the toolbar (arrow pointing down)
2. Or: Click on the axis and select "Sort"

Now departments are ranked by revenue!

**Step 4: Add More Detail**

Let's see how this breaks down by hospital branch:

1. Drag **"Hospital Branch"** to Color on the Marks card
2. Now you see: East (blue), Central (orange), South (green)

**Insights You Might Notice:**
- General Surgery generates the most revenue
- Some departments appear in multiple branches
- Revenue varies significantly by department

**Step 5: Add Revenue Labels**

1. Drag **"Revenue"** to Label on the Marks card
2. Right-click on a label → **"Format"**
3. In Format pane, select **"Currency (Custom)"**
4. Set to show thousands (K) or millions (M)

Now your bars are labeled with dollar amounts!

**Key Takeaway:**

We can see total revenue by department, but we don't know if these numbers are **good** or **bad**. We need the **Goals** data to make that comparison!

---

## Part 3: Understanding Joins

Joins combine data from multiple tables **within the same data source**. Let's learn how!

### Concept: What Are Joins?

**Definition:** A join combines rows from two or more tables based on a common field (called a "join key").

**Analogy:**

Imagine you have two lists:
- **List A:** Student names and their test scores
- **List B:** Student names and their homework scores

If you "join" these lists on "Student Name," you get one combined list showing each student's test score AND homework score together.

### Types of Joins

Tableau supports four join types:

| Join Type | What It Does | SQL Equivalent |
|-----------|--------------|----------------|
| **Inner** | Only rows that match in BOTH tables | INNER JOIN |
| **Left** | All rows from left table, matched rows from right | LEFT JOIN |
| **Right** | All rows from right table, matched rows from left | RIGHT JOIN |
| **Full Outer** | All rows from both tables, whether matched or not | FULL OUTER JOIN |

**Visual Example:**

```
Left Table:        Right Table:
A, B, C           B, C, D

INNER:    B, C    (only what matches)
LEFT:     A, B, C (all from left)
RIGHT:    B, C, D (all from right)
FULL:     A, B, C, D (everything)
```

---

### Exercise 3.1: Creating a Join (Same File Example)

For this example, we'll simulate joining data. In a real scenario, you might have:
- Multiple sheets in one Excel file
- Multiple tables in one database

**Step 1: Return to Data Source Page**

1. At the bottom of the screen, click the **"Data Source"** tab
2. You're back at the Data Source page

**Step 2: Understanding the Canvas**

The canvas area is where you see your tables. Currently:
- You have one table: "Hospital Visits"

**If you wanted to add another table from the same source:**
1. You'd drag another table/sheet to the canvas
2. Tableau would automatically attempt to join them
3. You'd see a Venn diagram icon showing the join

**Step 3: Understanding the Join Canvas**

Let's see where joins are configured:

1. Double-click on **"Hospital Visits"** in the canvas
2. This opens the **Physical Layer** (join canvas)
3. You'll see the table represented as a box

This is where you would add more tables and configure joins!

**Step 4: Return to Logical Layer**

1. Click the **X** in the upper right to close the physical layer
2. You're back at the logical layer

**Important Concepts:**

- **Logical Layer**: Where you define relationships (Tableau 2020.2+)
- **Physical Layer**: Where you define joins (traditional method)
- For now, we're learning joins, so we work in the physical layer

📖 **Reference:** [Join Your Data](https://help.tableau.com/current/pro/desktop/en-us/joining_tables.htm)

---

### Exercise 3.2: Understanding Join Requirements

For a join to work, you need:

1. **Tables from the same data source**
   - Same Excel file (different sheets)
   - Same database (different tables)
   - **NOT:** Different files (use blending instead)

2. **A common field (join key)**
   - Field must exist in both tables
   - Should contain matching values
   - Ideally: unique identifiers or categories

3. **Same data type**
   - Both fields must be same type (text, number, date)
   - "Department" (text) can join with "Department" (text) ✓
   - "Department" (text) cannot join with "Dept_ID" (number) ✗

**Common Join Keys:**

- Customer ID
- Product ID
- Department Name
- Date
- Employee ID
- Order Number

---

### Exercise 3.3: Simulated Join Example

Since our Hospital Visits file doesn't have multiple tables to join, let's understand how it would work.

**Scenario:** If Hospital Visits had TWO sheets:

**Sheet 1: Visit Details**
- Row_ID, Patient ID, Date, Department, Revenue

**Sheet 2: Department Info**
- Department, Department Type, Department Head

**To Join Them:**

1. Drag "Visit Details" to canvas
2. Double-click to open physical layer
3. Drag "Department Info" next to it
4. Tableau automatically suggests join on "Department" (if names match)
5. A Venn diagram appears showing the join type
6. Click the Venn diagram to configure:
   - Join type (Inner, Left, Right, Full)
   - Join fields (which fields to match on)

**Result:**

One combined table with:
- Visit details (Patient, Date, Revenue)
- Department info (Type, Head)
- Matched by Department name

**The Join Clause:**

```
Visit Details.Department = Department Info.Department
```

This is the join key - it tells Tableau how to match rows.

---

## Part 4: Data Blending

Data blending is how you combine data from **different data sources**. This is what we need for our Hospital analysis!

### Concept: What Is Data Blending?

**Definition:** Data blending combines data from separate data sources in the worksheet view, linked by common dimensions.

**Key Differences from Joins:**

| Aspect | Joins | Data Blending |
|--------|-------|---------------|
| Setup location | Data Source page | Worksheet |
| Number of sources | One data source | Multiple data sources |
| Data combination | Row-level merge | Aggregated merge |
| Performance | Faster (database does work) | Slower (Tableau does work) |
| Flexibility | Fixed for all sheets | Different per sheet |
| When to use | Same source | Different sources |

**Analogy:**

Think of a **join** like a recipe where you mix ingredients together in one bowl (you can't separate them afterward).

Think of **blending** like a meal with separate dishes on one plate (each dish stays distinct, but you eat them together).

---

### Exercise 4.1: Adding a Second Data Source

Now let's add the Hospital Goals data!

**Step 1: Return to Data Source Page**

1. Click the **"Data Source"** tab at the bottom

**Step 2: Add a New Data Source**

1. At the top left, next to "Hospital Visits - Primary," click **"Data"** menu
2. Select **"New Data Source"**
3. Or: Press **Ctrl+D** (Windows) / **Cmd+D** (Mac)

**Step 3: Connect to Hospital Goals**

1. Click **"Text file"** under "To a File"
2. Navigate to your **Tableau_Lab_3** folder
3. Select **Hospital Goals.csv**
4. Click **"Open"**

**Step 4: Verify the Goals Data**

You should see the Data Source page for Hospital Goals:

**Expected columns:**
- **Department** (text): Anaesthetics, Cardiology, ER, etc.
- **Goal** (number): 300000, 5000000, 6000000, etc.

**Check data types:**
- Department should be Abc (text)
- Goal should be # (number, whole number)

**Step 5: Rename the Data Source**

1. At the top, right-click on "Hospital Goals (Hospital Goals.csv)"
2. Select **"Rename"**
3. Type: **Hospital Goals - Secondary**
4. Press Enter

**Step 6: Look at the Data Pane**

Click on **"Sheet 1"** or create a new worksheet. In the Data pane (left side), you should now see:

- **Hospital Visits - Primary** (your first data source)
- **Hospital Goals - Secondary** (your second data source)

You can click between them to see different fields!

📖 **Reference:** [Multiple Data Sources](https://help.tableau.com/current/pro/desktop/en-us/multiple_connections.htm)

---

### Exercise 4.2: Creating Your First Data Blend

Let's blend the data to compare actuals vs. goals!

**Step 1: Create a New Worksheet**

1. Create a new worksheet (click + at bottom)
2. Rename it: **"Revenue vs Goals"**

**Step 2: Start with Primary Data Source**

1. Make sure **"Hospital Visits - Primary"** is selected in the Data pane
2. Drag **"Department"** to Rows
3. Drag **"Revenue"** to Columns
4. Sort descending

You should see the same revenue by department view as before.

**Step 3: Switch to Secondary Data Source**

1. In the Data pane, click on **"Hospital Goals - Secondary"**
2. The fields change to show: Department, Goal

**Step 4: Look for the Link Icon**

This is CRITICAL for blending!

In the Hospital Goals data pane, look at the **"Department"** field:
- You should see a **chain link icon** (🔗) next to it
- The icon might be **orange** (active link) or **gray** (inactive link)

**What does this mean?**

Tableau automatically detected that "Department" exists in BOTH data sources and created a potential link!

**If you DON'T see a chain link:**
- The field names might be different
- We'll fix this in the next exercise

**Step 5: Add Goal to the View**

1. With **"Hospital Goals - Secondary"** still selected
2. Drag **"Goal"** to the view next to Revenue
3. You can drop it on Columns (next to SUM(Revenue))

**What Should Happen:**

You should now see TWO measures side-by-side:
- SUM(Revenue) from primary source (actual revenue)
- SUM(Goal) from secondary source (target revenue)

**Important:** The Goal field will show **AGG(Goal)** instead of **SUM(Goal)**. This is normal for blended data!

**Step 6: Verify the Blend is Working**

Look at the Department field in **Hospital Goals - Secondary**:
- The chain link icon should now be **orange** 🔗 (active)
- This means the blend is active!

**If the chain link is gray:**
- Click on it to make it active (turns orange)
- The Goal values should update to match

**Step 7: Format for Clarity**

Let's make this easier to read:

1. Format Revenue:
   - Right-click SUM(Revenue) in Columns
   - Format → Currency

2. Format Goal:
   - Right-click AGG(Goal) in Columns
   - Format → Currency

3. Add labels:
   - Drag SUM(Revenue) to Label
   - Drag AGG(Goal) to Label

**Step 8: Create a Better Comparison View**

Let's make this side-by-side:

1. Remove Revenue and Goal from Columns
2. Create two separate bar charts:
   - Drag **"Measure Names"** to Columns
   - Drag **"Measure Values"** to Text
   - Filter Measure Names to show only Revenue and Goal

Or create a simpler view:

1. Keep Department on Rows
2. Put SUM(Revenue) on Columns
3. Put AGG(Goal) on Columns next to it
4. Change mark type to **Bar**

**What You Should See:**

For each department, two bars:
- Blue bar = Actual Revenue
- Orange bar = Goal Revenue

**Key Insights:**
- Which departments exceeded their goals?
- Which departments fell short?
- By how much?

📖 **Reference:** [Blend Your Data](https://help.tableau.com/current/pro/desktop/en-us/multiple_connections.htm)

---

### Exercise 4.3: Understanding the Blend Relationship

Let's explore how Tableau linked the data sources.

**Step 1: Check the Active Link**

In your view:
1. Look at **"Hospital Goals - Secondary"** in the Data pane
2. Find the **Department** field
3. Notice the orange chain link icon 🔗

**What this means:**
- Tableau is matching rows based on Department name
- For each department in your primary view, Tableau finds the matching department in the secondary source
- It then displays the corresponding Goal value

**Step 2: View Blend Relationships**

1. Click **"Data"** in the top menu
2. Select **"Edit Blend Relationships..."**

A dialog box opens showing how data sources are linked.

**What You See:**

**Primary Data Source:** Hospital Visits - Primary  
**Secondary Data Source:** Hospital Goals - Secondary

**Relationships:**
- Either "Automatic" or "Custom"
- Shows which fields are linked

**Automatic Relationships:**
Tableau automatically links fields with:
- Same name: "Department" = "Department"
- Same data type: Both are text

**Custom Relationships:**
You can manually specify links if names don't match

**Step 3: Understanding the Link Behavior**

The blend works like a **LEFT JOIN**:
- All departments from PRIMARY (Hospital Visits) appear
- Matched goals from SECONDARY appear next to them
- If a department has no matching goal, you see NULL or blank

**Example:**

Primary has: ER, Surgery, Nutrition, Neonatal  
Secondary has: ER, Surgery, Nutrition

**Result:**
- ER: Shows actual + goal ✓
- Surgery: Shows actual + goal ✓
- Nutrition: Shows actual + goal ✓
- Neonatal: Shows actual + blank (no goal found)

---

### Exercise 4.4: Manually Defining Blend Relationships

Sometimes Tableau can't automatically detect the link. Let's learn how to manually define it.

**Step 1: Open Blend Relationships**

1. Go to **Data** → **Edit Blend Relationships...**

**Step 2: Select Your Data Sources**

1. **Primary:** Hospital Visits - Primary
2. **Secondary:** Hospital Goals - Secondary

**Step 3: View Automatic Relationships**

Under "Automatic," you should see:
- Department (from primary) = Department (from secondary)

This was auto-detected because the names match.

**Step 4: Create a Custom Relationship**

Let's see how to manually add a link:

1. Select **"Custom"** (instead of Automatic)
2. Click **"Add..."** button

A dialog appears: "Add/Edit Field Mapping"

3. **Primary data source field:** Select "Department"
4. **Secondary data source field:** Select "Department"
5. Click **OK**

You've manually created the same relationship!

**Step 5: When You Need Custom Relationships**

You need custom when:
- Field names don't match (e.g., "Dept" in one, "Department" in another)
- You want to link on multiple fields (e.g., Department + Year)
- You want to link on dates at specific levels (Month, Year, etc.)

**Step 6: Close the Dialog**

Click **OK** to save your relationships.

**Important:** These blend relationships apply across ALL worksheets in this workbook!

---

### Exercise 4.5: Creating Calculations with Blended Data

Now let's calculate the difference between actual and goal.

**Step 1: Create a New Calculated Field**

1. In the **Hospital Visits - Primary** data pane
2. Right-click in empty space → **Create Calculated Field...**
3. Name: **Revenue vs Goal**

**Step 2: Write the Formula**

```
SUM([Revenue]) - SUM([Hospital Goals - Secondary].[Goal])
```

**Understanding This Formula:**

- `SUM([Revenue])` - Total revenue from primary source
- `SUM([Hospital Goals - Secondary].[Goal])` - Total goal from secondary source
- Note the syntax: `[DataSourceName].[FieldName]`

**Step 3: Troubleshoot if Needed**

If you get an error about blending:

Try this alternative:
```
SUM([Revenue]) - AGG([Hospital Goals - Secondary].[Goal])
```

Or create it as a simpler calculation after both fields are in the view.

**Step 4: Use the Calculation**

1. Create a new worksheet: **"Goal Performance"**
2. Drag **"Department"** to Rows
3. Drag **"Revenue vs Goal"** to Columns

**What You See:**

- Positive values = Exceeded goal! 🎉
- Negative values = Fell short of goal 😞
- Zero = Met goal exactly

**Step 5: Color by Performance**

1. Drag **"Revenue vs Goal"** to Color
2. Tableau automatically assigns colors:
   - Blue/Green = Positive (above goal)
   - Orange/Red = Negative (below goal)

3. Edit colors for clarity:
   - Click Color → Edit Colors
   - Choose "Red-Green Diverging"
   - Check "Stepped Color" (3 steps)
   - Check "Reversed"
   - Click OK

Now it's very visual:
- Green = Exceeded goal
- Red = Below goal

**Step 6: Add Reference Line**

Let's add a line at zero (the break-even point):

1. Right-click on the axis → **Add Reference Line**
2. Set to **"Constant"**
3. Value: **0**
4. Label: **"Goal Target"**
5. Click **OK**

Perfect! Now you can clearly see which departments are above or below their targets.

📖 **Reference:** [Calculations](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields.htm)

---

### Exercise 4.6: Understanding the Asterisk (*)

Sometimes when blending, you'll see an asterisk (*) instead of a value. Let's understand why.

**What the Asterisk Means:**

The * appears when Tableau finds **multiple values** in the secondary source for a single value in the primary source, and it doesn't know which one to display.

**Example:**

If "Department" isn't unique in the secondary source:

```
Primary (Visits):     Secondary (Goals):
ER                   ER - Goal: 6,000,000
                     ER - Goal: 5,500,000  (duplicate!)
```

Tableau thinks: "Which goal should I show for ER? I don't know!" → Shows *

**How to Fix:**

1. **Check for duplicates in secondary source**
   - Make sure your linking field is unique
   - Remove duplicate rows

2. **Aggregate appropriately**
   - Use SUM, AVG, MIN, or MAX to handle multiples
   - Example: MAX([Goal]) takes the highest goal

3. **Link on additional fields**
   - Add more fields to the blend relationship
   - Example: Link on Department + Year (if goals vary by year)

**In Our Case:**

Each department should have only ONE goal, so we shouldn't see asterisks. If you do, check your Hospital Goals data for duplicates!

---

## Part 5: Joins vs. Blending - When to Use Each

Now that you've learned both methods, let's understand when to use each.

### Decision Framework

```
START: Do I need to combine data?
  │
  ├─ Is all data in ONE data source (same file/database)?
  │  └─ YES → Use JOINS
  │     ├─ Same Excel file, different sheets? → JOIN
  │     ├─ Same database, different tables? → JOIN
  │     └─ Same CSV (logical, but uncommon)? → JOIN
  │
  └─ Is data in DIFFERENT sources?
     └─ YES → Use DATA BLENDING
        ├─ Different CSV files? → BLEND
        ├─ CSV + Excel? → BLEND
        ├─ File + Database? → BLEND
        └─ Different databases? → BLEND (or cross-db join if supported)
```

### Comparison Table

| Consideration | JOINS | DATA BLENDING |
|---------------|-------|---------------|
| **Setup** | Data Source page | Per worksheet |
| **Best for** | Same source | Different sources |
| **Performance** | Faster | Slower |
| **Row level detail** | Full detail available | Aggregated |
| **Duplicate data** | Can create duplication | Less duplication |
| **Flexibility** | Same for all sheets | Different per sheet |
| **Published data** | Can't join published sources | Can blend published sources |
| **COUNT DISTINCT** | Works normally | Doesn't work well |
| **LOD calculations** | Work normally | Limited |

### When to Use JOINS

**Use joins when:**

✅ Data is in the same source (file/database)  
✅ You need row-level detail  
✅ You want best performance  
✅ You need complex calculations (LOD, COUNTD)  
✅ The join won't create excessive duplication  

**Example Scenarios:**

1. **Multiple sheets in one Excel workbook**
   - Sheet 1: Orders
   - Sheet 2: Customers
   - JOIN on Customer ID

2. **Database tables**
   - Sales table
   - Products table
   - JOIN on Product ID

3. **When you need full transaction detail**
   - Every order line item
   - With product information
   - With customer information

### When to Use BLENDING

**Use blending when:**

✅ Data is in different sources  
✅ Data is at different levels of granularity  
✅ You're comparing aggregated metrics  
✅ You're using published data sources  
✅ Joining would create too much duplication  

**Example Scenarios:**

1. **Different files** (Like our hospital example!)
   - Visits.csv (transaction detail)
   - Goals.xlsx (summary targets)
   - BLEND on Department

2. **Different databases**
   - Salesforce (CRM data)
   - SQL Server (Financial data)
   - BLEND on Account

3. **Different granularity**
   - Daily sales (365 rows per year)
   - Annual targets (1 row per year)
   - BLEND on Year

4. **Published data sources**
   - Can't join published sources
   - Must blend instead

### Real-World Example

**Scenario:** Analyzing retail store performance

**Data Sources:**
1. **Transactions.csv** (50,000 rows)
   - Date, Store, Product, Quantity, Revenue

2. **Store_Targets.xlsx** (50 rows)
   - Store, Annual_Target, Manager

3. **Products.csv** (500 rows)
   - Product_ID, Product_Name, Category, Price

**Best Approach:**

1. **JOIN** Transactions + Products
   - Same level of detail (both are per transaction)
   - Need product details on every transaction
   - Use a data source join

2. **BLEND** the joined source + Store_Targets
   - Different levels (transactions vs. annual targets)
   - Comparing aggregates (actual vs. target)
   - Use data blending

**Result:**
- One data source with Transactions JOIN Products
- Blend that with Store_Targets
- Can compare actual sales vs. targets by store

📖 **Reference:** [Combine Data](https://help.tableau.com/current/pro/desktop/en-us/datasource_relationships_combine.htm)

---

## Part 6: Building a Complete Hospital Performance Dashboard

Now let's combine everything into a professional dashboard!

### Exercise 6.1: Creating Key Visualizations

We'll create 5 views for our dashboard.

**View 1: Revenue by Department (Actual vs Goal)**

1. New worksheet: **"Revenue vs Goals Bar"**
2. Drag **Department** to Rows
3. Drag **Measure Names** to Columns
4. Drag **Measure Values** to Columns
5. Filter Measure Names to show:
   - Revenue (from primary)
   - Goal (from secondary)
6. Sort by Revenue (descending)
7. Color each measure differently
8. Add value labels

**View 2: Goal Achievement Percentage**

1. New worksheet: **"Goal Achievement %"**
2. Create a calculated field: **Pct of Goal**

```
SUM([Revenue]) / SUM([Hospital Goals - Secondary].[Goal])
```

3. Drag **Department** to Rows
4. Drag **Pct of Goal** to Columns
5. Format as Percentage (0 decimals)
6. Add a reference line at 100% (goal line)
7. Color by performance:
   - >100% = Green (exceeded)
   - <100% = Red (below)

**View 3: Revenue by Hospital Branch**

1. New worksheet: **"Revenue by Branch"**
2. Drag **Hospital Branch** to Rows
3. Drag **Department Type** to Rows (right of Branch)
4. Drag **Revenue** to Columns
5. Add Department to Color for detail
6. Sort by Revenue

Shows which branches and types generate most revenue.

**View 4: High-Risk Patient Revenue**

1. New worksheet: **"High Risk Revenue"**
2. Drag **Patient Risk Profile** to Columns
3. Drag **Revenue** to Rows
4. Change mark type to Pie chart
5. Shows revenue split: High risk vs. Low risk

**View 5: Top Performing Departments**

1. New worksheet: **"Top 5 Departments"**
2. Drag **Department** to Rows
3. Drag **Revenue vs Goal** (your calculated field) to Columns
4. Filter to show only departments where Revenue vs Goal > 0
5. Sort descending
6. Create a Top N filter:
   - Drag Department to Filters
   - Select **"Top"**
   - Top 5 by SUM(Revenue vs Goal)
7. Color green (they exceeded goals!)

---

### Exercise 6.2: Building the Dashboard

Now let's combine these into one dashboard.

**Step 1: Create New Dashboard**

1. Click the **New Dashboard** icon at bottom
2. Or: Click **Dashboard** → **New Dashboard**
3. Or: Press **Ctrl+D** / **Cmd+D**

**Step 2: Configure Dashboard Size**

In the Dashboard pane (left):

1. Under "Size," select **"Desktop Browser (1000 x 800)"**
2. Or choose "Automatic" for responsive design

**Step 3: Add Title**

1. From the Objects section (left bottom), drag **"Text"** to the top
2. Double-click to edit
3. Type:

```
Hospital Department Performance Dashboard
Actual Revenue vs. Annual Goals
```

4. Format:
   - Bold
   - Size: 16
   - Center aligned
5. Click **OK**

**Step 4: Add Your Views**

From the Dashboard pane, drag your worksheets to the canvas:

1. **Top half:** 
   - Drag **"Revenue vs Goals Bar"** to top
   - Make it take about 40% of height

2. **Middle left:**
   - Drag **"Goal Achievement %"** below Revenue vs Goals
   - Takes left half

3. **Middle right:**
   - Drag **"High Risk Revenue"** next to Goal Achievement
   - Takes right half

4. **Bottom:**
   - Drag **"Revenue by Branch"** to bottom left
   - Drag **"Top 5 Departments"** to bottom right

Tableau will automatically arrange them in containers.

**Step 5: Add Interactivity**

Let's make it interactive:

1. Click on **"Revenue vs Goals Bar"** in the dashboard
2. Click the dropdown arrow (upper right of that view)
3. Select **"Use as Filter"**

Now clicking a department filters all other views!

**Step 6: Add Context Text**

1. Drag another **Text** object below the title
2. Type:

```
Dashboard Purpose: Compare actual revenue performance against annual department goals.
Green indicates departments exceeding goals. Red indicates departments below target.

Instructions: Click on any department to filter all views.

Data Sources: Hospital Visits (6,000+ patient visits) | Hospital Goals (departmental targets)
```

3. Format: Size 10, left aligned
4. Click **OK**

**Step 7: Format for Professional Look**

1. **Remove unnecessary titles:**
   - For each worksheet, click dropdown
   - Uncheck "Title" if it's redundant

2. **Adjust spacing:**
   - Drag borders between views to resize
   - Make important views larger

3. **Add borders:**
   - Format → Shading
   - Add subtle borders between sections

4. **Color consistency:**
   - Make sure colors have meaning
   - Green = Good/Exceeded
   - Red = Bad/Below
   - Blue = Neutral/Actual

**Step 8: Add Filters (Optional)**

You can add global filters:

1. In any worksheet, drag **Hospital Branch** to Filters
2. Right-click on the filter → **"Apply to Worksheets"** → **"All Using This Data Source"**
3. Right-click again → **"Show Filter"**
4. In the dashboard, the filter appears - drag it to a good location

Now users can filter the entire dashboard by branch!

**Step 9: Add Dashboard Actions (Advanced)**

Let's add a highlight action:

1. Dashboard menu → **"Actions..."**
2. Click **"Add Action"** → **"Highlight"**
3. Name: "Highlight Department"
4. Run on: **"Hover"**
5. Source: All sheets
6. Target: All sheets
7. Target Highlighting: **"Selected Fields"**
8. Fields: Department
9. Click **OK**

Now hovering over a department highlights it across all views!

📖 **Reference:** [Build a Dashboard](https://help.tableau.com/current/pro/desktop/en-us/dashboards_create.htm)

---

### Exercise 6.3: Adding Insights

Let's add annotations to highlight key insights.

**Step 1: Identify a Key Insight**

Looking at your "Revenue vs Goals Bar," identify:
- Which department exceeded goals by the MOST?
- Which department fell shortest of goals?

**Step 2: Add an Annotation**

1. In the dashboard, hover over the top-performing department bar
2. Right-click → **"Annotate"** → **"Point"**
3. Type:

```
Top Performer!
Exceeded annual goal by $XXX,XXX
```

4. Adjust annotation position
5. Click **OK**

**Step 3: Add Another for Underperformer**

1. Right-click on the department most below goal
2. Annotate → Point
3. Type:

```
Needs Attention
$XXX,XXX below annual target
Action plan recommended
```

4. Click **OK**

**Step 4: Format Annotations**

1. Right-click annotation → **"Format Annotation"**
2. Choose:
   - Different colors (green for good, red for concern)
   - Appropriate sizing
   - Add borders or shading

---

### Exercise 6.4: Creating a Story (Optional Advanced)

Stories let you create guided narratives through your data.

**Step 1: Create New Story**

1. Click **Story** → **New Story**
2. Or: Click the **New Story** icon at bottom

**Step 2: Add Story Points**

1. **Story Point 1:** "Overall Performance"
   - Drag your dashboard to the story
   - Add caption: "Hospital-wide revenue vs. goals"

2. **Story Point 2:** "Top Performers"
   - Create a new worksheet showing only departments exceeding goals
   - Add to story
   - Caption: "These 5 departments exceeded their targets"

3. **Story Point 3:** "Areas for Improvement"
   - Create a worksheet showing only departments below goals
   - Add to story
   - Caption: "These departments need support to meet goals"

**Step 3: Add Navigator Style**

1. In Story pane, under "Navigator," choose:
   - **"Numbers"** (shows 1, 2, 3...)
   - **"Dots"** (shows • • •)
   - **"Caption boxes"** (shows full caption)

**Step 4: Present**

Click through your story points to present a narrative!

📖 **Reference:** [Stories](https://help.tableau.com/current/pro/desktop/en-us/stories.htm)

---

## Challenge Exercises

Test your skills with these challenges!

### Challenge 1: Add Time-Based Analysis

**Question:** Create a visualization showing how revenue trends over time compared to goals. Do certain months perform better?

**Hints:**
- Use Date of Admit (monthly)
- Show revenue trend line
- Add annual goal as reference line (divide by 12 for monthly target)
- Identify seasonality patterns

**Expected Output:** Line chart with trend and target line.

---

### Challenge 2: Doctor Performance vs. Department Goals

**Question:** Which doctors contribute most to their department reaching goals? Show top 3 doctors per department.

**Hints:**
- Use Department and Doctor
- Calculate each doctor's contribution to department revenue
- Use Top N filter
- Show as % of department goal

**Expected Output:** Bar chart showing top doctors' contribution to department goals.

---

### Challenge 3: Branch Comparison Dashboard

**Question:** Create a dashboard comparing the three hospital branches (East, Central, South) on their goal achievement.

**Hints:**
- Filter or group by Hospital Branch
- Show goal achievement % for each branch
- Break down by department within branch
- Use small multiples or separate views

**Expected Output:** Multi-view dashboard with branch comparisons.

---

### Challenge 4: Risk Profile Impact on Goals

**Question:** Do high-risk patients generate more revenue? How does this impact goal achievement?

**Hints:**
- Segment revenue by Patient Risk Profile
- Calculate what % of revenue comes from high-risk patients
- Compare to overall goal achievement
- Create a scatter plot or segmented analysis

**Expected Output:** Analysis showing risk profile impact.

---

### Challenge 5: Using the Excel Version

**Question:** Repeat the blending exercise using **Hospital Goals.xlsx** instead of the CSV. What differences do you notice?

**Hints:**
- Connect to Excel file
- Excel might have additional features (multiple sheets, formatting)
- Blend should work identically
- Compare performance (Excel vs. CSV)

**Expected Output:** Same analysis but with Excel data source.

---

## Submission Requirements

### What to Submit

**1. Tableau Workbook (.twbx)**

Save your completed workbook:
1. **File** → **Save As**
2. Choose **"Tableau Packaged Workbook (.twbx)"**
3. Name: **LastName_FirstName_Lab3_DataBlending.twbx**
4. This includes all your data sources

**2. Documentation (PDF or Word)**

Create a document with:

**Part A: Screenshots**
- Screenshot of Data Source page showing both data sources
- Screenshot of Edit Blend Relationships dialog
- Screenshot of "Revenue vs Goals" worksheet showing the blend
- Screenshot of "Goal Achievement %" worksheet
- Screenshot of your final dashboard
- Screenshot of at least one challenge exercise (if attempted)

**Part B: Written Explanations**

Answer these questions (3-4 sentences each):

1. **Explain the difference between joins and data blending.** When would you use each?

2. **What is a "join key"?** Why is it important?

3. **What does the chain link icon (🔗) represent?** How do you know if a blend is active?

4. **What does the asterisk (*) mean in blended data?** How would you fix it?

5. **Describe the blend relationship in your Hospital analysis.** Which field links the two data sources?

6. **Why is the secondary source aggregated (AGG) instead of SUM?** How does blending differ from joining in this way?

**Part C: Analysis Insights**

Based on your dashboard, answer:

1. **Overall Performance:**
   - How many departments exceeded their goals?
   - How many departments fell short?
   - What's the total revenue across all departments?
   - What's the total goal across all departments?

2. **Top Performers:**
   - Which department exceeded its goal by the largest amount?
   - Which department has the highest goal achievement percentage?

3. **Areas for Improvement:**
   - Which department fell shortest of its goal?
   - Which department has the lowest goal achievement percentage?

4. **Branch Analysis:**
   - Which hospital branch generates the most revenue?
   - Are there any patterns by branch?

5. **Recommendations:**
   - What actions would you recommend for underperforming departments?
   - What best practices can top performers share?

**Part D: Technical Documentation**

Document your data connections:

1. **Primary Data Source:**
   - Name: Hospital Visits - Primary
   - File type: CSV
   - Number of records: (approximately 6,000)
   - Key fields used: Department, Revenue, Hospital Branch, etc.

2. **Secondary Data Source:**
   - Name: Hospital Goals - Secondary
   - File type: CSV (or xlsx if you used that)
   - Number of records: (approximately 14 departments)
   - Key fields used: Department, Goal

3. **Blend Relationship:**
   - Linking field: Department
   - Relationship type: Automatic or Custom
   - Active on worksheets: (list them)

**3. Naming Convention**
- Workbook: **LastName_FirstName_Lab3_DataBlending.twbx**
- Documentation: **LastName_FirstName_Lab3_Documentation.pdf**

---

## Troubleshooting Guide

### Common Issues and Solutions

**Issue: "Cannot blend the secondary data source because there is no field to link on"**

**Cause:** No common field between data sources, or fields have different names.

**Solutions:**
1. **Check field names:**
   - Are they exactly the same? (case-sensitive)
   - "Department" ≠ "Dept" ≠ "department"

2. **Manually define relationship:**
   - Data → Edit Blend Relationships
   - Select Custom
   - Add field mapping manually

3. **Rename fields to match:**
   - In Data Source page
   - Right-click field → Rename
   - Make names identical

---

**Issue: Chain link icon is gray, blend not working**

**Cause:** Link is inactive.

**Solution:**
1. Click the gray chain link icon
2. It should turn orange
3. Values should update in view

---

**Issue: Seeing asterisks (*) instead of values**

**Cause:** Multiple values in secondary source for one primary value.

**Solutions:**
1. **Check for duplicates:**
   - View the secondary data source
   - Ensure linking field is unique
   - Remove duplicate rows

2. **Aggregate appropriately:**
   - Use SUM, AVG, MAX, or MIN
   - This tells Tableau how to handle multiples

3. **Link on additional fields:**
   - Add more fields to blend relationship
   - Makes the link more specific

---

**Issue: "Cannot mix aggregate and non-aggregate arguments"**

**Cause:** Trying to use secondary source field incorrectly in calculation.

**Solution:**
Reference secondary fields correctly:
```
Correct: SUM([Hospital Goals - Secondary].[Goal])
Wrong:   [Hospital Goals - Secondary].[Goal]
```

Always wrap secondary fields in aggregation.

---

**Issue: Values from secondary source don't appear**

**Cause:** 
- No matching values
- Link field has different data types
- Link is inactive

**Solutions:**
1. **Check for matches:**
   - Do "Department" values match exactly?
   - Spelling must be identical
   - Check for extra spaces

2. **Verify data types:**
   - Both fields must be same type
   - Text = Text
   - Number = Number

3. **Activate the link:**
   - Look for chain link icon
   - Click to make it orange

4. **Check the data:**
   - Create separate views of each source
   - Verify matching values exist

---

**Issue: Performance is very slow**

**Cause:** Blending large datasets can be slow.

**Solutions:**
1. **Use joins instead if possible:**
   - If data can be in one source, join it

2. **Aggregate before blending:**
   - Pre-aggregate secondary source
   - Reduces data volume

3. **Use extracts:**
   - Create extracts of data sources
   - Much faster than live connections

4. **Filter data:**
   - Use filters to reduce data volume
   - Date ranges, specific departments, etc.

---

**Issue: Joined data has duplicate rows**

**Cause:** Join created more rows than expected (many-to-many relationship).

**Solution:**
- Don't use join; use blend instead
- Blending handles different granularities better
- Or: Check your join key - might not be unique

---

**Issue: Can't see secondary data source in Data pane**

**Cause:** No secondary source connected.

**Solution:**
1. Look at top of Data pane
2. Should see dropdown with data source names
3. If only one source:
   - Connect to additional data source
   - Data → New Data Source

---

**Issue: Downloaded data files won't open**

**Cause:** 
- File corrupted
- Wrong application
- Blocked download

**Solutions:**
1. **Re-download:**
   - Try downloading again
   - Use different browser
   - Check Downloads folder

2. **Unblock file (Windows):**
   - Right-click file → Properties
   - Check "Unblock" box
   - Click OK

3. **Verify file type:**
   - CSV opens in Tableau (don't need Excel)
   - Check file extension (.csv, .xlsx)

---

**Issue: "Cannot create extract" error**

**Cause:** File permission or disk space issue.

**Solution:**
1. Check disk space
2. Run Tableau as administrator
3. Save to different location
4. Use live connection instead of extract

---

### Getting Help

**Tableau's Built-In Help:**
1. Press **F1** in Tableau
2. Click the **?** icon in toolbar
3. Visit Tableau Help: [https://help.tableau.com](https://help.tableau.com)

**Useful Resources:**
- [Join Your Data](https://help.tableau.com/current/pro/desktop/en-us/joining_tables.htm)
- [Blend Your Data](https://help.tableau.com/current/pro/desktop/en-us/multiple_connections.htm)
- [Troubleshoot Blending](https://help.tableau.com/current/pro/desktop/en-us/multipleconnections_troubleshooting.htm)

**Community Resources:**
- Tableau Community Forums
- YouTube tutorials
- Stack Overflow (tag: tableau)

**Contact Your Instructor:**
- Include screenshots of error messages
- Describe what you were trying to do
- Share your .twbx file if possible

---

## Key Concepts Summary

### Joins

**Definition:** Combine tables from the same data source at the row level.

**When to Use:**
- Same Excel file (different sheets)
- Same database (different tables)
- Need row-level detail
- Want best performance

**How:**
- Configure on Data Source page
- Physical layer (join canvas)
- Define join type and join key
- Creates one merged table

**Join Types:**
- Inner (only matches)
- Left (all from left + matches)
- Right (all from right + matches)
- Full Outer (everything)

---

### Data Blending

**Definition:** Combine data from different sources at the aggregate level.

**When to Use:**
- Different files (CSV + Excel)
- Different databases
- Different granularities
- Published data sources

**How:**
- Connect to multiple sources
- Configure on worksheet
- Link via common dimensions
- Tableau aggregates then combines

**Key Features:**
- Primary and secondary sources
- Chain link icon (🔗)
- LEFT JOIN behavior
- AGG() instead of SUM()

---

### Decision Guide

**Same Source?** → JOIN  
**Different Sources?** → BLEND  
**Row-level detail needed?** → JOIN  
**Aggregated comparison?** → BLEND  
**Best performance?** → JOIN  
**Most flexibility?** → BLEND

---

## Additional Learning Resources

**Official Tableau Documentation:**
- **Data Source Basics:** [https://help.tableau.com/current/pro/desktop/en-us/datasource_prepare.htm](https://help.tableau.com/current/pro/desktop/en-us/datasource_prepare.htm)
- **Relationships:** [https://help.tableau.com/current/pro/desktop/en-us/relate_tables.htm](https://help.tableau.com/current/pro/desktop/en-us/relate_tables.htm)
- **Joins:** [https://help.tableau.com/current/pro/desktop/en-us/joining_tables.htm](https://help.tableau.com/current/pro/desktop/en-us/joining_tables.htm)
- **Blending:** [https://help.tableau.com/current/pro/desktop/en-us/multiple_connections.htm](https://help.tableau.com/current/pro/desktop/en-us/multiple_connections.htm)

**Video Tutorials:**
- Search "Tableau Data Blending Tutorial" on YouTube
- Search "Tableau Joins vs Blending" on YouTube
- Tableau's official training videos

**Practice:**
- Try blending other data sources
- Experiment with different join types
- Use Sample - Superstore for practice

---

## Glossary

**Aggregate:** Combine multiple values into a summary (SUM, AVG, COUNT, etc.).

**Blend:** Combine data from different data sources based on common dimensions.

**Data Source:** A connection to a file or database in Tableau.

**Join:** Combine tables from the same data source based on a common field.

**Join Key:** The field(s) used to match rows between tables in a join.

**Link:** Connection between data sources in a blend (shown by chain link icon).

**Logical Layer:** Canvas where you define relationships between tables.

**Physical Layer:** Canvas where you define joins between tables.

**Primary Data Source:** First data source used in a view (defines the view in blends).

**Secondary Data Source:** Additional data sources blended with the primary.

---

## Tips for Success

1. **Plan your data strategy:**
   - Understand your data sources before connecting
   - Decide join vs. blend early
   - Draw a diagram if helpful

2. **Check your data:**
   - Verify field names match (for blending)
   - Ensure data types are correct
   - Look for duplicates that cause problems

3. **Start simple:**
   - Connect to one source first
   - Verify it works
   - Then add additional sources

4. **Use descriptive names:**
   - Rename data sources clearly
   - Makes troubleshooting easier
   - Helps when you have many sources

5. **Test your blends:**
   - Create simple views first
   - Verify values are correct
   - Then build complex dashboards

6. **Watch for the asterisk:**
   - Indicates a problem with blend
   - Check for duplicate values
   - Aggregate appropriately

7. **Document your work:**
   - Note which fields link data sources
   - Explain your blend relationships
   - Makes debugging easier later

8. **Save frequently:**
   - Use .twbx to include data
   - Create backups before major changes
   - Test on copies if unsure

9. **Learn from examples:**
   - Study Tableau's sample workbooks
   - Reverse-engineer dashboards you like
   - Ask "how did they do that?"

10. **Practice makes perfect:**
    - Try different scenarios
    - Blend various data sources
    - Experiment with both methods

---

## Congratulations!

You've completed Lab 3 on Data Connections, Joins, and Blending! You now have the skills to combine data from multiple sources - a critical capability for real-world analytics.

**Key Takeaways:**

✅ Joins combine tables from the same source  
✅ Blending combines data from different sources  
✅ Chain link icon (🔗) indicates active blend  
✅ Blends work like LEFT JOIN  
✅ Secondary data is aggregated (AGG)  
✅ Choose the right method for your scenario  
✅ Can build dashboards with multiple sources  

**Next Steps:**

- Apply these techniques to your own data
- Experiment with more complex joins
- Try blending 3+ data sources
- Build real-world dashboards combining multiple files
- Explore relationships (Tableau 2020.2+)

---

**Lab Created By:** Dr. Lee  
**Last Updated:** 2025  
**Questions?** Contact your instructor or visit office hours

**Download Links:**
- Hospital Visits: [Download CSV](https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2003/Hospital%20Visits.csv)
- Hospital Goals (CSV): [Download CSV](https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2003/Hospital%20Goals.csv)
- Hospital Goals (Excel): [Download XLSX](https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2003/Hospital%20Goals.xlsx)

**Happy Blending!** 🎉📊
