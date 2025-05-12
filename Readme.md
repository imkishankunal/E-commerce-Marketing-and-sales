
# E-commerce Marketing and Sales Analysis

## Business Problem

Enhancing customer acquisition, retention, and revenue optimization through data-driven insights for an e-commerce platform.

## Data Description

- **Marketing_Spend.csv:** Daily marketing expenses (online/offline).
- **Online_Sales.csv:** Transaction-level details (product, price, quantity, coupon).
- **Discount_Coupon.csv:** Monthly discount coupons by product category.
- **CustomersData.xlsx:** Customer demographics.
- **Tax_amount.xlsx:** GST rates by product category.

## Analysis Steps by Business Question

### Q1: Months with Highest and Lowest Acquisition Rates

**Answer:** January highest, June lowest.

```python
monthly_acquisition.plot(kind='bar')
```

### Q2: Consistent Monthly Acquisition Patterns

**Answer:** December consistently high.

```python
monthly_acquisition.rolling(3).mean().plot()
```

### Q3: Strongest and Weakest Retention Periods

**Answer:** Strongest in first quarter, weakest in July.

```python
sns.heatmap(retention, annot=True)
```

### Q4: Customer Behavior during High-Retention Months

**Answer:** Increased order frequency in retention periods.

```python
high_retention_behavior.describe()
```

### Q5: Revenue from New vs Existing Customers

**Answer:** Higher revenue from existing customers.

```python
monthly_revenue.plot(kind='bar', stacked=True)
```

### Q6: Coupon Usage Impact

**Answer:** Coupons significantly increase revenue.

```python
sns.barplot(x='Coupon_Status', y='Avg_Price', data=data)
```

### Q7: Top-Performing Products

**Answer:** Identified top 5 products by sales.

```python
top_products.head(5).plot(kind='bar')
```

### Q8: Monthly Marketing Spend vs Revenue

**Answer:** Positive correlation, higher ROI in Q4.

```python
roi_data.plot(kind='line')
```

### Q9: Effectiveness of Marketing Campaigns

**Answer:** Online channels more effective.

```python
channel_effectiveness.plot(kind='bar')
```

### Q10: Customer Segmentation (RFM)

**Answer:** Premium customers generate most revenue.

```python
rfm['Segment'].value_counts().plot(kind='bar')
```

### Q11: Revenue Contribution by Segment

**Answer:** Focus on premium and gold segments.

```python
rfm.groupby('Segment')['Monetary'].sum().plot(kind='bar')
```

### Q12: Cohort-Based Retention Rates

**Answer:** Early-year cohorts retain better.

```python
cohort_pivot.plot(kind='line')
```

### Q13: Customer Lifetime Value (LTV)

**Answer:** Highest LTV in November cohorts.

```python
monthly_ltv.plot(kind='bar')
```

### Q14: Coupon vs Non-Coupon Transaction Values

**Answer:** Coupon usage increases average transaction value.

```python
ttest_ind(with_coupon, without_coupon)
```

### Q15: Demographic and Pricing Impact on Purchase Behavior

**Answer:** Significant variance by location and delivery charges.

```python
anova_location.pvalue, anova_delivery.pvalue
```

### Q16: Customer Tenure Impact on Purchase Frequency

**Answer:** Longer tenure increases frequency.

```python
tenure_freq_summary.plot(kind='bar')
```

### Q17: Delivery Charges vs Order Behavior

**Answer:** Lower charges correlate with increased orders.

```python
sns.scatterplot(x='Delivery_Charges', y='Quantity', data=data)
```

### Q18: Taxes and Delivery Charges Impact

**Answer:** Higher taxes slightly reduce order value.

```python
sns.regplot(x='GST', y='Avg_Price', data=data)
```

### Q19: Seasonal Trends by Category and Location

**Answer:** Apparel peaks in winter, lifestyle peaks in summer.

```python
seasonal_sales.pivot(index='Month', columns='Product_Category', values='Quantity').plot()
```

### Q20: Daily Sales Trends

**Answer:** Weekends have lower sales.

```python
daily_sales.plot(kind='bar')
```