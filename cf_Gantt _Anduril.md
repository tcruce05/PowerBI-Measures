CF Gantt = 
VAR StartDate =
CALCULATE(
    MIN(Anduril_Project_Tracker[Start Date - First Support Window]),
    REMOVEFILTERS(DimDate)
)
VAR EndDate =
CALCULATE(
    MIN(Anduril_Project_Tracker[End Date]),
    REMOVEFILTERS(DimDate)
)
VAR ProjectPeriod =
    MIN(DimDate[Date]) >= StartDate
    && MIN(DimDate[Date]) <= EndDate
VAR ProjectStatus =
CALCULATE(
    MIN(Anduril_Project_Tracker[Progress]),
    REMOVEFILTERS(DimDate)
)
VAR Result =
SWITCH(
    TRUE(),
    ProjectPeriod && ProjectStatus = "Completed", 1,
    ProjectPeriod && ProjectStatus = "In Progress", 2,
    ProjectPeriod && ProjectStatus = "Canceled", 3
)
RETURN
    Result