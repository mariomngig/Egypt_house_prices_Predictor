<h1>🏠 Egypt House Price Prediction</h1>

<b>This project builds a robust regression model to predict house prices in Egypt using a cleaned, well-prepared dataset. We achieved ~85% R² on the test set, outperforming models from other Kaggle submissions.</b>

<h2>📁 Dataset</h2>

* Source: Egypt_Houses_Price.csv (27,361 rows, 12 columns)

* Features include:

 - Type, Bedrooms, Bathrooms, Area, Furnished, Level, Compound, Payment_Option, Delivery_Date, Delivery_Term, City

 - Target: Price (in EGP, log-transformed)

<h2>🔧 Data Cleaning & Pre‑processing</h2>

* Dropped rows with missing/null values in key columns.

* Converted string-numerics (Bedrooms, Bathrooms, Area, Price) to numeric types; removed rows with "Unknown" or single anomalous '10+' entries.

* Removed low-correlation columns: Compound, Delivery_Term, Delivery_Date.

* Standardized categorical variables:

* Normalized values in Type, Furnished, Payment_Option.

* Addressed inconsistent entries and consolidated rare categories in City, marking those with <10 samples as "other".

* Level column:

 - Converted textual levels ("Ground", "Highest", "10+") to numeric codes; dropped columns with poor-quality entries.

* Identified and removed outliers via:

 - Minimum room area (< 8 m²/bedroom).

 - Bad bathroom-to-bedroom ratios.

 - Price extremes (< 800k or > 65 M EGP) and abnormal price_per_m² using ±1 std filter within each Type.

* Added Log_Price target variable for normalization.

* One-Hot encoded the cleaned City column and dropped the original.

<h2>🔍 Exploratory Data Analysis (EDA)</h2>

* Visualized distributions of Price (log‑scale), Area, Bedrooms, Bathrooms, and Level.

* Bar plots showcased price variance across Type, Furnished, and Payment_Option.

* Scatter plots revealed positive relationships between Area, Bedrooms, and log Price.

* Log transformation produced an approximately normal target distribution.

<h2>🧠 Model Training & Tuning</h2>

* Split data:

 - Training: 80% of 16,309 samples → train/validation

 - Test: 20%

* Used XGBRegressor.

* Initial fit: Training R² ~0.894, Validation R² ~0.853 → slight overfitting.

* Tuned complexity: max_depth=16, max_leaves=16.

* Reduced overfitting: Train R² ~0.870, Val R² ~0.850

* Final Test R² ~0.847 (~84.7%)

<h2>🚀 Results & Comparison</h2>

<b>Final test accuracy (~85%) surpasses multiple other models evaluated on the dataset, including:</b>

* Random Forest (~63% R²),

* Linear Regression (~45%),

* Gradient Boosting (~65%),

* XGBoost (default) (~65%)
