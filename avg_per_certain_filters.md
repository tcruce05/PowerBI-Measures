Average_TAT_DJI = 
AVERAGEX(
    FILTER(
        'UAV_Repairs',
        'UAV_Repairs'[Repair Company] = "DJI"
    ),
    'UAV_Repairs'[TAT]
)