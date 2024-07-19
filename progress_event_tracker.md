WIP (Open Orders at Week End) = 
VAR EndDatePerVisual = MAX(DimDate[Date])
VAR StartDatePerVisual = Min(DimDate[Date])
VAR RESULT = 
CALCULATE(
    COUNT(vMarathonSRO[sro_num]),
    vMarathonSRO[start_date] <= EndDatePerVisual,
    vMarathonSRO[start_date] > StartDatePerVisual
    ||
    ISBLANK(vMarathonSRO[end_date]),
    REMOVEFILTERS(DimDate[Date])
)
RETURN
RESULT
# Needs work as it is not pulling the data correctly for Open orders per week.