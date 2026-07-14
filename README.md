# Customer Churn Analysis Dashboard

![Dashboard Screenshot](https://github.com/user-attachments/assets/a7ede127-d3e4-456c-be7c-49716738ea32)

### 📊 [View Live Dashboard on Tableau Public](https://public.tableau.com/app/profile/pondharani.devendra/viz/Book1_17839575192110/Dashboard1)

## 🚀 Executive Summary
A modern, application-style Tableau dashboard designed to track customer churn, retention rates, and at-risk user segments. By layering transparent data visualizations over a custom-designed Figma user interface, this project transforms standard reporting into an intuitive, seamless executive tool. The analysis successfully identified a critical 4.6-month drop-off window and key price-sensitivity thresholds, providing actionable data to improve customer retention strategies.

## 🎯 Business Problem & Impact
Subscription-based businesses lose significant revenue due to unidentified churn signals. The goal of this project was to:
* Transition from reactive to proactive retention by segmenting users based on tenure and behavior.
* Identify the exact acquisition channels and product categories driving the highest churn.
* **Impact:** Provided a clear visualization of the 4.6-month critical drop-off window, allowing stakeholders to target "High Risk" and "Hibernating" customers before they cancel.

## 🛠️ Data Operations & Methodology
To ensure high accuracy in reporting, the raw data underwent rigorous preparation before visualization:
* **Data Cleaning & Imputation:** Processed unstructured subscription data, utilizing mean and median imputation techniques to handle missing numeric values.
* **Accurate Metric Tracking:** Exclusively utilized `COUNTD` (Count Distinct) on Customer IDs rather than standard row counts to guarantee unique human users were tracked without data duplication.
* **Logical Segmentation:** Engineered a conditional data funnel to categorize active users based on their lifespan to prioritize marketing and re-engagement efforts.

## 🧠 Advanced Technical Implementation
To achieve the customized UI and advanced analytics, several specialized Tableau techniques and calculated fields were executed.

**1. Risk Segmentation Logic (Calculated Field)**
Categorizes the user base into actionable groups based on current status and tenure.
```tableau
IF [Customer Status] = 'Churned' THEN 'Lost'
ELSEIF [Tenure Months] < 3 THEN 'High Risk'
ELSEIF [Tenure Months] >= 3 AND [Tenure Months] <= 6 THEN 'Hibernating'
ELSE 'Safe'
END
```

**2. Exact Churn Calculation**
Isolates and aggregates only the users who have officially left the platform.
```tableau
COUNTD(IF [Customer Status] = 'Churned' THEN [Customer ID] END)
```

**3. Custom Dual-Axis Donut Charts**
Utilized a zero-axis anchor to create a floating center over pie charts for tracking Origin Channels.
```tableau
MIN(0)
```

**4. UI/UX Canvas Integration**
* Stripped all default Tableau formatting (grid lines, zero lines, shading, row/column dividers).
* Applied **Floating Layouts** over fixed pixel dimensions to perfectly align transparent worksheets onto the custom Figma background canvas.

## 📊 Visual Features & Insights
* **Executive KPIs:** Real-time tracking of Total Churned, Churn Rate, Retention Rate, and At-Risk Customers.
* **Risk Segmentation (Proportional Treemap):** Instantly highlights the volume of users in the Safe, Hibernating, High Risk, and Lost buckets.
* **Behavioral Trends (Survival Curve):** A tenure line chart and monthly vertical bar chart pinpointing exactly when users historically drop off.
* **Origin & Category Tracking:** Dual-axis donut charts and horizontal bar charts ranking the exact acquisition channels and product categories driving churn.

## 💻 Tech Stack
* **Data Visualization & Analytics:** Tableau / Tableau Public
* **Data Processing & Engineering:** Python, Pandas
* **UI/UX Design:** Figma

## 📂 Repository Contents
* `Customer_Churn_Analysis.twbx`: The packaged Tableau workbook containing all dashboards, datasets, and calculated fields.
* `Dataset`: The raw and cleaned subscription data utilized for this analysis.
* `UI_Background.png`: The custom application interface designed in Figma.

## 📬 Let's Connect
If you have any questions about this project, my data cleaning methodologies, or would like to discuss data analysis opportunities, feel free to reach out:

* **Email:** pondharani.devendra22@gmail.com
* **LinkedIn:** [Pondharani Devendra](https://www.linkedin.com/in/pondharani-devendra-a809b339b/)
