# DATA ANALYSIS PROJECT REPORT: Temporal Patterns in Urban Crime 

**Student Name:** [Your Name]
**Student ID:** [Your ID] 
**Course / Section:** [Course Code] 
**Instructor:** [Instructor Name] 
**Date of Submission:** May 2, 2026 

---

## 1. Executive Summary 
This project investigates urban crime patterns using a dataset of over 1,000 incidents . The primary goal was to identify how time-based variables—such as the hour of the day and the day of the week—influence crime frequency and type . Using **Pandas** for data manipulation and **NumPy** for statistical anomaly detection, the analysis revealed that crime is not evenly distributed across the clock . Key findings indicate that the "Night" period accounts for the highest proportion of incidents and that specific high-density "Areas" exhibit crime volumes that are statistically significant outliers (Z-score > 1.5) . These insights suggest that public safety resources should be prioritized based on temporal and geographic hotspots .

---

## 2. Introduction and Project Objectives 
Understanding when and where crimes occur is essential for effective law enforcement and community safety planning . This project explores a real-world crime dataset to uncover hidden temporal trends .

| Item | Your Content |
| :--- | :--- |
| **Dataset name** | Crime Data from 2020 to Present  |
| **Dataset source** | [Insert link to dataset]  |
| **Main project goal** | To analyze the relationship between time-based features and crime frequency . |
| **Research Question 1** | How does the frequency of crime vary across different times of day (Morning, Afternoon, Evening, Night)?  |
| **Research Question 2** | Which geographic areas act as statistical "High Density Zones" based on Z-score analysis?  |
| **Research Question 3** | Is there a visible relationship between the time of day and the specific types of crime committed?  |

---

## 3. Dataset Description 
The dataset contains detailed logs of criminal incidents, including the date, time, location (Area), and victim demographics .

### 3.1 Basic Dataset Information 
| Property | Value |
| :--- | :--- |
| **Number of rows** | [Insert final shape from df.shape]  |
| **Number of columns** | [Insert number of columns]  |
| **Data types present** | Numerical, Categorical, and Date-Time  |
| **Target / Key variables** | `CRIME`, `TIME OF DAY`, `AREA NAME`  |
| **Potential issues** | Missing weapon data and non-standard gender entries  |

---

## 4. Data Cleaning and Preparation 
Four major cleaning steps were performed to ensure the analysis was accurate .

| Issue Found | Action Taken | Reason / Justification | Code Reference |
| :--- | :--- | :--- | :--- |
| Missing Occurrence Dates | Dropped rows with `NaN` in `DATE OCC` | Primary analysis is time-based; missing dates are unusable. | Cell 2  |
| Inconsistent Gender Labels | Used `.str.upper()` and replaced "UNKNOWN"/"X" with `np.nan` | Standardizes categories for accurate demographic pivoting. | Cell 2  |
| Missing Weapon Data | Filled `NaN` with "WEAPON UNKNOWN" | Prevents loss of data rows while acknowledging missing info. | Cell 2  |
| Incorrect Date Types | Converted strings to `pd.to_datetime` | Enables extraction of month, year, and day names. | Cell 2  |

---

## 5. Feature Engineering 
New features were derived to facilitate deeper analysis .

| New Feature | How It Was Created | Why It Is Useful |
| :--- | :--- | :--- |
| **HOUR OCC** | Extracted the hour from the `TIME OCC` HHMM integer. | Allows for hourly trend analysis . |
| **TIME OF DAY** | A custom function grouping hours into Morning, Afternoon, Evening, and Night. | Simplifies complex hourly data into actionable shifts . |
| **DAY OF WEEK** | Extracted from `DATE OCC` using `.dt.day_name()`. | Enables comparison of weekday vs. weekend crime rates . |

---

## 6. Analysis Methodology 
* **Pandas:** Used for loading the dataset, loading date formats, cleaning, grouping, and creating summary tables .
* **NumPy:** Used for numerical computations including mean, standard deviation, and Z-scores to identify statistical anomalies .
* **Matplotlib:** Used to create at least 4 meaningful visualizations supporting the research questions .

---

## 7. Analysis and Visualizations 

### 7.1 Research Question 1: Temporal Distribution 
**Analysis:** We aggregated crime counts by the engineered `TIME OF DAY` feature .
* **Visualization:** Bar Chart showing crime counts per Time of Day .
* **Interpretation:** The analysis indicates that the "Night" period is the most active for crime incidents .

### 7.2 Research Question 2: Geographic Hotspots 
**Analysis:** Applied Z-score analysis to identify high-density zones .
* **Visualization:** Bar chart for top 5 Areas .
* **Interpretation:** Areas with a Z-score > 1.5 represent statistical high-crime density locations .

### 7.3 Research Question 3: Relationship Analysis 
**Analysis:** Correlated Time of Day with Crime types using pivot tables and stacked bar charts .
* **Visualization:** Stacked bar chart for Relationship Between Time of Day and Top Crime Types .
* **Interpretation:** Specific crime types vary significantly across different times of the day .

---

## 8. NumPy-Based Custom Computation 
| Component | Description |
| :--- | :--- |
| **Computation used** | Area Safety Z-Score Calculation  |
| **Purpose** | To identify areas that are statistically anomalous compared to the mean . |
| **Logic** | $Z = (x - \mu) / \sigma$ using `np.mean()` and `np.std()` . |
| **Result / Takeaway** | Identified areas that act as high-density outliers . |

---

## 9. Key Findings 
1.  **Temporal Peak:** The "Night" period contains the highest total count of crimes .
2.  **High-Risk Areas:** Z-score analysis identifies specific areas as high-density zones .
3.  **Outlier Spikes:** Specific dates were identified as outliers with crime spikes beyond normal variations .
4.  **Weapon Trends:** Blunt objects and unknown weapons represent common choices in the top 5 weapon categories .
5.  **Gender Patterns:** Distinct crime patterns were visible based on victim sex through relationship analysis .

---

## 10. Limitations 
The project is subject to limitations such as reporting bias and incomplete data in columns like "WEAPON" . Correlation between time and crime does not imply direct causation .

---

## 11. Conclusion 
The analysis successfully identifies key temporal and geographic patterns in urban crime . Future work could involve predictive modeling based on these identified hotspots .

---

## 12. References / Dataset Source 
* Crime Data from 2020 to Present. [Insert Source URL] 
