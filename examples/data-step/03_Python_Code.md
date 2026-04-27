# Example 1: Python / Pandas Equivalent

```python
import pandas as pd
from datetime import datetime

# Load standard input dataset
df = pd.read_csv('raw_transactions.csv')

# Name Split
df['FirstName'] = df['CustomerName'].str.split().str[0]
df['LastName']  = df['CustomerName'].str.split().str[-1]

# Dallas Area Enrichment
df['City'] = 'Dallas'
df['State'] = 'TX'
df['Zip'] = '75201'

# Calculated Fields
df['DaysSinceInvoice'] = (datetime.today() - pd.to_datetime(df['InvoiceDate'])).dt.days

def get_category(days):
    if days < 30: return 'Current'
    elif days < 90: return '30-90'
    else: return 'Old'

df['AmountCategory'] = df['DaysSinceInvoice'].apply(get_category)

# Save matching SAS target
df.to_parquet('clean_transactions.parquet')
print("✅ Transformation complete. Output shape:", df.shape)
print(df.head())
