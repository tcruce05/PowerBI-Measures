DimDate = 
VAR _calendar =
    CALENDAR(MIN('Anduril_Project_Tracker'[Start Date - First Support Window]), TODAY())
RETURN
    ADDCOLUMNS(
        _calendar,
        "Year", YEAR( [Date] ),
        "MonthNumber", MONTH( [Date] ),
        "Month", FORMAT( [Date], "mmm" ),
        "Quarter", "QTR" & FORMAT( [Date], "Q" ),
        "MonthYearNumber", FORMAT( [Date], "yy mm" ),
        "Month Year", FORMAT( [Date], "mmm yyyy" ),
        "WeekNo", WEEKNUM([Date], 1),
        "WeekdayNo", WEEKDAY([Date],1),
        "Weekday", FORMAT([Date], "DDD"),
        "EndOfWeek", [Date] + (7 - WEEKDAY( [Date], 1))
    )