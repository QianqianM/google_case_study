🚴 How Does a Bike-Share Navigate Speedy Success?
[🔗 View the full project here](https://qianqianm.github.io/GoogleCaseStudy/)

**📌 Overview**

This project is part of the Google Data Analytics Capstone Case Study.
I analyzed historical trip data from Cyclistic, a fictional bike-share company in Chicago, to answer this key business question:
How do casual riders and annual members use Cyclistic bikes differently, and how can we convert casual riders into members?

The analysis follows the six-step data analysis process:
Ask → Prepare → Process → Analyze → Share → Act

**📊 Key Insights**

Casual riders tend to ride mostly on weekends and for leisure.

Annual members ride more during weekdays, often for commuting.

Members’ ride durations are generally shorter but more frequent.

Marketing opportunities exist in targeting casual riders who frequently rent during peak seasons.

**🛠️ Tools & Skills Used**

Excel – Initial cleaning, duplicate removal, pivot tables, and exploratory calculations
SQL – Data storage, transformation, and deeper analysis
Tableau – Data visualization and dashboard creation

**🔍 My Approach**

**1️⃣ Data Cleaning (Excel)**
Removed duplicates and null values

Converted started_at and ended_at to short date format

Created new calculated fields:
ride_length (trip duration)
day_of_week (numeric weekday value)
Filtered out trips with zero or negative ride durations

**2️⃣ Initial Exploration (Excel)**
Built pivot tables for quick pattern recognition
Performed basic descriptive statistics

**3️⃣ Deeper Analysis (SQL & Visualization)**
Combined and queried multiple months of trip data
Created clear, professional visuals and dashboards to share findings with stakeholders

**📈 Outcomes**

Identified clear behavioral differences between casual riders and members
Suggested marketing strategies to:
Promote annual memberships to casual riders who frequently ride during weekends
Emphasize cost-effectiveness and convenience for commuters

**🚀 Next Steps**

Test targeted marketing campaigns for high-frequency casual riders
Expand analysis to include seasonal trends and demographic data
Automate data cleaning and processing pipeline for future datasets