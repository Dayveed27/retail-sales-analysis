# Nigeria Retail Sales Analysis

## Project overview
This project analyses a sample of Nigerian retail sales records using Python. It demonstrates data inspection, cleaning, feature engineering, exploratory data analysis (EDA), and introductory statistical testing.

## Objectives
- Understand the structure and quality of the retail dataset.
- Calculate gross sales, discounts, and net sales.
- Explore sales by product category, product, state, month, and sales channel.
- Summarise customer ratings and returns.
- Use statistical tests to investigate associations in the data.

## Dataset
The source file is `data/raw/nigeria_retail_sales.csv`. It contains 1,525 rows and 16 columns, covering order records from 1 January 2025 to 31 December 2025.

Fields include order date and ID, customer ID and age, gender, state, sales channel, product category/name, quantity, unit price, discount percentage, payment method, delivery days, customer rating, and return indicator.

The source data has missing values in `customer_age` (75), `payment_method` (40), and `customer_rating` (223). Missing values should be handled based on meaning: age can be median-imputed if justified, unknown payment methods can be labelled `Unknown`, and missing ratings should generally remain missing because a customer may not have submitted a rating.

## Tools
- Python
- pandas and NumPy
- Matplotlib and Seaborn
- SciPy
- Jupyter Notebook

## Methodology
1. Inspect dimensions, column names, types, summary statistics, missing values, and duplicates.
2. Standardise column names and selected category labels.
3. Parse `order_date` as a datetime value.
4. Flag implausible values for review instead of automatically deleting records.
5. Calculate:
   - `gross_sales_ngn = quantity × unit_price_ngn`
   - `discount_amount_ngn = gross_sales_ngn × discount_pct / 100`
   - `net_sales_ngn = gross_sales_ngn − discount_amount_ngn`
6. Create month and weekday fields for time-based analysis.
7. Explore sales by category, product, state, channel, and month.
8. Use a chi-square test to examine association between gender and product category, and Spearman correlation to assess the association between quantity and net sales.

## Initial descriptive findings
Using the source data and calculating discounts as percentages:
- Total calculated net sales: **₦166,241,315**
- Records: **1,525**
- Unique orders: **1,500**
- Unique customers: **548**
- Highest net sales by product category: **Electronics** (approximately ₦90,083,405 after standardising category capitalisation)
- Highest net sales by state: **Lagos** (approximately ₦41,834,240)
- Highest net sales by channel: **Website** (approximately ₦56,137,175)
- Top product by units sold: **Bluetooth Speaker** (477 units)
- Mean of observed customer ratings: approximately **3.86/5**
- Return indicator mean: approximately **4.92% of records**

These are descriptive results for this dataset, not claims about all Nigerian retail businesses. Values may change slightly if invalid records are excluded or additional cleaning decisions are made. Because there are 1,525 records but 1,500 unique order IDs, record-level counts should not automatically be described as order counts.

## Visualisations
The notebook saves these charts in `images/` when the Stage 5 chart cell is run:
- `net_sales_by_category.png`
- `top_10_products.png`
- `top_10_states.png`
- `monthly_sales_trend.png`

## Outputs
- `data/clean/nigeria_retail_sales_clean.csv`
- `data/clean/retail_sales_key_findings.csv`
- `images/` chart files

## Limitations
- This dataset may not represent the full Nigerian retail market.
- Missing customer ratings may not be random.
- Net sales are calculated from quantity, unit price, and discount percentage; taxes, shipping, and other adjustments are not represented unless present in the source data.
- Association and correlation do not establish causation.
- Statistical test assumptions and expected cell frequencies should be checked before drawing conclusions.

## How to run
1. Place the source CSV in `data/raw/nigeria_retail_sales.csv`.
2. Open `notebooks/01_cleaning.ipynb` in Jupyter.
3. Run the notebook cells from top to bottom.
4. Review the outputs, then update the findings in this README if your final cleaning choices change the results.

## GitHub checklist
Before pushing:
- Keep the original CSV unchanged.
- Confirm generated files are saved in the expected folders.
- Review `git status`.
- Do not commit tokens, passwords, or other credentials.
