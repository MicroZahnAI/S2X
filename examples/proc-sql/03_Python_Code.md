# Example 2: Python / Pandas Equivalent

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

# Amount Category using pandas
df['AmountCategory'] = pd.cut(df['DaysSinceInvoice'], 
                              bins=[-1, 30, 90, float('inf')], 
                              labels=['Current', '30-90', 'Old'])

# Save matching SAS target
df.to_parquet('clean_transactions.parquet')
print("✅ PROC SQL equivalent complete. Output shape:", df.shape)
print(df.head())
