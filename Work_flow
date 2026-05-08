# Project Workflow & Technical Implementation

## Data Loading & Integration

The workforce attendance dataset was imported into Power BI Desktop using CSV and Excel-based attendance records containing employee attendance, work-from-home, and leave tracking information.

---

# Data Transformation Using Power Query

The dataset was cleaned, structured, and transformed using Power Query Editor to prepare the data for workforce analytics and reporting.

The transformation process included:

* Organizing raw attendance records
* Standardizing column structures
* Removing inconsistencies and unnecessary values
* Creating reusable transformation logic for multiple monthly sheets

A duplicate query named `Template` was created to establish a reusable transformation workflow.

---

# Data Preparation & Structuring

The following transformation steps were performed:

### Sheet Selection & Header Formatting

* Selected monthly attendance sheets (e.g., April 2022)
* Promoted the first row as headers
* Renamed and standardized column names for consistency

### Date Consolidation

Attendance dates were originally stored across multiple columns.

Using the **Unpivot Columns** transformation:

* All date columns were consolidated into a single `Date` column
* `Employee ID` and `Employee Name` columns were preserved

This improved data normalization and enabled time-series analysis.

---

# Date Formatting & Cleanup

The consolidated date column was:

* Renamed as `Date`
* Converted into proper date format
* Cleaned to remove invalid text-based values

This ensured compatibility with Power BI time intelligence functions and trend analysis.

---

# Parameter Creation & Dynamic Processing

A Power Query parameter named `Worksheet` was created to dynamically process different monthly attendance sheets.

This approach improved:

* Reusability
* Scalability
* Transformation efficiency

---

# Custom Transformation Function

The template query was converted into a reusable Power Query transformation function named:

```plaintext id="lhmz0i"
GetData
```

This function enabled automated transformation processing across multiple attendance sheets.

---

# Invoking Dynamic Queries

Using the `Invoke Custom Column` feature:

* The `GetData` function was applied to all attendance sheets
* Monthly workforce data was consolidated into a unified analytical dataset

This significantly reduced manual preprocessing effort.

---

# Data Modeling & DAX Calculations

After loading the transformed dataset into Power BI, several DAX measures were created to support workforce analytics.

## Total Working Days

```DAX id="i1njjw"
Total Working Days =
VAR totaldays = COUNT('Final Data'[Date])

VAR nonworkingdays =
CALCULATE(
    COUNT('Final Data'[Value]),
    'Final Data'[Value] IN {"WO","HO"}
)

RETURN
totaldays - nonworkingdays
```

---

## Present Days

```DAX id="lsmktt"
Present Days =
VAR Presentdays =
CALCULATE(
    COUNT('Final Data'[Value]),
    'Final Data'[Value] = "P"
)

RETURN
Presentdays + [WFH Count]
```

---

## Presence Percentage

```DAX id="cok4ii"
Presence % =
DIVIDE([Present Days], [Total Working Days], 0)
```

---

## Work From Home Count

```DAX id="eh3oqx"
WFH Count =
SUM('Final Data'[WFH Count])
```

---

## Sick Leave Count

```DAX id="tkn6hj"
SL Count =
SUM('Final Data'[SL Count])
```

---

## Sick Leave Percentage

```DAX id="7mpp0o"
SL % =
DIVIDE([SL Count], [Total Working Days], 0)
```

---

# Dashboard Development

Interactive Power BI visualizations were developed to improve workforce monitoring and operational reporting.

The dashboard included:

### KPI Cards

* Presence Percentage
* Work From Home Percentage
* Sick Leave Percentage

### Matrix Visualizations

* Attendance Matrix Overview
* Daily Attendance Breakdown
* Workforce Metrics by Weekday

### Trend Analysis

Area charts were created to visualize:

* Day-wise Presence %
* Work From Home %
* Sick Leave %

These visualizations improved workforce trend analysis and operational visibility.

---

# Key Learning Outcomes

This project strengthened practical understanding of:

* Power Query transformations
* Dynamic query processing
* DAX measure creation
* Workforce analytics modeling
* Interactive dashboard development
* Matrix visualization techniques
* Business-focused reporting in Power BI

The project also improved the ability to transform raw operational data into actionable workforce intelligence.
