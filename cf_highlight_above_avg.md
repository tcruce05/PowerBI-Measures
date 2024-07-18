AboveAvg =
VAR Sales = [Total Sales]
VAR AvgSalesOverall =
AVERAGEX(
  ALLEXCEPT(dimDate, dimDate[Date], dimDate[Day], dimDate[DayNo], dimDate[Month], dimDate[MonthNo]),
  CALCULATE([Total Sales])
)
VAR Result =
If(
  Sales > AvgSalesOverall,
  1,
  0
)
RETURN
Result
