MaxMin =
VAR Sales = [Total Sales]
VAR MaxSalesOverall =
MAXX(
  ALLSELECTED('dimDate'[Year], dimDate[Quarter], dimDate[QuarterNo]),
  CALCULATE([Total Sales]) -- Base Measure
)
VAR MinSalesOverall =
MINX(
  ALLSELECTED('dimDate'[Year], dimDate[Quarter], dimDate[QuarterNo]),
  CALCULATE([Total Sales])
)
VAR Result =
SWITCH(
  TRUE(),
  Sales = MaxSalesOverall, "#22957e",
  Sales = MinSalesOverall, "#ff908c",
  "#7bc8fe"
)
RETURN
Result
