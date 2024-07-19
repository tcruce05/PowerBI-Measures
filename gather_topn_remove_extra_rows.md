Failure Codes = 
VAR LatestRow = 
    TOPN(
        1, 
        fs_sro_oper_all, 
        fs_sro_oper_all[sro_num], 
        DESC
    )
RETURN
    IF(
        HASONEVALUE(fs_sro_oper_all[sro_num]),
        CONCATENATEX(
            FILTER(
                fs_sro_oper_all, 
                fs_sro_oper_all[sro_num] = MAXX(LatestRow, fs_sro_oper_all[sro_num])
            ), 
            fs_sro_oper_all[Failure Codes], 
            ""
        ),
        BLANK()
    )