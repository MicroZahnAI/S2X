# Example 1: DATA Step

### Input Dataset (Standard - used across all examples)
```sas
data work.raw_transactions;
  input CustomerName $40. StreetAddress $50. InvoiceDate :date9. InvoiceNum $10. Product $30.;
  format InvoiceDate date9.;
datalines;
John Smith               123 Main St          15APR2026  INV-784512   Widget Pro
Maria Garcia             456 Oak Ave          22APR2026  INV-784513   Premium Service
Robert Chen              789 Pine Rd          28APR2026  INV-784514   Basic Plan
;
run;
