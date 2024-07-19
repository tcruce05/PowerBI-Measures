Units Received = 
CALCULATE(
    COUNT(vMarathonSRO[sro_num]),
    NOT(ISBLANK(vMarathonSRO[start_date])),
    DATESYTD(vMarathonSRO[start_date])
)