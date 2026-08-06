# 🛒 Amazon Sales & Discount Analytics | Pandas & NumPy Exploration

## 📌 Executive Summary
This project analyzes **1,000+ Amazon product listings** to uncover pricing strategies, discount impact on customer satisfaction, and category-level review engagement. Using **Pandas** for complex data cleaning and **NumPy** for vectorized mathematical transformations, the analysis evaluates whether steep discount strategies drive better customer ratings or merely signal clearance inventory.

---

## 🛠️ Key Technical Implementations

1. **Robust Data Wrangling & Type Casting:**
   - Stripped localized currency symbols (`₹`), percentage indicators (`%`), and comma delimiters across price and volume columns.
   - Handled non-numeric string noise (e.g., `'|'` values in rating fields) using `pd.to_numeric(..., errors='coerce')`.
   - Filled any NaN value in rating and rating_count columns with the mean of the rest of column.
   - Extracted top-level hierarchical product categories from deeply nested string paths.

2. **Vectorized Feature Engineering (NumPy):**
   - **`discount_amount`**: Derived total nominal consumer savings ($\text{Actual} - \text{Discounted}$).
   - **`price_per_rating`**: Evaluated cost relative to product quality rating.
   - **`rating_tier`**: Classified products into performance brackets (`Exceptional`, `Good`, `Average`, `Low`) via fast C-compiled `np.select()` conditional mapping.

3. **Exploratory Data Analysis For Business Insights:**
   - Using Pandas aggregations and Numpy statistical methods to answer some core business questions.
   - Implemented Interquartile Range ($IQR$) bounds to isolate anomalous discount strategies ($Q_3 + 1.5 \times IQR$).

---

## 📊 Key Business Insights

- **Discounts Do Not Drive Ratings:** Correlation analysis revealed a **near-zero correlation** ($r \approx 0.02$) between discount percentage and product rating. High discounts do not compensate for subpar product quality.
- **Algorithm Bias Toward High Ratings:** Over **80% of top-performing items** fall within the `Good` (4.0–4.4) or `Exceptional` (4.5+) performance tiers, demonstrating Amazon's search algorithm prioritization of highly rated listings.
- **Category Dominance:** Electronics and Accessories dominate product volume and review engagement, maintaining consistent rating medians despite aggressive pricing cuts.

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- Pandas & NumPy

### Installation
```bash
# 1. Clone repository
git clone [https://github.com/botrosanwar/Amazon-Sales-Analysis.git](https://github.com/botrosanwar/Amazon-Sales-Analysis.git)
cd amazon-sales-analysis

# 2. Install dependencies
pip install -r requirements.txt

# 3. Launch Notebook
jupyter notebook notebooks/amazon_sales_analysis.ipynb
```