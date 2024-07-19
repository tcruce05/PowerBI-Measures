Units Ready To Be Shipped = 
CALCULATE( 
    COUNT(vMarathonSRO[sro_stat_date]),
    USERELATIONSHIP(DimDate[Date], vMarathonSRO[sro_stat_date]),
    KEEPFILTERS(vMarathonSRO[stat_code] = "SHIP HLD")
)