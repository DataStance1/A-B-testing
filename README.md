# A-B-testing
**Date of Analysis:** November 6, 2025

**Project Goal:** To identify if publishing articles during specific times of morning (early morning vs. late morning) influences simulated article engagement on a media platform.

**Hypothesis:** Articles published in the early hours of the morning (6AM–9AM) will exhibit higher simulated engagement compared to articles published in the late hours of the morning (10AM–12PM).

---

### **1. Data Acquisition Summary**
* **API Used:** NewsAPI.org
* **Query:** 'Tesla'
* **Data Period:** Articles fetched from 2025-11-05.
* **Total Articles Fetched:** 300 articles.

---

### **2. A/B Test Group Simulation**
* Articles were assigned to two groups based on their `publication_hour`:
    * **Group A (Early_Morning):** Articles published between 6 AM and 9 AM.
    * **Group B (Late_Morning):** Articles published between 10 AM and 12 PM.
* **Simulated Engagement Score:** Since real engagement data is not available from the API, a `simulated_engagement_score` was created. This score incorporates a base random value, title word count, a simulated source popularity factor, and a deliberate positive bias for Group A (EarlyMorning posts) to create a scenario where the hypothesis might be supported.
* **Group Sizes:**
    * Group A: 108 articles
    * Group B: 183 articles 
---

### **3. Data Cleaning & Exploration Highlights**
* **Missing Data Handling:** Rows with missing `title` or `description` were dropped. Missing `author`, `urlToImage`, and `content` were filled with placeholder values.
* **Data Types:** `publishedAt` was successfully converted to datetime objects, and `publication_hour` was extracted as an integer.
* **Descriptive Statistics:**
    * Average simulated engagement score for Group A: 75.535443
    * Average simulated engagement score for Group B: 66.655195

---

### **4. Analysis & Visualization Highlights**
* The histogram of "Distribution of Title Word Count" shows that most articles have headlines between X and Y words.
* The average engagement varied across different news sources, with `Source Name` showing the highest simulated engagement.
* **Outlier Management:** 2 outliers in the `simulated_engagement_score` were identified using the IQR method

---

### **5. A/B Test and Interpretation**
* **Test Performed:** Independent Samples T-test (Welch's t-test, assuming unequal variances).
* **Null Hypothesis (H0):** There is no much difference in mean simulated engagement between early morning and late morning posts.
* **Alternative Hypothesis (H1):** Early morning posts have more engagement than late morning posts.
* **Significance Level (alpha):** 0.05

* **Results:**
    * Mean Engagement Group A: 75.54
    * Mean Engagement Group B: 66.68
    * T-statistic: 4.697
    * P-value: 0.000

* **Interpretation:**
    * Given the p-value of 0.000 is less than our significance level of 0.05, we reject the null hypothesis.
    * This implies that there is a significant difference in simulated article engagement between articles published in the early morning hours and those published in the late morning hours.
    * Specifically, Group A (early morning posts) shows a higher average simulated engagement, supporting our hypothesis.

---

### **6. Key Insights & Recommendations**

**Recommendation:**
* Based on this simulated A/B test, it is recommended to prioritize article publication in the early morning timeframe (6AM to 9AM), as indicated by a significantly higher simulated engagement.

**Considerations Outliers:**

* **Outliers:** 2 were spotted. The removal of outliers from the `simulated_engagement_score` was crucial because they could have skewed the mean engagement scores for one or both groups, potentially leading to a false positive or false negative in our statistical significance test. This step strengthens the robustness of our A/B test results.

---
"""
