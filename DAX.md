5 Year Avg = [Total Sum] / 5


Customers FY22 = 
CALCULATE(
  DISTINCTCOUNT('Grain Receipt Summary'[Account Name]),
  'Grain Receipt Summary'[Fiscal Year] = 2022
)


Customers FY23 = 
CALCULATE(
  DISTINCTCOUNT('Grain Receipt Summary'[Account Name]),
  'Grain Receipt Summary'[Fiscal Year] = 2023
)


Customers FY24 = 
CALCULATE(
  DISTINCTCOUNT('Grain Receipt Summary'[Account Name]),
  'Grain Receipt Summary'[Fiscal Year] = 2024
)


Customers FY25 = 
CALCULATE(
  DISTINCTCOUNT('Grain Receipt Summary'[Account Name]),
  'Grain Receipt Summary'[Fiscal Year] = 2025
)


Customers FY26 = 
CALCULATE(
  DISTINCTCOUNT('Grain Receipt Summary'[Account Name]),
  'Grain Receipt Summary'[Fiscal Year] = 2026
)


FilteredCustomers = 
DISTINCTCOUNT('Grain Receipt Summary'[Account Name])


FY 22 = CALCULATE(
    SUM('Grain Receipt Summary'[BU]),
    'Grain Receipt Summary'[Fiscal Year] = 2022)


FY 23 = CALCULATE(
    SUM('Grain Receipt Summary'[BU]),
    'Grain Receipt Summary'[Fiscal Year] = 2023)


FY 24 = CALCULATE(
    SUM('Grain Receipt Summary'[BU]),
    'Grain Receipt Summary'[Fiscal Year] = 2024)


FY 25 = CALCULATE(
    SUM('Grain Receipt Summary'[BU]),
    'Grain Receipt Summary'[Fiscal Year] = 2025)


FY 26 = CALCULATE(
    SUM('Grain Receipt Summary'[BU]),
    'Grain Receipt Summary'[Fiscal Year] = 2026)


Gain/Loss = ('Measures Table'[FY 26]) - ('MEasures Table'[FY 25])


