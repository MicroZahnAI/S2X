# Example 1: Source-to-Target (S2T) Mapping

**Source:** `WORK.RAW_TRANSACTIONS`  
**Target:** `WORK.CLEAN_TRANSACTIONS`

| Source Library/Table       | Source Field       | Target Library/Table       | Target Field       | Source Logic                          | Target Logic                          | Notes                     |
|----------------------------|--------------------|----------------------------|--------------------|---------------------------------------|---------------------------------------|---------------------------|
| WORK.RAW_TRANSACTIONS      | CustomerName       | WORK.CLEAN_TRANSACTIONS    | CustomerName       | Direct copy                           | Direct                                | Full name retained        |
| WORK.RAW_TRANSACTIONS      | CustomerName       | WORK.CLEAN_TRANSACTIONS    | FirstName          | SCAN(CustomerName, 1)                 | Same                                  | First name extraction     |
| WORK.RAW_TRANSACTIONS      | CustomerName       | WORK.CLEAN_TRANSACTIONS    | LastName           | SCAN(CustomerName, -1)                | Same                                  | Last name extraction      |
| WORK.RAW_TRANSACTIONS      | StreetAddress      | WORK.CLEAN_TRANSACTIONS    | StreetAddress      | Direct copy                           | Direct                                | Address line 1            |
| -                          | -                  | WORK.CLEAN_TRANSACTIONS    | City               | Hard-coded enrichment                 | 'Dallas'                              | Dallas area example       |
| -                          | -                  | WORK.CLEAN_TRANSACTIONS    | State              | Hard-coded enrichment                 | 'TX'                                  | Dallas area example       |
| -                          | -                  | WORK.CLEAN_TRANSACTIONS    | Zip                | Hard-coded enrichment                 | '75201'                               | Dallas area example       |
| WORK.RAW_TRANSACTIONS      | InvoiceDate        | WORK.CLEAN_TRANSACTIONS    | InvoiceDate        | Direct copy                           | Direct                                | Date retained             |
| WORK.RAW_TRANSACTIONS      | InvoiceNum         | WORK.CLEAN_TRANSACTIONS    | InvoiceNum         | Direct copy                           | Direct                                | Invoice identifier        |
| WORK.RAW_TRANSACTIONS      | Product            | WORK.CLEAN_TRANSACTIONS    | Product            | Direct copy                           | Direct                                | Product name              |
| WORK.RAW_TRANSACTIONS      | InvoiceDate        | WORK.CLEAN_TRANSACTIONS    | DaysSinceInvoice   | INTCK('day', InvoiceDate, TODAY())    | Same                                  | Aging calculation         |
| WORK.RAW_TRANSACTIONS      | InvoiceDate        | WORK.CLEAN_TRANSACTIONS    | AmountCategory     | IF-THEN logic                         | Same                                  | Derived aging bucket      |

**Note:** All output variables from the target dataset (`clean_transactions`) are included above.
