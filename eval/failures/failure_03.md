# Failure Analysis 3

## Document Text
```text
INVOICE from Global Suppliers
Total Due £450.00 Date 24/12/23
Various mixed assorted widgets bundle - 100 units at 4.5
```

## Expected JSON
```json
{"vendor": "Global Suppliers", "currency": "GBP", "total": 450.0, "date": "2023-12-24"}
```

## Actual Output
```json
{"vendor": "Global Suppliers", "currency": "£", "total": 450.0, "date": "24/12/23"}
```

## Analysis
1. **What went wrong**: Currency was output as a symbol rather than the 3-letter ISO code GBP. Date wasn't formatted to YYYY-MM-DD.
2. **Why it failed**: The document format for British dates wasn't heavily represented in the dataset permutations.
3. **Training Data Fix**: Inject 10 more synthetic rows covering European/UK date formats explicitly paired with the expected output.
