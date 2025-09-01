# ETL Project (etl_1)

This repository contains my practice work on ETL (Extract, Transform, Load).

## ✨ Highlights
- Robust **date parsing** with `errors='coerce'`
- Safe **numeric coercion** + NA handling
- Generic cleaner for dimensional tables
- Clear logging on success/failure per file

## 📦 Requirements
- Python 3.9+
- Packages: `pandas`, `numpy` (optional), `requests` (optional if you later fetch over HTTP)

Install:
```bash
pip install pandas numpy
git clone https://github.com/aguchhait-stack/etl_1.git
cd etl_1
jupyter notebook
# ETL Project (etl_1)

This repository contains my practice work on ETL (Extract, Transform, Load).

## ✨ Highlights
- Robust **date parsing** with \`errors='coerce'\`
- Safe **numeric coercion** + NA handling
- Generic cleaner for dimensional tables
- Clear logging on success/failure per file

## 📦 Requirements
- Python 3.9+
- Packages: \`pandas\`, \`numpy\` (optional), \`requests\` (optional if you later fetch over HTTP)

Install:
\`\`\`bash
pip install pandas numpy
\`\`\`

## 🚀 Quick Start (Clone Instructions)
Clone the repo and open the notebooks in Jupyter:

\`\`\`bash
git clone https://github.com/aguchhait-stack/etl_1.git
cd etl_1
jupyter notebook
\`\`\`

Or run Python scripts (if available):

\`\`\`bash
python etl_script.py
\`\`\`

## 🧹 Example ETL Pipeline (Python)
\`\`\`python
import os
import pandas as pd

def clean_fact_sales(df):
    df['Order Date'] = pd.to_datetime(df['Order Date'], format='%Y-%m-%d', errors='coerce')
    df['Ship Date']  = pd.to_datetime(df['Ship Date'],  format='%Y-%m-%d', errors='coerce')
    df['Returns']    = df['Returns'].replace('#N/A', 0).fillna(0)
    df['Quantity']   = pd.to_numeric(df['Quantity'], errors='coerce').fillna(0).astype(int)
    return df

def clean_generic(df):
    df[df.select_dtypes(include='object').columns] = df.select_dtypes(include='object')
    df.replace("#N/A", pd.NA, inplace=True)
    df = df.dropna(how="all")
    return df

base_url  = "<BASE_URL_TO_YOUR_CSVS>/"
csv_files = ["fact_sales.csv", "dim_customers.csv", "dim_dates.csv", "dim_locations.csv", "dim_payments.csv", "dim_products.csv"]

for file_name in csv_files:
    url = base_url + file_name
    try:
        df = pd.read_csv(url, header=0, sep=",", encoding='utf-8')
        if file_name == "fact_sales.csv":
            df = clean_fact_sales(df)
        else:
            df = clean_generic(df)
        output_dir = "/Users/arijitguchhait/Desktop/Windows 11/Shared"
        os.makedirs(output_dir, exist_ok=True)
        df.to_csv(os.path.join(output_dir, file_name), index=False)
        print(f"Saved: {file_name} to {output_dir}")
    except Exception as e:
        print(f"Failed to process: {file_name}: {e}")
\`\`\`

## 👤 Author
Arijit Guchhait
