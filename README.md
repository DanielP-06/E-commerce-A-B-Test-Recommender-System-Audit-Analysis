# E-commerce A/B Test: Recommender System Audit & Analysis

## Project Overview
This project presents a forensic audit and in-depth analysis of an abandoned A/B test concerning a new recommender system for an e-commerce platform. The primary goal was to evaluate the impact of the new system on key conversion metrics across the user funnel: product page views, cart additions, and ultimate purchases. The analysis assesses the integrity of the experiment, examines user behavior patterns, and employs statistical Z-tests to determine the significance of observed differences. Contrary to initial expectations, the findings indicate that the new recommender system negatively impacted conversion rates.

## Problem
An international online store launched an A/B test for a new recommender system but abandoned it. The task is to act as a data auditor, verifying the experiment's integrity, analyzing its results, and determining whether the new recommender system was effective in increasing conversion, particularly by the expected 10% across key funnel stages product_page, product_cart, purchase.

## Project Objectives
*   **Experiment Integrity Validation:** Verify that the technical design was followed and no biases existed due to user overlap or external events.
*   **Exploratory Data Analysis (EDA):** Analyze user navigation patterns and event distributions to understand user interaction with the sales funnel.
*   **Recommender System Efficacy Evaluation:** Determine if the new system really generated a real 10% increase in conversion at critical funnel stages.
*   **Statistical Confirmation:** Apply Z-tests to ensure that observed differences between the control (A) and experimental (B) groups are statistically significant and not due to chance.

## Data Description
The analysis utilizes four datasets related to the A/B test:
*   ab_project_marketing_events_us.csv: Calendar of marketing events for 2020.
*   final_ab_new_users_upd_us.csv: All users registered between December 7-21, 2020.
*   final_ab_events_upd_us.csv: All events performed by new users from December 7, 2020, to January 1, 2021.
*   final_ab_participants_upd_us.csv: Table containing data of test participants.

## Methodology
1.  **Data Exploration & Preprocessing:** Initial review of data types, missing values, and duplicates. Date columns were converted to datetime objects. Missing values in 'details' for non-purchase events were confirmed as expected.
2.  **Experiment Integrity Check:** 
    *   Filtered participants for the 'recommender_system_test'.
    *   Verified no users were assigned to both control (A) and experimental (B) groups.
    *   Applied a 14-day window filter for events post-registration as per test specifications.
    *   Identified a significant discrepancy in the number of participants compared to the expected 6,000, affecting statistical power.
3.  **Exploratory Data Analysis (EDA):**
    *   Analyzed the distribution of events per user, observing group A's higher activity.
    *   Examined event distribution over time, noting disproportionate activity between groups and a significant drop after the Christmas period.
    *   Identified potential issues like unbalanced groups and holiday season interference.
4.  **Funnel Conversion Analysis:**
    *   Calculated unique users at each stage of the conversion funnel (login -> product_page -> product_cart -> purchase) for both groups.
    *   Computed conversion rates at each stage.
    *   Observed a non-linear funnel, indicating direct purchases bypassing the cart probably by direct-buy buttons.
5.  **Statistical Testing (Z-Test):**
    *   Formulated null ($H_0$) and alternative ($H_1$) hypotheses for each funnel stage.
    *   Applied proportions_ztest to compare conversion rates between Group A and Group B for 'product_page', 'product_cart', and 'purchase' events.
    *   Used a significance level ($\\alpha$) of 0.05.

## Key Findings & Conclusions
*   **Underperformance of New System:** The new recommender system (Group B) did not achieve the expected 10% conversion increase. Instead, it showed lower conversion rates across all funnel stages compared to the control (Group A).
*   **Statistically Significant Decreases:** Z-tests confirmed statistically significant decreases in conversion for Group B at the product_page and purchase stages (p-value < 0.05). This indicates the observed drops are not due to chance.
*   **Funnel Bottleneck:** The largest drop-off for Group B occurred after login, with fewer users proceeding to view product pages, suggesting the new recommendations might not be engaging or relevant.
*   **Experiment Design Flaws:**
    *   **Unbalanced Groups:** The control group (A) was significantly larger than the experimental group (B), impacting the reliability of comparisons.
    *   **Seasonal Interference:** The test ran during the December holiday season, a period prone to anomalous user behavior influenced by marketing campaigns.
    *   **Inconsistent Activity:** Group A exhibited disproportionately higher and more erratic activity compared to Group B, further questioning random assignment and experiment integrity.

## Recommendations
*   **Do NOT Implement the New System:** Based on the significant negative impact on conversion at critical stages, implementing the new recommender system is not advisable due to high risk of revenue loss.
*   **Technical Review:** Conduct a thorough technical review of the new recommender algorithm to understand its underlying mechanisms and identify potential flaws.
*   **Rethink Experiment Design:** Plan a new A/B test under more controlled conditions:
    *   **Stable Season:** Conduct the test during a period of stable e-commerce traffic, avoiding major holidays.
    *   **Balanced Groups:** Ensure a 50/50 split of users between control and experimental groups from the outset.
    *   **Appropriate Sample Size:** Aim for the specified sample size of 6,000 participants to ensure sufficient statistical power.

## How to Run
To run this analysis locally or in Google Colab, follow these steps:

1.  **Clone the Repository (if applicable):**
2.  **Download Datasets:** Ensure the following CSV files are placed in the drive directory or update the paths in the notebook to your local structure:
3.  **Install Dependencies:** All necessary libraries are standard in most Python data science environments. If running locally, ensure you have them installed:
4.  **Open the Notebook:** 
5.  **Run Cells:** Execute the cells sequentially.

## Contact
danielpineda_06@hotmail.com
