WIP = 
CALCULATE(
    SUM(vcombined_wip_by_customer_and_type[quantity]),
    CROSSFILTER('Date'[Date],
    vcombined_wip_by_customer_and_type[date],Both)
    )
# Not using this measure for now - does work