# Tableau Lab 1: Introduction to Tableau - Your First Steps

**Course:** Data Analytics & Visualization  
**Software:** Tableau Desktop Public Edition  
**Dataset:** Superstore Sales Data  
**Estimated Time:** 90-120 minutes  
**Difficulty:** Absolute Beginner

---

## 📋 Table of Contents

1. [Welcome to Tableau!](#welcome-to-tableau)
2. [Learning Objectives](#learning-objectives)
3. [Prerequisites](#prerequisites)
4. [Part 1: Installing Tableau Desktop Public Edition](#part-1-installing-tableau-desktop-public-edition)
5. [Part 2: Understanding the Tableau Interface](#part-2-understanding-the-tableau-interface)
6. [Part 3: Connecting to Your First Data Source](#part-3-connecting-to-your-first-data-source)
7. [Part 4: Exploring Your Data](#part-4-exploring-your-data)
8. [Part 5: Creating Your First Visualization](#part-5-creating-your-first-visualization)
9. [Part 6: Understanding Dimensions and Measures](#part-6-understanding-dimensions-and-measures)
10. [Part 7: Saving and Sharing Your Work](#part-7-saving-and-sharing-your-work)
11. [Quick Reference Guide](#quick-reference-guide)
12. [Submission Requirements](#submission-requirements)
13. [Troubleshooting](#troubleshooting)

---

## 🎉 Welcome to Tableau!

Congratulations on starting your journey with Tableau - one of the world's leading data visualization tools! 

**What is Tableau?**

Tableau is software that turns data (like Excel spreadsheets) into beautiful, interactive visualizations (charts, graphs, and dashboards) that help you understand and communicate insights quickly.

**Why Learn Tableau?**

- **In-demand skill:** Top companies worldwide use Tableau
- **Visual thinking:** See patterns and trends instantly
- **Easy to learn:** Drag and drop - no coding required!
- **Powerful:** Professional-grade analytics
- **Free version available:** Tableau Desktop Public Edition

**What You'll Build Today:**

By the end of this lab, you'll create your first interactive visualization showing sales data across different product categories - all from scratch!

---

## 🎯 Learning Objectives

By the end of this lab, you will be able to:

- Install and launch Tableau Desktop Public Edition
- Navigate the Tableau interface confidently
- Connect to a CSV data file
- Understand the difference between dimensions and measures
- Create a simple bar chart
- Customize colors and labels
- Save your work
- Understand basic Tableau terminology

**No prior experience needed!** This lab assumes you've never opened Tableau before.

---

## 📚 Prerequisites

### Required Software

**Tableau Desktop Public Edition (FREE):**
- Download: [https://public.tableau.com/app/discover](https://public.tableau.com/app/discover)
- Compatible with: Windows 10/11 or macOS
- Free forever - no credit card required!

### Required Dataset

**Superstore.csv** - A sample retail dataset with:
- Sales transactions
- Product information
- Customer details
- Geographic data

**Download Link:**
```
https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2001/Superstore.csv
```

### What You Should Know

**Absolutely nothing about Tableau!** 

But you should be comfortable with:
- Using a computer (Windows or Mac)
- Finding and opening files
- Basic familiarity with spreadsheets (helpful but not required)

### Official Documentation

Bookmark these for reference:
- **Main Help:** [https://help.tableau.com/current/pro/desktop/en-us/default.htm](https://help.tableau.com/current/pro/desktop/en-us/default.htm)
- **Getting Started:** [https://help.tableau.com/current/pro/desktop/en-us/gettingstarted_overview.htm](https://help.tableau.com/current/pro/desktop/en-us/gettingstarted_overview.htm)
- **User Interface:** [https://help.tableau.com/current/pro/desktop/en-us/environment_workspace.htm](https://help.tableau.com/current/pro/desktop/en-us/environment_workspace.htm)

---

## Part 1: Installing Tableau Desktop Public Edition

Let's get Tableau installed on your computer!

### Exercise 1.1: Downloading Tableau

**Step 1: Visit the Tableau Public Website**

1. Open your web browser (Chrome, Firefox, Safari, Edge)
2. Navigate to: [https://public.tableau.com/app/discover](https://public.tableau.com/app/discover)
3. You'll see the Tableau Public home page

**Step 2: Start the Download**

1. Look for a button that says **"DOWNLOAD THE APP"** or **"Download Tableau Public"**
2. Click it
3. The download will start automatically (file is about 500MB-1GB)

**Note:** The website may ask for your email. This is optional for download but required to save work online later.

**Step 3: Wait for Download to Complete**

The download may take 5-15 minutes depending on your internet speed. While waiting, continue reading!

**What is Tableau Public Edition?**

- **Free forever** - no expiration
- **Full visualization capabilities** - all chart types
- **Limitation:** Your work saves to Tableau's public server (visible to others)
- **Perfect for learning!**

📖 **Reference:** [Download Tableau Public](https://www.tableau.com/products/public/download)

---

### Exercise 1.2: Installing Tableau

Once download completes, let's install it!

**For Windows:**

**Step 1: Locate Downloaded File**
1. Open your **Downloads** folder
2. Find file named: `TableauPublic-[version].exe`
3. Double-click it

**Step 2: Run Installer**
1. Click **"Yes"** if Windows asks for permission
2. Installer window opens
3. Choose language (English)
4. Click **"Install"**

**Step 3: Wait for Installation**
- Progress bar shows installation
- Takes about 5-10 minutes
- May install additional components

**Step 4: Complete Installation**
1. Click **"Finish"** when done
2. Tableau Public Edition is now installed!

**For macOS:**

**Step 1: Locate Downloaded File**
1. Open your **Downloads** folder
2. Find file: `TableauPublic-[version].dmg`
3. Double-click it

**Step 2: Install**
1. Drag the Tableau icon to Applications folder
2. Wait for copy to complete
3. Eject the installer disk image

**Step 3: First Launch**
1. Go to **Applications** folder
2. Find **Tableau Public**
3. Right-click → **"Open"**
4. Click **"Open"** again (bypasses security check first time)

**Troubleshooting Installation:**

- **Not enough space?** Free up at least 2GB
- **Admin rights?** Contact your IT department
- **Mac security?** System Preferences → Security → Allow Tableau
- **Still stuck?** See [Installation Guide](https://help.tableau.com/current/public/desktop/en-us/getstarted_buildmanual_ex1basic.htm)

---

### Exercise 1.3: Launching Tableau for the First Time

**Step 1: Open Tableau**

**Windows:**
1. Click **Start** menu
2. Type "Tableau Public"
3. Click the Tableau Public icon

**Mac:**
1. Open **Finder**
2. Go to **Applications**
3. Double-click **Tableau Public**

**Step 2: Wait for Startup**

Tableau takes a few moments to load (10-20 seconds):
- Splash screen appears
- Loading bar
- Then the Start page opens

**Step 3: First-Time Setup (Optional)**

Tableau may ask:
- **Email address** (for saving to cloud) - you can skip for now
- **Usage statistics** - your choice
- **Tutorial** - you can skip (this lab is your tutorial!)

**You're In!**

When you see the **Start page** with options to connect to data, you're ready to go!

**What You Should See:**

- **Left side:** Connection options (Excel, Text File, etc.)
- **Center:** Sample workbooks and templates
- **Right side:** Recent work (empty for now)
- **Top:** Menu bar (File, Data, Worksheet, etc.)

🎉 **Congratulations!** Tableau is installed and running!

---

## Part 2: Understanding the Tableau Interface

Before diving into data, let's understand what you're looking at.

### Exercise 2.1: The Start Page

When you first open Tableau, you see the **Start Page**.

**Left Side - Connect:**

This is where you choose your data source:

**To a File:**
- Excel
- Text file (CSV, TXT)
- JSON file
- PDF
- Spatial file
- Statistical file

**To a Server:**
- Tableau Server
- MySQL
- Microsoft SQL Server
- Amazon Redshift
- And many more...

**For this lab:** We'll use **"Text file"** (for our CSV)

**Center - Open:**

- Sample workbooks (pre-built examples)
- Recent workbooks (ones you've opened)
- Template workbooks (starter templates)

**Bottom - Discover:**

- Tableau Public gallery
- Featured visualizations
- Learning resources

**Understanding the Layout:**

Think of the Start Page as your **home base** - you always return here to:
- Connect to data
- Open existing work
- Start new projects

📖 **Reference:** [Tableau Workspace](https://help.tableau.com/current/pro/desktop/en-us/environment_workspace.htm)

---

### Exercise 2.2: Tour of the Tableau Workspace

We'll see this soon, but let's understand what you'll encounter:

**The Tableau workspace has THREE main areas:**

**1. Data Source Page**
- Where you connect to and prepare data
- See a preview of your data
- Check data types
- Join multiple tables

**2. Worksheet**
- Where you build individual visualizations
- Create charts, graphs, maps
- Most of your time spent here

**3. Dashboard**
- Where you combine multiple worksheets
- Create interactive reports
- Professional presentations

**The Workspace Elements:**

**Top - Menu Bar:**
- File, Data, Worksheet, Dashboard, Story, Analysis, Map, Format, Server, Window, Help
- Like any software menu

**Left - Data Pane:**
- Lists all your data fields
- Dimensions (categories) in blue
- Measures (numbers) in green

**Center - Canvas:**
- Where your visualizations appear
- Drag and drop area
- Interactive workspace

**Right - Show Me:**
- Suggests chart types
- Quick visualization options

**Bottom - Shelf Area:**
- **Columns** and **Rows** shelves (main building blocks)
- **Filters** shelf
- **Pages** shelf
- **Marks** card (Color, Size, Label, etc.)

**Don't Worry!**

This will make much more sense once we start building. Just know these areas exist!

---

## Part 3: Connecting to Your First Data Source

Now let's connect to data - the first step in any Tableau project!

### Exercise 3.1: Downloading the Superstore Data

**Step 1: Create a Folder for This Lab**

1. On your computer, create a new folder
2. Name it: **Tableau_Lab_1**
3. Suggested location:
   - **Windows:** `Documents\Tableau_Labs\Lab_1`
   - **Mac:** `Documents/Tableau_Labs/Lab_1`

**Step 2: Download the Superstore Data**

1. Open your web browser
2. Copy and paste this URL:

```
https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2001/Superstore.csv
```

3. Press Enter
4. The file downloads automatically (called `Superstore.csv`)
5. Move the downloaded file to your **Tableau_Lab_1** folder

**Step 3: Verify the Download**

1. Navigate to your **Tableau_Lab_1** folder
2. You should see: **Superstore.csv**
3. File size: approximately 2-3 MB
4. **Don't open it yet!** We'll open it through Tableau

**What's in This Data?**

The Superstore dataset contains:
- **9,000+ rows** of sales data
- **Order information:** dates, IDs, priorities
- **Products:** categories, names, prices
- **Customers:** names, segments, locations
- **Financial:** sales, profit, discounts
- **Shipping:** modes, costs, dates

**Perfect for learning!** It's realistic but manageable.

---

### Exercise 3.2: Connecting to the CSV File

Now let's connect Tableau to your data!

**Step 1: Start from the Start Page**

If Tableau isn't open:
1. Launch Tableau Desktop Public Edition
2. You should see the Start page

If you're already in Tableau:
1. Click **File** → **New** to return to Start page

**Step 2: Choose Connection Type**

1. On the left side, find the **"Connect"** section
2. Under **"To a File"**, click **"Text file"**
   - Note: CSV files are text files to Tableau

**Step 3: Navigate to Your File**

A file browser window opens:

1. Navigate to your **Tableau_Lab_1** folder
2. Select **Superstore.csv**
3. Click **"Open"**

**What Happens Next:**

Tableau loads your data and takes you to the **Data Source page**!

**Step 4: First Look at Data Source Page**

You should now see:

**Top Left:**
- "Superstore.csv" appears under Connections

**Center Canvas:**
- A box labeled "Superstore" appears
- This represents your data table

**Bottom Grid:**
- Preview of your data (first 1,000 rows)
- All columns visible
- Sample values shown

🎉 **Success!** You're connected to data!

📖 **Reference:** [Connect to a File](https://help.tableau.com/current/pro/desktop/en-us/examples_text.htm)

---

### Exercise 3.3: Understanding the Data Source Page

Let's explore what you're looking at!

**Top Area - Connections:**

**Left Pane:**
- Shows "Superstore.csv"
- Your active data connection
- Can add more connections here

**Center Canvas:**
- Shows "Superstore" table
- Drag and drop area for joining tables
- For now, we have just one table (simple!)

**Bottom Area - Data Preview:**

This is a grid showing your data:

**Column Headers:**
Look at the top of each column. You'll see:
- **Column name**: Category, Sales, Customer Name, etc.
- **Data type icon**: 
  - **Abc** = Text (strings)
  - **#** = Number
  - **📅** = Date
  - **🌐** = Geographic

**Step 1: Check Your Data Types**

Scroll through the columns and verify these data types:

Should be **Text (Abc):**
- Category
- Sub-Category
- Customer Name
- City
- State
- Region
- Product Name

Should be **Number (#):**
- Sales
- Quantity
- Discount
- Profit
- Shipping Cost

Should be **Date (📅):**
- Order Date
- Ship Date

**Step 2: Fix Incorrect Data Types (If Needed)**

If a data type is wrong:

1. Click the **icon** above the column name
2. Select the correct data type from the dropdown:
   - **String** (text)
   - **Number (decimal)**
   - **Number (whole)**
   - **Date & Time**
   - **Geographic Role** (for locations)

**Common Issues:**
- Order Date showing as text? Change to Date
- Sales showing as text? Change to Number (decimal)

**Step 3: Rename Your Data Source (Optional but Good Practice)**

1. At the top, you see "Superstore (Superstore.csv)"
2. Right-click on it
3. Select **"Rename"**
4. Type: **Superstore Sales Data**
5. Press Enter

This makes it clearer what your data is!

---

## Part 4: Exploring Your Data

Before visualizing, let's understand what data we have.

### Exercise 4.1: Viewing Data in the Grid

You're looking at a preview grid (like Excel).

**Step 1: Scroll Through Columns**

1. Use the horizontal scrollbar at the bottom
2. You'll see many columns:
   - Category
   - City
   - Customer Name
   - Order Date
   - Sales
   - Profit
   - And more...

**Step 2: Scroll Through Rows**

1. Use the vertical scrollbar
2. You're seeing the first 1,000 rows
3. Notice: Each row = one order line item

**Step 3: Understanding Row-Level Data**

Each row represents:
- One item from one order
- Example: "John Smith ordered 3 chairs on March 15, 2019"

Multiple rows can have the same:
- Customer (repeat customers)
- Order ID (multi-item orders)
- Date (many orders per day)

**Step 4: Check Data Volume**

Look at the bottom left of the screen:
- Should show approximately **9,427 rows**
- This is how much data you have

**Step 5: Examine Sample Values**

Click on different cells:
- Sales values range from small to large amounts
- Dates span 2017-2020
- Three main categories: Furniture, Office Supplies, Technology

**Key Insight:**

This data is too much to understand by looking at rows. That's why we need visualizations!

---

### Exercise 4.2: Understanding Data Fields

Let's understand what each field means.

**Major Field Groups:**

**1. Order Information:**
- **Order ID**: Unique identifier for each order
- **Order Date**: When order was placed
- **Ship Date**: When order was shipped
- **Ship Mode**: How it was shipped
- **Order Priority**: Urgency level

**2. Product Information:**
- **Category**: Furniture, Office Supplies, or Technology
- **Sub-Category**: Specific product type (Chairs, Phones, etc.)
- **Item**: Specific product name
- **Department**: Which department

**3. Customer Information:**
- **Customer ID**: Unique customer identifier
- **Customer Name**: Customer's name
- **Customer Segment**: Consumer, Corporate, or Home Office

**4. Geographic Information:**
- **Region**: East, West, Central, South
- **State**: US State
- **City**: City name
- **Postal Code**: Zip code

**5. Financial Information:**
- **Sales**: Revenue amount
- **Quantity**: Number of items
- **Discount**: Discount applied
- **Profit**: Profit amount
- **Shipping Cost**: Cost to ship

**Step 1: Identify Key Fields**

For our first visualization, we'll focus on:
- **Category** (what was sold)
- **Sales** (how much money)

Simple and powerful!

---

## Part 5: Creating Your First Visualization

This is the exciting part - let's make your first chart!

### Exercise 5.1: Moving to a Worksheet

**Step 1: Navigate to a Worksheet**

At the bottom of your screen, you'll see tabs. Find and click **"Sheet 1"**

**What Just Happened:**

You moved from the **Data Source page** to a **Worksheet**!

This is where the magic happens - where you build visualizations.

**Step 2: Understanding the Worksheet Layout**

You should now see:

**Left Side - Data Pane:**
A list of all your fields, organized into:
- **Dimensions** (blue background) - Categories
- **Measures** (green background) - Numbers

**Center - Canvas:**
Empty white space (your future chart will appear here)

**Top Center - Shelves:**
- **Columns** shelf
- **Rows** shelf
- These say "Drop field here"

**Top Right - Show Me:**
Panel showing different chart types

**Left Center - Marks Card:**
Area for customizing your visualization

**This is your workspace!** Everything happens here.

📖 **Reference:** [Workspace Areas](https://help.tableau.com/current/pro/desktop/en-us/environment_workspace.htm)

---

### Exercise 5.2: Your Very First Chart!

Let's create a bar chart showing sales by category.

**The Big Moment - Watch This!**

**Step 1: Add Category to Rows**

1. Look at the **Data Pane** on the left
2. Under **Dimensions** (blue section), find **"Category"**
3. **Click and drag** "Category"
4. Drop it on the **Rows** shelf (says "Drop field here")

**What You Should See:**

Three items appear in your canvas:
- Furniture
- Office Supplies
- Technology

These are your three categories!

**Step 2: Add Sales to Columns**

1. In the **Data Pane**, scroll down to **Measures** (green section)
2. Find **"Sales"**
3. **Click and drag** "Sales"
4. Drop it on the **Columns** shelf

**🎉 BOOM! Your First Chart!**

You just created a horizontal bar chart!

**What You're Looking At:**

- Three horizontal bars (one per category)
- **Technology** has the longest bar (most sales)
- **Furniture** is next
- **Office Supplies** is shortest
- Each bar's length = total sales for that category

**The Number You See:**

Look at the Columns shelf - it says **"SUM(Sales)"**

Tableau automatically:
- Added up (summed) all sales for each category
- Created bars proportional to those sums
- Made a chart!

**You did it!** 🎉🎊👏

This is your first Tableau visualization!

---

### Exercise 5.3: Understanding What Just Happened

Let's break down what Tableau did:

**Step 1: The Aggregation**

When you dragged Sales to the view, Tableau:
1. Looked at all 9,000+ rows of data
2. Grouped them by Category
3. Added up all Sales for each category
4. Drew bars proportional to those totals

**Step 2: Check the Numbers**

Hover your mouse over each bar:
- A tooltip appears
- Shows exact sales amount
- Example: "Technology: $836,154"

Try it! Hover over each bar and see the values.

**Step 3: Reading Your Chart**

What does this chart tell you?

- **Question:** Which category generates the most sales?
- **Answer:** Technology! ($836K)
- **Question:** By how much?
- **Answer:** About $100K more than Furniture

You just answered business questions with data!

**Step 4: Rename Your Sheet**

Good practice: Always name your sheets descriptively

1. At the bottom, right-click on "Sheet 1"
2. Select **"Rename Sheet"**
3. Type: **Sales by Category**
4. Press Enter

Now it's clear what this sheet shows!

---

### Exercise 5.4: Making Your Chart Vertical

Most people prefer vertical bars. Let's flip it!

**Method 1: Drag and Drop**

1. Grab the **"Category"** pill from Rows shelf
2. Drag it to the **Columns** shelf
3. Grab the **"SUM(Sales)"** pill from Columns shelf
4. Drag it to the **Rows** shelf

**Method 2: Swap Button (Easier!)**

1. Look in the toolbar at the top
2. Find the **Swap** icon (two curved arrows)
3. Click it once

**What Changed:**

- Bars are now vertical (pointing up)
- Categories along the bottom (X-axis)
- Sales going up the left side (Y-axis)
- Taller bars = more sales

**Which is Better?**

Personal preference! Vertical bars are more common, but horizontal can be better for:
- Long category names
- Many categories
- Emphasis on rankings

For now, let's keep them **vertical** (Category on Columns, Sales on Rows).

---

### Exercise 5.5: Adding Color

Let's make this chart more visually appealing!

**Step 1: Locate the Marks Card**

On the left side, below the Data Pane, find the **Marks** card.

It shows:
- A dropdown (currently says "Automatic" or "Bar")
- Buttons: Color, Size, Label, Detail, Tooltip, Shape

**Step 2: Color Each Category Differently**

1. In the Data Pane, find **"Category"** under Dimensions
2. **Drag** "Category" to the **Color** button on the Marks card
3. Release the mouse

**What Happened:**

Each category now has its own color:
- Furniture: Blue
- Office Supplies: Orange
- Technology: Red (or green/gray depending on defaults)

A **color legend** appeared on the right side showing which color = which category.

**Step 3: Customize the Colors (Optional)**

Want to change the colors?

1. Click on **Color** on the Marks card
2. Click **"Edit Colors..."**
3. Select a category (e.g., "Furniture")
4. Click on the color square
5. Choose a new color
6. Click **"OK"**
7. Repeat for other categories
8. Click **"OK"** when done

**Pro Tip:** Choose meaningful colors
- Blue = Professional/Corporate
- Green = Growth/Money
- Red = Urgent/Important

---

### Exercise 5.6: Adding Value Labels

Let's display the exact sales numbers on each bar.

**Step 1: Add Labels**

1. Find **"Sales"** in the Measures section (green)
2. **Drag** "Sales" to the **Label** button on the Marks card

**What Happened:**

Numbers now appear on (or above) each bar showing exact sales values!

**Step 2: Format the Labels**

The numbers might show too many decimal places. Let's fix that:

1. Click **Label** on the Marks card
2. Check that **"Show mark labels"** is checked
3. Click the **"..."** button next to "Text"
4. Or: Right-click on a label in the chart → **"Format"**

5. In the Format pane that appears on the left:
   - Find **"Numbers"**
   - Click the dropdown
   - Select **"Currency (Custom)"**
   - Decimal places: **0** (for whole dollars)
   - Click away to apply

**What You See Now:**

Labels show as: **$836,154** instead of 836154.2341

Much more readable!

**Step 3: Adjust Label Position (If Needed)**

If labels overlap or look odd:

1. Click **Label** on Marks card
2. Under **"Alignment"**, try different options:
   - Top
   - Center  
   - Bottom
3. Try **Horizontal** alignment options too

Choose what looks best!

---

### Exercise 5.7: Adding a Title

Every chart needs a good title!

**Step 1: Edit the Sheet Title**

At the top of your worksheet, you'll see the sheet name: "Sales by Category"

1. Double-click on this title
2. Or: Right-click → **"Edit Title..."**

**Step 2: Write a Descriptive Title**

The Edit Title dialog opens. Type:

```
Total Sales by Product Category
2017-2020 Superstore Data
```

Or make it more impactful:

```
Technology Leads Sales at $836K
Product Category Performance Overview
```

**Step 3: Format the Title**

1. Select the text you just typed
2. Make it **Bold**
3. Increase font size to **14** or **16**
4. Choose **Center** alignment
5. Click **OK**

**Your chart now has:**
- Clear title
- Colored bars
- Value labels
- Professional appearance!

---

## Part 6: Understanding Dimensions and Measures

This is THE most important concept in Tableau!

### Exercise 6.1: What Are Dimensions?

**Definition:**

**Dimensions** are categorical fields that describe your data. They answer "WHAT?"

**Think of dimensions as:**
- Labels
- Categories
- Groups
- Descriptions

**In Tableau:**
- Shown with **blue** background
- Located in the top section of Data Pane
- Examples: Category, Region, Customer Name, Date

**What Dimensions Do:**

When you use a dimension in a view:
- Creates headers/labels
- Splits data into groups
- Defines rows or columns

**Example from Your Chart:**

**Category** is a dimension:
- Creates three groups: Furniture, Office Supplies, Technology
- Labels your bars
- Answers: "What are we comparing?"

**Other Dimensions in Your Data:**

- **Region**: East, West, Central, South
- **State**: California, Texas, New York, etc.
- **Customer Segment**: Consumer, Corporate, Home Office
- **Ship Mode**: Regular Air, Delivery Truck, etc.

**Key Insight:**

Dimensions are the "slicers and dicers" of your data. They let you break down and group your information in different ways.

---

### Exercise 6.2: What Are Measures?

**Definition:**

**Measures** are numeric fields that can be aggregated (added up, averaged, etc.). They answer "HOW MUCH?"

**Think of measures as:**
- Numbers
- Quantities
- Amounts
- Metrics

**In Tableau:**
- Shown with **green** background
- Located in the bottom section of Data Pane
- Examples: Sales, Profit, Quantity, Discount

**What Measures Do:**

When you use a measure in a view:
- Gets aggregated (SUM, AVG, COUNT, etc.)
- Creates values for bars/lines/areas
- Shows magnitudes

**Example from Your Chart:**

**Sales** is a measure:
- Tableau automatically summed all sales
- Creates bar heights/lengths
- Answers: "How much did each category sell?"

**Other Measures in Your Data:**

- **Profit**: How much money was made
- **Quantity**: How many items sold
- **Discount**: How much discount given
- **Shipping Cost**: How much shipping cost

**Key Insight:**

Measures are the "numbers" you're analyzing. They get aggregated to show totals, averages, or other summaries.

---

### Exercise 6.3: The Dimension-Measure Relationship

**How They Work Together:**

**Dimensions** define the structure (rows/columns)  
**Measures** fill in the values

**Think of it like a table:**

| Dimension (Category) | Measure (Sales) |
|---------------------|----------------|
| Furniture | $741,999 |
| Office Supplies | $719,047 |
| Technology | $836,154 |

Dimensions = Row headers  
Measures = Cell values

**In Your Chart:**

- **Dimension (Category)**: Created 3 bars (structure)
- **Measure (Sales)**: Determined bar heights (values)

**The Power of This:**

Change the dimension → See data grouped differently  
Change the measure → See different values  
Change aggregation → See different calculations

**Try This Experiment:**

**Step 1: Remove Sales from Rows**

1. Grab the **SUM(Sales)** pill from Rows shelf
2. Drag it off the shelf (anywhere outside)
3. Bars disappear! Only category labels remain

**Step 2: Try Different Measures**

1. Drag **"Profit"** to Rows
   - Now shows profit by category!

2. Remove Profit, try **"Quantity"**
   - Now shows quantity sold by category!

3. Remove Quantity, try **"Discount"**
   - Now shows total discount by category!

**Step 3: Put Sales Back**

Drag **"Sales"** back to Rows to restore your original chart.

**What You Learned:**

Same structure (3 categories), but different measures tell different stories!

📖 **Reference:** [Dimensions and Measures](https://help.tableau.com/current/pro/desktop/en-us/datafields_typesandroles.htm)

---

### Exercise 6.4: Understanding Aggregation

You've seen **SUM(Sales)** - what does that mean?

**What is Aggregation?**

Aggregation means combining multiple values into one.

**Common Aggregations:**

| Aggregation | What It Does | Example |
|-------------|--------------|---------|
| **SUM** | Adds all values | Total sales |
| **AVG** | Calculates average | Average order value |
| **MIN** | Finds minimum | Lowest price |
| **MAX** | Finds maximum | Highest quantity |
| **COUNT** | Counts records | Number of orders |
| **COUNTD** | Counts unique values | Number of customers |

**In Your Chart:**

**SUM(Sales)** means:
- For Furniture: Add up sales from ALL furniture orders
- For Office Supplies: Add up sales from ALL office supply orders
- For Technology: Add up sales from ALL technology orders

**Try Different Aggregations:**

**Step 1: Change Aggregation**

1. Right-click on **SUM(Sales)** in Rows shelf
2. Hover over **"Measure (Sum)"**
3. You'll see options: Sum, Average, Median, Count, etc.

**Step 2: Try Average**

1. Select **"Average"**
2. The pill changes to **AVG(Sales)**
3. Bars change size!

**What This Shows:**

Now showing **average sales per order** instead of **total sales**.

Notice:
- Values are MUCH smaller (hundreds vs. hundreds of thousands)
- Rankings might change
- Different story!

**Step 3: Try Count**

1. Right-click → Measure → **"Count"**
2. Now it's **CNT(Sales)**
3. Shows: How many sales records for each category

**Step 4: Back to Sum**

1. Right-click → Measure → **"Sum"**
2. Return to **SUM(Sales)** - your total sales view

**Key Takeaway:**

The aggregation method completely changes what your chart shows! Always be aware of how your measures are aggregated.

---

## Part 7: Saving and Sharing Your Work

You've created something great - let's save it!

### Exercise 7.1: Saving Your Workbook

**Understanding Tableau Files:**

Tableau has two save formats:

**.twb (Tableau Workbook):**
- Saves your visualizations
- Does NOT include data
- Smaller file size
- Links to original data file

**.twbx (Tableau Packaged Workbook):**
- Saves visualizations AND data
- Everything in one file
- Larger file size
- Portable!

**For this lab:** Use **.twbx** so your data travels with your work!

**Step 1: Save Your First Workbook**

1. Click **File** in the menu bar
2. Click **"Save to Tableau Public As..."**

**Note:** Tableau Public Edition requires saving to their cloud. If you want local-only saves, you'd need Tableau Desktop (paid version).

**Step 2: Create an Account (If First Time)**

If you haven't already:

1. Enter your email address
2. Create a password
3. Click **"Create My Account"**
4. Check your email for verification (if required)

**Step 3: Name Your Workbook**

1. Title: **My First Tableau Workbook - Lab 1**
2. Description (optional): "Created during Lab 1, shows sales by category"
3. Choose **"Unlisted"** if you don't want it publicly searchable
4. Click **"Save"**

**What Happens:**

- Your workbook uploads to Tableau Public
- A web browser opens showing your work online
- File is now saved in the cloud

**Alternative: Save Locally (Extract Required)**

If you want to save locally:

1. **File** → **"Export Packaged Workbook"**
2. Choose location: Your **Tableau_Lab_1** folder
3. Name: **LastName_FirstName_Lab1.twbx**
4. Click **"Save"**

This creates a local backup!

📖 **Reference:** [Save Your Work](https://help.tableau.com/current/pro/desktop/en-us/save_savework.htm)

---

### Exercise 7.2: Exploring Your Saved Work

**Online:**

After saving to Tableau Public:

1. Your browser opens to your online workbook
2. You (and others with the link) can interact with it
3. It's live and interactive!

**Your Profile:**

Visit: [https://public.tableau.com/app/profile/your.name](https://public.tableau.com/app/profile)

You'll see:
- Your published workbooks
- Views and stats
- Your public profile

**Privacy Settings:**

- **Public**: Anyone can find it
- **Unlisted**: Only people with link can see it
- You can change this anytime

---

### Exercise 7.3: Opening Your Work Later

**From Tableau Public Server:**

1. Open Tableau Desktop Public Edition
2. Click **"Open from Tableau Public"**
3. Sign in
4. Select your workbook
5. Click **"Open"**

**From Local File:**

1. Open Tableau Desktop Public Edition
2. Click **"Open Workbook"**
3. Navigate to your .twbx file
4. Click **"Open"**

---

## Quick Reference Guide

### Essential Shortcuts

| Action | Windows | Mac |
|--------|---------|-----|
| New Worksheet | Ctrl + M | Cmd + M |
| New Dashboard | Ctrl + D | Cmd + D |
| Save | Ctrl + S | Cmd + S |
| Undo | Ctrl + Z | Cmd + Z |
| Redo | Ctrl + Y | Cmd + Y |
| Swap Rows/Columns | Ctrl + W | Cmd + W |
| Show Me | Ctrl + 1 | Cmd + 1 |

### Key Concepts

**Dimensions (Blue):**
- Categories, labels, groups
- Text, dates, locations
- Create structure (rows/columns)

**Measures (Green):**
- Numbers, quantities, amounts
- Always aggregated (SUM, AVG, etc.)
- Create values (bar heights, etc.)

**Pills:**
- Blue pill = Dimension
- Green pill = Measure
- Shape indicates discrete vs. continuous

**Shelves:**
- **Rows**: Vertical structure
- **Columns**: Horizontal structure
- **Filters**: What to include/exclude
- **Marks Card**: How to display

### Common Chart Types

- **Bar Chart**: Compare categories
- **Line Chart**: Trends over time
- **Pie Chart**: Parts of whole
- **Scatter Plot**: Relationship between two measures
- **Map**: Geographic data

---

## Submission Requirements

### What to Submit

**1. Tableau Workbook**

Either:
- Share link to your Tableau Public workbook, OR
- Submit your .twbx file

**Naming:** LastName_FirstName_Lab1.twbx

**2. Screenshot Document (PDF or Word)**

Create a document with:

**Part A: Screenshots**

Include screenshots of:
1. **Tableau Start Page** (showing you have it installed)
2. **Data Source Page** (showing connected to Superstore.csv)
3. **Your First Chart** (Sales by Category bar chart)
4. **Marks Card** (showing Color button in use)
5. **Your Final Chart** (with colors and labels)

**Part B: Written Responses**

Answer these questions (2-3 sentences each):

1. **What is Tableau?** In your own words, explain what Tableau does and why it's useful.

2. **Dimensions vs. Measures:** Explain the difference between dimensions and measures. Give an example of each from the Superstore data.

3. **Your Chart:** What does your "Sales by Category" chart show? What business insight can you draw from it?

4. **Aggregation:** What does SUM(Sales) mean? Why does Tableau automatically aggregate measures?

5. **Reflection:** What was the easiest part of this lab? What was the most challenging? What would you like to learn next?

**Part C: Your Data Observations**

Based on the Superstore data, answer:

1. Which category has the highest sales?
2. What is the dollar amount of those sales?
3. How much more (or less) are the other categories compared to the top category?
4. If you were a store manager, what would you conclude from this data?

**3. Naming Convention**

- Workbook: **LastName_FirstName_Lab1.twbx**
- Document: **LastName_FirstName_Lab1_Documentation.pdf**

---

## Troubleshooting

### Installation Issues

**Problem: "Not enough disk space"**

**Solution:**
- Free up at least 2GB of space
- Uninstall unused programs
- Empty recycle bin

**Problem: "Need administrator rights"**

**Solution:**
- Contact your IT department
- Or install in user folder if allowed
- Or use Tableau in a computer lab

---

### Connection Issues

**Problem: "Can't find the CSV file"**

**Solution:**
- Make sure file is fully downloaded
- Check your Downloads folder
- Verify file name: Superstore.csv
- Try downloading again

**Problem: "File won't open"**

**Solution:**
- Don't open CSV in Excel first
- Use Tableau's "Text file" connector
- Check file isn't corrupted (re-download)

---

### Chart Issues

**Problem: "Nothing appears when I drag fields"**

**Solution:**
- Make sure you're on a Worksheet (not Data Source page)
- Try dragging to Rows or Columns shelf directly
- Check that the field isn't already in the view

**Problem: "Bars are tiny or huge"**

**Solution:**
- Right-click axis → "Edit Axis"
- Check "Include zero"
- Adjust range manually

**Problem: "Colors won't change"**

**Solution:**
- Make sure you dragged field to Color button (not just onto chart)
- Try clicking Color button to edit manually
- Check if field has values (not all null)

---

### Saving Issues

**Problem: "Can't save to Tableau Public"**

**Solution:**
- Check internet connection
- Verify email/password
- Try "Export Packaged Workbook" for local save

**Problem: "File too large"**

**Solution:**
- Use .twb instead of .twbx (doesn't include data)
- Or use data extract
- Or publish to Tableau Public

---

### General Issues

**Problem: "Tableau is slow"**

**Solution:**
- Close other programs
- Use data extract (Data → Extract Data)
- Simplify your visualization
- Restart Tableau

**Problem: "I made a mistake and want to undo"**

**Solution:**
- Press Ctrl+Z (Windows) or Cmd+Z (Mac)
- Or: Edit menu → Undo
- Can undo multiple steps

**Problem: "I'm lost and don't know what to do"**

**Solution:**
- Reread the exercise from the start
- Check the reference documentation links
- Try File → New to start fresh
- Ask your instructor for help

---

## Next Steps

### Continue Learning

**Official Tableau Resources:**
- **Free Training Videos:** [https://www.tableau.com/learn/training](https://www.tableau.com/learn/training)
- **Getting Started Guide:** [https://help.tableau.com/current/pro/desktop/en-us/gettingstarted_overview.htm](https://help.tableau.com/current/pro/desktop/en-us/gettingstarted_overview.htm)
- **Community Forums:** [https://community.tableau.com/](https://community.tableau.com/)

**What's Next in This Course:**
- **Lab 2:** Creating multiple visualizations (bar charts, line charts, maps)
- **Lab 3:** Connecting multiple data sources (joins and blending)
- **Lab 4:** Calculations and aggregations
- **Lab 5:** Level of detail expressions

**Practice Ideas:**
1. Try creating different chart types with your data
2. Explore other fields in the Superstore data
3. Change dimensions and measures to see different views
4. Download other sample datasets and practice connecting
5. Visit Tableau Public gallery for inspiration

---

## Congratulations! 🎉

**You've completed Lab 1!**

You now know how to:
✅ Install Tableau Desktop Public Edition  
✅ Connect to a CSV data file  
✅ Navigate the Tableau interface  
✅ Understand dimensions vs. measures  
✅ Create a bar chart  
✅ Add colors and labels  
✅ Save your work  

**You're officially a Tableau user!**

This is just the beginning. With practice, you'll create amazing visualizations that communicate insights, drive decisions, and tell compelling stories with data.

**Remember:** Every expert started exactly where you are now - opening Tableau for the first time, dragging their first field, seeing their first chart appear. You've taken that crucial first step!

---

**Lab Created By:** Dr. Lee  
**Last Updated:** 2025  
**Questions?** Contact your instructor or visit office hours

**Data Source:**
- **Download Link:** [Superstore.csv](https://github.com/fenago/tableau-fundamentals/raw/refs/heads/master/Lab%2001/Superstore.csv)

**Welcome to the world of data visualization!** 🌟📊🚀
