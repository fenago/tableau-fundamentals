# Tableau Lab 2: Creating Your First Visualizations

**Course:** Data Analytics & Visualization  
**Software:** Tableau Desktop Public Edition  
**Dataset:** Superstore Sales Data  
**Estimated Time:** 120-150 minutes  
**Difficulty:** Beginner

---

## 📋 Table of Contents

1. [Learning Objectives](#learning-objectives)
2. [Prerequisites](#prerequisites)
3. [What You'll Learn](#what-youll-learn)
4. [Understanding Visualizations](#understanding-visualizations)
5. [Part 1: Download and Setup](#part-1-download-and-setup)
6. [Part 2: Your First Bar Chart](#part-2-your-first-bar-chart)
7. [Part 3: Creating Line Charts](#part-3-creating-line-charts)
8. [Part 4: Understanding the Marks Card](#part-4-understanding-the-marks-card)
9. [Part 5: Adding Colors and Details](#part-5-adding-colors-and-details)
10. [Part 6: Filters and Sorting](#part-6-filters-and-sorting)
11. [Part 7: Building Multiple Visualizations](#part-7-building-multiple-visualizations)
12. [Part 8: Creating Your First Dashboard](#part-8-creating-your-first-dashboard)
13. [Challenge Exercises](#challenge-exercises)
14. [Submission Requirements](#submission-requirements)
15. [Troubleshooting Guide](#troubleshooting-guide)

---

## 🎯 Learning Objectives

By the end of this lab, you will be able to:

- Connect to a CSV data file in Tableau
- Create bar charts to compare categorical data
- Build line charts to show trends over time
- Use the Marks card to customize visualizations
- Apply colors, sizes, and labels to your charts
- Filter data to focus on specific information
- Sort data to highlight top or bottom values
- Combine multiple visualizations into a dashboard
- Choose the right chart type for your data

---

## 📚 Prerequisites

**Required Software:**
- **Tableau Desktop Public Edition** (free version)
  - Download: [https://public.tableau.com/app/discover](https://public.tableau.com/app/discover)
  - Make sure you have the latest version installed

**Required Dataset (You'll download this):**
- **Superstore.csv** - Retail sales data with products, customers, and orders

**What You Should Already Know:**
- How to navigate your computer and find downloaded files
- Basic understanding of spreadsheets (rows and columns)
- Willingness to learn and experiment!

**Official Documentation (Keep These Open!):**
- **Main Help:** [https://help.tableau.com/current/pro/desktop/en-us/default.htm](https://help.tableau.com/current/pro/desktop/en-us/default.htm)
- **Getting Started:** [https://help.tableau.com/current/pro/desktop/en-us/gettingstarted_overview.htm](https://help.tableau.com/current/pro/desktop/en-us/gettingstarted_overview.htm)
- **Build Common Chart Types:** [https://help.tableau.com/current/pro/desktop/en-us/buildexamples_overview.htm](https://help.tableau.com/current/pro/desktop/en-us/buildexamples_overview.htm)
- **Bar Charts:** [https://help.tableau.com/current/pro/desktop/en-us/buildexamples_bar.htm](https://help.tableau.com/current/pro/desktop/en-us/buildexamples_bar.htm)
- **Line Charts:** [https://help.tableau.com/current/pro/desktop/en-us/buildexamples_line.htm](https://help.tableau.com/current/pro/desktop/en-us/buildexamples_line.htm)

---

## 🎓 What You'll Learn

**The Big Picture:**

Data visualization turns numbers into pictures that our brains can understand quickly. Instead of looking at thousands of rows in a spreadsheet, you can see patterns, trends, and insights instantly through charts and graphs.

**In This Lab:**

You'll learn to create the TWO most fundamental chart types:

1. **BAR CHARTS** - Compare things
   - Which product sells the most?
   - Which region has highest profit?
   - What are the top 10 customers?

2. **LINE CHARTS** - Show trends over time
   - Are sales increasing or decreasing?
   - What's the sales pattern by month?
   - When do we make the most profit?

**Why These Matter:**

These two chart types solve 80% of business questions! Master these, and you'll be able to communicate insights effectively.

---

## 🔍 Understanding Visualizations

Before we start building, let's understand what makes a good visualization.

### What is Data Visualization?

**Definition:** Data visualization is the graphical representation of information and data using visual elements like charts, graphs, and maps.

**Why We Need It:**

Our brains process visual information 60,000 times faster than text. A good chart can reveal insights that would take hours to find in raw data.

**Example:**

Instead of reading: "Sales in Q1: $50K, Q2: $75K, Q3: $60K, Q4: $90K"

A line chart shows you instantly: Sales are trending upward with seasonal variation!

### Chart Types Overview

| Chart Type | Best For | Example Question |
|------------|----------|------------------|
| **Bar Chart** | Comparing categories | Which product category generates most revenue? |
| **Line Chart** | Trends over time | How have sales changed this year? |
| **Pie Chart** | Parts of a whole | What percentage of sales comes from each region? |
| **Scatter Plot** | Relationships | Does discount affect profit? |
| **Map** | Geographic data | Where are our customers located? |

**In This Lab:**

We'll focus on Bar and Line charts - the foundation of data visualization!

---

## Part 1: Download and Setup

### Exercise 1.1: Downloading Your Data

Let's get the Superstore dataset.

**Step 1: Create a Lab Folder**

1. On your computer, create a folder: **Tableau_Lab_2**
2. Suggested location:
   - Windows: `Documents\Tableau_Labs\Lab_2`
   - Mac: `Documents/Tableau_Labs/Lab_2`

**Step 2: Download the Superstore Data (CSV Version)**

1. Open your web browser
2. Navigate to:

```
https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2002/Superstore.csv
```

3. The file should download automatically
4. Move it to your **Tableau_Lab_2** folder

**Step 3: Download Superstore (Excel Version - Optional)**

If you prefer Excel format or want to practice with both:

```
https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2002/Superstore.xlsx
```

**Note:** Both files contain the same data. We'll use the CSV version in this lab.

**Step 4: Verify Your Download**

Check your **Tableau_Lab_2** folder contains:
- ✓ Superstore.csv

**Don't open it yet!** We'll connect to it directly in Tableau.

---

### Exercise 1.2: Understanding Your Dataset

Before connecting, let's understand what data we're working with.

**The Superstore Dataset:**

This dataset contains sales transactions from a fictional retail company. Think of it like data from Amazon or Walmart, but simplified for learning.

**Key Fields You'll Use:**

**Dimensions (Categories - Blue pills):**
- **Category**: Product category (Furniture, Office Supplies, Technology)
- **Sub-Category**: Specific product type (Phones, Chairs, Binders, etc.)
- **Region**: Geographic region (East, West, Central, South)
- **State**: US State
- **City**: City name
- **Customer Name**: Name of customer
- **Customer Segment**: Type of customer (Consumer, Corporate, Home Office)
- **Order Date**: When order was placed
- **Ship Date**: When order was shipped
- **Ship Mode**: Shipping method

**Measures (Numbers - Green pills):**
- **Sales**: Revenue in dollars
- **Profit**: Profit in dollars
- **Quantity**: Number of items ordered
- **Discount**: Discount percentage
- **Shipping Cost**: Cost to ship

**Understanding Dimensions vs. Measures:**

Think of dimensions as the "what" and measures as the "how much":
- Dimension: What region? → East
- Measure: How much sales? → $50,000

---

### Exercise 1.3: Connecting to Your Data

Now let's load the data into Tableau!

**Step 1: Open Tableau Desktop Public Edition**

1. Launch Tableau from your computer
2. Wait for the Start page to appear

**Step 2: Connect to Your CSV File**

1. On the Start page, look at the left side under **"Connect"**
2. Find the section **"To a File"**
3. Click **"Text file"**
4. A file browser window opens
5. Navigate to your **Tableau_Lab_2** folder
6. Select **Superstore.csv**
7. Click **"Open"**

**Step 3: Explore the Data Source Page**

Tableau opens the **Data Source** page. Let's explore it!

**What You're Looking At:**

1. **Top Left (Connections):**
   - Shows "Superstore.csv" - your data source

2. **Center (Canvas):**
   - Shows "Superstore" table
   - This is where you'd add more tables if needed

3. **Bottom (Data Grid):**
   - Preview of your data (first 1,000 rows)
   - All your columns with sample values

**Step 4: Examine the Data Types**

Look at the icons above each column name in the data grid:

**Icons you'll see:**
- **Abc** (Text): Category, Customer Name, State, City
- **#** (Number): Sales, Profit, Quantity, Discount
- **📅** (Date): Order Date, Ship Date
- **🌐** (Geographic): State, City (may have globe icon)

**If a data type looks wrong:**
1. Click the icon above the column
2. Select the correct type from the menu

**Common fixes needed:**
- Order Date should be 📅 (Date), not Abc (Text)
- Sales should be # (Number), not Abc (Text)

**Step 5: Rename Your Data Source (Optional but Recommended)**

1. At the top left, you see "Superstore (Superstore.csv)"
2. Right-click on it
3. Select **"Rename"**
4. Type: **Superstore Sales**
5. Press Enter

This makes it easier to identify later!

📖 **Reference:** [Connect to a File](https://help.tableau.com/current/pro/desktop/en-us/examples_text.htm)

---

### Exercise 1.4: Your First Look at the Data

Before building visualizations, let's peek at the raw data.

**Step 1: View Data in Grid**

You're already looking at it! The data grid at the bottom shows:
- Rows: Each row = one line item from an order
- Columns: Different attributes and measurements

**Step 2: Scroll Through the Data**

1. Use the scrollbar at the bottom to see all columns
2. Use the side scrollbar to see more rows
3. Notice patterns:
   - Multiple items can be on the same Order ID
   - Some orders have discounts, some don't
   - Profit can be positive or negative (losses!)

**Step 3: Understanding the Data Structure**

**What is a "row"?**

Each row represents ONE line item from ONE order.

Example:
- Order ID 6: Customer bought scissors, 2 units, $7 sales
- Order ID 193: Customer bought 25 boxes, $312 sales

**Step 4: Check Data Volume**

Look at the bottom left of the data grid:
- Should say something like "9,427 rows"
- This means 9,427+ line items in the dataset
- Spanning multiple years (2017-2020)

**Key Insight:**

This is too much data to understand by looking at rows. We need visualizations!

---

## Part 2: Your First Bar Chart

Bar charts compare categories. Let's build one to see which product categories generate the most sales!

### Exercise 2.1: Creating a Simple Bar Chart

**Step 1: Go to a Worksheet**

1. At the bottom of the screen, click **"Sheet 1"**
2. You're now in the **Worksheet** view
3. This is where you'll build your visualizations

**Understanding the Worksheet:**

**Left Side - Data Pane:**
- Lists all your fields
- **Dimensions** (blue) at top
- **Measures** (green) at bottom

**Center - Canvas:**
- Empty white space where your chart will appear
- Has shelves: Columns, Rows, Marks card

**Top - Toolbar:**
- Tools for formatting and customizing

**Right - Show Me:**
- Suggests chart types based on your selections

**Step 2: Rename Your Sheet**

1. Right-click on "Sheet 1" at the bottom
2. Select **"Rename Sheet"**
3. Type: **Sales by Category**
4. Press Enter

Good practice: Always name sheets descriptively!

**Step 3: Build Your First Chart!**

Now for the magic moment:

1. From the Data pane (left), find **"Category"** under Dimensions
2. **Drag** "Category" to the **Rows** shelf (the empty space that says "Drop field here")
3. You should see three categories appear: Furniture, Office Supplies, Technology

4. Now find **"Sales"** under Measures
5. **Drag** "Sales" to the **Columns** shelf

**What Just Happened?**

Tableau created a bar chart showing sales for each category!

**What You Should See:**
- Three horizontal bars (one per category)
- Technology appears to have the highest sales
- Each bar's length represents total sales
- The pill on Columns says **"SUM(Sales)"** (Tableau automatically summed the sales)

**Step 4: Understanding What Tableau Did**

When you dragged Sales to the view, Tableau:
1. Added up ALL sales for each category (aggregation)
2. Created a bar for each category
3. Made the bar length proportional to total sales
4. Added axis labels and numbers

You just answered: "Which category generates the most sales?"

**Step 5: Read the Chart**

Hover your mouse over each bar:
- A tooltip appears showing exact values
- Example: "Technology: $836,154"

The bars tell the story:
- Technology: Highest sales (~$836K)
- Furniture: Medium sales (~$742K)
- Office Supplies: Similar to Furniture (~$719K)

**Congratulations!** 🎉 You created your first Tableau visualization!

📖 **Reference:** [Build a Bar Chart](https://help.tableau.com/current/pro/desktop/en-us/buildexamples_bar.htm)

---

### Exercise 2.2: Making Your Bar Chart Vertical

Right now your bars are horizontal. Let's make them vertical (more common for bar charts).

**Step 1: Swap Rows and Columns**

**Method 1 - Drag and Drop:**
1. Drag the **"Category"** pill from Rows
2. Drop it on **Columns**
3. Drag the **"SUM(Sales)"** pill from Columns
4. Drop it on **Rows**

**Method 2 - Use the Swap Button:**
1. Look in the toolbar for the **Swap** icon (two arrows forming a square)
2. Click it
3. Rows and Columns instantly switch!

**What Changed:**

Now you have vertical bars:
- Categories along the bottom (X-axis)
- Sales going up (Y-axis)
- Taller bars = more sales

**Why This Matters:**

Visual convention: Vertical bars often feel more natural for showing "how much" or "how high."

**Step 2: Examine the Axes**

Look at your chart:

**X-Axis (bottom):**
- Shows the three categories
- Furniture, Office Supplies, Technology

**Y-Axis (left side):**
- Shows sales amounts
- Starts at $0
- Goes up to ~$900K

**The bars:**
- Height represents sales volume
- Technology is tallest (most sales)

---

### Exercise 2.3: Adding Color

Let's make this chart more visually appealing!

**Step 1: Color by Category**

1. Look at the **Marks card** (below the Data pane, shows "Automatic")
2. Find **"Category"** in the Data pane
3. **Drag** "Category" to the **Color** button on the Marks card

**What Happened:**

Each category now has its own color:
- Furniture: Blue
- Office Supplies: Orange  
- Technology: Red (or different colors)

**Step 2: Understanding the Legend**

A color legend appeared on the right side:
- Shows which color = which category
- You can click on items to highlight them

**Step 3: Customize the Colors**

Let's change the colors:

1. Click on **Color** on the Marks card
2. Click **"Edit Colors..."**
3. A dialog box opens showing current color assignments

4. To change a color:
   - Select "Furniture"
   - Click on the color palette
   - Choose a new color (try a darker blue)
   - Click "OK"

5. Repeat for other categories if desired
6. Click **"OK"** to close the dialog

**Pro Tip:** Choose meaningful colors!
- Green often represents "good" or "profitable"
- Red often represents "bad" or "loss"
- Blue is neutral

---

### Exercise 2.4: Adding Labels

Let's add exact sales numbers to each bar.

**Step 1: Add Value Labels**

1. Find **"Sales"** in the Measures section
2. **Drag** "Sales" to the **Label** button on the Marks card

**What Happened:**

Each bar now shows the exact sales value!
- You can see the numbers without hovering

**Step 2: Format the Labels**

The numbers might show many decimal places. Let's fix that:

1. Click on **Label** on the Marks card
2. In the menu that appears, check **"Show mark labels"** (should already be checked)
3. Click the **"..." button** next to "Text"
4. Or simply right-click on a label in the view → **"Format"**

5. In the Format pane (left side):
   - Find **"Numbers"**
   - Click the dropdown
   - Select **"Currency (Custom)"**
   - Set Decimal places to **0**
   - Click **OK**

**What Changed:**

Now labels show as currency:
- $836,154 instead of 836154.47123
- Much more readable!

**Step 3: Adjust Label Position**

If labels overlap or look awkward:

1. Click **Label** on Marks card
2. Try different **"Alignment"** options
3. Try **"Horizontal"** alignment
4. Choose **"Center"** or **"Top"**

---

### Exercise 2.5: Sorting Your Bars

Let's organize the bars by sales amount (highest to lowest).

**Step 1: Sort Descending**

**Method 1 - Toolbar Button:**
1. Look in the toolbar at the top
2. Find the **Sort Descending** button (looks like bars going down with arrow)
3. Click it

**Method 2 - Right-Click:**
1. Right-click on the axis (where it says "Category")
2. Select **"Sort..."**
3. Choose:
   - Sort By: **"Field"**
   - Field Name: **"Sales"**
   - Aggregation: **"Sum"**
   - Sort Order: **"Descending"**
4. Click **OK**

**What Changed:**

Bars are now ordered by value:
1. Technology (highest sales)
2. Furniture (medium)
3. Office Supplies (lowest)

**Why This Matters:**

Sorted charts make comparisons instant:
- Top performer immediately visible
- Easy to see rankings
- Brain processes the pattern faster

---

### Exercise 2.6: Adding a Title

Every chart needs a good title!

**Step 1: Edit the Title**

1. At the top of your worksheet, you'll see the sheet name: "Sales by Category"
2. Double-click on it
3. Or: Right-click → **"Edit Title..."**

**Step 2: Write a Descriptive Title**

In the Edit Title dialog:

1. Clear the existing text
2. Type a meaningful title:

```
Total Sales by Product Category
```

Or make it more specific:

```
Technology Leads in Sales Revenue Across All Categories
```

3. Click **OK**

**Step 3: Format the Title (Optional)**

1. Select your title text
2. Make it bold
3. Increase font size
4. Center align

**Good Title Practices:**
- ✅ Describes what the chart shows
- ✅ Includes key insight if space allows
- ✅ Uses action words or clear labels
- ❌ Avoid vague titles like "Chart 1" or "Data"

---

## Part 3: Creating Line Charts

Line charts show trends over time. Let's build one to see how sales change throughout the years!

### Exercise 3.1: Your First Line Chart

**Step 1: Create a New Worksheet**

1. At the bottom, click the **New Worksheet** button (icon looks like a page with +)
2. Or: Press **Ctrl+M** (Windows) / **Cmd+M** (Mac)
3. Rename the new sheet: **Sales Over Time**

**Step 2: Add Date to Columns**

1. Find **"Order Date"** under Dimensions
2. **Drag** "Order Date" to **Columns**

**What Happened:**

Tableau automatically converted the date to **YEAR(Order Date)**:
- Created column headers: 2017, 2018, 2019, 2020
- Tableau is smart about dates!

**Step 3: Add Sales to Rows**

1. Find **"Sales"** under Measures
2. **Drag** "Sales" to **Rows**

**What You See:**

A line chart! Tableau automatically chose a line because you used a date field.

**The line shows:**
- Sales for each year
- Trend from 2017 to 2020
- Overall pattern

**Step 4: Read the Trend**

Look at your line:
- Does it go up? (Sales increasing)
- Does it go down? (Sales decreasing)
- Is it flat? (Sales stable)
- Are there dips or peaks?

Hover over each point to see exact values.

**What the Data Shows:**

You should see sales generally increasing from 2017 to 2020 - a positive trend!

📖 **Reference:** [Build a Line Chart](https://help.tableau.com/current/pro/desktop/en-us/buildexamples_line.htm)

---

### Exercise 3.2: Changing Date Granularity

Right now you're viewing by YEAR. Let's see MONTHLY trends.

**Step 1: Understand Date Hierarchies**

Tableau organizes dates in levels:
- Year (2020)
- Quarter (Q1, Q2, Q3, Q4)
- Month (January, February, etc.)
- Week
- Day

**Step 2: Drill Down to Month**

1. Click on the **YEAR(Order Date)** pill on Columns
2. You'll see a little **+** sign appear on the left side of the pill
3. Click the **+** sign

**What Happened:**

Tableau added **QUARTER(Order Date)** to your view:
- Now you see quarterly data
- More detailed than yearly

**Step 3: Continue to Month**

1. Click the **+** sign on **QUARTER(Order Date)**
2. Now **MONTH(Order Date)** is added
3. Your line shows monthly trends!

**Step 4: Remove Intermediate Levels**

You probably don't need Year and Quarter cluttering the view:

1. Right-click on **YEAR(Order Date)** pill
2. Select **"Remove"**
3. Right-click on **QUARTER(Order Date)** pill
4. Select **"Remove"**

Now you have only MONTH showing - much cleaner!

**What You See:**

A more detailed line chart showing monthly patterns:
- Seasonal trends become visible
- You can see which months are strong
- Which months are weak

---

### Exercise 3.3: Understanding Continuous vs. Discrete Dates

This is important! Dates can display in two ways.

**Current State: Discrete (Blue Pill)**

If your **MONTH(Order Date)** pill is BLUE:
- Each month is a separate category
- Chart shows individual month headers

**Try Continuous (Green Pill):**

1. Right-click on **MONTH(Order Date)** (blue pill)
2. Hover over the date value (you'll see "May 2017", "June 2017", etc. with a blue or green indicator)
3. Select the **GREEN** option (continuous)

**What Changed:**

- The pill turned GREEN
- The X-axis becomes a continuous timeline
- Looks more like a traditional line chart
- Gaps between data points are proportional to actual time

**Difference Summary:**

| Discrete (Blue) | Continuous (Green) |
|-----------------|-------------------|
| Separate categories | Continuous scale |
| Category headers | Date axis |
| Best for comparing periods | Best for showing trends |

**Which to Use?**

- **Discrete**: Comparing monthly totals
- **Continuous**: Seeing smooth trends over time

Try both and see which you prefer!

---

### Exercise 3.4: Adding Multiple Measures

Let's compare Sales AND Profit on the same chart.

**Step 1: Add Profit to Rows**

1. Find **"Profit"** under Measures
2. **Drag** "Profit" to **Rows**
3. Drop it to the **RIGHT** of **SUM(Sales)**

**What Happened:**

Two separate lines now appear:
- One for Sales
- One for Profit
- Each with its own Y-axis

**Problem:**

The two Y-axes have very different scales:
- Sales axis: $0 to $150K
- Profit axis: $0 to $20K

This makes comparison difficult!

**Step 2: Synchronize Axes**

1. Right-click on the **Profit** axis (right side)
2. Select **"Synchronize Axis"**

**What Changed:**

Now both lines use the same scale:
- Both measure from $0 to $150K
- Easier to compare relative magnitudes

**Note:** This only works well if the values are similar in scale!

**Step 3: Add Colors**

Let's make it easier to distinguish the lines:

1. Look at the **Marks** shelf
2. You should see multiple Marks cards now:
   - All (affects everything)
   - SUM(Sales)
   - SUM(Profit)

3. Click on the **SUM(Sales)** card
4. Click **Color**
5. Choose a color (e.g., Blue)

6. Click on the **SUM(Profit)** card
7. Click **Color**
8. Choose a different color (e.g., Green)

**Now you can easily see:**
- Sales line (blue): Higher, upward trend
- Profit line (green): Lower, follows similar pattern

---

### Exercise 3.5: Adding Markers to Lines

Make data points more visible!

**Step 1: Add Markers**

1. Click on the **All** Marks card (affects all lines)
2. Click on **Color**
3. Click **"Markers"** tab at the top
4. Check **"Show markers"**
5. Adjust **"Size"** slider if needed
6. Click **OK**

**What Changed:**

Each data point now has a circle marker:
- Makes individual months easier to see
- Easier to hover for exact values
- More visually engaging

**Step 2: Alternative Method - Mark Type**

You can also change the entire mark type:

1. On the **All** Marks card, click the dropdown that says "Line"
2. Try **"Shape"** instead
3. This shows only the points, no line!

4. Click it again and select **"Line"** to go back

**Pro Tip:**

Line + markers is a great combination for monthly or quarterly data!

---

## Part 4: Understanding the Marks Card

The Marks card is your control center for customizing visualizations. Let's master it!

### Exercise 4.1: Exploring the Marks Card

**Step 1: Locate the Marks Card**

It's below the Data pane, showing:
- A dropdown (currently says "Automatic" or "Bar" or "Line")
- Buttons: Color, Size, Label, Detail, Tooltip

**Step 2: Understanding Mark Types**

Click the dropdown on the Marks card. You'll see options:

| Mark Type | What It Creates | Best For |
|-----------|----------------|----------|
| **Automatic** | Tableau decides | Let Tableau choose |
| **Bar** | Bars | Comparing categories |
| **Line** | Lines | Trends over time |
| **Area** | Filled area under line | Cumulative trends |
| **Square** | Squares | Heat maps |
| **Circle** | Circles/Dots | Scatter plots |
| **Shape** | Custom shapes | Special markers |
| **Text** | Text labels | Tables, labels |
| **Map** | Geographic map | Location data |
| **Pie** | Pie slices | Parts of whole (use sparingly!) |
| **Gantt Bar** | Horizontal timeline bars | Project timelines |
| **Polygon** | Custom shapes | Custom maps |
| **Density** | Density visualization | Lots of data points |

**Step 3: Try Different Mark Types**

Go back to your **Sales by Category** sheet:

1. Currently shows bars
2. Click the Marks dropdown
3. Try **"Circle"**
   - Bars become dots

4. Try **"Text"**
   - Shows values as text only

5. Try **"Square"**
   - Shows as squares

6. Return to **"Bar"** - the best choice for this data!

**Key Insight:**

Tableau usually picks the right mark type automatically, but you can override it when needed!

---

### Exercise 4.2: The Color Button

Color makes visualizations pop and can encode additional information.

**Create a New Sheet: Sales by Region**

1. New worksheet
2. Rename: **Sales by Region**
3. Drag **"Region"** to Rows
4. Drag **"Sales"** to Columns
5. Sort descending

**Step 1: Apply Solid Color**

1. On Marks card, click **Color**
2. Choose any color you like
3. All bars become that color

**Step 2: Color by Category**

1. Drag **"Category"** to the **Color** button on Marks card

**What Happened:**

Each region's bar is now segmented by category:
- You see multiple colors stacked in each bar
- This is a **stacked bar chart**
- Shows how each region's sales breaks down by category

**Step 3: Adjust Transparency**

1. Click **Color** on Marks card
2. Look for **"Opacity"** slider
3. Drag it left to make colors more transparent
4. Drag right to make them more solid
5. Try 75% opacity

**Step 4: Add Borders**

1. Still in the Color menu
2. Find **"Effects"**
3. Click **"Border"**
4. Choose a color (black or dark gray)
5. Click **OK**

Now each color section has a visible border!

---

### Exercise 4.3: The Size Button

Control how big or small your marks appear.

**Go to Your Sales Over Time Sheet**

**Step 1: Adjust Line Thickness**

1. On Marks card, click **Size**
2. A slider appears
3. Drag right to make the line thicker
4. Drag left to make it thinner
5. Try a medium thickness

**Step 2: Adjust Marker Size**

If you added markers earlier:

1. The **Size** slider also controls marker size
2. Bigger slider = bigger markers
3. Find a balanced size where markers are visible but not overwhelming

**Go to Sales by Category Sheet**

**Step 3: Adjust Bar Width**

1. Click **Size** on Marks card
2. Drag the slider
3. Notice bars get fatter or skinnier

**Pro Tip:**

Tableau automatically sets good default sizes, but you can fine-tune for emphasis or space constraints.

---

### Exercise 4.4: The Label Button

Labels display values directly on your charts.

**Step 1: Show/Hide Labels**

1. On Sales by Category sheet
2. Click **Label** on Marks card
3. Check **"Show mark labels"**
4. Values appear on bars

**Step 2: Customize Label Content**

1. Still in the Label menu
2. Click the **"..."** button next to "Text"
3. A dialog opens showing what to display

4. You can add multiple fields:
   - Currently shows **<SUM(Sales)>**
   - You can add Category name
   - Drag **"Category"** from left list
   - Now labels show both category and sales

**Step 3: Format Labels**

1. Back in the Label menu
2. Choose font style (Bold, Italic)
3. Choose alignment (Center, Top, Bottom)
4. Choose font color

**Step 4: Callouts vs. Labels**

Try different label types:

1. In Label menu, find **"Marks to Label"**
2. Options:
   - **All**: Label everything
   - **Min/Max**: Label only highest and lowest
   - **Selected**: Label only what you click

3. Try **"Min/Max"** - labels only on extremes!

**Best Practice:**

- Use labels when values are important
- Don't overcrowd with too many labels
- Make sure labels don't overlap

---

### Exercise 4.5: The Detail Button

Detail adds granularity without changing the visualization type.

**Create New Sheet: Monthly Sales Detail**

1. New worksheet: **Monthly Sales Detail**
2. Drag **"Order Date"** to Columns (it becomes YEAR)
3. Drag **"Sales"** to Rows

**Step 1: Add Detail Without Splitting**

You have yearly data. Want to see monthly detail without separate lines?

1. Drag **"Order Date"** to **Detail** on Marks card
2. Right-click on it (in the Detail section)
3. Change to **"Month"**

**What Happened:**

The view still shows one line, but now:
- Hover over the line
- Tooltip shows monthly breakdown
- More data points without visual clutter

**Step 2: Using Detail for Aggregation Level**

Detail changes the level at which data is aggregated:

1. Drag **"Category"** to **Detail**
2. Now each point represents Sales per Year per Category
3. But you still see one line (the total)

This is useful for:
- Keeping aggregation level correct
- Providing detail in tooltips
- Maintaining proper granularity for calculations

---

### Exercise 4.6: The Tooltip Button

Tooltips are the boxes that appear when you hover. Let's customize them!

**Step 1: Access Tooltip Editor**

1. On any sheet, click **Tooltip** on Marks card
2. A rich text editor opens

**Step 2: Understanding Default Tooltips**

You'll see something like:

```
<Category>
Sales: <SUM(Sales)>
```

**What this means:**
- Text in **<angle brackets>** = dynamic fields
- Other text = static labels
- Tableau fills in actual values on hover

**Step 3: Customize Your Tooltip**

Edit the text to make it more informative:

```
Product Category: <Category>
Total Sales: <SUM(Sales)>
Percentage of Total: <SUM(Sales)> / <TOTAL(SUM(Sales))>

This category represents <Category>  of total revenue.
```

**Step 4: Format Tooltip Text**

1. Select text to format
2. Use toolbar to:
   - Make text **Bold** or *Italic*
   - Change font size
   - Change colors
   - Add bullets

**Step 5: Add More Fields**

1. Click **"Insert"** menu
2. Select **"All Fields"** to see available fields
3. Add fields like:
   - <Profit>
   - <Quantity>
   - <Customer Name>

**Step 6: Test Your Tooltip**

1. Click **OK** to close editor
2. Hover over your chart
3. See your custom tooltip!

**Best Practices:**
- Keep tooltips concise
- Include relevant context
- Format for readability
- Don't include too many fields (overwhelming)

---

## Part 5: Adding Colors and Details

Let's create more sophisticated visualizations with colors and breakdowns.

### Exercise 5.1: Stacked Bar Charts

Show how totals break down by another dimension.

**Create New Sheet: Sales by Region and Category**

1. New worksheet: **Regional Sales Breakdown**
2. Drag **"Region"** to Rows
3. Drag **"Sales"** to Columns
4. Sort descending

**Step 1: Add Category to Color**

1. Drag **"Category"** to **Color** on Marks card

**What You Get:**

A stacked bar chart where:
- Each region has one bar
- Bar is divided into colored segments (one per category)
- Total length = total sales for that region
- Colors show category breakdown

**Step 2: Read the Chart**

This chart answers multiple questions:
- Which region has highest sales? (West)
- How does each category contribute? (segments)
- Do all regions have similar category mix? (compare proportions)

**Step 3: Add Value Labels**

1. Drag **"Sales"** to **Label**
2. Format as currency
3. Now you see exact $ for each segment

**Optional: Percentage Labels**

Want to show percentages instead?

1. Create a calculated field: **Pct of Region Sales**
2. Formula: `SUM([Sales]) / TOTAL(SUM([Sales]))`
3. This calculates percent of total by region
4. Use as label

---

### Exercise 5.2: Side-by-Side Bars

Compare categories side-by-side instead of stacked.

**Starting from Regional Sales Breakdown:**

**Step 1: Move Category to Columns**

1. Drag **"Category"** from Color button
2. Drop it on **Columns** (next to Sales)

**What Changed:**

Now instead of stacked colors:
- Each region has 3 separate bars (one per category)
- Bars are grouped together
- Easier to compare exact values
- Harder to see total per region

**When to Use Each:**

- **Stacked**: See totals AND composition
- **Side-by-side**: Compare individual values precisely

**Step 2: Try Both with Row/Column Placement**

Experiment:

1. Put **Category** on Columns, **Region** on Rows → groups by region
2. Put **Region** on Columns, **Category** on Rows → groups by category
3. Swap them around to see different perspectives!

---

### Exercise 5.3: Using Color to Highlight**

Color can draw attention to important data points.

**Create New Sheet: Profit Analysis**

1. New worksheet: **Profit by Sub-Category**
2. Drag **"Sub-Category"** to Rows
3. Drag **"Profit"** to Columns
4. Sort descending

**Step 1: Color by Profit Value**

1. Drag **"Profit"** to **Color** on Marks card

**What Happened:**

Bars are now colored by their value:
- Positive profit = Blue/Green (good!)
- Negative profit = Orange/Red (losses!)
- Creates a diverging color scheme automatically

**This instantly highlights:**
- Which sub-categories are profitable
- Which are losing money
- How much profit/loss

**Step 2: Customize the Color Scheme**

1. Click **Color** on Marks card
2. Click **"Edit Colors..."**
3. Select a diverging palette:
   - Try **"Red-Green Diverging"**
   - Or **"Orange-Blue Diverging"**
4. Check **"Stepped Color"** for discrete ranges
5. Set to **3 steps**: Negative (red), Zero (white), Positive (green)
6. Click **OK**

**Step 3: Add a Reference Line at Zero**

Show where break-even is:

1. Right-click on the axis
2. **"Add Reference Line..."**
3. **"Line"** tab
4. Value: **Constant** = **0**
5. Label: **"Break Even"**
6. Line color: Black
7. Click **OK**

Now it's crystal clear which products are profitable!

---

### Exercise 5.4: Using Size to Encode Data

Size can show magnitude of values.

**Create New Sheet: Sales by Customer**

1. New worksheet: **Top Customers**
2. Drag **"Customer Name"** to Rows
3. Drag **"Sales"** to Columns
4. Sort descending
5. Filter to Top 20 customers (we'll learn filtering next)

**Step 1: Show as Circles**

1. Change mark type to **"Circle"**
2. Bars become dots

**Step 2: Encode Sales with Size**

1. Drag **"Sales"** to **Size** on Marks card

**What Happened:**

Circles are now sized by sales:
- Bigger circles = bigger customers
- Smaller circles = smaller customers
- Creates a bubble chart!

**Step 3: Add Color by Segment**

1. Drag **"Customer Segment"** to **Color**
2. Now you see:
   - Size = sales amount
   - Color = customer type (Consumer, Corporate, Home Office)

**Step 4: Add Labels**

1. Drag **"Customer Name"** to **Label**
2. Now each bubble is labeled

**This visualization shows:**
- Top customers by size
- Customer type by color
- Creates a more engaging view than bars

---

## Part 6: Filters and Sorting

Filters help you focus on specific data. Let's master filtering!

### Exercise 6.1: Creating Your First Filter

**Create New Sheet: Filtered Sales**

1. New worksheet: **West Region Sales**
2. Drag **"Sub-Category"** to Rows
3. Drag **"Sales"** to Columns

You see all regions combined. Let's filter to just West.

**Step 1: Add a Dimension Filter**

1. Find **"Region"** in Dimensions
2. **Drag** "Region" to the **Filters** shelf (above Marks card)
3. A dialog appears: "Filter [Region]"

**Step 2: Select Values**

In the Filter dialog:

1. You see a list of all regions with checkboxes:
   - ☐ Central
   - ☐ East
   - ☐ South
   - ☐ West

2. **Uncheck "All"** first
3. **Check only "West"**
4. Click **OK**

**What Happened:**

Now your chart shows only West region data:
- All other regions are hidden
- Sales values recalculated for West only
- Chart automatically updated

**The filter appears:**
- In the Filters shelf
- Shows "Region: West"

📖 **Reference:** [Filter Data](https://help.tableau.com/current/pro/desktop/en-us/filtering.htm)

---

### Exercise 6.2: Showing the Filter to Users**

Let viewers change the filter themselves!

**Step 1: Show Filter Control**

1. Find the **"Region"** filter in the Filters shelf
2. Right-click on it
3. Select **"Show Filter"**

**What Happened:**

A filter control appears on the right side of your sheet:
- Shows checkboxes for all regions
- Users can check/uncheck to change view
- Interactive!

**Step 2: Try Different Filter Types**

Right-click on the filter control (on the right) → **"Single Value (list)"**

Options:
- **Single Value (list)**: Radio buttons - choose one
- **Single Value (dropdown)**: Dropdown menu - choose one
- **Multiple Values (list)**: Checkboxes - choose multiple
- **Multiple Values (dropdown)**: Dropdown with checkboxes
- **Multiple Values (custom list)**: Custom selections
- **Wildcard Match**: Search/filter text
- **Slider**: Range slider (for continuous data)

Try **"Single Value (dropdown)"** for a cleaner look.

**Step 3: Customize Filter Appearance**

Right-click on filter control → **"Customize..."**

You can:
- Change title ("Region" → "Choose Region:")
- Show "All" option
- Show "Apply" button
- Alphabetical sorting

---

### Exercise 6.3: Filtering Measures (Numbers)

Let's filter by sales value instead of categories.

**Step 1: Add Sales Filter**

1. Drag **"Sales"** from Measures to Filters shelf
2. A different dialog appears - for numbers!

**Step 2: Choose Aggregation**

Dialog asks: "How do you want to filter?"
- **All values**: Filter every individual row
- **Sum**: Filter by total sales
- **Average**: Filter by average sales
- **Other aggregations**: Min, Max, etc.

Choose **"Sum"** → Click **"Next"**

**Step 3: Set the Range**

You see a range slider:
- Minimum sales value on left
- Maximum on right
- Current data range shown

**Options:**

**Range of Values:**
- Drag sliders to set min and max
- Example: Show only sub-categories with $50K-$200K in sales

**At Least:**
- Set minimum threshold
- Example: Sales ≥ $100,000

**At Most:**
- Set maximum threshold

**Special:**
- Null values
- Non-null values

**Choose "At Least":**
- Set to **$50,000**
- Click **OK**

**What Happened:**

Only sub-categories with at least $50K in sales show:
- Low-selling items filtered out
- Focus on significant products

---

### Exercise 6.4: Top N Filters

Show only top performers!

**Step 1: Create Top 10 Filter**

1. With your Sub-Category/Sales chart
2. Drag **"Sub-Category"** to Filters shelf (again)
3. In the dialog, switch to **"Top"** tab at the top

**Step 2: Configure Top N**

In the Top tab:

1. Choose **"By field"**
2. Select **"Top"** (not Bottom)
3. Enter **10**
4. By field: **"Sales"**
5. Aggregation: **"Sum"**
6. Click **OK**

**What You Get:**

Only the top 10 sub-categories by sales!
- Bottom performers hidden
- Focus on best sellers
- Automatically updates if data changes

**Step 3: Show Filter and Make Interactive**

1. Right-click on Sub-Category filter → **"Show Filter"**
2. Users can now change the number!
3. In the filter control, enter different numbers (5, 15, 20)
4. Chart updates instantly

**Use Cases:**
- Top 10 Customers
- Top 5 Products
- Bottom 10 Loss-Making Items (use "Bottom" instead of "Top")

---

### Exercise 6.5: Relative Date Filters

Filter data by date ranges - super useful!

**Create New Sheet: Recent Sales Trends**

1. New worksheet: **Recent Sales**
2. Drag **"Order Date"** to Columns (continuous, month level)
3. Drag **"Sales"** to Rows

**Step 1: Add Date Filter**

1. Drag **"Order Date"** to Filters shelf
2. In the dialog, you see options:
   - Relative Date
   - Range of Dates
   - Date Part (specific months/years)

3. Choose **"Relative date"** → Click **"Next"**

**Step 2: Configure Relative Filter**

Options appear:

**Anchor:**
- Today (always current)
- Specific date (fixed)

**Period:**
- Years
- Quarters
- Months
- Weeks
- Days

**Range:**
- Last X periods
- Next X periods
- Current period
- To date

**Example - Last 6 Months:**

1. Anchor: **Today**
2. Period: **Months**
3. Set to: **"Last 6 months"**
4. Click **OK**

**What This Does:**

Shows only the last 6 months of data:
- Always updates based on current date
- Perfect for "Recent Trends" dashboards
- Automatically rolling window

**Other Useful Filters:**
- "Last 30 days"
- "Current year to date"
- "Last 4 quarters"
- "Year to date (YTD)"

---

### Exercise 6.6: Action Filters (Interactive Highlighting)

Make charts filter each other!

We'll set this up in Part 8 when we build a dashboard, but here's a preview:

**What are Action Filters?**

Click on one chart → automatically filters another chart

**Example:**

Dashboard with two charts:
1. Sales by Region (bar chart)
2. Sales by Category (bar chart)

Setup an action: Click "West" region → second chart shows only West data

**We'll implement this when building our dashboard!**

---

## Part 7: Building Multiple Visualizations

Now let's create several different charts to practice!

### Exercise 7.1: Geographic Map

Visualize data by location!

**Step 1: Create New Sheet**

1. New worksheet: **Sales Map**

**Step 2: Build the Map**

1. Double-click **"State"** in Dimensions

**What Happened:**

Tableau automatically created a map!
- Each state shown
- Geographic data recognized

**Step 3: Add Sales to Color**

1. Drag **"Sales"** to **Color** on Marks card

**Now you see:**

A choropleth map (filled map):
- States colored by sales intensity
- Darker = more sales
- Lighter = fewer sales

**Step 4: Customize Map Colors**

1. Click **Color** → **"Edit Colors..."**
2. Choose a sequential palette:
   - **"Blue"** (professional)
   - **"Green-Blue"** (earnings)
   - **"Orange-Gold"** (warm)
3. Check **"Stepped Color"** for categories
4. Or leave unchecked for continuous gradient

**Step 5: Add Labels**

1. Drag **"State"** to **Label**
2. State abbreviations appear on map

Or show sales values:
1. Drag **"Sales"** to Label instead
2. Format as currency

**Step 6: Add Tooltips**

Click **Tooltip** and add:

```
State: <State>
Total Sales: <SUM(Sales)>
Total Profit: <SUM(Profit)>
Number of Orders: <CNTD(Order ID)>
```

**Map Benefits:**
- Geographic patterns immediately visible
- See regional differences at a glance
- Great for stakeholder presentations

📖 **Reference:** [Build Maps](https://help.tableau.com/current/pro/desktop/en-us/maps_build.htm)

---

### Exercise 7.2: Scatter Plot

Show relationships between two measures.

**Step 1: Create New Sheet**

1. New worksheet: **Sales vs Profit**

**Step 2: Build the Scatter Plot**

1. Drag **"Sales"** to Columns
2. Drag **"Profit"** to Rows
3. Change mark type to **"Circle"**

**What You See:**

One big circle! That's because all data is aggregated into one point.

**Step 3: Add Detail**

1. Drag **"Sub-Category"** to **Detail** on Marks card

**Now:**

One circle per sub-category:
- X-axis = Sales
- Y-axis = Profit
- Each bubble = one sub-category

**Step 4: Label the Points**

1. Drag **"Sub-Category"** to **Label**
2. Now you can identify each point

**Step 5: Color by Category**

1. Drag **"Category"** to **Color**
2. Points colored by parent category

**Step 6: Size by Quantity**

1. Drag **"Quantity"** to **Size**
2. Bigger bubbles = more units sold

**Reading the Chart:**

- **Upper right**: High sales, high profit (good!)
- **Lower right**: High sales, low/negative profit (concerning!)
- **Upper left**: Low sales, high profit per sale (niche?)
- **Lower left**: Low sales, low profit (consider discontinuing?)

**Add a Reference Line:**

Show break-even on profit:

1. Right-click Y-axis → **"Add Reference Line"**
2. Value: 0
3. Label: "Break Even"

**Insights You Might Find:**

- Tables: High sales but negative profit!
- Copiers: High sales AND high profit
- Some items lose money despite decent sales

---

### Exercise 7.3: Treemap

Show hierarchical data with nested rectangles.

**Step 1: Create New Sheet**

1. New worksheet: **Product Treemap**

**Step 2: Build the Treemap**

1. Drag **"Category"** to **Color**
2. Drag **"Sub-Category"** to **Detail**
3. Drag **"Sales"** to **Size**
4. Change mark type to **"Square"**

**Or use Show Me:**

1. Select **"Category"** (Ctrl+click)
2. Select **"Sales"** (Ctrl+click)
3. Click **"Show Me"** button (top right)
4. Choose **"Treemaps"** icon

**What You See:**

Nested rectangles:
- Each rectangle = one sub-category
- Size = sales volume
- Color = category
- Larger rectangles = higher sales

**Step 3: Add Labels**

1. Drag **"Sub-Category"** to **Label**
2. Drag **"Sales"** to Label (shows both name and value)

**Step 4: Improve Label Visibility**

Labels might be hard to read. Fix:

1. Click **Label** on Marks card
2. Font size: **Automatic** or smaller
3. Check **"Allow labels to overlap other marks"** if needed

**Reading a Treemap:**

- Quick visual comparison of sizes
- See proportions at a glance
- Identify top contributors
- Spot categories taking up space

**Best For:**
- Product mix analysis
- Budget allocation
- Portfolio composition
- Resource distribution

---

### Exercise 7.4: Dual-Axis Chart

Combine two measures on one chart.

**Step 1: Create New Sheet**

1. New worksheet: **Sales and Profit Trend**

**Step 2: Build Initial Chart**

1. Drag **"Order Date"** to Columns (continuous month)
2. Drag **"Sales"** to Rows
3. Drag **"Profit"** to Rows (next to Sales)

**You Have:**

Two separate charts stacked vertically.

**Step 3: Create Dual Axis**

1. Right-click on the **Profit** pill on Rows
2. Select **"Dual Axis"**

**What Happened:**

Charts overlaid:
- Sales and Profit on same plot
- Two Y-axes (left and right)
- Can compare trends directly

**Step 4: Synchronize Axes**

1. Right-click on one Y-axis
2. Select **"Synchronize Axis"**

Both now use same scale (if appropriate).

**Step 5: Differentiate the Lines**

Use the separate Marks cards:

1. Click **SUM(Sales)** Marks card
2. Color: Blue
3. Size: Thicker

4. Click **SUM(Profit)** Marks card
5. Color: Green
6. Size: Thinner

Or use different mark types:

1. SUM(Sales): Line
2. SUM(Profit): Area (filled)

**Step 6: Add a Title**

```
Monthly Sales and Profit Trends
Shows revenue (blue line) and profitability (green area) over time
```

**Use Cases:**
- Sales vs. Target
- Actual vs. Forecast
- Revenue vs. Costs
- Multiple related metrics

---

### Exercise 7.5: Highlight Table (Heatmap)

Use color to show values in a table.

**Step 1: Create New Sheet**

1. New worksheet: **Sales Heatmap**

**Step 2: Build the Table**

1. Drag **"Region"** to Rows
2. Drag **"Category"** to Columns
3. Drag **"Sales"** to **Color**
4. Drag **"Sales"** to **Text** (shows values)

**What You Get:**

A heatmap:
- Rows = Regions
- Columns = Categories
- Color intensity = Sales amount
- Numbers show exact values

**Step 3: Format the Heatmap**

**Colors:**
1. Click **Color** → **"Edit Colors..."**
2. Choose **"Orange-Gold"** or **"Blue-Green"**
3. Choose continuous or stepped
4. Adjust start/end points

**Numbers:**
1. Format as currency
2. Adjust font size if needed

**Borders:**
1. Click **Color**
2. **"Border"** → Choose color
3. Makes cells distinct

**Step 4: Add More Detail**

Drag **"Sub-Category"** to Rows:
- More granular view
- See product breakdown
- Deeper heat map

**Reading the Heatmap:**

- Darkest cells = highest sales
- Lightest cells = lowest sales
- Spot patterns and outliers instantly
- Compare multiple dimensions at once

**Best For:**
- Quick comparisons across two dimensions
- Spotting patterns in tabular data
- Dense information display
- Performance matrices

---

## Part 8: Creating Your First Dashboard

Dashboards combine multiple visualizations into one view. Let's build one!

### Exercise 8.1: Planning Your Dashboard

**Before Building, Plan:**

**What story do you want to tell?**

Let's create: **"Superstore Sales Executive Summary"**

**Visualizations to include:**
1. Sales Overview (KPI number)
2. Sales by Category (bar chart)
3. Sales Trend (line chart)
4. Regional Map (map)
5. Top Products (table or bar)

**Target Audience:** Executives who want quick insights

---

### Exercise 8.2: Creating the Dashboard

**Step 1: Create New Dashboard**

1. At the bottom, click **"New Dashboard"** icon (looks like a grid)
2. Or: **Dashboard** menu → **"New Dashboard"**
3. Or: Press **Ctrl+D** / **Cmd+D**

**You're now on the Dashboard view:**

**Left pane - Dashboard pane:**
- Size options
- List of your worksheets
- Objects (Text, Image, Web Page, etc.)

**Center - Canvas:**
- Empty space where you'll build
- Gray background

**Step 2: Set Dashboard Size**

In Dashboard pane, under **"Size"**:

Options:
- **Desktop Browser**: Fixed size (1000 x 800)
- **Automatic**: Responsive sizing
- **Range**: Min/max dimensions
- **Exactly**: Custom size

Choose: **Desktop Browser (1000 x 800)** for this lab

**Step 3: Add Your First Worksheet**

From the Dashboard pane:

1. You see all your worksheets listed
2. Drag **"Sales by Category"** onto the canvas
3. Drop it in the center

**What Happened:**

The chart appears in your dashboard!

**Step 4: Add More Worksheets**

1. Drag **"Sales Over Time"** to the dashboard
2. Tableau shows drop zones (gray areas)
3. Drop it **below** Sales by Category

4. Drag **"Sales Map"** to the dashboard
5. Drop it to the **right** of Sales by Category

**Layout Tips:**

- **Horizontal containers**: Side by side
- **Vertical containers**: Stacked
- Drop in **center** of existing view to replace
- Drop on **edge** to add next to

**Step 5: Arrange Your Layout**

Adjust sizes:

1. Hover between views
2. Cursor becomes resize arrows ↔
3. Drag to resize

Create a balanced layout:
- Top half: Category chart and Map side-by-side
- Bottom half: Trend line chart (full width)

📖 **Reference:** [Build a Dashboard](https://help.tableau.com/current/pro/desktop/en-us/dashboards_create.htm)

---

### Exercise 8.3: Adding Dashboard Title

**Step 1: Add Text Object**

1. In Dashboard pane (left), find **"Objects"** section
2. Drag **"Text"** object to top of dashboard
3. Drop it above all other views

**Step 2: Edit the Title**

Double-click the text object:

```
Superstore Sales Dashboard
Executive Summary Q4 2020

Key Metrics and Trends
```

**Step 3: Format the Title**

1. Select all text
2. Make **Bold**
3. Font size: **16** or **18**
4. Center align
5. Click **OK**

**Step 4: Style the Title Box**

1. Click the dropdown arrow on the title (upper right)
2. **Format** → **Shading**
3. Background: Light gray
4. Border: Thin black line

---

### Exercise 8.4: Adding Interactivity with Filters

Make the dashboard interactive!

**Step 1: Add a Global Filter**

1. In one of your worksheets in the dashboard
2. Click the dropdown arrow (upper right of that view)
3. **"Filters"** → **"Region"**
4. The Region filter appears on the dashboard!

**Step 2: Apply to All Worksheets**

1. Click the dropdown on the Region filter
2. **"Apply to Worksheets"** → **"All Using This Data Source"**

Now filtering one view filters them all!

**Step 3: Add More Filters**

Add filters for:
- Category
- Date range

**Step 4: Format Filters**

1. Click dropdown on each filter
2. Choose **"Single Value (dropdown)"** for cleaner look
3. **"Customize"** to change titles

**Step 5: Use as Filter Action**

Alternative to showing filter controls:

1. Click on a worksheet (like Sales by Category)
2. Click dropdown → **"Use as Filter"**

Now clicking a bar filters the entire dashboard!

---

### Exercise 8.5: Adding Navigation and Context

**Step 1: Add Descriptive Text**

1. Drag **"Text"** object below title
2. Add context:

```
This dashboard provides an overview of Superstore sales performance.
Use the filters to explore by region, category, or time period.
Click on any chart element to filter all views.

Last Updated: [Date]
Data Source: Superstore Sales 2017-2020
```

**Step 2: Add Legends**

If legends aren't showing:

1. Click dropdown on a worksheet
2. Check **"Legend"** → **"Color Legend"**
3. Legend appears

Position legends:
- Drag them to different locations
- Or hide if redundant

**Step 3: Remove Unnecessary Titles**

Clean up:

1. Each worksheet shows its title
2. If redundant, hide them:
   - Click dropdown on worksheet
   - Uncheck **"Title"**

But keep titles if they add clarity!

**Step 4: Add a Footer**

1. Drag **"Text"** object to bottom
2. Add footer text:

```
© 2024 Your Company | Confidential
For questions contact: analytics@company.com
```

---

### Exercise 8.6: Polishing Your Dashboard

Make it professional!

**Step 1: Consistent Colors**

Ensure all views use same color scheme:
- Same colors for same categories
- Consistent legends
- Coordinated palette

**Step 2: Alignment**

Make everything line up:

1. Use **"Objects"** → **"Blank"** for spacing
2. Adjust sizes to create balance
3. Even margins around elements

**Step 3: Dashboard Formatting**

1. **Format** menu → **"Dashboard"**
2. Set:
   - Background color
   - Border styles
   - Shading
   - Outer padding

Try a subtle background color (very light gray).

**Step 4: Add Logo (Optional)**

If you have a company logo:

1. Drag **"Image"** object to dashboard
2. Top corner or footer
3. Select your logo file
4. Resize appropriately

**Step 5: Test Interactivity**

1. Try all filters
2. Click "Use as Filter" elements
3. Ensure everything updates correctly
4. Test with different data ranges

---

### Exercise 8.7: Creating Multiple Dashboard Views

Create different views for different audiences!

**Step 1: Duplicate Dashboard**

1. Right-click on your dashboard tab (bottom)
2. **"Duplicate"**
3. Rename: **"Sales Dashboard - Mobile"**

**Step 2: Optimize for Mobile**

In the new dashboard:

1. **Size** → **"Phone"** or **"Tablet"**
2. Rearrange for vertical layout:
   - Stack views vertically
   - Simplify (fewer views)
   - Larger text/buttons

**Step 3: Create Executive vs. Detail Dashboards**

**Executive Dashboard:**
- High-level KPIs
- Summary charts
- Trends only
- Clean and simple

**Detailed Dashboard:**
- All worksheets
- Multiple filters
- Drill-down capability
- Dense information

Create one of each!

---

## Challenge Exercises

Test your skills!

### Challenge 1: Profit Analysis Dashboard

**Goal:** Create a comprehensive profit analysis.

**Requirements:**
1. Profit by Category (bar chart)
2. Profit by Region (map)
3. Profit vs. Sales scatter plot
4. Identify loss-making products
5. Show profit margin % by sub-category
6. Add trend line showing profit over time

**Bonus:**
- Use reference lines to show targets
- Color negative profits red, positive green
- Calculate and show profit margin = Profit/Sales

---

### Challenge 2: Customer Segment Analysis

**Goal:** Compare customer segments (Consumer, Corporate, Home Office).

**Requirements:**
1. Sales by Segment (pie or bar)
2. Profitability by Segment
3. Average order value by Segment
4. Top customers in each Segment
5. Segment trends over time

**Bonus:**
- Calculate metrics like:
  - Customer Lifetime Value
  - Average items per order
  - Discount usage by segment

---

### Challenge 3: Time-Series Analysis

**Goal:** Deep dive into temporal patterns.

**Requirements:**
1. Daily sales trend
2. Monthly sales with year-over-year comparison
3. Seasonal patterns (by month across years)
4. Day of week analysis
5. Add forecast (if using Tableau Desktop Pro)

**Bonus:**
- Add annotations for key events
- Show moving averages
- Highlight outliers

---

### Challenge 4: Geographic Deep Dive

**Goal:** Comprehensive location analysis.

**Requirements:**
1. Sales by State (filled map)
2. Top 5 cities per region
3. Shipping cost analysis by location
4. Delivery time (Ship Date - Order Date) by region
5. Compare urban vs. rural (if data allows)

**Bonus:**
- Create custom territories
- Add distance calculations
- Show shipping efficiency

---

### Challenge 5: Product Performance Matrix

**Goal:** Comprehensive product analysis.

**Requirements:**
1. 2x2 matrix: Sales (X) vs. Profit (Y)
2. Quadrants labeled:
   - Stars (high sales, high profit)
   - Cash Cows (low sales, high profit)
   - Dogs (low sales, low profit)
   - Problem Children (high sales, low profit)
3. Size by quantity sold
4. Color by category
5. Table of metrics for each quadrant

---

## Submission Requirements

### What to Submit

**1. Tableau Workbook (.twbx)**

Save your work:

1. **File** → **"Save to Tableau Public As..."**
2. Create account if needed (free)
3. Name: **YourName_Lab2_Visualizations**
4. Publish

Or save locally:

1. **File** → **"Save As"**
2. Choose **"Tableau Packaged Workbook (.twbx)"**
3. Name: **LastName_FirstName_Lab2_Visualizations.twbx**
4. Save to your Lab folder

**2. Documentation (PDF or Word)**

Create a document with:

**Part A: Screenshots**

Include screenshots of:
- Sales by Category bar chart
- Sales Over Time line chart
- Sales by Region map
- Your final dashboard
- At least one challenge exercise (if attempted)

For each screenshot, add caption explaining what it shows.

**Part B: Written Explanations**

Answer these questions (3-4 sentences each):

1. **Bar Charts vs. Line Charts:** When should you use each? Give examples from your lab.

2. **Marks Card:** Explain the purpose of the Color, Size, and Label buttons on the Marks card. Give an example of when you'd use each.

3. **Filters:** Describe three different types of filters you created and why each was useful.

4. **Dashboard Design:** What principles did you follow when arranging your dashboard? Why?

5. **Insights:** What's one interesting insight you discovered from your visualizations?

**Part C: Analysis Insights**

Based on your visualizations, answer:

1. **Top Performers:**
   - Which category generates the most sales?
   - Which region is most profitable?
   - What's the top-selling sub-category?

2. **Trends:**
   - Are sales increasing or decreasing over time?
   - Any seasonal patterns?
   - Any concerning trends?

3. **Problem Areas:**
   - Any products losing money?
   - Any underperforming regions?
   - What recommendations would you make?

4. **Opportunities:**
   - Where should the company focus efforts?
   - What products should be promoted?
   - Any geographic expansion opportunities?

**Part D: Visualization Choices**

For each major visualization, explain:
- Why you chose that chart type
- What question it answers
- What makes it effective
- Any challenges you faced

**3. Naming Convention**

- Workbook: **LastName_FirstName_Lab2_Visualizations.twbx**
- Documentation: **LastName_FirstName_Lab2_Documentation.pdf**

---

## Troubleshooting Guide

### Common Issues and Solutions

**Issue: Data isn't showing up in my visualization**

**Possible Causes:**
- Field is on wrong shelf
- Filter is too restrictive
- Data type is wrong
- Null values

**Solutions:**
1. Check that dimensions are on Rows or Columns
2. Check that measures are aggregated properly
3. Remove all filters temporarily
4. Check Data Source page for correct data types
5. Look for "Null" in your data

---

**Issue: Bars/lines don't look right**

**Possible Cause:** Wrong mark type selected.

**Solution:**
1. Check the Marks card dropdown
2. For categories: Use Bar
3. For time series: Use Line
4. Let Tableau use "Automatic" if unsure

---

**Issue: Colors aren't showing**

**Possible Cause:** Nothing on Color button.

**Solution:**
1. Drag a field to Color on Marks card
2. Or click Color and choose a color manually
3. Check if field is actually varying (not all same value)

---

**Issue: Can't see all data points**

**Possible Causes:**
- View is aggregated too much
- Filter hiding data
- Date granularity too high

**Solutions:**
1. Change date granularity (Year → Month → Day)
2. Check filters
3. Add more detail to view (Detail button)
4. Disaggregate (Analysis menu → Uncheck "Aggregate Measures")

---

**Issue: Chart is too crowded**

**Solutions:**
1. Apply a Top N filter
2. Increase view size
3. Use a different chart type
4. Remove some dimensions
5. Use a dashboard with multiple simpler views

---

**Issue: Tooltips don't show**

**Solutions:**
1. Check that Tooltip is enabled (Worksheet menu)
2. Click on Tooltip on Marks card
3. Make sure fields are present
4. Check if tooltip is hidden behind other elements

---

**Issue: Dashboard looks messy**

**Solutions:**
1. Remove unnecessary titles (uncheck "Title")
2. Hide redundant legends
3. Use consistent colors across views
4. Add blank objects for spacing
5. Align elements carefully
6. Simplify - fewer is often better

---

**Issue: Dashboard doesn't update when filtering**

**Solution:**
1. Check that filter is applied to all worksheets
2. Filter dropdown → "Apply to Worksheets" → "All Using This Data Source"
3. Check if "Use as Filter" is enabled on clicked elements

---

### Getting Help

**Tableau Resources:**

1. **Press F1** in Tableau for context help
2. **Help Menu** → "Tableau Help"
3. Official documentation: [https://help.tableau.com](https://help.tableau.com)
4. Video tutorials: [https://www.tableau.com/learn/training](https://www.tableau.com/learn/training)

**Community Resources:**

- Tableau Community Forums
- YouTube: Search "Tableau tutorial [your topic]"
- LinkedIn Learning
- Coursera courses

**Contact Your Instructor:**

- Include screenshot of issue
- Describe what you were trying to do
- What happened vs. what you expected
- Share your .twbx file if possible

---

## Key Concepts Summary

### Chart Types

**Bar Chart:**
- **Use:** Compare categories
- **Example:** Sales by Category
- **Best Practice:** Sort by value, use color meaningfully

**Line Chart:**
- **Use:** Show trends over time
- **Example:** Monthly sales
- **Best Practice:** Use continuous dates, add markers

**Map:**
- **Use:** Geographic data
- **Example:** Sales by State
- **Best Practice:** Use color to show intensity, add tooltips

**Scatter Plot:**
- **Use:** Show relationships between two measures
- **Example:** Sales vs. Profit
- **Best Practice:** Add trend lines, color by third dimension

**Treemap:**
- **Use:** Hierarchical data, proportions
- **Example:** Product mix
- **Best Practice:** Size by value, color by category

---

### Marks Card

**Color:** Encode data with color (categories or values)
**Size:** Make marks bigger/smaller based on values
**Label:** Show text on marks
**Detail:** Add granularity without changing visualization
**Tooltip:** Customize hover information

---

### Filters

**Dimension Filters:** Filter categories (Region, Category)
**Measure Filters:** Filter by values (Sales > $50K)
**Date Filters:** Filter time periods (Last 6 months)
**Top N Filters:** Show only top/bottom performers

---

### Dashboard Best Practices

✅ **Do:**
- Plan your layout before building
- Use consistent colors
- Add titles and context
- Make it interactive with filters
- Test with different data
- Keep it simple and focused

❌ **Don't:**
- Overcrowd with too many views
- Use too many different colors
- Forget to label axes
- Ignore white space
- Make users guess what things mean

---

## Additional Learning Resources

**Official Tableau Resources:**

- **Getting Started:** [https://help.tableau.com/current/pro/desktop/en-us/gettingstarted_overview.htm](https://help.tableau.com/current/pro/desktop/en-us/gettingstarted_overview.htm)
- **Build Common Charts:** [https://help.tableau.com/current/pro/desktop/en-us/buildexamples_overview.htm](https://help.tableau.com/current/pro/desktop/en-us/buildexamples_overview.htm)
- **Visual Best Practices:** [https://help.tableau.com/current/pro/desktop/en-us/viewparts_marks_marktypes.htm](https://help.tableau.com/current/pro/desktop/en-us/viewparts_marks_marktypes.htm)

**Download Links:**
- **Superstore CSV:** [Download CSV](https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2002/Superstore.csv)
- **Superstore Excel:** [Download XLSX](https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2002/Superstore.xlsx)

**Video Tutorials:**
- Search "Tableau bar chart tutorial" on YouTube
- Search "Tableau dashboard tutorial for beginners"
- Tableau's official training videos

**Practice Datasets:**
- Sample - Superstore (built into Tableau)
- Sample - Coffee Chain (built-in)
- Public datasets on data.gov
- Kaggle datasets

---

## Tips for Success

1. **Start Simple:** Begin with basic charts, add complexity gradually

2. **Ask Questions:** Every visualization should answer a question

3. **Use Show Me:** When stuck, try the Show Me panel for suggestions

4. **Experiment:** Try different chart types to see what works

5. **Color Meaningfully:** Use color to convey information, not just decoration

6. **Label Clearly:** Viewers shouldn't have to guess what things mean

7. **Tell a Story:** Arrange visualizations to guide viewers through insights

8. **Get Feedback:** Show your work to others and iterate

9. **Save Often:** Use .twbx to keep data and work together

10. **Practice:** The more you build, the better you'll get!

---

## Congratulations!

You've completed Lab 2 on Creating Visualizations! You now know how to:

✅ Build bar charts to compare data  
✅ Create line charts to show trends  
✅ Use the Marks card effectively  
✅ Apply colors, sizes, and labels  
✅ Filter and sort data  
✅ Build interactive dashboards  
✅ Choose the right chart for your data  

**You're well on your way to becoming a Tableau analyst!**

---

**Lab Created By:** Dr. Lee  
**Last Updated:** 2025  
**Questions?** Contact your instructor or visit office hours

**Happy Visualizing!** 🎉📊📈
