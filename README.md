# Power BI for Wealth Management: Companion Dataset

The practice dataset for the ebook **From Spreadsheets to Dashboards: Power BI for Wealth Management Professionals**.

**All data in this workbook is fictional.** Every client, adviser, fund, email address and figure was generated for training purposes. Any resemblance to real people or firms is coincidental.

## Download

Download the latest version from the **[Releases](../../releases)** page, or open `Wealth_Training_Data.xlsx` in this repository and select **Download raw file**.

## What's inside

| Sheet | Rows | Columns | Used in |
| --- | --- | --- | --- |
| Clients | 508 | ClientID, ClientName, Region, Segment, AdviserID, JoinDate | Chapters 2–7 |
| Advisers | 20 | AdviserID, AdviserName, AdviserEmail, Team, Office | Chapters 3, 5, 7 |
| Holdings | ~74,000 | HoldingID, ClientID, AssetClass, Fund, Currency, Value, ValuationDate | Chapters 2–6 |
| Transactions | ~8,400 | TransactionID, ClientID, Date, Type, Amount | Chapters 2, 4, 6 |
| FXRates | 108 | Date, Currency, RateToGBP | Chapter 2 |
| Benchmark | 36 | Date, MonthlyReturn | Chapter 6 |

The data covers 36 month-ends, from October 2023 to September 2026.

### Notes

- **Holdings** has one valuation per fund per client per month-end. Value is in the fund's own currency (GBP, USD or EUR); Chapter 2 converts it to GBP using FXRates.
- **Transactions** Type is Deposit, Withdrawal or Fee. Amounts are always positive; the type gives the direction. Fees are charged quarterly.
- **Benchmark** MonthlyReturn is stored as a decimal (0.012 = 1.2%).
- **AdviserEmail** addresses use the reserved `example.com` domain, so you can test row-level security safely.

### Deliberate data-quality problems

The dataset includes some untidiness on purpose, for the Chapter 2 cleaning exercises:

- Inconsistent capitals and stray spaces in Clients[Region], for example "london" and "London "
- Eight duplicate rows in Clients
- Transactions[Date] stored as UK-format text (dd/mm/yyyy)

Do not "fix" these in the source file; fixing them in Power Query is the exercise.

## Regenerating the data

`build_dataset.py` recreates the workbook. It needs Python 3 with `pandas`, `numpy` and `openpyxl`:

```
pip install pandas numpy openpyxl
python build_dataset.py
```

The random seed is fixed, so the output is the same every time.

## Licence

This dataset is shared under the [Creative Commons Attribution 4.0 International licence (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). You may use, share and adapt it, including in your own training, as long as you credit the source.

## About

Created by Liz Nwachukwu, a BI developer and Power BI trainer. Questions or feedback: open an [issue](../../issues) or visit [github.com/LizNwachukwu](https://github.com/LizNwachukwu).
