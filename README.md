# MTN Nigeria Customer Churn — SQL Analysis

## Project Overview

This project explores customer behavior and churn patterns using SQL logical and comparison operators on a telecom dataset modeled after MTN Nigeria customers.

The dataset contains customer demographics, device types, data usage, satisfaction ratings, revenue metrics, and churn status. All queries were executed and validated in a PostgreSQL environment.

The main objective of this project is to demonstrate strong SQL filtering logic while answering real business questions relevant to the telecommunications industry.

---

## Why This Project Is Useful

Telecommunication companies depend heavily on customer analytics to:

* Reduce customer churn
* Identify high-value users
* Optimise pricing strategies
* Improve customer experience

This project simulates real analytical scenarios such as:

* Detecting heavy data users
* Finding loyal high-spending customers
* Locating churn-prone segments
* Supporting targeted marketing strategies

It also serves as a strong portfolio example of SQL operator mastery.

---

## Dataset Information

The dataset used for this analysis is publicly available on Kaggle.

**MTN Nigeria Customer Churn Dataset (CSV format)** 

[Download Dataset Here](https://www.kaggle.com/datasets/oluwademiladeadeniyi/mtn-nigeria-customer-churn)

### Data Source

* Device types, data plans, and pricing were referenced from the **MTN Nigeria eShop**.
* Customer behaviour patterns, churn indicators, demographics, and revenue metrics were **synthetically generated** to simulate real-world telecom operations while maintaining realistic distributions.

### Total Revenue Column

The `total_revenue` column was calculated as:

> **Unit price of subscribed plan × Number of purchases**

This allows revenue-based customer segmentation and ARPU-style analysis.

---

## How to Get Started

To explore this analysis:

1. Download the dataset from Kaggle using the link above.
2. Import the CSV file into PostgreSQL or any SQL-supported database.
3. Create a table named:

```sql
mtn_customer_churn
```

4. Run the SQL queries below to reproduce the analysis.

---

## SQL Queries, Results & Data Validation

All results below were generated and validated in PostgreSQL.

---

### 🔹 Query 1: Mature Heavy Data Users

**Business Question:**
Who are the older customers that consume large volumes of data?

```sql
SELECT customer_id, full_name, age, data_usage
FROM mtn_customer_churn
WHERE age > 40
  AND data_usage > 100;
```

**Result Validation:**
Returned customers such as **Ifeanyi Park (53)** and **Zainab Morton (78)**.

**Observation:**
High data consumption (up to **179.85GB**) appears common among older broadband users, suggesting strong dependence on home or fixed internet services.

---

### 🔹 Query 2: High-Value Loyal Customers

**Business Question:**
Which customers are highly satisfied, heavy users, and big spenders?

```sql
SELECT *
FROM mtn_customer_churn
WHERE satisfaction_rate = 5
  AND data_usage > 150
  AND total_revenue > 300000;
```

**Total Rows Returned:** **7**

**Observation:**
These customers represent the highest-value segment, with revenue reaching up to **₦1,050,000**.
All had **Excellent** reviews, confirming strong loyalty and satisfaction.

---

### 🔹 Query 3: Broadband Device Segments

**Business Question:**
Which customers purchased major broadband devices?

```sql
SELECT *
FROM mtn_customer_churn
WHERE mtn_device IN ('4G Router', 'Broadband MiFi', '5G Broadband Router');
```

**Total Rows Returned:** **673**

**Observation:**
Over **70% of the dataset** uses high-speed broadband devices, indicating strong broadband adoption across the customer base.

---

### 🔹 Query 4: High-Potential Regional Filtering

**Business Question:**
Which valuable customers are outside Kogi and not low spenders?

```sql
SELECT *
FROM mtn_customer_churn
WHERE state <> 'Kogi'
  AND data_usage >= 50
  AND total_revenue >= 100000;
```

**Total Rows Returned:** **365**

**Observation:**
High-potential customers were identified across states like **Sokoto, Jigawa, and Kwara**, showing opportunity beyond traditional commercial hubs.

---

### 🔹 Query 5: Targeted Demographics (Youth, Lagos, or Churned)

**Business Question:**
Which customers fall into key marketing or retention segments?

```sql
SELECT *
FROM mtn_customer_churn
WHERE (gender = 'Female' AND age < 30)
   OR state = 'Lagos'
   OR customer_churn_status = 'Yes';
```

**Total Rows Returned:** **354**

**Observation:**
This group includes young users, urban customers, and churned users — supporting targeted youth plans, urban promotions, and win-back campaigns.

---

### 🔹 Query 6: Satisfied Moderate Data Users

**Business Question:**
Which satisfied customers still have room to increase usage?

```sql
SELECT *
FROM mtn_customer_churn
WHERE data_usage BETWEEN 50 AND 100
  AND satisfaction_rate >= 4;
```

**Total Rows Returned:** **88**

**Observation:**
These customers are stable but underutilising high-capacity plans — ideal for upselling higher data bundles.

---

### 🔹 Query 7: Active or Senior Customers

**Business Question:**
Which customers show continued engagement or long-term value?

```sql
SELECT *
FROM mtn_customer_churn
WHERE customer_review <> 'Poor'
   OR customer_churn_status <> 'Yes'
   OR age > 60;
```

**Total Rows Returned:** **935**

**Observation:**
Most customers remain active or satisfied, indicating churn is concentrated in specific behavioral segments rather than system-wide dissatisfaction.

---

### 🔹 Query 8: Low Revenue Risk Outside Abuja

**Business Question:**
Who are low-usage or low-spend customers outside FCT?

```sql
SELECT *
FROM mtn_customer_churn
WHERE (data_usage < 50 OR total_revenue < 50000)
  AND state <> 'Abuja (FCT)';
```

**Total Rows Returned:** **480**

**Observation:**
This segment represents customers most vulnerable to churn and best suited for promotional incentives and network engagement programs.

---

## Key Findings

* High data usage correlates strongly with broadband device ownership.
* Only a small group of customers generate very high revenue.
* Churn risk is higher among low-usage and low-spend customers.
* Broadband penetration is strong across many states, not only Lagos or Abuja.
* Moderately satisfied users represent strong upsell opportunities.

---

## Actionable Recommendations

* **Introduce loyalty rewards** for high-revenue customers to reduce churn risk.
* **Promote upgrade bundles** to moderate data users with high satisfaction.
* **Deploy retention campaigns** for low-spend customers outside major cities.
* **Strengthen broadband expansion** given strong router and MiFi adoption.
* **Develop youth-focused data plans** for younger demographic segments.

---

## Reflection

This project strengthened my SQL proficiency, particularly in:

* Combining multiple logical operators
* Writing business-focused filters
* Structuring readable analytical queries
* Interpreting query outputs beyond technical results

It also reinforced how SQL directly supports customer intelligence and revenue optimisation strategies in subscription-based industries.

---

## Author & Maintenance

**Adeniyi Oluwademilade Adedamola**
Junior Data Analyst Intern — Vephla University
Focus: SQL • Power BI • Excel • Customer Analytics

This repository is maintained as part of my professional data analytics portfolio.

---

## Related Links

* [Kaggle Dataset](https://www.kaggle.com/datasets/oluwademiladeadeniyi/mtn-nigeria-customer-churn)

* [Power BI Intelligence Report](https://github.com/Demibolt007/MTN-Nigeria-Customer-Churn-Intelligence-Report-Q1-2025)

