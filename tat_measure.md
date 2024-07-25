TAT Groupings = 
IF(
  'Bell Canada SRO Data'[days_in_house] > 90,
  "91+",
  IF('Bell Canada SRO Data'[days_in_house] > 45,
  "46-90",
  "0-45"
  )
)
