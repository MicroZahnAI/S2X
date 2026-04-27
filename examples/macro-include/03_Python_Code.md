# Example 3: Python / Pandas Equivalent (Scalable Function)

```python
import pandas as pd
from datetime import datetime

def clean_customer_data(input_file: str, output_file: str = 'clean_transactions.parquet'):
    """Reusable function that mirrors the SAS macro logic"""
    
    # Load standard input dataset
    df = pd.read_csv(input_file)
    
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
    df.to_parquet(output_file)
    print("✅ Macro-style transformation complete. Output shape:", df.shape)
    print(df.head())
    return df

# Example usage
if __name__ == "__main__":
    clean_customer_data('raw_transactions.csv')
