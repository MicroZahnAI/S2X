# Example 2: PROC SQL

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
   DATA SET TRANSFORMATION LOGIC (PROC SQL)
   ================================================================ */
proc sql;
  create table work.clean_transactions as
  select 
    CustomerName,
    scan(CustomerName, 1) as FirstName,
    scan(CustomerName, -1) as LastName,
    StreetAddress,
    'Dallas' as City,
    'TX' as State,
    '75201' as Zip,
    InvoiceDate,
    InvoiceNum,
    Product,
    intck('day', InvoiceDate, today()) as DaysSinceInvoice,
    case 
      when intck('day', InvoiceDate, today()) < 30 then 'Current'
      when intck('day', InvoiceDate, today()) < 90 then '30-90'
      else 'Old'
    end as AmountCategory
  from work.raw_transactions;
quit;
