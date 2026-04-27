# Example 1: DATA Step

```sas
/* ================================================================
   STANDARD INPUT DATASET (used across all 3 examples)
   ================================================================ */
data work.raw_transactions;
  input CustomerName $40. StreetAddress $50. InvoiceDate :date9. InvoiceNum $10. Product $30.;
  format InvoiceDate date9.;
datalines;
John Smith               123 Main St          15APR2026  INV-784512   Widget Pro
Maria Garcia             456 Oak Ave          22APR2026  INV-784513   Premium Service
Robert Chen              789 Pine Rd          28APR2026  INV-784514   Basic Plan
;
run;

/* ================================================================
   DATA SET TRANSFORMATION LOGIC (DATA Step)
   ================================================================ */
data work.clean_transactions;
  set work.raw_transactions;
  
  /* Name Split */
  FirstName = scan(CustomerName, 1);
  LastName  = scan(CustomerName, -1);
  
  /* Dallas Area Enrichment */
  City = 'Dallas';
  State = 'TX';
  Zip = '75201';
  
  /* Calculated Fields */
  DaysSinceInvoice = intck('day', InvoiceDate, today());
  if DaysSinceInvoice < 30 then AmountCategory = 'Current';
  else if DaysSinceInvoice < 90 then AmountCategory = '30-90';
  else AmountCategory = 'Old';
run;
