# Tableau Data Visualization Project: Call Center KPI Dashboard

**Overview**

This project involves creating a Key Performance Indicator (KPI) Dashboard for a call center manager. The dashboard provides a clear and concise summary of key metrics related to team performance, call volume, and resolution rates. The goal is to help stakeholders track trends, monitor progress, and make data-driven decisions.

## Skills Used

- **Data Cleaning & Preparation:** Handling incorrect time formats and transforming data for effective visualization.

- **Calculated Fields:** Creating custom fields for date, time, and resolution rate calculations.

- **Data Visualization:** Designing multiple sheets with call volume, resolution rates, satisfaction ratings, and employee performance insights.

- **Filtering & Aggregation:** Extracting data for the most recent month and day.

- **Dashboard Formatting:** Combining all visual elements into an interactive and user-friendly dashboard.

## Step-by-Step Process

**1. Data Cleaning & Preparation**

- The raw dataset had incorrect formatting for the time and duration columns.

- Fixed the Time Format: Created a calculated field to extract time correctly:

- Full time format: `STR(DATEPART('hour',[Time])) + ':' + STR(DATEPART('minute',[Time])) + ':' + STR(DATEPART('second',[Time]))`

- Hour-only format: `DATEPART('hour',[Time])`

- Converted "Avg Talk Duration" to seconds: `(DATEPART('minute',[Avg Talk Duration]) * 60) + DATEPART('second',[Avg Talk Duration])`

- Changed the Date Column to the correct date datatype.

**2. Creating the KPI Dashboard Sheets**

- First Sheet: Satisfaction Ratings

  - Visualized the satisfaction ratings of calls, showing the count of each rating.

  - Filtered to show only the most recent month’s data:

  - Created a calculated field: `DATEPART('month',[Date]) = DATEPART('month',{MAX([Date])}) AND DATEPART('year',[Date]) = DATEPART('year',{MAX([Date])})`

- Second Sheet: Call Volume Analysis

  - Examined call volume trends by day of the week and hour of the day.

  - Added an average line to highlight above-average call days and hours.

- Third Sheet: Resolution Rates

  - Calculated the percentage of resolved calls: `SUM(IF([Resolved] = 'Y') THEN 1 ELSE 0 END) / COUNT([Resolved])`

  - Visualized the resolution rate to track efficiency in call resolution.

- Fourth Sheet: Most Recent Day Stats

  - Added a "most recent day" ticker to show:

  - Number of calls received today.

  - Average call duration.

  - Used a formula similar to the most recent month but adjusted for the day: `DATEPART('day',[Date]) = DATEPART('day',{MAX([Date])}) AND DATEPART('month',[Date]) = DATEPART('month',{MAX([Date])}) AND DATEPART('year',[Date]) = DATEPART('year',{MAX([Date])})`

  - Calculated average call duration in minutes: `ROUND(AVG([Talk Duration seconds])/60,2)`

**3. Drilling Down to Employee Performance**

- Created a step chart to show:

  - Resolution rate per employee.

  - Satisfaction rating per employee.

  - Speed of answer per employee.

  _Found that answer time and satisfaction rating were similar across employees, so pivoted to call volume and resolution rates._

-Identified which employees had the highest and lowest resolution rates.

**4. Finalizing the Dashboard**

- Integrated all visuals into the KPI dashboard.

- Applied formatting to improve readability and user experience.

- Ensured dynamic filtering so the dashboard always displays the most recent month’s data.

## Conclusion

This project successfully delivers a dynamic and insightful KPI Dashboard for the call center manager, allowing real-time tracking of team performance, call trends, and resolution efficiency. The dashboard provides valuable insights into call handling effectiveness, helping to drive data-informed decisions for the organization.
