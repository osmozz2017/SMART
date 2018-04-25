HDD/SSD Real-Life Reliability Test
==================================

This is a project to estimate reliability of HDD/SSD drives in real-life conditions by
the analysis of SMART data collected by Linux users at https://linux-hardware.org. The
primary aim of the project is to find drives with longest "power on hours" and minimal
number of errors.

Everyone can contribute to this report by uploading probes of their computers by
the hw-probe tool: https://github.com/linuxhw/hw-probe

Total drives: 20569.

Contents
--------

1. [ About         ](#about)
2. [ HDD by Model  ](#hdd-by-model)
3. [ HDD by Family ](#hdd-by-family)
4. [ HDD by Vendor ](#hdd-by-vendor)
5. [ SSD by Model  ](#ssd-by-model)
6. [ SSD by Family ](#ssd-by-family)
7. [ SSD by Vendor ](#ssd-by-vendor)

About
-----

The structure of the reports directory is the following:

    {KIND OF DRIVE}/{VENDOR}/{MODEL PREFIX}/{MODEL}/{DRIVE ID}

    ( e.g. HDD/Seagate/ST1000/ST1000LM035-1RK172/3F1554E2F97E )

Based on SMART data we determine most reliable drive models and vendors by the
following formula:

    Rating = MAX( Power_On_Hours / ( 1 + Number_Of_Important_Errors ) ) / ( 365*24 )

    ( i.e. Rating = "Years before/between errors" )

Number_Of_Important_Errors — number of important errors that can indicate a drive failure:

* Current_Pending_Sector
* ECC_Uncorr_Error_Count
* End-to-End_Error
* Offline_Uncorrectable
* Reallocated_Event_Count
* Reallocated_Sector_Ct
* Reported_Uncorrect
* Soft_Read_Error_Rate
* Spin_Retry_Count
* Total_Pending_Sectors
* Unc_Soft_Read_Err_Rate

The list of important SMART attributes is taken from recent studies of Google [1] and
Backblaze [2]. If an attribute exceeds the value of 1000 then it's counted as '1000 +
log10(X - 999)'.

The list of tracked attributes and rating calculation method can be discussed. Please
suggest your ideas in "issues".

You can perform your own analysis of collected reports if needed.

* [1] Google, "Failure Trends in a Large Disk Drive Population" (https://research.google.com/archive/disk_failures.pdf)
* [2] Backblaze, "Hard Drive SMART Stats" (https://www.backblaze.com/blog/hard-drive-smart-stats/)

HDD by Model
------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

See complete list of tested HDD samples in the Appendix 1 (All_HDD.md).

| MFG       | Model              | Size   | Samples | Days  | Err   | Rating |
|-----------|--------------------|--------|---------|-------|-------|--------|
| Samsung   | SV1021H            | 10 GB  | 1       | 5713  | 0     | 15.65  |
| Hitachi   | HDS728040PLA320... | 40 GB  | 1       | 3516  | 0     | 9.63   |
| Samsung   | HE160HJ            | 160 GB | 1       | 2967  | 0     | 8.13   |
| WDC       | WD2500YS-01SHB0    | 251 GB | 1       | 2484  | 0     | 6.81   |
| Fujitsu   | MHV2040BH          | 40 GB  | 1       | 2224  | 0     | 6.09   |
| WDC       | WD2500AAJS-61B4A0  | 250 GB | 1       | 2168  | 0     | 5.94   |
| WDC       | WD740GD-00FLA1     | 74 GB  | 1       | 2163  | 0     | 5.93   |
| HP        | GB0250EAFYK        | 250 GB | 1       | 2025  | 0     | 5.55   |
| Hitachi   | HUA722020ALA331    | 2 TB   | 1       | 2009  | 0     | 5.51   |
| WDC       | WD2003FYPS-27Y2B0  | 2 TB   | 4       | 2277  | 1     | 5.45   |
| WDC       | WD1600AABS-61PRA0  | 160 GB | 1       | 1982  | 0     | 5.43   |
| WDC       | WD1601ABYS-01C0A0  | 164 GB | 1       | 1982  | 0     | 5.43   |
| WDC       | WD1600AAJS-00RYA0  | 160 GB | 1       | 1970  | 0     | 5.40   |
| Seagate   | ST3750641NS        | 750 GB | 1       | 1968  | 0     | 5.39   |
| WDC       | WD7500AAKS-22RBA0  | 750 GB | 1       | 1816  | 0     | 4.98   |
| WDC       | WD360GD-00FNA0     | 37 GB  | 2       | 2599  | 1     | 4.95   |
| Hitachi   | HUA721050KLA330    | 500 GB | 2       | 1774  | 0     | 4.86   |
| WDC       | WD2500KS-22MJB0    | 250 GB | 1       | 1734  | 0     | 4.75   |
| Seagate   | ST960813AS         | 60 GB  | 1       | 1729  | 0     | 4.74   |
| WDC       | WD5000ABYS-01TNA0  | 500 GB | 1       | 1707  | 0     | 4.68   |
| WDC       | WD1600JS-88MHB0    | 160 GB | 1       | 1667  | 0     | 4.57   |
| WDC       | WD3200AAJS-22RYA0  | 320 GB | 3       | 1653  | 0     | 4.53   |
| HP        | FB080C4080         | 80 GB  | 1       | 1630  | 0     | 4.47   |
| WDC       | WD3200AAVS-00ZTB0  | 320 GB | 1       | 1583  | 0     | 4.34   |
| WDC       | WD2502ABYS-01B7A0  | 251 GB | 2       | 1576  | 0     | 4.32   |
| WDC       | WD2502ABYS-23B7... | 250 GB | 2       | 1520  | 0     | 4.16   |
| WDC       | WD2000JD-00GBB0    | 200 GB | 1       | 1482  | 0     | 4.06   |
| WDC       | WD3200AAJB-00TYA0  | 320 GB | 1       | 1442  | 0     | 3.95   |
| WDC       | WD800JD-75MSA2     | 79 GB  | 1       | 1432  | 0     | 3.92   |
| Hitachi   | HDT722520DLAT80    | 200 GB | 2       | 1406  | 0     | 3.85   |
| Hitachi   | HUA723030ALA640    | 3 TB   | 1       | 1403  | 0     | 3.84   |
| WDC       | WD2500JB-22REA0    | 250 GB | 1       | 1398  | 0     | 3.83   |
| WDC       | WD2500AAJS-22RYA0  | 250 GB | 1       | 1365  | 0     | 3.74   |
| WDC       | WD10EACS-00D6B1    | 1 TB   | 2       | 1668  | 1     | 3.73   |
| WDC       | WD7500BPVT-80HXZT1 | 750 GB | 1       | 1360  | 0     | 3.73   |
| WDC       | WD3200AAJB-00WGA0  | 320 GB | 2       | 1356  | 0     | 3.72   |
| WDC       | WD4000AAJS-65TKA0  | 400 GB | 1       | 1341  | 0     | 3.68   |
| WDC       | WD1200JS-55NCB1    | 120 GB | 1       | 1322  | 0     | 3.62   |
| WDC       | WD20EADS-00S2B0    | 2 TB   | 1       | 1315  | 0     | 3.60   |
| WDC       | WD2500AAKX-08ERMA0 | 250 GB | 1       | 1306  | 0     | 3.58   |
| WDC       | WD10EACS-00D6B0    | 1 TB   | 3       | 1602  | 3     | 3.55   |
| WDC       | WD5000AAKS-07YGA0  | 500 GB | 2       | 1295  | 0     | 3.55   |
| Hitachi   | HCS5C3232SLA380    | 320 GB | 1       | 1281  | 0     | 3.51   |
| WDC       | WD4000AAKS-00A7B0  | 400 GB | 1       | 1280  | 0     | 3.51   |
| WDC       | WD15EVDS-68V9B0    | 1.5 TB | 1       | 1276  | 0     | 3.50   |
| WDC       | WD800JD-08LSA0     | 80 GB  | 8       | 1415  | 3     | 3.46   |
| WDC       | WD2500JS-00NCB1    | 250 GB | 5       | 1239  | 0     | 3.40   |
| WDC       | WD10EAVS-00D7B0    | 1 TB   | 2       | 1238  | 0     | 3.39   |
| Samsung   | SP0451N            | 40 GB  | 1       | 1237  | 0     | 3.39   |
| WDC       | WD6400AACS-00G8B0  | 640 GB | 2       | 1216  | 0     | 3.33   |
| WDC       | WD1200JD-00HBB0    | 120 GB | 5       | 1410  | 3     | 3.32   |
| Seagate   | ST3160828AS        | 159 GB | 1       | 1198  | 0     | 3.28   |
| Seagate   | ST3300631A         | 300 GB | 1       | 1185  | 0     | 3.25   |
| WDC       | WD1001FALS-40U9B0  | 1 TB   | 1       | 1175  | 0     | 3.22   |
| WDC       | WD2001FASS-00W2B0  | 2 TB   | 1       | 1171  | 0     | 3.21   |
| WDC       | WD3200AAJS-07RYA0  | 320 GB | 1       | 1168  | 0     | 3.20   |
| WDC       | WD1500AHFD-00RAR5  | 150 GB | 1       | 1164  | 0     | 3.19   |
| WDC       | WD5000AVJB-63YUA0  | 500 GB | 1       | 1163  | 0     | 3.19   |
| WDC       | WD1600JB-00REA0    | 160 GB | 7       | 1289  | 4     | 3.18   |
| WDC       | WD2503ABYX-01WERA0 | 251 GB | 1       | 1155  | 0     | 3.16   |
| WDC       | WD800JD-00HKA0     | 80 GB  | 2       | 1144  | 0     | 3.14   |
| Seagate   | ST160LM003 HN-M... | 160 GB | 1       | 1139  | 0     | 3.12   |
| WDC       | WD2500JS-00MHB0    | 250 GB | 3       | 1136  | 0     | 3.11   |
| WDC       | WD5003AZEX-00RKKA0 | 500 GB | 2       | 1135  | 0     | 3.11   |
| Hitachi   | HDT722520DLA380    | 200 GB | 3       | 1295  | 1     | 3.11   |
| WDC       | WD5001ABYS-01YNA0  | 500 GB | 1       | 1126  | 0     | 3.09   |
| Fujitsu   | MHW2060BH          | 60 GB  | 1       | 1118  | 0     | 3.06   |
| WDC       | WD3200AAJS-40VWA0  | 320 GB | 1       | 1118  | 0     | 3.06   |
| Fujitsu   | MHZ2250BH G1       | 250 GB | 1       | 1112  | 0     | 3.05   |
| WDC       | WD7500AACS-00D6B0  | 750 GB | 1       | 1107  | 0     | 3.03   |
| WDC       | WD1200JS-00SGB0    | 120 GB | 2       | 1091  | 0     | 2.99   |
| WDC       | WD1600AAJS-00M0A0  | 160 GB | 3       | 1088  | 0     | 2.98   |
| WDC       | WD7500AARX-00N0YB0 | 750 GB | 1       | 1081  | 0     | 2.96   |
| WDC       | WD6400AAKS-75A7B2  | 640 GB | 2       | 1080  | 0     | 2.96   |
| Hitachi   | HDT721075SLA380    | 750 GB | 1       | 1074  | 0     | 2.94   |
| WDC       | WD7500AYYS-01RCA0  | 750 GB | 3       | 1197  | 1     | 2.94   |
| WDC       | WD6400AACS-00D6B1  | 640 GB | 1       | 1058  | 0     | 2.90   |
| Seagate   | ST3250823AS        | 250 GB | 9       | 1243  | 28    | 2.90   |
| WDC       | WD3200AAKS-00G3A0  | 320 GB | 5       | 1057  | 0     | 2.90   |
| Seagate   | ST3400620A         | 400 GB | 3       | 1802  | 61    | 2.88   |
| WDC       | WD2500JS-00MHB1    | 250 GB | 2       | 1052  | 0     | 2.88   |
| WDC       | WD3200JD-00KLB0    | 320 GB | 1       | 1045  | 0     | 2.87   |
| WDC       | WD800BB-75FRA0     | 80 GB  | 2       | 1034  | 0     | 2.83   |
| Seagate   | ST340823A          | 40 GB  | 1       | 1034  | 0     | 2.83   |
| WDC       | WD800BB-22JHA0     | 80 GB  | 2       | 1029  | 0     | 2.82   |
| WDC       | WD800AAJS-75M0A0   | 80 GB  | 2       | 1114  | 4     | 2.81   |
| WDC       | WD1001FALS-00J7B0  | 1 TB   | 7       | 1021  | 0     | 2.80   |
| WDC       | WD400LB-00DNA0     | 40 GB  | 2       | 1103  | 2     | 2.78   |
| WDC       | WD200BB-00DEA0     | 20 GB  | 1       | 1015  | 0     | 2.78   |
| Samsung   | HD040GJ            | 40 GB  | 3       | 1344  | 41    | 2.78   |
| Hitachi   | HUA723020ALA640    | 2 TB   | 10      | 1014  | 0     | 2.78   |
| WDC       | WD1600JB-00EVA0    | 160 GB | 1       | 1012  | 0     | 2.77   |
| WDC       | WD1600AAJS-22PSA0  | 160 GB | 11      | 1032  | 1     | 2.74   |
| Hitachi   | HDT725032VLA380    | 320 GB | 7       | 1356  | 139   | 2.73   |
| Seagate   | ST3500630A         | 500 GB | 6       | 1465  | 8     | 2.72   |
| Hitachi   | HTS545032B9SA00    | 320 GB | 2       | 989   | 0     | 2.71   |
| WDC       | WD1000FYPS-01ZKB0  | 1 TB   | 1       | 989   | 0     | 2.71   |
| WDC       | WD1600BEVS-75RST0  | 160 GB | 1       | 984   | 0     | 2.70   |
| WDC       | WD400JB-00JJC0     | 40 GB  | 1       | 980   | 0     | 2.69   |
| Samsung   | HD040GJ-P          | 40 GB  | 1       | 975   | 0     | 2.67   |
| Hitachi   | HDS728040PLAT20    | 41 GB  | 4       | 1171  | 1     | 2.67   |
| WDC       | WD10EALS-002BA0    | 1 TB   | 2       | 969   | 0     | 2.66   |
| WDC       | WD2500AAKS-22VSA0  | 250 GB | 1       | 967   | 0     | 2.65   |
| WDC       | WD20NMVW-11AV3S2   | 2 TB   | 1       | 967   | 0     | 2.65   |
| WDC       | WD1500HLFS-01G6U3  | 150 GB | 1       | 963   | 0     | 2.64   |
| Hitachi   | HDT725040VLA360    | 400 GB | 2       | 962   | 0     | 2.64   |
| Seagate   | ST3250820SCE       | 250 GB | 2       | 960   | 0     | 2.63   |
| WDC       | WD2000JS-00MVB1    | 200 GB | 1       | 957   | 0     | 2.62   |
| Quantum   | FIREBALLP AS20.5   | 20 GB  | 1       | 946   | 0     | 2.59   |
| WDC       | WD2500JS-22NCB1    | 250 GB | 6       | 1085  | 1     | 2.59   |
| Hitachi   | HDS721075KLA330    | 750 GB | 6       | 1268  | 17    | 2.57   |
| Seagate   | ST250LT020-1AE14C  | 250 GB | 1       | 936   | 0     | 2.57   |
| WDC       | WD5000AAKB-00YSA0  | 500 GB | 2       | 935   | 0     | 2.56   |
| WDC       | WD800JB-00DUA3     | 80 GB  | 1       | 923   | 0     | 2.53   |
| Hitachi   | HDS5C3015ALA632    | 1.5 TB | 2       | 1186  | 160   | 2.51   |
| Seagate   | ST3300622A         | 300 GB | 1       | 912   | 0     | 2.50   |
| WDC       | WD15EARS-00J2GB0   | 1.5 TB | 1       | 905   | 0     | 2.48   |
| Seagate   | ST3400833AS        | 400 GB | 1       | 905   | 0     | 2.48   |
| WDC       | WD3200AAJB-56WGA0  | 320 GB | 2       | 904   | 0     | 2.48   |
| Seagate   | ST3300831AS        | 300 GB | 2       | 1451  | 4     | 2.48   |
| WDC       | WD400BB-71DGA0     | 40 GB  | 1       | 900   | 0     | 2.47   |
| Seagate   | ST3802110AS        | 80 GB  | 2       | 898   | 0     | 2.46   |
| WDC       | WD10EARX-32N0YB0   | 1 TB   | 1       | 897   | 0     | 2.46   |
| WDC       | WD800JD-60LSA5     | 80 GB  | 12      | 937   | 1     | 2.45   |
| Hitachi   | HDS5C3030ALA630    | 3 TB   | 1       | 891   | 0     | 2.44   |
| WDC       | WD30EZRX-00DC0B0   | 3 TB   | 6       | 888   | 0     | 2.43   |
| WDC       | WD800BB-22HEA1     | 80 GB  | 1       | 888   | 0     | 2.43   |
| WDC       | WD5000AAKS-00TMA0  | 500 GB | 3       | 888   | 0     | 2.43   |
| WDC       | WD2500AAJS-55RYA0  | 250 GB | 2       | 887   | 0     | 2.43   |
| Seagate   | ST360015A          | 60 GB  | 1       | 885   | 0     | 2.43   |
| WDC       | WD6400AAKS-00A7B2  | 640 GB | 5       | 882   | 0     | 2.42   |
| WDC       | WD2500AAJS-75VWA0  | 250 GB | 1       | 880   | 0     | 2.41   |
| WDC       | WD1600AAJS-75WAA0  | 160 GB | 2       | 880   | 0     | 2.41   |
| Seagate   | ST91000640NS 81... | 1 TB   | 1       | 878   | 0     | 2.41   |
| WDC       | WD3200BEVE-00A0HT0 | 320 GB | 2       | 877   | 0     | 2.40   |
| WDC       | WD1600JS-55NCB1    | 160 GB | 4       | 873   | 0     | 2.39   |
| Seagate   | ST360021A          | 60 GB  | 3       | 868   | 0     | 2.38   |
| WDC       | WD1600BEVS-08VAT2  | 160 GB | 5       | 957   | 1     | 2.37   |
| WDC       | WD800BB-75JHA0     | 79 GB  | 1       | 865   | 0     | 2.37   |
| WDC       | WD2500AAJS-75M0A0  | 250 GB | 1       | 862   | 0     | 2.36   |
| WDC       | WD3202ABYS-02B7A0  | 320 GB | 6       | 929   | 1     | 2.36   |
| WDC       | WD7500AAKS-00RBA0  | 750 GB | 6       | 988   | 84    | 2.36   |
| WDC       | WD740ADFD-00NLR1   | 74 GB  | 1       | 852   | 0     | 2.34   |
| WDC       | WD800AAJS-22PSA0   | 80 GB  | 4       | 852   | 0     | 2.33   |
| WDC       | WD4000KS-00MNB0    | 400 GB | 3       | 851   | 0     | 2.33   |
| WDC       | WD10EACS-00ZJB0    | 1 TB   | 2       | 851   | 0     | 2.33   |
| Hitachi   | HCS5C1050CLA382    | 500 GB | 1       | 848   | 0     | 2.33   |
| WDC       | WD7502AAEX-00Z3A0  | 750 GB | 1       | 848   | 0     | 2.32   |
| Hitachi   | HDS721016CLA382    | 160 GB | 5       | 1003  | 2     | 2.31   |
| WDC       | WD1600BB-55RDA0    | 160 GB | 2       | 841   | 0     | 2.31   |
| WDC       | WD2500JS-55NCB1    | 250 GB | 2       | 1144  | 16    | 2.30   |
| WDC       | WD800JD-75MSA3     | 80 GB  | 16      | 971   | 1     | 2.29   |
| WDC       | WD2500YS-01SHB1    | 250 GB | 6       | 999   | 1     | 2.29   |
| WDC       | WD1200JB-00EVA0    | 120 GB | 2       | 836   | 0     | 2.29   |
| Seagate   | ST3750840AS        | 750 GB | 1       | 828   | 0     | 2.27   |
| WDC       | WD800BB-00DKA0     | 80 GB  | 3       | 968   | 1     | 2.27   |
| WDC       | WD400BB-00DEA0     | 40 GB  | 1       | 825   | 0     | 2.26   |
| WDC       | WD800BD-88JMC0     | 80 GB  | 2       | 824   | 0     | 2.26   |
| WDC       | WD10EADS-00L5B1    | 1 TB   | 23      | 1264  | 4     | 2.25   |
| WDC       | WD10EALX-089BA0    | 1 TB   | 2       | 818   | 0     | 2.24   |
| WDC       | WD2500BEVE-00WZT0  | 250 GB | 2       | 817   | 0     | 2.24   |
| WDC       | WD400BB-00LNA0     | 40 GB  | 1       | 817   | 0     | 2.24   |
| Hitachi   | HDT725050VLA380    | 500 GB | 2       | 1280  | 19    | 2.23   |
| WDC       | WD5000AAKS-00YGA0  | 500 GB | 14      | 980   | 2     | 2.23   |
| WDC       | WD2500JB-00GVC0    | 250 GB | 2       | 807   | 0     | 2.21   |
| Hitachi   | HDT725050VLA360    | 500 GB | 2       | 1051  | 2     | 2.21   |
| Seagate   | ST3320620NS        | 320 GB | 2       | 1021  | 1     | 2.21   |
| WDC       | WD15EARS-00S0XB0   | 1.5 TB | 1       | 802   | 0     | 2.20   |
| WDC       | WD6400AAKS-00A7B0  | 640 GB | 7       | 1065  | 5     | 2.19   |
| WDC       | WD1600JS-75NCB3    | 160 GB | 3       | 794   | 0     | 2.18   |
| Hitachi   | HTS723232L9SA62    | 320 GB | 1       | 794   | 0     | 2.18   |
| Seagate   | ST3120213AS        | 120 GB | 1       | 789   | 0     | 2.16   |
| HGST      | HDN726060ALE610    | 6 TB   | 1       | 787   | 0     | 2.16   |
| Seagate   | ST6000DM001-1XY17Z | 6 TB   | 1       | 783   | 0     | 2.15   |
| Seagate   | ST6000VN0021-1Z... | 6 TB   | 1       | 783   | 0     | 2.15   |
| WDC       | WD6001FFWX-68Z39N0 | 6 TB   | 1       | 782   | 0     | 2.14   |
| Seagate   | ST91603110CS       | 160 GB | 1       | 781   | 0     | 2.14   |
| WDC       | WD5000AADS-56S9B0  | 500 GB | 1       | 777   | 0     | 2.13   |
| WDC       | WD2500AAJS-00VTA0  | 250 GB | 17      | 845   | 5     | 2.12   |
| WDC       | WD2500BB-00GUA0    | 250 GB | 1       | 773   | 0     | 2.12   |
| Fujitsu   | MHV2100AH          | 100 GB | 1       | 773   | 0     | 2.12   |
| WDC       | WD2500JS-60NCB2    | 250 GB | 2       | 772   | 0     | 2.12   |
| Hitachi   | HTS723225L9A362    | 250 GB | 1       | 770   | 0     | 2.11   |
| WDC       | WD1500HLFS-01G6U1  | 150 GB | 3       | 770   | 0     | 2.11   |
| WDC       | WD3200AAKS-00VYA0  | 320 GB | 5       | 821   | 1     | 2.11   |
| WDC       | WD1600AAJS-07PSA0  | 160 GB | 3       | 1618  | 9     | 2.10   |
| Hitachi   | HTS722012K9SA00    | 120 GB | 3       | 851   | 340   | 2.10   |
| WDC       | WD3200AAKX-083CA1  | 320 GB | 1       | 763   | 0     | 2.09   |
| WDC       | WD5001AALS-00L3B2  | 500 GB | 23      | 941   | 4     | 2.09   |
| WDC       | WD5000AAKS-65YGA0  | 500 GB | 6       | 762   | 0     | 2.09   |
| Samsung   | SP1644N            | 160 GB | 2       | 871   | 790   | 2.09   |
| WDC       | WD1600JS-60MHB1    | 160 GB | 4       | 759   | 0     | 2.08   |
| WDC       | WD2500JD-55HBB0    | 250 GB | 2       | 1468  | 16    | 2.07   |
| WDC       | WD7501AALS-00J7B1  | 750 GB | 7       | 1005  | 1     | 2.07   |
| WDC       | WD4000AAKS-00YGA0  | 400 GB | 4       | 993   | 1     | 2.06   |
| WDC       | WD3000JS-19PDB0    | 300 GB | 1       | 751   | 0     | 2.06   |
| WDC       | WD2500AAKS-00VSA0  | 250 GB | 16      | 854   | 1     | 2.05   |
| Seagate   | ST9750422AS        | 750 GB | 1       | 746   | 0     | 2.05   |
| Quantum   | FIREBALLP AS40.0   | 40 GB  | 1       | 744   | 0     | 2.04   |
| WDC       | WD400BB-60JKA0     | 40 GB  | 2       | 741   | 0     | 2.03   |
| Fujitsu   | MHV2060AH PL       | 52 GB  | 1       | 741   | 0     | 2.03   |
| WDC       | WD1600YS-01SHB1    | 164 GB | 5       | 739   | 0     | 2.03   |
| WDC       | WD5000AAKS-00A7B0  | 500 GB | 19      | 972   | 9     | 2.01   |
| WDC       | WD1600AAJS-60PSA0  | 160 GB | 4       | 904   | 257   | 2.01   |
| WDC       | WD5000HHTZ-04N21V0 | 500 GB | 4       | 722   | 0     | 1.98   |
| WDC       | WD800JD-00LSA0     | 80 GB  | 15      | 1035  | 15    | 1.98   |
| WDC       | WD3200BEVT-75ZCT2  | 320 GB | 2       | 720   | 0     | 1.97   |
| WDC       | WD5000AACS-00ZUB0  | 500 GB | 8       | 765   | 1     | 1.97   |
| Seagate   | ST310211A          | 10 GB  | 1       | 716   | 0     | 1.96   |
| WDC       | WD1600BB-56RDA0    | 160 GB | 2       | 715   | 0     | 1.96   |
| WDC       | WD6402AAEX-00Z3A0  | 640 GB | 3       | 715   | 0     | 1.96   |
| WDC       | WD1502FAEX-007BA0  | 1.5 TB | 5       | 816   | 35    | 1.96   |
| WDC       | WD1600JS-58NCB1    | 160 GB | 1       | 712   | 0     | 1.95   |
| WDC       | WD3200AAKS-22B3A0  | 320 GB | 1       | 712   | 0     | 1.95   |
| Samsung   | HD300LJ            | 300 GB | 6       | 1133  | 568   | 1.95   |
| WDC       | WD2000JS-22MHB0    | 200 GB | 2       | 2525  | 19    | 1.95   |
| Seagate   | ST1000VM002-9ZL162 | 1 TB   | 1       | 709   | 0     | 1.95   |
| WDC       | WD200BB-32CFC0     | 20 GB  | 1       | 709   | 0     | 1.94   |
| WDC       | WD800AAJS-22WAA0   | 80 GB  | 1       | 708   | 0     | 1.94   |
| WDC       | WD7500AALX-009BA0  | 750 GB | 5       | 707   | 0     | 1.94   |
| WDC       | WD3200AAJS-65B4A0  | 320 GB | 1       | 699   | 0     | 1.92   |
| Seagate   | ST3300620AS        | 300 GB | 1       | 692   | 0     | 1.90   |
| WDC       | WD6400AAKS-65A7B0  | 640 GB | 5       | 787   | 3     | 1.89   |
| WDC       | WD1001FALS-00Y6A0  | 1 TB   | 4       | 936   | 28    | 1.88   |
| Seagate   | ST340215AS         | 40 GB  | 1       | 686   | 0     | 1.88   |
| Hitachi   | HDS722580VLSA80    | 82 GB  | 2       | 1317  | 1007  | 1.88   |
| Fujitsu   | MHZ2080BH G2       | 80 GB  | 1       | 684   | 0     | 1.88   |
| WDC       | WD30EZRX-00MMMB0   | 3 TB   | 5       | 883   | 2     | 1.87   |
| WDC       | WD15EARS-22Z5B1    | 1.5 TB | 3       | 675   | 0     | 1.85   |
| WDC       | WD800BB-75DKA0     | 80 GB  | 1       | 672   | 0     | 1.84   |
| WDC       | WD1200JS-55MHB0    | 120 GB | 2       | 671   | 0     | 1.84   |
| Hitachi   | HDT725025VLA380    | 250 GB | 5       | 1050  | 2     | 1.83   |
| Hitachi   | HDS723015BLA642    | 1.5 TB | 5       | 795   | 4     | 1.83   |
| Seagate   | ST4000NM0033-9Z... | 4 TB   | 1       | 667   | 0     | 1.83   |
| WDC       | WD1502FYPS-01U1B1  | 1.5 TB | 1       | 667   | 0     | 1.83   |
| WDC       | WD2500KS-00MJB0    | 250 GB | 14      | 895   | 24    | 1.83   |
| WDC       | WD30EURS-63R8UY0   | 3 TB   | 2       | 664   | 0     | 1.82   |
| WDC       | WD1200JD-00FYB0    | 120 GB | 1       | 661   | 0     | 1.81   |
| WDC       | WD1600AAJS-07WAA0  | 160 GB | 3       | 1260  | 283   | 1.81   |
| WDC       | WD740ADFD-00NLR5   | 74 GB  | 1       | 659   | 0     | 1.81   |
| Seagate   | ST3400620AS        | 400 GB | 17      | 919   | 10    | 1.80   |
| WDC       | WD6401AALS-00L3B2  | 640 GB | 14      | 886   | 7     | 1.80   |
| WDC       | WD5000BPVT-75HXZT1 | 500 GB | 1       | 657   | 0     | 1.80   |
| WDC       | WD2003FYYS-02W0B0  | 2 TB   | 3       | 755   | 1     | 1.80   |
| WDC       | WD2500AAKX-22ERMA0 | 250 GB | 1       | 656   | 0     | 1.80   |
| WDC       | WD1600JS-98NCB1    | 160 GB | 1       | 655   | 0     | 1.80   |
| Hitachi   | HTS723216L9SA60    | 160 GB | 2       | 654   | 0     | 1.79   |
| WDC       | WD3200AAJS-65RYA0  | 320 GB | 2       | 652   | 0     | 1.79   |
| WDC       | WD800AAJS-00PSA0   | 80 GB  | 9       | 853   | 82    | 1.79   |
| WDC       | WD5000AAKS-00Z7B0  | 500 GB | 1       | 652   | 0     | 1.79   |
| WDC       | WD400BD-60JPA0     | 40 GB  | 1       | 651   | 0     | 1.78   |
| WDC       | WD1600AAJS-60M0A0  | 160 GB | 2       | 648   | 0     | 1.78   |
| Hitachi   | HDS722020ALA330    | 2 TB   | 9       | 1034  | 9     | 1.78   |
| Seagate   | ST980812AS         | 80 GB  | 1       | 647   | 0     | 1.77   |
| WDC       | WD5000AAKS-07TMA0  | 500 GB | 1       | 646   | 0     | 1.77   |
| Hitachi   | HDS5C1010CLA382    | 1 TB   | 6       | 646   | 0     | 1.77   |
| Toshiba   | DT01ABA050V        | 500 GB | 1       | 644   | 0     | 1.77   |
| WDC       | WD10EADS-65L5B1    | 1 TB   | 8       | 1184  | 4     | 1.77   |
| Fujitsu   | MHW2080BH PL       | 80 GB  | 2       | 644   | 0     | 1.77   |
| WDC       | WD5000AAKS-00C8A0  | 500 GB | 2       | 1045  | 93    | 1.76   |
| WDC       | WD5000AAJS-00TKA0  | 500 GB | 1       | 641   | 0     | 1.76   |
| WDC       | WD1001FALS-19J7B0  | 1 TB   | 1       | 641   | 0     | 1.76   |
| Seagate   | ST31500541AS       | 1.5 TB | 7       | 909   | 53    | 1.76   |
| WDC       | WD1001FALS-403AA0  | 1 TB   | 1       | 639   | 0     | 1.75   |
| WDC       | WD1600JS-98MHB0    | 160 GB | 1       | 638   | 0     | 1.75   |
| WDC       | WD5000AAKS-00D2B0  | 500 GB | 6       | 807   | 3     | 1.75   |
| WDC       | WD1200JS-00MHB0    | 120 GB | 11      | 684   | 1     | 1.75   |
| Seagate   | ST2000VM003-1CT164 | 2 TB   | 4       | 792   | 1     | 1.74   |
| WDC       | WD6400AAKS-65Z7B0  | 640 GB | 4       | 704   | 5     | 1.74   |
| WDC       | WD3200AAKS-22SBA0  | 320 GB | 1       | 633   | 0     | 1.73   |
| WDC       | WD1600AABS-00PRA0  | 160 GB | 1       | 630   | 0     | 1.73   |
| WDC       | WD7501AALS-00J7B0  | 750 GB | 12      | 943   | 73    | 1.73   |
| Toshiba   | MK1032GSX          | 100 GB | 3       | 628   | 0     | 1.72   |
| WDC       | WD7500BPKX-60HPJT0 | 750 GB | 1       | 627   | 0     | 1.72   |
| WDC       | WD2500AAJS-00Z0A0  | 250 GB | 1       | 626   | 0     | 1.72   |
| WDC       | WD4000BEVT-11ZAT0  | 400 GB | 1       | 626   | 0     | 1.72   |
| WDC       | WD1600AAJB-00WRA0  | 160 GB | 2       | 950   | 543   | 1.72   |
| WDC       | WD2002FYPS-02W3B0  | 2 TB   | 1       | 626   | 0     | 1.72   |
| WDC       | WD800JD-22MSA1     | 80 GB  | 8       | 625   | 0     | 1.71   |
| WDC       | WD2500AAJS-08L7A0  | 250 GB | 2       | 624   | 0     | 1.71   |
| Hitachi   | HDT722525DLA380    | 250 GB | 7       | 1308  | 3     | 1.71   |
| WDC       | WD3200AAJS-00VWA0  | 320 GB | 7       | 622   | 0     | 1.71   |
| WDC       | WD360GD-00FLC0     | 37 GB  | 1       | 622   | 0     | 1.70   |
| WDC       | WD1600AAJS-55PSA0  | 160 GB | 1       | 620   | 0     | 1.70   |
| WDC       | WD6400BEVT-00A0RT0 | 640 GB | 1       | 619   | 0     | 1.70   |
| WDC       | WD800BB-55JKA0     | 80 GB  | 3       | 852   | 2     | 1.70   |
| Hitachi   | HDS5C1032CLA382    | 320 GB | 4       | 714   | 3     | 1.69   |
| Hitachi   | HDS723020BLA642    | 2 TB   | 15      | 797   | 70    | 1.69   |
| WDC       | WD3200AAJS-65VWA0  | 320 GB | 2       | 617   | 0     | 1.69   |
| WDC       | WD800BB-00JHA0     | 80 GB  | 6       | 1044  | 5     | 1.68   |
| Seagate   | ST3320620AS        | 320 GB | 79      | 998   | 232   | 1.68   |
| Seagate   | ST3320413CS        | 320 GB | 6       | 646   | 20    | 1.68   |
| WDC       | WD20EADS-00R6B0    | 2 TB   | 4       | 802   | 2     | 1.68   |
| Samsung   | HD083GJ            | 80 GB  | 2       | 610   | 0     | 1.67   |
| WDC       | WD2500JS-22MHB0    | 250 GB | 3       | 610   | 0     | 1.67   |
| Hitachi   | HDS721075CLA332    | 750 GB | 2       | 610   | 0     | 1.67   |
| WDC       | WD2500BEKT-75PVMT0 | 250 GB | 3       | 609   | 0     | 1.67   |
| Seagate   | ST3160023A         | 160 GB | 13      | 851   | 157   | 1.67   |
| Seagate   | ST31000526SV       | 1 TB   | 3       | 769   | 343   | 1.67   |
| WDC       | WD800JD-75MSA1     | 80 GB  | 1       | 607   | 0     | 1.66   |
| Seagate   | ST3250620NS        | 250 GB | 11      | 988   | 195   | 1.66   |
| WDC       | WD1002FAEX-007BA0  | 1 TB   | 2       | 709   | 1     | 1.66   |
| Seagate   | ST32000644NS       | 2 TB   | 2       | 608   | 1     | 1.66   |
| Seagate   | ST3160812AS        | 160 GB | 26      | 923   | 406   | 1.66   |
| WDC       | WD3000JS-60PDB0    | 300 GB | 2       | 603   | 0     | 1.65   |
| Hitachi   | HTS545016B9SA02    | 160 GB | 1       | 602   | 0     | 1.65   |
| Seagate   | ST9200420AS        | 200 GB | 2       | 601   | 0     | 1.65   |
| WDC       | WD800JD-23LSA0     | 80 GB  | 1       | 1202  | 1     | 1.65   |
| WDC       | WD1600JS-23MHB0    | 160 GB | 1       | 600   | 0     | 1.64   |
| WDC       | WD30EFRX-68AX9N0   | 3 TB   | 6       | 785   | 2     | 1.64   |
| WDC       | WD3200AAKS-00L9A0  | 320 GB | 31      | 819   | 9     | 1.64   |
| Seagate   | ST3500320NS        | 500 GB | 6       | 985   | 190   | 1.64   |
| Hitachi   | HDS723020BLE640    | 2 TB   | 7       | 596   | 0     | 1.63   |
| WDC       | WD1002FAEX-00Y9A0  | 1 TB   | 23      | 684   | 32    | 1.63   |
| Hitachi   | HDS728080PLAT20    | 82 GB  | 13      | 780   | 10    | 1.63   |
| Seagate   | ST3250820AS        | 250 GB | 31      | 860   | 340   | 1.62   |
| WDC       | WD20EARX-008FB0    | 2 TB   | 2       | 591   | 0     | 1.62   |
| WDC       | WD2500BEVS-26UST0  | 250 GB | 3       | 588   | 0     | 1.61   |
| WDC       | WD1200BEVS-22RST0  | 120 GB | 2       | 587   | 0     | 1.61   |
| WDC       | WD3200AAKS-75L9A0  | 320 GB | 11      | 636   | 1     | 1.61   |
| WDC       | WD10EALS-00Z8A0    | 1 TB   | 20      | 856   | 73    | 1.60   |
| Samsung   | HD204UI            | 2 TB   | 10      | 751   | 10    | 1.60   |
| Seagate   | ST2000DL003-9VT166 | 2 TB   | 45      | 692   | 80    | 1.60   |
| WDC       | WD20EARS-55MVWB0   | 2 TB   | 1       | 584   | 0     | 1.60   |
| WDC       | WD800BB-63JKC0     | 80 GB  | 1       | 584   | 0     | 1.60   |
| WDC       | WD2500AVJS-63WDA0  | 250 GB | 2       | 582   | 0     | 1.60   |
| WDC       | WD3200AAJS-61B4A0  | 320 GB | 1       | 581   | 0     | 1.59   |
| Maxtor    | STM3320620A        | 320 GB | 2       | 579   | 0     | 1.59   |
| WDC       | WD2500BEKT-60V5T1  | 250 GB | 1       | 578   | 0     | 1.59   |
| WDC       | WD1600BEVS-22RST0  | 160 GB | 23      | 608   | 25    | 1.59   |
| Hitachi   | HDS721612PLA380    | 120 GB | 4       | 1082  | 3     | 1.58   |
| WDC       | WD1500ADFD-00NLR1  | 150 GB | 1       | 574   | 0     | 1.57   |
| Seagate   | ST3160212AS        | 160 GB | 2       | 572   | 0     | 1.57   |
| WDC       | WD15EVDS-63V9B1    | 1.5 TB | 1       | 571   | 0     | 1.57   |
| WDC       | WD10EURX-63FH1Y0   | 1 TB   | 4       | 570   | 0     | 1.56   |
| WDC       | WD5000AACS-00G8B1  | 500 GB | 8       | 842   | 4     | 1.56   |
| WDC       | WD10EADS-00M2B0    | 1 TB   | 21      | 828   | 96    | 1.56   |
| Seagate   | ST3500630AS        | 500 GB | 21      | 952   | 355   | 1.56   |
| Seagate   | ST380215AS         | 80 GB  | 13      | 979   | 860   | 1.54   |
| WDC       | WD1600AAJS-60M0A1  | 160 GB | 1       | 1125  | 1     | 1.54   |
| Hitachi   | HDS728080PLA380    | 80 GB  | 24      | 752   | 8     | 1.54   |
| Seagate   | ST3320413AS        | 320 GB | 6       | 836   | 4     | 1.53   |
| Hitachi   | HDP725040GLA360    | 400 GB | 2       | 882   | 2     | 1.53   |
| WDC       | WD2500JB-98GVA0    | 250 GB | 1       | 3354  | 5     | 1.53   |
| Fujitsu   | MHY2250BH          | 250 GB | 5       | 862   | 65    | 1.53   |
| WDC       | WD2000JS-00MHB0    | 200 GB | 7       | 769   | 20    | 1.53   |
| WDC       | WD5000BEVT-75A0RT0 | 500 GB | 2       | 557   | 0     | 1.53   |
| Samsung   | HD253GJ            | 250 GB | 7       | 764   | 17    | 1.52   |
| WDC       | WD6400AAKS-22A7B0  | 640 GB | 5       | 1024  | 6     | 1.52   |
| WDC       | WD3000JS-00PDB0    | 300 GB | 1       | 554   | 0     | 1.52   |
| Seagate   | ST32000645NS       | 2 TB   | 4       | 553   | 0     | 1.52   |
| Seagate   | ST3200826AS        | 200 GB | 8       | 910   | 5     | 1.52   |
| WDC       | WD5000AVCS-732DY1  | 500 GB | 1       | 551   | 0     | 1.51   |
| WDC       | WD3200BPVT-00HXZT0 | 320 GB | 1       | 549   | 0     | 1.51   |
| WDC       | WD1600JS-00SGB0    | 160 GB | 1       | 549   | 0     | 1.50   |
| WDC       | WD400BB-00JHC0     | 40 GB  | 4       | 872   | 24    | 1.50   |
| WDC       | WD360ADFD-00NLR1   | 37 GB  | 1       | 547   | 0     | 1.50   |
| Fujitsu   | MHW2120BH          | 120 GB | 12      | 632   | 1     | 1.50   |
| Seagate   | ST3200827A         | 200 GB | 1       | 544   | 0     | 1.49   |
| WDC       | WD1001FALS-00J7B1  | 1 TB   | 9       | 815   | 4     | 1.49   |
| WDC       | WD800JD-00LUA0     | 80 GB  | 1       | 544   | 0     | 1.49   |
| MediaMax  | WL1000GSA6472C     | 1 TB   | 1       | 543   | 0     | 1.49   |
| Hitachi   | HDT725025VLAT80    | 250 GB | 2       | 1843  | 2     | 1.49   |
| WDC       | WD3200AAJS-08L7A0  | 320 GB | 6       | 761   | 290   | 1.48   |
| WDC       | WD3000HLFS-01G6U0  | 300 GB | 1       | 540   | 0     | 1.48   |
| WDC       | WD2000JB-00REA0    | 200 GB | 3       | 837   | 1     | 1.48   |
| Fujitsu   | MHV2100BH          | 100 GB | 3       | 700   | 2     | 1.48   |
| WDC       | WD1200JS-00NCB1    | 120 GB | 1       | 539   | 0     | 1.48   |
| WDC       | WD3000HLFS-01G6U4  | 300 GB | 1       | 536   | 0     | 1.47   |
| WDC       | WD800AAJS-22L7A0   | 80 GB  | 1       | 534   | 0     | 1.46   |
| WDC       | WD7502AAEX-00Y9A0  | 750 GB | 4       | 532   | 0     | 1.46   |
| HGST      | HDN724040ALE640    | 4 TB   | 2       | 532   | 0     | 1.46   |
| WDC       | WD1600JS-22MHB0    | 160 GB | 3       | 700   | 9     | 1.46   |
| Seagate   | ST3750640NS        | 750 GB | 6       | 1275  | 524   | 1.45   |
| WDC       | WD6400AAKS-65A7B2  | 640 GB | 10      | 1030  | 49    | 1.45   |
| Seagate   | ST3320418AS        | 320 GB | 60      | 751   | 83    | 1.45   |
| WDC       | WD20EFRX-68AX9N0   | 2 TB   | 7       | 618   | 1     | 1.45   |
| WDC       | WD7500BPVT-00HXZT1 | 750 GB | 1       | 525   | 0     | 1.44   |
| Samsung   | HD103SI            | 1 TB   | 20      | 862   | 164   | 1.44   |
| Maxtor    | 4K020H1            | 20 GB  | 1       | 522   | 0     | 1.43   |
| Seagate   | ST640LM000 HM641JI | 640 GB | 1       | 521   | 0     | 1.43   |
| WDC       | WD1600AAJS-00B4A0  | 160 GB | 13      | 736   | 103   | 1.42   |
| WDC       | WD800JD-00MSA1     | 80 GB  | 5       | 701   | 15    | 1.42   |
| WDC       | WD1600AAJS-60B4A0  | 160 GB | 1       | 518   | 0     | 1.42   |
| WDC       | WD800JD-55MUA1     | 80 GB  | 6       | 602   | 2     | 1.42   |
| Samsung   | HD103UJ            | 1 TB   | 26      | 799   | 161   | 1.42   |
| WDC       | WD5000AAJS-00A8B0  | 500 GB | 2       | 516   | 0     | 1.41   |
| Seagate   | ST3160215ACE       | 160 GB | 3       | 809   | 72    | 1.41   |
| ExcelStor | J9250S             | 250 GB | 2       | 512   | 0     | 1.41   |
| WDC       | WD10EADS-00P8B0    | 1 TB   | 4       | 846   | 4     | 1.40   |
| WDC       | WD10EARS-00Z5B1    | 1 TB   | 5       | 717   | 46    | 1.40   |
| WDC       | WD1500HLFS-01MZUV0 | 150 GB | 2       | 511   | 0     | 1.40   |
| WDC       | WD10JPVT-24A1YT0   | 1 TB   | 1       | 511   | 0     | 1.40   |
| WDC       | WD5000BEVT-35A0RT0 | 500 GB | 7       | 584   | 2     | 1.40   |
| Samsung   | HD103SJ            | 1 TB   | 54      | 712   | 18    | 1.40   |
| Seagate   | ST3000VX000-1CU166 | 3 TB   | 3       | 509   | 0     | 1.40   |
| WDC       | WD3200AAJS-55B4A0  | 320 GB | 2       | 749   | 4     | 1.40   |
| WDC       | WD6400AAKS-55A7B0  | 640 GB | 1       | 507   | 0     | 1.39   |
| WDC       | WD2002FAEX-007BA0  | 2 TB   | 10      | 585   | 2     | 1.39   |
| Hitachi   | HDS5C3020ALA632    | 2 TB   | 8       | 507   | 0     | 1.39   |
| Seagate   | ST340014A          | 40 GB  | 59      | 740   | 49    | 1.39   |
| Toshiba   | MK2559GSXP         | 250 GB | 3       | 506   | 0     | 1.39   |
| WDC       | WD1600AAJS-00PSA0  | 160 GB | 19      | 833   | 73    | 1.39   |
| WDC       | WD5000AVDS-63U7B1  | 500 GB | 3       | 505   | 0     | 1.38   |
| Hitachi   | HDS721010CLA332    | 1 TB   | 68      | 770   | 77    | 1.38   |
| Toshiba   | MK2556GSYF         | 250 GB | 1       | 503   | 0     | 1.38   |
| Seagate   | ST340015A          | 40 GB  | 3       | 763   | 45    | 1.38   |
| WDC       | WD10EARS-003BB1    | 1 TB   | 6       | 730   | 14    | 1.38   |
| Seagate   | ST3320620A         | 320 GB | 19      | 662   | 6     | 1.38   |
| Seagate   | ST3250620AS        | 250 GB | 41      | 855   | 406   | 1.37   |
| WDC       | WD1600AAJS-08PSA0  | 160 GB | 6       | 700   | 15    | 1.37   |
| WDC       | WD10EARS-22Y5B1    | 1 TB   | 7       | 927   | 36    | 1.37   |
| WDC       | WD800JD-55MSA1     | 80 GB  | 2       | 497   | 0     | 1.36   |
| WDC       | WD200EB-00BHF0     | 20 GB  | 1       | 992   | 1     | 1.36   |
| WDC       | WD1200JD-00GBB0    | 120 GB | 3       | 754   | 4     | 1.36   |
| Seagate   | ST3500630NS        | 500 GB | 5       | 684   | 529   | 1.36   |
| Seagate   | ST380012ACE        | 80 GB  | 3       | 494   | 0     | 1.36   |
| WDC       | WD1600AAJS-75M0A0  | 160 GB | 1       | 494   | 0     | 1.35   |
| Fujitsu   | MPE3136AH          | 13 GB  | 1       | 494   | 0     | 1.35   |
| WDC       | WD1001FALS-00E3A0  | 1 TB   | 3       | 779   | 2     | 1.35   |
| WDC       | WD10EADX-22TDHB0   | 1 TB   | 3       | 634   | 3     | 1.35   |
| WDC       | WD1002FAEX-00Z3A0  | 1 TB   | 41      | 683   | 124   | 1.35   |
| Seagate   | ST3808110AS        | 80 GB  | 23      | 820   | 301   | 1.35   |
| WDC       | WD2500BEKT-75PVMT1 | 250 GB | 1       | 490   | 0     | 1.34   |
| Seagate   | ST1000VX000-9YW162 | 1 TB   | 3       | 487   | 0     | 1.34   |
| Fujitsu   | MHT2040AH          | 40 GB  | 1       | 484   | 0     | 1.33   |
| Seagate   | ST3160815AS        | 160 GB | 109     | 749   | 454   | 1.33   |
| WDC       | WD7500AADS-00M2B0  | 750 GB | 13      | 900   | 27    | 1.33   |
| Seagate   | ST31000524NS       | 1 TB   | 2       | 731   | 9     | 1.32   |
| Hitachi   | HDP725025GLA380    | 250 GB | 26      | 819   | 99    | 1.32   |
| Seagate   | ST3500413AS        | 500 GB | 81      | 575   | 36    | 1.32   |
| WDC       | WD4000AAKS-00TMA0  | 400 GB | 4       | 551   | 1     | 1.32   |
| WDC       | WD7500BPKT-22PK4T0 | 750 GB | 5       | 481   | 0     | 1.32   |
| Seagate   | ST9640423AS        | 640 GB | 3       | 704   | 387   | 1.32   |
| WDC       | WD5001AALS-00E3A0  | 500 GB | 7       | 480   | 0     | 1.32   |
| WDC       | WD20EARS-00MVWB0   | 2 TB   | 29      | 747   | 80    | 1.31   |
| WDC       | WD1600JS-00NCB1    | 160 GB | 12      | 567   | 3     | 1.31   |
| WDC       | WD2500AAJB-00J3A0  | 250 GB | 8       | 856   | 7     | 1.31   |
| WDC       | WD1600JS-60MHB5    | 160 GB | 1       | 478   | 0     | 1.31   |
| Seagate   | ST380819AS         | 80 GB  | 1       | 478   | 0     | 1.31   |
| WDC       | WD20EARS-00S8B1    | 2 TB   | 7       | 649   | 2     | 1.31   |
| WDC       | WD3200AAKS-61L9A0  | 320 GB | 3       | 483   | 10    | 1.31   |
| Seagate   | ST380011A          | 80 GB  | 104     | 772   | 117   | 1.31   |
| Hitachi   | HUA722050CLA330    | 500 GB | 2       | 476   | 0     | 1.31   |
| WDC       | WD7500AZEX-00ZF5A0 | 750 GB | 5       | 475   | 0     | 1.30   |
| Seagate   | ST3160212A         | 160 GB | 8       | 750   | 101   | 1.30   |
| WDC       | WD2500AAJB-00WGA0  | 250 GB | 3       | 1215  | 8     | 1.30   |
| Seagate   | ST3750525AS        | 750 GB | 9       | 595   | 1     | 1.30   |
| WDC       | WD1200JB-00GVA0    | 120 GB | 3       | 836   | 1     | 1.30   |
| Seagate   | ST3802110A         | 80 GB  | 25      | 718   | 450   | 1.30   |
| WDC       | WD3200AAJB-56R1A0  | 320 GB | 1       | 473   | 0     | 1.30   |
| WDC       | WD5000AAKS-00V0A0  | 500 GB | 3       | 556   | 2     | 1.30   |
| WDC       | WD5000LPVT-60G33T0 | 500 GB | 1       | 472   | 0     | 1.29   |
| WDC       | WD5000BPKT-60PK4T0 | 500 GB | 2       | 653   | 128   | 1.29   |
| WDC       | WD2500AAKS-00B3A0  | 250 GB | 2       | 1018  | 5     | 1.29   |
| WDC       | WD5000AAKS-75A7B2  | 500 GB | 3       | 1015  | 6     | 1.29   |
| WDC       | WD2500AAKS-00L9A0  | 250 GB | 8       | 958   | 5     | 1.29   |
| Seagate   | ST3160215A         | 160 GB | 15      | 698   | 203   | 1.28   |
| WDC       | WD2000JB-00GVA0    | 200 GB | 2       | 468   | 0     | 1.28   |
| Seagate   | ST380815AS         | 80 GB  | 83      | 678   | 247   | 1.28   |
| Seagate   | ST32000646NS       | 2 TB   | 1       | 467   | 0     | 1.28   |
| Samsung   | SV0221N            | 20 GB  | 1       | 2328  | 4     | 1.28   |
| WDC       | WD5000AAKS-75V0A0  | 500 GB | 2       | 521   | 4     | 1.27   |
| Seagate   | ST98823A           | 80 GB  | 4       | 612   | 323   | 1.27   |
| Hitachi   | HDT721064SLA380    | 640 GB | 1       | 464   | 0     | 1.27   |
| WDC       | WD2500AAJS-00V4A0  | 250 GB | 3       | 589   | 1     | 1.27   |
| Seagate   | ST380013AS         | 80 GB  | 20      | 1091  | 89    | 1.27   |
| Seagate   | ST3120026AS        | 120 GB | 20      | 1170  | 10    | 1.27   |
| Hitachi   | HDP725050GLA360    | 500 GB | 54      | 896   | 46    | 1.26   |
| Samsung   | HD105SI            | 1 TB   | 7       | 684   | 552   | 1.26   |
| WDC       | WD10EZEX-00ZF5A0   | 1 TB   | 8       | 514   | 2     | 1.26   |
| Seagate   | ST3250312AS        | 250 GB | 11      | 607   | 11    | 1.26   |
| Seagate   | ST3250624AS        | 250 GB | 11      | 762   | 119   | 1.25   |
| Hitachi   | HDS728040PLA320    | 40 GB  | 2       | 1201  | 8     | 1.25   |
| Seagate   | ST320LM000 HM321HI | 320 GB | 8       | 481   | 2     | 1.25   |
| Samsung   | HD502HJ            | 500 GB | 63      | 597   | 52    | 1.25   |
| Seagate   | ST380012A          | 80 GB  | 1       | 456   | 0     | 1.25   |
| WDC       | WD2500AABS-00SDA0  | 250 GB | 1       | 455   | 0     | 1.25   |
| Seagate   | ST3120026A         | 120 GB | 15      | 926   | 204   | 1.25   |
| WDC       | WD5000AAKS-007AA0  | 500 GB | 6       | 846   | 17    | 1.25   |
| WDC       | WD1600BEVS-07RST0  | 160 GB | 5       | 521   | 1     | 1.24   |
| Seagate   | ST1000DL002-9TT153 | 1 TB   | 17      | 898   | 492   | 1.24   |
| Samsung   | HD153WI            | 1.5 TB | 1       | 451   | 0     | 1.24   |
| WDC       | WD7500BPVT-24HXZT1 | 750 GB | 6       | 544   | 1     | 1.23   |
| Hitachi   | HDS728080PLA380... | 80 GB  | 1       | 449   | 0     | 1.23   |
| WDC       | WD5000BEKT-00KA9T0 | 500 GB | 2       | 1084  | 7     | 1.23   |
| ExcelStor | J360               | 61 GB  | 1       | 897   | 1     | 1.23   |
| Toshiba   | MK1234GAX          | 120 GB | 2       | 448   | 0     | 1.23   |
| Hitachi   | HDS721050CLA362    | 500 GB | 89      | 614   | 12    | 1.23   |
| WDC       | WD800JB-00JJA0     | 80 GB  | 2       | 873   | 8     | 1.23   |
| Hitachi   | HTS541064A9E680    | 640 GB | 3       | 447   | 0     | 1.22   |
| WDC       | WD15EARX-00ZUDB0   | 1.5 TB | 2       | 776   | 3     | 1.22   |
| WDC       | WD3200YS-01PGB0    | 320 GB | 1       | 446   | 0     | 1.22   |
| WDC       | WD1600AAJS-00Z4A0  | 160 GB | 1       | 445   | 0     | 1.22   |
| WDC       | WD740GD-00FLA2     | 74 GB  | 1       | 1330  | 2     | 1.22   |
| WDC       | WD1600BEKT-75A25T0 | 160 GB | 1       | 442   | 0     | 1.21   |
| WDC       | WD5000AAKX-221CA0  | 500 GB | 1       | 882   | 1     | 1.21   |
| WDC       | WD3200LPVX-80V0TT0 | 320 GB | 1       | 440   | 0     | 1.21   |
| Hitachi   | HTS721080G9SA00    | 80 GB  | 2       | 439   | 0     | 1.21   |
| WDC       | WD10EARX-00N0YB0   | 1 TB   | 39      | 574   | 4     | 1.20   |
| WDC       | WD15EZRX-00DC0B0   | 1.5 TB | 1       | 438   | 0     | 1.20   |
| WDC       | WD5000AADS-00M2B0  | 500 GB | 15      | 643   | 5     | 1.20   |
| Maxtor    | STM3160211AS       | 160 GB | 2       | 437   | 0     | 1.20   |
| WDC       | WD1600BEVT-00ZCT0  | 160 GB | 3       | 435   | 0     | 1.19   |
| WDC       | WD10EALX-759BA1    | 1 TB   | 3       | 553   | 1     | 1.19   |
| WDC       | WD5000AAVS-00ZTB0  | 500 GB | 3       | 433   | 0     | 1.19   |
| Seagate   | ST3160812A         | 160 GB | 22      | 661   | 420   | 1.19   |
| Hitachi   | HDT721016SLA380    | 160 GB | 9       | 612   | 7     | 1.19   |
| Seagate   | ST380817AS         | 80 GB  | 33      | 674   | 9     | 1.18   |
| WDC       | WD2500JS-60NCB1    | 250 GB | 5       | 553   | 1     | 1.18   |
| WDC       | WD7500BPKX-80HPJT0 | 750 GB | 2       | 431   | 0     | 1.18   |
| Hitachi   | HTS543216A7A384    | 160 GB | 2       | 430   | 0     | 1.18   |
| Samsung   | HD160JJ-P          | 160 GB | 5       | 1099  | 610   | 1.18   |
| Hitachi   | HTE545025B9A300    | 250 GB | 1       | 430   | 0     | 1.18   |
| WDC       | WD1200JS-00MHB1    | 120 GB | 2       | 647   | 12    | 1.18   |
| WDC       | WD2500HHTZ-04N21V0 | 250 GB | 3       | 429   | 0     | 1.18   |
| WDC       | WD2500AAKS-00VYA0  | 250 GB | 2       | 428   | 0     | 1.17   |
| Seagate   | ST500LM011 HM501II | 500 GB | 1       | 428   | 0     | 1.17   |
| WDC       | WD3200AAKS-00B3A0  | 320 GB | 27      | 662   | 41    | 1.17   |
| Toshiba   | MK4058GSX          | 400 GB | 1       | 425   | 0     | 1.16   |
| Fujitsu   | MHV2100AT PL       | 100 GB | 1       | 424   | 0     | 1.16   |
| WDC       | WD1200LB-55EDA0    | 120 GB | 1       | 423   | 0     | 1.16   |
| Seagate   | ST3200827AS        | 200 GB | 19      | 816   | 201   | 1.16   |
| Samsung   | HD501LJ            | 500 GB | 25      | 793   | 409   | 1.16   |
| WDC       | WD7500BPVT-80HXZT3 | 750 GB | 7       | 475   | 1     | 1.15   |
| Seagate   | ST3120022A         | 120 GB | 30      | 666   | 24    | 1.15   |
| WDC       | WD5000AAKS-22A7B2  | 500 GB | 3       | 939   | 6     | 1.15   |
| Toshiba   | MK6461GSY          | 640 GB | 2       | 420   | 0     | 1.15   |
| WDC       | WD7500BPKT-80PK4T0 | 750 GB | 2       | 420   | 0     | 1.15   |
| WDC       | WD2500JS-00SGB0    | 250 GB | 5       | 566   | 1     | 1.15   |
| WDC       | WD3200AAKS-00SBA0  | 320 GB | 9       | 686   | 21    | 1.15   |
| WDC       | WD5000AAKS-75A7B0  | 500 GB | 1       | 417   | 0     | 1.14   |
| WDC       | WD5000AZRX-00A8LB0 | 500 GB | 50      | 430   | 1     | 1.14   |
| Hitachi   | HTS545050KTA300    | 500 GB | 1       | 834   | 1     | 1.14   |
| WDC       | WD20EARX-00PASB0   | 2 TB   | 44      | 615   | 163   | 1.14   |
| WDC       | WD1600AAJS-00L7A0  | 160 GB | 20      | 706   | 4     | 1.14   |
| Maxtor    | STM3500630AS       | 500 GB | 1       | 416   | 0     | 1.14   |
| WDC       | WD2500AAJS-22VTA0  | 250 GB | 4       | 751   | 7     | 1.14   |
| Seagate   | ST3120814A         | 120 GB | 12      | 823   | 252   | 1.14   |
| Seagate   | ST3500411SV        | 500 GB | 2       | 694   | 37    | 1.13   |
| WDC       | WD15EARX-00PASB0   | 1.5 TB | 4       | 412   | 0     | 1.13   |
| Seagate   | ST94813AS          | 40 GB  | 2       | 412   | 0     | 1.13   |
| Seagate   | ST31000525SV       | 1 TB   | 2       | 782   | 2     | 1.13   |
| Seagate   | ST3320820AS        | 320 GB | 5       | 586   | 615   | 1.13   |
| WDC       | WD15EADS-00P8B0    | 1.5 TB | 5       | 600   | 4     | 1.13   |
| Hitachi   | HDP725032GLA360    | 320 GB | 10      | 859   | 158   | 1.13   |
| Maxtor    | 6V320F0            | 320 GB | 1       | 410   | 0     | 1.13   |
| Maxtor    | STM3160215AS       | 160 GB | 10      | 864   | 491   | 1.13   |
| Seagate   | ST1000DM005 HD1... | 1 TB   | 8       | 542   | 2     | 1.12   |
| WDC       | WD5000LPVT-16G33T0 | 500 GB | 2       | 408   | 0     | 1.12   |
| WDC       | WD7500AARS-00Y5B1  | 750 GB | 10      | 482   | 3     | 1.12   |
| WDC       | WD800EB-11DJF0     | 80 GB  | 1       | 407   | 0     | 1.12   |
| WDC       | WD5000AAKS-00V2B0  | 500 GB | 2       | 665   | 1     | 1.12   |
| WDC       | WD2500JD-00HBB0    | 250 GB | 1       | 406   | 0     | 1.11   |
| Samsung   | HM251HI            | 250 GB | 4       | 532   | 3     | 1.11   |
| WDC       | WD10EURX-63C57Y0   | 1 TB   | 1       | 405   | 0     | 1.11   |
| Hitachi   | HTS721080G9AT00    | 80 GB  | 1       | 405   | 0     | 1.11   |
| WDC       | WD10EZEX-00RKKA0   | 1 TB   | 46      | 485   | 48    | 1.11   |
| WDC       | WD2500AAKS-00V6A0  | 250 GB | 1       | 404   | 0     | 1.11   |
| WDC       | WD2500JS-60MHB5    | 250 GB | 2       | 1170  | 18    | 1.11   |
| WDC       | WD1600AAJS-00V4A0  | 160 GB | 5       | 408   | 15    | 1.11   |
| Fujitsu   | MHZ2320BH G1       | 320 GB | 5       | 572   | 5     | 1.11   |
| Fujitsu   | MHW2160BH PL       | 160 GB | 5       | 800   | 11    | 1.11   |
| Fujitsu   | MHV2080AH          | 80 GB  | 2       | 402   | 0     | 1.10   |
| Fujitsu   | MHV2080AT PL       | 80 GB  | 2       | 402   | 0     | 1.10   |
| Seagate   | ST3250318AS        | 250 GB | 67      | 674   | 124   | 1.10   |
| WDC       | WD1200BB-00GUC0    | 120 GB | 1       | 1606  | 3     | 1.10   |
| Hitachi   | HDS723030ALA640    | 3 TB   | 2       | 400   | 0     | 1.10   |
| Toshiba   | MK1031GAS          | 100 GB | 2       | 647   | 4     | 1.10   |
| WDC       | WD1600AAJS-00WAA0  | 160 GB | 6       | 431   | 3     | 1.10   |
| WDC       | WD10EADS-11P8B2    | 1 TB   | 1       | 799   | 1     | 1.10   |
| WDC       | WD10EZEX-19ZF5A0   | 1 TB   | 1       | 399   | 0     | 1.09   |
| WDC       | WD2500BEVS-08VAT2  | 250 GB | 2       | 398   | 0     | 1.09   |
| Seagate   | ST3160815A         | 160 GB | 27      | 686   | 187   | 1.09   |
| WDC       | WD2500AAKS-00YGA0  | 250 GB | 1       | 397   | 0     | 1.09   |
| WDC       | WD1600BB-22RDA0    | 160 GB | 1       | 396   | 0     | 1.09   |
| Seagate   | ST2000DM001-9YN164 | 2 TB   | 28      | 606   | 239   | 1.09   |
| Samsung   | HD642JJ            | 640 GB | 15      | 1011  | 362   | 1.09   |
| WDC       | WD3200AAKS-00L6A0  | 320 GB | 3       | 579   | 4     | 1.09   |
| WDC       | WD6400BPVT-35HXZT1 | 640 GB | 2       | 395   | 0     | 1.08   |
| WDC       | WD2001FASS-00U0B0  | 2 TB   | 1       | 1578  | 3     | 1.08   |
| Seagate   | ST3160318AS        | 160 GB | 33      | 668   | 106   | 1.08   |
| WDC       | WD15EARS-00S8B1    | 1.5 TB | 2       | 1078  | 4     | 1.08   |
| WDC       | WD1600AAJS-07M0A0  | 160 GB | 2       | 822   | 1     | 1.08   |
| WDC       | WD6400AARS-00Y5B1  | 640 GB | 11      | 672   | 6     | 1.07   |
| Seagate   | ST2000NC001-1DY164 | 2 TB   | 4       | 390   | 0     | 1.07   |
| WDC       | WD5002ABYS-01B1B0  | 500 GB | 7       | 880   | 4     | 1.07   |
| WDC       | WD6400BPVT-80HXZT3 | 640 GB | 7       | 663   | 10    | 1.07   |
| Fujitsu   | MHV2040AH          | 40 GB  | 4       | 749   | 5     | 1.07   |
| Hitachi   | HUA721010KLA330... | 1 TB   | 1       | 1947  | 4     | 1.07   |
| WDC       | WD1600AAJB-00PVA0  | 160 GB | 8       | 714   | 226   | 1.07   |
| Seagate   | ST3200820A         | 200 GB | 3       | 464   | 101   | 1.06   |
| WDC       | WD3200AAJS-00B4A0  | 320 GB | 14      | 848   | 152   | 1.06   |
| WDC       | WD5000BEKT-75KA9T0 | 500 GB | 1       | 387   | 0     | 1.06   |
| WDC       | WD5000LPVT-00FMCT0 | 500 GB | 3       | 387   | 0     | 1.06   |
| WDC       | WD10EZEX-00KUWA0   | 1 TB   | 10      | 469   | 2     | 1.06   |
| WDC       | WD3200BPVT-00JJ5T0 | 320 GB | 5       | 386   | 0     | 1.06   |
| Seagate   | ST3250820ACE       | 250 GB | 3       | 520   | 698   | 1.05   |
| WDC       | WD5000BEVT-00A03T0 | 500 GB | 3       | 384   | 0     | 1.05   |
| WDC       | WD800JD-22JNA0     | 80 GB  | 1       | 383   | 0     | 1.05   |
| WDC       | WD10EFRX-68JCSN0   | 1 TB   | 7       | 487   | 147   | 1.05   |
| Seagate   | ST3500418AS        | 500 GB | 228     | 686   | 176   | 1.05   |
| Seagate   | ST1500DM003-1CH16G | 1.5 TB | 7       | 416   | 2     | 1.05   |
| WDC       | WD7500AZEX-00RKKA0 | 750 GB | 5       | 381   | 0     | 1.04   |
| WDC       | WD2000JD-22HBB0    | 200 GB | 3       | 993   | 7     | 1.04   |
| Seagate   | ST3200820AS        | 200 GB | 18      | 717   | 590   | 1.04   |
| WDC       | WD5000AAKS-00A7B2  | 500 GB | 24      | 795   | 19    | 1.04   |
| WDC       | WD1600AAJS-60WAA0  | 160 GB | 2       | 517   | 506   | 1.04   |
| Samsung   | HD161HJ 41R0186LEN | 160 GB | 1       | 380   | 0     | 1.04   |
| Seagate   | ST340212AS         | 40 GB  | 2       | 1049  | 105   | 1.04   |
| WDC       | WD10EALX-008EA0    | 1 TB   | 3       | 379   | 0     | 1.04   |
| Maxtor    | STM380215AS        | 80 GB  | 6       | 678   | 809   | 1.04   |
| Seagate   | ST3500514NS        | 500 GB | 7       | 1213  | 128   | 1.04   |
| Seagate   | ST3160811AS        | 160 GB | 63      | 793   | 415   | 1.04   |
| WDC       | WD5000BEVT-24A0RT0 | 500 GB | 17      | 513   | 3     | 1.03   |
| Seagate   | ST3250820A         | 250 GB | 8       | 861   | 412   | 1.03   |
| WDC       | WD2000JS-00SGB0    | 200 GB | 1       | 377   | 0     | 1.03   |
| Fujitsu   | MHZ2160BH G2       | 160 GB | 18      | 512   | 347   | 1.03   |
| WDC       | WD5000AAJS-22TKA0  | 500 GB | 1       | 376   | 0     | 1.03   |
| WDC       | WD800BEVS-08RST2   | 80 GB  | 2       | 376   | 0     | 1.03   |
| WDC       | WD2500BEVS-22UST0  | 250 GB | 33      | 505   | 19    | 1.03   |
| WDC       | WD3200AAKS-00V1A0  | 320 GB | 5       | 845   | 319   | 1.03   |
| Seagate   | ST9320328CS        | 320 GB | 4       | 730   | 424   | 1.03   |
| Samsung   | HD502IJ            | 500 GB | 20      | 762   | 372   | 1.03   |
| WDC       | WD800BB-00JKA0     | 80 GB  | 1       | 374   | 0     | 1.03   |
| WDC       | WD1200BEVS-22UST0  | 120 GB | 12      | 550   | 134   | 1.03   |
| Seagate   | ST9402112A         | 40 GB  | 1       | 1117  | 2     | 1.02   |
| Maxtor    | 6V080E0            | 81 GB  | 7       | 788   | 7     | 1.02   |
| Hitachi   | HDS721616PLA380    | 160 GB | 53      | 846   | 118   | 1.02   |
| WDC       | WD6400BPVT-22HXZT3 | 640 GB | 4       | 372   | 0     | 1.02   |
| WDC       | WD1000CHTZ-04JCPV0 | 1 TB   | 1       | 371   | 0     | 1.02   |
| WDC       | WD3200AAKS-00UU3A0 | 320 GB | 7       | 609   | 17    | 1.02   |
| WDC       | WD5000AAKX-083CA1  | 500 GB | 4       | 439   | 183   | 1.02   |
| WDC       | WD1600JS-00MHB0    | 160 GB | 5       | 566   | 36    | 1.01   |
| Maxtor    | 7V300F0            | 300 GB | 1       | 738   | 1     | 1.01   |
| Hitachi   | HDS5C1050CLA382    | 500 GB | 10      | 603   | 136   | 1.01   |
| WDC       | WD10EZEX-08RKKA0   | 1 TB   | 3       | 368   | 0     | 1.01   |
| WDC       | WD2500AAKX-001CA0  | 250 GB | 19      | 441   | 75    | 1.01   |
| WDC       | WD6400AAVS-00G9B1  | 640 GB | 1       | 367   | 0     | 1.01   |
| Samsung   | HD252HJ            | 250 GB | 16      | 704   | 160   | 1.01   |
| WDC       | WD6400AAKS-22A7B2  | 640 GB | 9       | 556   | 2     | 1.01   |
| WDC       | WD5000BPVT-22HXZT3 | 500 GB | 28      | 463   | 2     | 1.00   |
| WDC       | WD3200BPVT-55JJ5T0 | 320 GB | 2       | 366   | 0     | 1.00   |
| Seagate   | ST4000VM000-1F3168 | 4 TB   | 2       | 365   | 0     | 1.00   |
| Hitachi   | HDS721680PLAT80    | 80 GB  | 5       | 810   | 4     | 1.00   |
| Hitachi   | HDS721050CLA662    | 500 GB | 6       | 491   | 172   | 1.00   |
| Hitachi   | HDT721010SLA360    | 1 TB   | 16      | 736   | 10    | 1.00   |
| WDC       | WD800JB-00JJC0     | 80 GB  | 18      | 626   | 30    | 1.00   |
| WDC       | WD5000AAKX-603CA0  | 500 GB | 8       | 450   | 127   | 1.00   |
| WDC       | WD3000HLHX-01JJPV0 | 300 GB | 2       | 385   | 2     | 1.00   |
| WDC       | WD5000BPVT-24HXZT3 | 500 GB | 12      | 424   | 1     | 1.00   |
| WDC       | WD10EARS-00MVWB0   | 1 TB   | 21      | 838   | 46    | 1.00   |
| Hitachi   | HTS723220L9A360    | 200 GB | 1       | 363   | 0     | 0.99   |
| WDC       | WD20EARS-00J99B0   | 2 TB   | 1       | 362   | 0     | 0.99   |
| WDC       | WD5000AAKS-22A7B0  | 500 GB | 10      | 922   | 6     | 0.99   |
| WDC       | WD10EZRX-00A8LB0   | 1 TB   | 28      | 361   | 0     | 0.99   |
| WDC       | WD10EALX-009BA0    | 1 TB   | 37      | 584   | 15    | 0.99   |
| WDC       | WD5000AADS-00S9B0  | 500 GB | 69      | 645   | 37    | 0.99   |
| WDC       | WD5000BPVT-80HXZT3 | 500 GB | 19      | 420   | 58    | 0.99   |
| Maxtor    | STM3160212A        | 160 GB | 2       | 817   | 1     | 0.99   |
| WDC       | WD1600JS-56MHB1    | 160 GB | 5       | 477   | 5     | 0.99   |
| Samsung   | SP1613N            | 160 GB | 1       | 1079  | 2     | 0.99   |
| WDC       | WD2500BEVT-22ZCT0  | 250 GB | 18      | 465   | 1     | 0.98   |
| Samsung   | HD401LJ            | 400 GB | 1       | 357   | 0     | 0.98   |
| WDC       | WD7500BPVT-75A1YT0 | 750 GB | 1       | 357   | 0     | 0.98   |
| Seagate   | ST3500830AS        | 500 GB | 5       | 580   | 1     | 0.98   |
| Seagate   | ST3250310NS        | 250 GB | 3       | 737   | 755   | 0.98   |
| Fujitsu   | MHW2120BJ G2       | 120 GB | 1       | 356   | 0     | 0.98   |
| Seagate   | ST3160211AS        | 160 GB | 5       | 765   | 1271  | 0.97   |
| WDC       | WD3200AAJS-00M0A0  | 320 GB | 2       | 574   | 1     | 0.97   |
| Toshiba   | MK3261GSYG         | 320 GB | 1       | 354   | 0     | 0.97   |
| WDC       | WD800BB-00JHC0     | 80 GB  | 14      | 674   | 125   | 0.97   |
| Maxtor    | STM3320820AS       | 320 GB | 9       | 724   | 118   | 0.97   |
| Hitachi   | HDS721010CLA330    | 1 TB   | 26      | 546   | 46    | 0.97   |
| WDC       | WD2500BEKT-60PVMT0 | 250 GB | 6       | 353   | 0     | 0.97   |
| WDC       | WD3200BEVT-22ZCT0  | 320 GB | 54      | 457   | 118   | 0.97   |
| WDC       | WD5000BPKX-60HPJT0 | 500 GB | 2       | 353   | 0     | 0.97   |
| Seagate   | ST380811AS         | 80 GB  | 39      | 514   | 383   | 0.97   |
| Seagate   | ST380215A          | 80 GB  | 21      | 485   | 21    | 0.96   |
| WDC       | WD10JPVT-60A1YT0   | 1 TB   | 2       | 455   | 505   | 0.96   |
| Fujitsu   | MHV2120AH          | 120 GB | 2       | 482   | 3     | 0.96   |
| WDC       | WD25EZRX-00MMMB0   | 2.5 TB | 1       | 1049  | 2     | 0.96   |
| WDC       | WD3200AAKB-00WHA0  | 320 GB | 1       | 349   | 0     | 0.96   |
| Seagate   | ST500DM002-1BC142  | 500 GB | 34      | 527   | 170   | 0.96   |
| WDC       | WD3000BLFS-08YBU0  | 300 GB | 1       | 349   | 0     | 0.96   |
| WDC       | WD6000BLHX-01V7BV0 | 600 GB | 1       | 349   | 0     | 0.96   |
| Hitachi   | HCP725032GLA380    | 320 GB | 2       | 1006  | 2     | 0.96   |
| Seagate   | ST3120827AS        | 120 GB | 31      | 715   | 13    | 0.95   |
| Toshiba   | MK6465GSXN         | 640 GB | 6       | 529   | 197   | 0.95   |
| IBM/Hi... | IC35L040AVVA07-0   | 41 GB  | 3       | 711   | 2     | 0.95   |
| WDC       | WD1600BEVS-08RST2  | 160 GB | 1       | 345   | 0     | 0.95   |
| WDC       | WD6400BPVT-16HXZT1 | 640 GB | 1       | 1037  | 2     | 0.95   |
| Seagate   | ST9160411ASG       | 160 GB | 1       | 345   | 0     | 0.95   |
| Hitachi   | HTS541610J9SA00    | 100 GB | 1       | 344   | 0     | 0.94   |
| Samsung   | HD251HJ            | 250 GB | 7       | 753   | 62    | 0.94   |
| WDC       | WD10EZEX-60ZF5A0   | 1 TB   | 31      | 389   | 51    | 0.94   |
| WDC       | WD800BB-00FRA0     | 80 GB  | 2       | 441   | 16    | 0.94   |
| WDC       | WD7500BPVT-60HXZT3 | 750 GB | 4       | 609   | 265   | 0.94   |
| WDC       | WD5000BPVT-22HXZT1 | 500 GB | 13      | 445   | 1     | 0.94   |
| WDC       | WD6400BPVT-55HXZT2 | 640 GB | 1       | 340   | 0     | 0.93   |
| WDC       | WD7500BPKT-75PK4T0 | 750 GB | 4       | 340   | 0     | 0.93   |
| WDC       | WD15EARX-22PASB0   | 1.5 TB | 1       | 340   | 0     | 0.93   |
| WDC       | WD20EARX-55PASB0   | 2 TB   | 3       | 340   | 0     | 0.93   |
| WDC       | WD10EALX-559BA0    | 1 TB   | 4       | 599   | 8     | 0.93   |
| Seagate   | ST2000NM0033-9Z... | 2 TB   | 3       | 339   | 0     | 0.93   |
| Hitachi   | HDT721032SLA360    | 320 GB | 17      | 835   | 13    | 0.93   |
| ExcelStor | J680               | 82 GB  | 1       | 1687  | 4     | 0.92   |
| IBM/Hi... | IC35L090AVV207-0   | 80 GB  | 2       | 735   | 2     | 0.92   |
| Seagate   | ST3250410AS        | 250 GB | 120     | 771   | 250   | 0.92   |
| HGST      | HUS724020ALA640    | 2 TB   | 6       | 335   | 0     | 0.92   |
| Seagate   | ST3160827AS        | 160 GB | 17      | 863   | 20    | 0.92   |
| Toshiba   | MK6034GAX          | 60 GB  | 1       | 335   | 0     | 0.92   |
| WDC       | WD10EARS-00Y5B1    | 1 TB   | 60      | 770   | 74    | 0.92   |
| Samsung   | HD322HJ            | 320 GB | 15      | 632   | 106   | 0.92   |
| WDC       | WD20EZRX-00DC0B0   | 2 TB   | 13      | 387   | 2     | 0.92   |
| Maxtor    | STM3160815AS       | 160 GB | 16      | 595   | 220   | 0.92   |
| WDC       | WD5000BHTZ-04JCPV0 | 500 GB | 1       | 334   | 0     | 0.92   |
| Samsung   | HD161GJ            | 160 GB | 13      | 607   | 165   | 0.92   |
| WDC       | WD3200BEVT-80A0RT0 | 320 GB | 27      | 452   | 6     | 0.91   |
| WDC       | WD5000BEVT-60A0RT0 | 500 GB | 1       | 667   | 1     | 0.91   |
| WDC       | WD4000FYYZ-01UL1B1 | 4 TB   | 1       | 333   | 0     | 0.91   |
| WDC       | WD10EADX-00TDHB0   | 1 TB   | 4       | 741   | 17    | 0.91   |
| Seagate   | ST320DM000-1BC14C  | 320 GB | 12      | 370   | 3     | 0.91   |
| Hitachi   | HDS721680PLA380    | 80 GB  | 33      | 650   | 166   | 0.91   |
| Fujitsu   | MJA2250BH FFS G1   | 250 GB | 2       | 332   | 0     | 0.91   |
| Hitachi   | HDS721025CLA382    | 250 GB | 10      | 401   | 3     | 0.91   |
| WDC       | WD1001FALS-00U9B0  | 1 TB   | 1       | 995   | 2     | 0.91   |
| Hitachi   | HDS721032CLA362    | 320 GB | 27      | 659   | 36    | 0.91   |
| Samsung   | HD154UI            | 1.5 TB | 23      | 742   | 321   | 0.90   |
| Fujitsu   | MHW2080BH          | 80 GB  | 3       | 565   | 6     | 0.90   |
| Seagate   | ST3250310AS        | 250 GB | 110     | 785   | 211   | 0.90   |
| Hitachi   | HTS725016A9A364    | 160 GB | 5       | 366   | 204   | 0.90   |
| WDC       | WD20EARS-07MVWB0   | 2 TB   | 1       | 329   | 0     | 0.90   |
| Hitachi   | HDT721075SLA360    | 750 GB | 1       | 328   | 0     | 0.90   |
| WDC       | WD15EARS-00MVWB0   | 1.5 TB | 28      | 795   | 365   | 0.90   |
| WDC       | WD5000AAKS-00UU3A0 | 500 GB | 38      | 610   | 34    | 0.90   |
| Seagate   | ST3000VX000-9YW166 | 3 TB   | 1       | 327   | 0     | 0.90   |
| WDC       | WD2500AAKX-083CA1  | 250 GB | 5       | 706   | 5     | 0.90   |
| WDC       | WD6401AALS-00E3A0  | 640 GB | 3       | 579   | 4     | 0.90   |
| WDC       | WD6400AAKS-40H2B0  | 640 GB | 2       | 1447  | 406   | 0.90   |
| WDC       | WD1600BEVS-26VAT0  | 160 GB | 1       | 326   | 0     | 0.89   |
| WDC       | WD5000LPLX-66ZNTT0 | 500 GB | 1       | 326   | 0     | 0.89   |
| Samsung   | HD080HJ            | 80 GB  | 69      | 788   | 361   | 0.89   |
| WDC       | WD1002FBYS-02A6B0  | 1 TB   | 3       | 531   | 3     | 0.89   |
| WDC       | WD3200AAKS-75VYA0  | 320 GB | 2       | 324   | 0     | 0.89   |
| Seagate   | ST3000DM001-1ER166 | 3 TB   | 4       | 324   | 0     | 0.89   |
| WDC       | WD5000AAKS-00E4A0  | 500 GB | 4       | 703   | 4     | 0.89   |
| Hitachi   | HDT725032VLA360    | 320 GB | 11      | 623   | 4     | 0.89   |
| Hitachi   | HDS725050KLA360    | 500 GB | 1       | 1941  | 5     | 0.89   |
| Hitachi   | HTS725050A7E630    | 500 GB | 5       | 419   | 1017  | 0.89   |
| Hitachi   | HDE721010SLA330    | 1 TB   | 1       | 323   | 0     | 0.89   |
| WDC       | WD1001FALS-00E8B0  | 1 TB   | 8       | 759   | 279   | 0.89   |
| Samsung   | HD503HI            | 500 GB | 12      | 567   | 23    | 0.88   |
| WDC       | WD2500AAKX-00U6AA0 | 250 GB | 2       | 327   | 4     | 0.88   |
| Hitachi   | HDS721050CLA660    | 500 GB | 6       | 441   | 14    | 0.88   |
| Seagate   | ST1000NC001-1DY162 | 1 TB   | 2       | 321   | 0     | 0.88   |
| WDC       | WD800BEVT-22ZCT0   | 80 GB  | 1       | 321   | 0     | 0.88   |
| Seagate   | ST32000542AS       | 2 TB   | 13      | 815   | 532   | 0.88   |
| WDC       | WD2500AAJS-08B4A0  | 250 GB | 2       | 931   | 1211  | 0.88   |
| WDC       | WD1600BEVT-22ZCT0  | 160 GB | 56      | 446   | 66    | 0.88   |
| WDC       | WD10JPVT-55A1YT0   | 1 TB   | 1       | 320   | 0     | 0.88   |
| WDC       | WD5000AZDX-00SC2B0 | 500 GB | 2       | 319   | 0     | 0.88   |
| WDC       | WD1200BEVS-75UST0  | 120 GB | 9       | 411   | 2     | 0.88   |
| WDC       | WD6400BPVT-22HXZT1 | 640 GB | 2       | 318   | 0     | 0.87   |
| WDC       | WD2500BEVT-75ZCT2  | 250 GB | 2       | 317   | 0     | 0.87   |
| WDC       | WD5003ABYX-01WERA0 | 500 GB | 6       | 556   | 3     | 0.87   |
| WDC       | WD3200AAKX-001CA0  | 320 GB | 24      | 551   | 17    | 0.87   |
| Fujitsu   | MHV2100AT          | 100 GB | 1       | 316   | 0     | 0.87   |
| Maxtor    | STM380815AS        | 80 GB  | 14      | 612   | 868   | 0.87   |
| WDC       | WD20EURX-63T0FY0   | 2 TB   | 4       | 315   | 0     | 0.87   |
| WDC       | WD800BEVS-00UST0   | 80 GB  | 1       | 315   | 0     | 0.86   |
| Toshiba   | MK8007GAH          | 80 GB  | 1       | 315   | 0     | 0.86   |
| Seagate   | ST3200822AS        | 200 GB | 11      | 734   | 194   | 0.86   |
| WDC       | WD6400BEVT-60A0RT0 | 640 GB | 2       | 382   | 18    | 0.86   |
| WDC       | WD2500BEVT-35A23T0 | 250 GB | 16      | 429   | 2     | 0.86   |
| WDC       | WD2500BEVT-00A23T0 | 250 GB | 6       | 657   | 6     | 0.86   |
| WDC       | WD2000JD-00HBB0    | 200 GB | 3       | 636   | 3     | 0.86   |
| WDC       | WD5000BPKT-00PK4T0 | 500 GB | 3       | 340   | 1     | 0.86   |
| WDC       | WD740GD-00FLA0     | 74 GB  | 1       | 2195  | 6     | 0.86   |
| WDC       | WD5000BPVT-00HXZT1 | 500 GB | 8       | 441   | 79    | 0.86   |
| WDC       | WD800BB-00FJA0     | 80 GB  | 5       | 405   | 42    | 0.86   |
| WDC       | WD800AAJS-00L7A0   | 80 GB  | 1       | 313   | 0     | 0.86   |
| Fujitsu   | MHY2200BH          | 200 GB | 11      | 615   | 53    | 0.86   |
| Toshiba   | MK6459GSXP         | 640 GB | 8       | 404   | 373   | 0.86   |
| Samsung   | HD753LJ            | 750 GB | 19      | 784   | 260   | 0.85   |
| WDC       | WD10JPVT-08A1YT1   | 1 TB   | 2       | 311   | 0     | 0.85   |
| Seagate   | ST3160021A         | 160 GB | 7       | 514   | 866   | 0.85   |
| IBM/Hi... | IC35L120AVV207-0   | 123 GB | 1       | 933   | 2     | 0.85   |
| ExcelStor | J8160S             | 160 GB | 3       | 462   | 3     | 0.85   |
| Samsung   | HN-M500MBB         | 500 GB | 22      | 398   | 3     | 0.85   |
| Seagate   | ST2000NM0011       | 2 TB   | 2       | 1218  | 7     | 0.85   |
| WDC       | WD800JD-22LSA0     | 80 GB  | 5       | 562   | 132   | 0.85   |
| WDC       | WD1200JB-00DUA3    | 120 GB | 1       | 1235  | 3     | 0.85   |
| WDC       | WD1600JS-40TGB0    | 160 GB | 1       | 308   | 0     | 0.85   |
| WDC       | WD3200AAJS-22L7A0  | 320 GB | 4       | 768   | 57    | 0.85   |
| WDC       | WD5000AAKX-001CA0  | 500 GB | 115     | 560   | 62    | 0.85   |
| Samsung   | HM641JI            | 640 GB | 11      | 394   | 93    | 0.84   |
| WDC       | WD3200BEVT-00SCST0 | 320 GB | 1       | 306   | 0     | 0.84   |
| WDC       | WD400BB-00JHA0     | 40 GB  | 1       | 1836  | 5     | 0.84   |
| WDC       | WD30EFRX-68EUZN0   | 3 TB   | 16      | 328   | 1     | 0.84   |
| Seagate   | STM3320418AS       | 320 GB | 9       | 574   | 43    | 0.84   |
| WDC       | WD5000AAJS-19A8B0  | 500 GB | 1       | 305   | 0     | 0.84   |
| WDC       | WD10JPVT-16A1YT0   | 1 TB   | 1       | 304   | 0     | 0.84   |
| Seagate   | ST250DM001 HD253GJ | 250 GB | 5       | 304   | 0     | 0.83   |
| Samsung   | HD400LJ            | 400 GB | 2       | 477   | 5     | 0.83   |
| WDC       | WD2000JS-55MHB0    | 200 GB | 1       | 303   | 0     | 0.83   |
| Seagate   | ST2000DM001-1CH164 | 2 TB   | 66      | 411   | 120   | 0.83   |
| WDC       | WD7500BPVT-22HXZT3 | 750 GB | 21      | 364   | 1     | 0.83   |
| WDC       | WD5000BPVT-08HXZT3 | 500 GB | 7       | 331   | 1     | 0.83   |
| Seagate   | ST1500LM006 HN-... | 1.5 TB | 1       | 302   | 0     | 0.83   |
| WDC       | WD3200BEKT-60PVMT0 | 320 GB | 3       | 301   | 0     | 0.83   |
| WDC       | WD3200BPVT-35ZEST0 | 320 GB | 16      | 362   | 2     | 0.82   |
| Seagate   | ST9250410AS        | 250 GB | 21      | 427   | 98    | 0.82   |
| WDC       | WD600BEAS-22KZT0   | 60 GB  | 1       | 300   | 0     | 0.82   |
| WDC       | WD5002AALX-00J37A0 | 500 GB | 7       | 522   | 3     | 0.82   |
| Seagate   | ST3250620A         | 250 GB | 11      | 534   | 58    | 0.82   |
| WDC       | WD2500BEVS-75UST0  | 250 GB | 6       | 298   | 0     | 0.82   |
| Seagate   | ST1000NM0033-9Z... | 1 TB   | 16      | 309   | 64    | 0.82   |
| Seagate   | ST1000DM003-9YN162 | 1 TB   | 67      | 490   | 263   | 0.82   |
| Seagate   | ST340016A          | 40 GB  | 19      | 640   | 36    | 0.82   |
| WDC       | WD5003AZEX-00K1GA0 | 500 GB | 15      | 364   | 72    | 0.81   |
| Fujitsu   | MHX2300BT          | 300 GB | 3       | 759   | 47    | 0.81   |
| WDC       | WD800BB-56JKC0     | 80 GB  | 2       | 450   | 4     | 0.81   |
| Toshiba   | DT01ACA300         | 3 TB   | 28      | 355   | 73    | 0.81   |
| WDC       | WD3200BEKT-08PVMT1 | 320 GB | 2       | 293   | 0     | 0.80   |
| WDC       | WD2500AAJS-07M0A0  | 250 GB | 3       | 622   | 6     | 0.80   |
| Hitachi   | HDS721050CLA360    | 500 GB | 33      | 412   | 61    | 0.80   |
| Samsung   | SV1203N            | 120 GB | 2       | 441   | 3     | 0.80   |
| Seagate   | ST1000VX000-1CU162 | 1 TB   | 18      | 312   | 56    | 0.80   |
| Seagate   | ST500DM005 HD502HJ | 500 GB | 25      | 393   | 3     | 0.80   |
| WDC       | WD2500BEKT-75A25T0 | 250 GB | 1       | 292   | 0     | 0.80   |
| WDC       | WD2500AAJS-60Z0A0  | 250 GB | 2       | 291   | 0     | 0.80   |
| WDC       | WD3200AAJS-22B4A0  | 320 GB | 4       | 1078  | 7     | 0.80   |
| Seagate   | ST31000520AS       | 1 TB   | 12      | 961   | 477   | 0.80   |
| Magnet... | MD02500-BJDW-RO    | 250 GB | 1       | 291   | 0     | 0.80   |
| Seagate   | ST2000LM003 HN-... | 2 TB   | 10      | 291   | 0     | 0.80   |
| WDC       | WD10EZEX-00ER1A0   | 1 TB   | 2       | 290   | 0     | 0.80   |
| WDC       | WD10EZRX-00DC0B0   | 1 TB   | 3       | 290   | 0     | 0.80   |
| Hitachi   | HCS5C1025CLA382    | 250 GB | 1       | 290   | 0     | 0.80   |
| Samsung   | HM321HI            | 320 GB | 50      | 427   | 45    | 0.79   |
| WDC       | WD2500BEVT-24A23T0 | 250 GB | 13      | 367   | 45    | 0.79   |
| Seagate   | ST2000VX002-1AH166 | 2 TB   | 1       | 288   | 0     | 0.79   |
| IBM/Hi... | IC35L120AVV207-1   | 123 GB | 1       | 288   | 0     | 0.79   |
| WDC       | WD3200LPVT-08G33T1 | 320 GB | 2       | 287   | 0     | 0.79   |
| WDC       | WD3000GLFS-01F8U0  | 300 GB | 1       | 287   | 0     | 0.79   |
| Maxtor    | STM380811AS        | 80 GB  | 4       | 500   | 5     | 0.79   |
| Toshiba   | MK3029GAC          | 30 GB  | 1       | 287   | 0     | 0.79   |
| WDC       | WD7500BPVX-22JC3T0 | 750 GB | 9       | 356   | 1     | 0.79   |
| WDC       | WD5000LPVT-22G33T0 | 500 GB | 12      | 314   | 97    | 0.79   |
| WDC       | WD2500AAJS-00B4A0  | 250 GB | 13      | 665   | 59    | 0.78   |
| Toshiba   | MK4025GAS          | 40 GB  | 1       | 571   | 1     | 0.78   |
| Seagate   | ST31000524AS       | 1 TB   | 116     | 525   | 234   | 0.78   |
| WDC       | WD5000LPVT-75G33T0 | 500 GB | 4       | 341   | 2     | 0.78   |
| Toshiba   | HDWA130            | 3 TB   | 1       | 285   | 0     | 0.78   |
| WDC       | WD2500BEKT-00PVMT0 | 250 GB | 1       | 284   | 0     | 0.78   |
| Seagate   | ST3160316AS        | 160 GB | 8       | 470   | 11    | 0.78   |
| WDC       | WD6402AAEX-00Y9A0  | 640 GB | 2       | 555   | 15    | 0.78   |
| Seagate   | ST320011A          | 20 GB  | 6       | 539   | 5     | 0.78   |
| WDC       | WD1600BEVS-60RST0  | 160 GB | 7       | 518   | 323   | 0.78   |
| Samsung   | HD502HI            | 500 GB | 12      | 529   | 107   | 0.78   |
| Hitachi   | HDS721032CLA662    | 320 GB | 1       | 283   | 0     | 0.78   |
| WDC       | WD5000AAKS-65A7B0  | 500 GB | 4       | 505   | 101   | 0.77   |
| WDC       | WD2003FZEX-00Z4SA0 | 2 TB   | 3       | 282   | 0     | 0.77   |
| WDC       | WD1600BEVT-75ZCT2  | 160 GB | 10      | 335   | 6     | 0.77   |
| WDC       | WD6400AACS-00G8B1  | 640 GB | 5       | 667   | 6     | 0.77   |
| WDC       | WD1600BEVT-60ZCT1  | 160 GB | 3       | 391   | 336   | 0.77   |
| Toshiba   | DT01ACA200         | 2 TB   | 50      | 291   | 41    | 0.77   |
| Seagate   | ST2000DX001-1NS164 | 2 TB   | 2       | 279   | 0     | 0.77   |
| WDC       | WD800BB-22JHC0     | 80 GB  | 8       | 452   | 47    | 0.76   |
| WDC       | WD1600JS-60NCB1    | 160 GB | 4       | 602   | 78    | 0.76   |
| Fujitsu   | MHW2100BH          | 100 GB | 1       | 279   | 0     | 0.76   |
| Samsung   | HD321KJ            | 320 GB | 40      | 692   | 287   | 0.76   |
| WDC       | WD100EB-00BHF0     | 10 GB  | 1       | 557   | 1     | 0.76   |
| WDC       | WD800AAJS-00WAA0   | 80 GB  | 3       | 279   | 4     | 0.76   |
| Hitachi   | HDP725050GLAT80    | 500 GB | 1       | 278   | 0     | 0.76   |
| WDC       | WD20EZRX-00D8PB0   | 2 TB   | 18      | 319   | 27    | 0.76   |
| Toshiba   | MK8032GSX          | 80 GB  | 6       | 425   | 214   | 0.75   |
| WDC       | WD5000BPVT-35HXZT1 | 500 GB | 3       | 275   | 0     | 0.75   |
| WDC       | WD1200BEVT-22ZCT0  | 120 GB | 1       | 274   | 0     | 0.75   |
| Fujitsu   | MJA2160BH G2       | 160 GB | 3       | 420   | 74    | 0.75   |
| Seagate   | ST3160023AS        | 160 GB | 9       | 735   | 52    | 0.75   |
| WDC       | WD3200BEKT-60V5T1  | 320 GB | 17      | 464   | 341   | 0.75   |
| WDC       | WD10EADS-22M2B0    | 1 TB   | 4       | 799   | 5     | 0.75   |
| WDC       | WD1600AAJS-00YZCA0 | 160 GB | 8       | 541   | 45    | 0.75   |
| Hitachi   | HUA721010KLA330    | 1 TB   | 2       | 272   | 0     | 0.75   |
| WDC       | WD3200BPVT-55ZEST0 | 320 GB | 2       | 316   | 2     | 0.75   |
| Seagate   | ST1000DM003-1CH162 | 1 TB   | 188     | 351   | 18    | 0.75   |
| WDC       | WD5000AAKX-08ERMA0 | 500 GB | 15      | 398   | 155   | 0.74   |
| WDC       | WD10EZEX-21M2NA0   | 1 TB   | 17      | 284   | 1     | 0.74   |
| WDC       | WD5000BPVT-00HXZT3 | 500 GB | 7       | 387   | 70    | 0.74   |
| Toshiba   | MK2035GSS          | 200 GB | 6       | 524   | 21    | 0.74   |
| Samsung   | HD250HJ            | 250 GB | 26      | 804   | 670   | 0.74   |
| WDC       | WD10JPVX-16JC3T3   | 1 TB   | 2       | 268   | 0     | 0.74   |
| WDC       | WD800BEVS-22RST0   | 80 GB  | 19      | 416   | 66    | 0.74   |
| WDC       | WD5003ABYX-01WERA1 | 500 GB | 4       | 452   | 1     | 0.74   |
| WDC       | WD5000AAKS-22V1A0  | 500 GB | 8       | 566   | 169   | 0.74   |
| WDC       | WD5000AAKX-00ERMA0 | 500 GB | 61      | 388   | 5     | 0.73   |
| WDC       | WD1200JD-22HBB0    | 120 GB | 2       | 1602  | 5     | 0.73   |
| WDC       | WD3200BPVT-22ZEST0 | 320 GB | 34      | 411   | 29    | 0.73   |
| WDC       | WD3200LPVT-00FMCT0 | 320 GB | 1       | 266   | 0     | 0.73   |
| WDC       | WD3200BEKX-75B7WT0 | 320 GB | 1       | 266   | 0     | 0.73   |
| WDC       | WD3001FAEX-00MJRA0 | 3 TB   | 1       | 265   | 0     | 0.73   |
| WDC       | WD5000AAKS-65A7B2  | 500 GB | 1       | 265   | 0     | 0.73   |
| WDC       | WD2500AAKS-61L9A0  | 250 GB | 1       | 265   | 0     | 0.73   |
| WDC       | WD2500BEKT-00A25T0 | 250 GB | 1       | 264   | 0     | 0.73   |
| Seagate   | ST3250824AS        | 250 GB | 13      | 720   | 658   | 0.73   |
| WDC       | WD2500BEKT-60A25T1 | 250 GB | 5       | 436   | 2     | 0.73   |
| WDC       | WD5000AAJS-22YFA0  | 500 GB | 4       | 805   | 528   | 0.72   |
| WDC       | WD1200BEVS-07RST0  | 120 GB | 2       | 263   | 0     | 0.72   |
| WDC       | WD3200AAJS-00L7A0  | 320 GB | 48      | 700   | 73    | 0.72   |
| Hitachi   | HTS545032B9A300    | 320 GB | 63      | 479   | 145   | 0.72   |
| Fujitsu   | MHY2120BH          | 120 GB | 11      | 457   | 423   | 0.72   |
| WDC       | WD6400BPVT-00HXZT1 | 640 GB | 2       | 260   | 0     | 0.71   |
| Hitachi   | HTS542516K9A300    | 160 GB | 6       | 789   | 220   | 0.71   |
| Seagate   | STM3500418AS       | 500 GB | 17      | 740   | 445   | 0.71   |
| Seagate   | ST91208220AS       | 120 GB | 2       | 461   | 507   | 0.71   |
| WDC       | WD800JD-00JNC0     | 80 GB  | 3       | 539   | 20    | 0.71   |
| WDC       | WD6000HLHX-01JJPV0 | 600 GB | 6       | 462   | 5     | 0.71   |
| Seagate   | ST31000528AS       | 1 TB   | 120     | 595   | 252   | 0.70   |
| Hitachi   | HDT721032SLA380    | 320 GB | 5       | 580   | 471   | 0.70   |
| WDC       | WD10EURX-56FH1Y0   | 1 TB   | 1       | 256   | 0     | 0.70   |
| WDC       | WD7500BPVT-24HXZT3 | 750 GB | 8       | 309   | 32    | 0.70   |
| WDC       | WD10EAVS-00D7B1    | 1 TB   | 3       | 552   | 3     | 0.70   |
| WDC       | WD10JPVX-08JC3T5   | 1 TB   | 4       | 254   | 0     | 0.70   |
| Fujitsu   | MHX2250BT          | 250 GB | 2       | 409   | 5     | 0.70   |
| Maxtor    | STM3320620AS       | 320 GB | 2       | 254   | 0     | 0.70   |
| Seagate   | ST3750528AS        | 750 GB | 28      | 664   | 176   | 0.70   |
| Seagate   | ST2000VX000-1CU164 | 2 TB   | 8       | 254   | 0     | 0.70   |
| WDC       | WD3200BEKT-00F3T0  | 320 GB | 2       | 253   | 0     | 0.69   |
| WDC       | WD800BEVS-07RST0   | 80 GB  | 1       | 253   | 0     | 0.69   |
| Toshiba   | MD04ACA400         | 4 TB   | 1       | 253   | 0     | 0.69   |
| WDC       | WD40PURX-64GVNY0   | 4 TB   | 1       | 253   | 0     | 0.69   |
| WDC       | WD7500AZEX-00BN5A0 | 750 GB | 1       | 252   | 0     | 0.69   |
| HP        | VB0250EAVER        | 250 GB | 2       | 252   | 0     | 0.69   |
| WDC       | WD1600JS-08NCB1    | 160 GB | 3       | 556   | 44    | 0.69   |
| Seagate   | ST3120211AS        | 120 GB | 4       | 601   | 15    | 0.69   |
| WDC       | WD3200AAKS-00V6A0  | 320 GB | 2       | 383   | 1     | 0.69   |
| Samsung   | HD163GJ            | 160 GB | 1       | 251   | 0     | 0.69   |
| Maxtor    | STM3250820AS       | 250 GB | 7       | 723   | 239   | 0.69   |
| Hitachi   | HDS721010CLA632    | 1 TB   | 1       | 251   | 0     | 0.69   |
| Maxtor    | 6V160E0            | 160 GB | 5       | 299   | 1     | 0.69   |
| Maxtor    | 6L020J1            | 20 GB  | 2       | 463   | 3     | 0.69   |
| Hitachi   | HTS547550A9E384    | 500 GB | 91      | 373   | 258   | 0.68   |
| WDC       | WD2500JB-00REA0    | 250 GB | 7       | 617   | 31    | 0.68   |
| WDC       | WD3200AAJS-60M0A0  | 320 GB | 1       | 749   | 2     | 0.68   |
| WDC       | WD20EURS-63S48Y0   | 2 TB   | 2       | 266   | 1011  | 0.68   |
| WDC       | WD3200BPVT-24JJ5T0 | 320 GB | 36      | 304   | 52    | 0.68   |
| Samsung   | HD120IJ            | 120 GB | 16      | 836   | 305   | 0.68   |
| Toshiba   | MQ01ABD075         | 750 GB | 61      | 326   | 9     | 0.68   |
| Apple     | HDD HTS545050A7... | 500 GB | 5       | 293   | 3     | 0.68   |
| Hitachi   | HTS545050B9A300    | 500 GB | 67      | 519   | 181   | 0.68   |
| WDC       | WD1003FBYZ-010FB0  | 1 TB   | 5       | 442   | 3     | 0.68   |
| Seagate   | ST3160215AS        | 160 GB | 11      | 467   | 761   | 0.68   |
| WDC       | WD3200BPVT-24ZEST0 | 320 GB | 15      | 311   | 4     | 0.68   |
| WDC       | WD2500AAKS-00UU3A0 | 250 GB | 1       | 247   | 0     | 0.68   |
| WDC       | WD5000AAKS-07A7B0  | 500 GB | 3       | 704   | 6     | 0.68   |
| WDC       | WD2000JS-00MHB1    | 200 GB | 1       | 246   | 0     | 0.68   |
| Hitachi   | HCT721016SLA380    | 160 GB | 3       | 246   | 0     | 0.67   |
| Fujitsu   | MJA2500BH FFS G1   | 500 GB | 1       | 246   | 0     | 0.67   |
| Seagate   | ST250DM000-1BD141  | 250 GB | 50      | 386   | 145   | 0.67   |
| Samsung   | HM320HJ            | 320 GB | 3       | 415   | 422   | 0.67   |
| WDC       | WD1600AAJS-22L7A0  | 160 GB | 12      | 447   | 7     | 0.67   |
| Seagate   | ST980813AS         | 80 GB  | 1       | 246   | 0     | 0.67   |
| Toshiba   | HDWA120            | 2 TB   | 1       | 245   | 0     | 0.67   |
| Hitachi   | HDT722516DLA380    | 164 GB | 7       | 764   | 81    | 0.67   |
| WDC       | WD800JB-00ETA0     | 80 GB  | 4       | 1139  | 341   | 0.67   |
| WDC       | WD7500BPVT-22A1YT0 | 750 GB | 1       | 733   | 2     | 0.67   |
| WDC       | WD1600BB-00RDA0    | 160 GB | 2       | 691   | 39    | 0.67   |
| WDC       | WD5000BEVT-11A0RT0 | 500 GB | 1       | 243   | 0     | 0.67   |
| Samsung   | SP0411N            | 40 GB  | 1       | 4382  | 17    | 0.67   |
| Maxtor    | STM3250310AS       | 250 GB | 37      | 572   | 372   | 0.67   |
| WDC       | WD2500AAKX-00ERMA0 | 250 GB | 15      | 351   | 91    | 0.67   |
| WDC       | WD1600AAJB-22WRA0  | 160 GB | 2       | 722   | 3     | 0.67   |
| WDC       | WD5000AAKS-08V0A0  | 500 GB | 4       | 465   | 5     | 0.66   |
| WDC       | WD2500AAJS-07B4A0  | 250 GB | 1       | 2180  | 8     | 0.66   |
| WDC       | WD10EALX-229BA0    | 1 TB   | 4       | 783   | 10    | 0.66   |
| WDC       | WD10EAVS-22D7B0    | 1 TB   | 1       | 2174  | 8     | 0.66   |
| Fujitsu   | MHW2080AT          | 80 GB  | 1       | 241   | 0     | 0.66   |
| WDC       | WD5000AAKX-08ANVA0 | 500 GB | 2       | 241   | 0     | 0.66   |
| Toshiba   | MK5075GSX          | 500 GB | 8       | 317   | 160   | 0.66   |
| WDC       | WD2502ABYS-18B7A0  | 250 GB | 1       | 239   | 0     | 0.66   |
| WDC       | WD1000DHTZ-04N21V0 | 1 TB   | 2       | 643   | 4     | 0.66   |
| WDC       | WD10JPVT-08A1YT2   | 1 TB   | 6       | 303   | 1     | 0.66   |
| WDC       | WD10EZEX-00UD2A0   | 1 TB   | 6       | 319   | 3     | 0.66   |
| WDC       | WD2500BEVT-22A23T0 | 250 GB | 34      | 381   | 37    | 0.66   |
| WDC       | WD3200BEVT-00A0RT0 | 320 GB | 14      | 302   | 16    | 0.65   |
| WDC       | WD6400AAKS-00H2B0  | 640 GB | 1       | 238   | 0     | 0.65   |
| Seagate   | ST9320423AS        | 320 GB | 24      | 371   | 253   | 0.65   |
| Seagate   | ST500DM002-1BD142  | 500 GB | 304     | 346   | 71    | 0.65   |
| Seagate   | ST1000DM003-1ER162 | 1 TB   | 102     | 238   | 2     | 0.65   |
| WDC       | WD800AAJS-00B4A0   | 80 GB  | 3       | 370   | 4     | 0.65   |
| Seagate   | ST750LM022 HN-M... | 750 GB | 64      | 304   | 27    | 0.65   |
| Hitachi   | HTS541010G9AT00    | 100 GB | 1       | 474   | 1     | 0.65   |
| Seagate   | ST320410A          | 20 GB  | 3       | 1020  | 17    | 0.65   |
| WDC       | WD10EFRX-68PJCN0   | 1 TB   | 16      | 256   | 1     | 0.65   |
| WDC       | WD3200BPVT-22JJ5T0 | 320 GB | 76      | 285   | 50    | 0.65   |
| WDC       | WD3200AAJS-00YZCA0 | 320 GB | 9       | 526   | 6     | 0.65   |
| WDC       | WD3200BEVS-26VAT0  | 320 GB | 1       | 235   | 0     | 0.64   |
| Seagate   | ST2000VX000-1ES164 | 2 TB   | 4       | 234   | 0     | 0.64   |
| WDC       | WD1200BEVS-60UST0  | 120 GB | 4       | 605   | 605   | 0.64   |
| Hitachi   | HTS545025B9A300    | 250 GB | 67      | 421   | 144   | 0.64   |
| WDC       | WD3200BEKT-75KA9T0 | 320 GB | 1       | 234   | 0     | 0.64   |
| WDC       | WD5000AARS-003BB1  | 500 GB | 4       | 576   | 5     | 0.64   |
| Samsung   | HD320KJ            | 320 GB | 1       | 234   | 0     | 0.64   |
| WDC       | WD5000AADS-67S9B0  | 500 GB | 1       | 2104  | 8     | 0.64   |
| Samsung   | HM250HI            | 250 GB | 47      | 329   | 9     | 0.64   |
| WDC       | WD7501AALS-00E3A0  | 750 GB | 7       | 623   | 52    | 0.64   |
| Samsung   | HM500JI            | 500 GB | 16      | 361   | 4     | 0.64   |
| WDC       | WD5000BEVT-00A0RT0 | 500 GB | 6       | 387   | 78    | 0.64   |
| Seagate   | ST1500DL003-9VT16L | 1.5 TB | 19      | 733   | 258   | 0.64   |
| WDC       | WD5000BPVT-55HXZT3 | 500 GB | 1       | 233   | 0     | 0.64   |
| Samsung   | HM320II            | 320 GB | 12      | 422   | 339   | 0.64   |
| WDC       | WD6400BPVT-26HXZT1 | 640 GB | 1       | 232   | 0     | 0.64   |
| WDC       | WD10SPCX-24HWST1   | 1 TB   | 1       | 232   | 0     | 0.64   |
| Seagate   | ST500NM0011        | 500 GB | 7       | 750   | 85    | 0.64   |
| WDC       | WD5000AAKS-00V1A0  | 500 GB | 33      | 749   | 168   | 0.64   |
| WDC       | WD7500BPVT-75HXZT3 | 750 GB | 2       | 231   | 0     | 0.63   |
| Hitachi   | HTS547575A9E384    | 750 GB | 71      | 379   | 411   | 0.63   |
| WDC       | WD10EZEX-60M2NA0   | 1 TB   | 6       | 283   | 168   | 0.63   |
| Seagate   | ST3160813AS        | 160 GB | 23      | 848   | 185   | 0.63   |
| WDC       | WD5000BPVT-75HXZT3 | 500 GB | 13      | 420   | 3     | 0.63   |
| Toshiba   | MK5065GSXF         | 500 GB | 5       | 385   | 6     | 0.63   |
| WDC       | WD5000BPVT-22A1YT0 | 500 GB | 7       | 229   | 0     | 0.63   |
| Toshiba   | L200 Hard drive    | 2 TB   | 2       | 229   | 0     | 0.63   |
| WDC       | WD5002ABYS-02B1B0  | 500 GB | 4       | 557   | 3     | 0.63   |
| WDC       | WD800BB-98JHC0     | 80 GB  | 1       | 1829  | 7     | 0.63   |
| Hitachi   | HDS721010DLE630    | 1 TB   | 21      | 562   | 361   | 0.63   |
| Seagate   | ST9160411AS        | 160 GB | 2       | 474   | 14    | 0.63   |
| Seagate   | ST1000VM002-1CT162 | 1 TB   | 2       | 227   | 0     | 0.62   |
| Seagate   | ST9120822AS        | 120 GB | 25      | 439   | 142   | 0.62   |
| WDC       | WD3200AAJS-60Z0A0  | 320 GB | 4       | 546   | 61    | 0.62   |
| WDC       | WD10EZRX-00L4HB0   | 1 TB   | 25      | 258   | 6     | 0.62   |
| WDC       | WD2500YD-01NVB1    | 251 GB | 1       | 1357  | 5     | 0.62   |
| Seagate   | ST3250823A         | 250 GB | 4       | 854   | 659   | 0.62   |
| WDC       | WD5000BEKT-80KA9T1 | 500 GB | 4       | 280   | 1     | 0.62   |
| Apple     | HDD HTS541010A9... | 1 TB   | 8       | 271   | 253   | 0.62   |
| WDC       | WD10EZEX-08M2NA0   | 1 TB   | 43      | 249   | 2     | 0.62   |
| Samsung   | SP1624N            | 160 GB | 1       | 225   | 0     | 0.62   |
| WDC       | WD5000LPVT-08G33T1 | 500 GB | 9       | 224   | 0     | 0.62   |
| Toshiba   | MK5076GSXN         | 500 GB | 1       | 224   | 0     | 0.62   |
| WDC       | WD10EZEX-22RKKA0   | 1 TB   | 2       | 224   | 0     | 0.61   |
| WDC       | WD3200BPVT-75JJ5T0 | 320 GB | 2       | 330   | 4     | 0.61   |
| WDC       | WD3200BEVT-60ZCT1  | 320 GB | 2       | 386   | 10    | 0.61   |
| Hitachi   | HDS721010CLA630    | 1 TB   | 5       | 307   | 1     | 0.61   |
| Fujitsu   | MHW2120BJ FFS G2   | 120 GB | 1       | 221   | 0     | 0.61   |
| Seagate   | ST250DM000-1BC141  | 250 GB | 8       | 297   | 12    | 0.61   |
| Toshiba   | MQ01ABD032         | 320 GB | 47      | 267   | 65    | 0.60   |
| Samsung   | MP0402H            | 40 GB  | 3       | 263   | 2     | 0.60   |
| Maxtor    | STM3250820A        | 250 GB | 3       | 587   | 435   | 0.60   |
| Seagate   | ST1000LM014-1EJ164 | 1 TB   | 24      | 307   | 193   | 0.60   |
| WDC       | WD3200AAKX-221CA1  | 320 GB | 1       | 218   | 0     | 0.60   |
| Samsung   | HD321HJ            | 320 GB | 3       | 720   | 52    | 0.60   |
| Samsung   | HD082GJ            | 80 GB  | 8       | 401   | 280   | 0.60   |
| Fujitsu   | MHZ2160BH G1       | 160 GB | 6       | 280   | 1     | 0.60   |
| WDC       | WD3000HLFS-75G6U1  | 300 GB | 1       | 218   | 0     | 0.60   |
| Maxtor    | 6G160P0            | 160 GB | 2       | 217   | 0     | 0.60   |
| Hitachi   | HTS541010A9E680    | 1 TB   | 6       | 371   | 526   | 0.60   |
| Seagate   | ST3000DM001-1CH166 | 3 TB   | 12      | 310   | 338   | 0.59   |
| WDC       | WD3200AZDX-00SC2B0 | 320 GB | 2       | 379   | 440   | 0.59   |
| Seagate   | ST9160823ASG       | 160 GB | 2       | 400   | 506   | 0.59   |
| WDC       | WD10EZEX-75ZF5A0   | 1 TB   | 4       | 215   | 0     | 0.59   |
| Hitachi   | HDS721010KLA330    | 1 TB   | 5       | 575   | 10    | 0.59   |
| WDC       | WD1003FZEX-00MK2A0 | 1 TB   | 24      | 214   | 0     | 0.59   |
| Hitachi   | HTS541080G9SA00    | 80 GB  | 4       | 467   | 5     | 0.59   |
| Samsung   | HD160JJ            | 160 GB | 48      | 804   | 444   | 0.59   |
| Toshiba   | DT01ACA100         | 1 TB   | 131     | 251   | 12    | 0.58   |
| WDC       | WD20NPVX-00EA4T0   | 2 TB   | 1       | 212   | 0     | 0.58   |
| Hitachi   | HTS542516K9SA00    | 160 GB | 28      | 557   | 215   | 0.58   |
| Hitachi   | HTS545016B9A300    | 160 GB | 25      | 307   | 49    | 0.58   |
| WDC       | WD10EZEX-00BN5A0   | 1 TB   | 64      | 231   | 2     | 0.58   |
| WDC       | WD1600JB-00GVC0    | 160 GB | 1       | 210   | 0     | 0.58   |
| Seagate   | ST320014A          | 20 GB  | 5       | 626   | 16    | 0.58   |
| Seagate   | ST3160212ACE       | 160 GB | 4       | 492   | 27    | 0.57   |
| WDC       | WD1600JD-00HBB0    | 160 GB | 3       | 696   | 6     | 0.57   |
| Samsung   | SP0802N            | 80 GB  | 17      | 705   | 57    | 0.57   |
| Seagate   | ST32000641AS       | 2 TB   | 6       | 473   | 268   | 0.57   |
| WDC       | WD10JPVT-22A1YT0   | 1 TB   | 5       | 321   | 1     | 0.57   |
| Seagate   | ST320DM000-1BD14C  | 320 GB | 25      | 259   | 46    | 0.57   |
| WDC       | WD5000BEKT-80KA9T0 | 500 GB | 3       | 317   | 1     | 0.57   |
| Maxtor    | 6V200E0            | 203 GB | 4       | 698   | 477   | 0.57   |
| IBM/Hi... | IC35L040AVVN07-0   | 41 GB  | 2       | 576   | 3     | 0.57   |
| Seagate   | ST2000VN000-1HJ164 | 2 TB   | 1       | 208   | 0     | 0.57   |
| WDC       | WD400BB-00FJA0     | 40 GB  | 2       | 699   | 222   | 0.57   |
| Seagate   | STM3250318AS       | 250 GB | 16      | 439   | 125   | 0.57   |
| Hitachi   | HDT721025SLA380    | 250 GB | 7       | 550   | 5     | 0.57   |
| WDC       | WD1600BJKT-75F4T0  | 160 GB | 3       | 243   | 1     | 0.57   |
| WDC       | WD2500AAJS-65M0A0  | 250 GB | 3       | 500   | 13    | 0.57   |
| Samsung   | HN-M320MBB         | 320 GB | 3       | 401   | 3     | 0.57   |
| Seagate   | ST33000651AS       | 3 TB   | 1       | 207   | 0     | 0.57   |
| Samsung   | HD161HJ            | 160 GB | 25      | 888   | 531   | 0.57   |
| Seagate   | ST9750420AS        | 750 GB | 32      | 380   | 75    | 0.57   |
| WDC       | WD1600BEVT-24A23T0 | 160 GB | 8       | 246   | 2     | 0.57   |
| WDC       | WD20PURX-64P6ZY0   | 2 TB   | 4       | 206   | 0     | 0.56   |
| Samsung   | HD322GJ            | 320 GB | 14      | 333   | 22    | 0.56   |
| WDC       | WD800JD-00LSA5     | 80 GB  | 1       | 205   | 0     | 0.56   |
| WDC       | WD15EARS-00Z5B1    | 1.5 TB | 18      | 940   | 665   | 0.56   |
| WDC       | WD10EURS-630AB1    | 1 TB   | 1       | 1846  | 8     | 0.56   |
| WDC       | WD1200JB-00GVC0    | 120 GB | 3       | 539   | 4     | 0.56   |
| WDC       | WD5000AAKX-00U6AA0 | 500 GB | 9       | 304   | 3     | 0.56   |
| WDC       | WD3200AVVS-56L2B0  | 320 GB | 4       | 323   | 17    | 0.56   |
| Hitachi   | HTS723232L9SA60    | 320 GB | 2       | 292   | 4     | 0.56   |
| WDC       | WD3200BPVT-80JJ5T0 | 320 GB | 44      | 281   | 54    | 0.56   |
| WDC       | WD20EZRX-22D8PB0   | 2 TB   | 1       | 203   | 0     | 0.56   |
| Seagate   | ST320LM001 HN-M... | 320 GB | 23      | 228   | 2     | 0.56   |
| WDC       | WD5003AZEX-00MK2A0 | 500 GB | 7       | 256   | 1     | 0.56   |
| WDC       | WD10EZEX-22BN5A0   | 1 TB   | 10      | 290   | 2     | 0.55   |
| Samsung   | HM501II            | 500 GB | 2       | 265   | 2     | 0.55   |
| Seagate   | ST360014A          | 60 GB  | 2       | 757   | 21    | 0.55   |
| WDC       | WD1600AAJS-60Z0A0  | 160 GB | 2       | 199   | 0     | 0.55   |
| Seagate   | ST980813ASG        | 80 GB  | 2       | 436   | 6     | 0.55   |
| WDC       | WD10JPVX-60JC3T0   | 1 TB   | 7       | 236   | 115   | 0.55   |
| Seagate   | ST1000VX001-1HH162 | 1 TB   | 2       | 198   | 0     | 0.54   |
| Toshiba   | HDWN180            | 8 TB   | 1       | 198   | 0     | 0.54   |
| WDC       | WD30PURX-64P6ZY0   | 3 TB   | 2       | 197   | 0     | 0.54   |
| WDC       | WD10EADS-11M2B2    | 1 TB   | 1       | 1778  | 8     | 0.54   |
| WDC       | WD6400BPVT-60HXZT1 | 640 GB | 2       | 408   | 42    | 0.54   |
| WDC       | WD3200BEVT-22A23T0 | 320 GB | 24      | 510   | 83    | 0.54   |
| WDC       | WD400BD-75MRA1     | 40 GB  | 1       | 196   | 0     | 0.54   |
| HGST      | HTS541075A9E680    | 750 GB | 18      | 248   | 398   | 0.54   |
| Quantum   | FIREBALLlct15 30   | 30 GB  | 1       | 391   | 1     | 0.54   |
| Hitachi   | HDS721612PLAT80    | 123 GB | 1       | 1366  | 6     | 0.53   |
| WDC       | WD5000BEVT-22A0RT0 | 500 GB | 25      | 519   | 25    | 0.53   |
| WDC       | WD2500BEVT-80A23T0 | 250 GB | 14      | 345   | 49    | 0.53   |
| Seagate   | ST94011A           | 40 GB  | 1       | 194   | 0     | 0.53   |
| Seagate   | ST320414A          | 20 GB  | 1       | 194   | 0     | 0.53   |
| WDC       | WD400BB-00DKA0     | 40 GB  | 1       | 193   | 0     | 0.53   |
| Seagate   | ST3750640AS        | 750 GB | 7       | 910   | 399   | 0.53   |
| Samsung   | SP0822N            | 80 GB  | 4       | 194   | 1     | 0.53   |
| Hitachi   | HTS545032A7E380    | 320 GB | 17      | 271   | 124   | 0.53   |
| WDC       | WD2500AAJS-00L7A0  | 250 GB | 16      | 501   | 15    | 0.53   |
| Seagate   | ST500LM012 HN-M... | 500 GB | 115     | 278   | 47    | 0.52   |
| WDC       | WD1600AABS-62PRA0  | 160 GB | 1       | 190   | 0     | 0.52   |
| WDC       | WD4001FAEX-00MJRA0 | 4 TB   | 1       | 190   | 0     | 0.52   |
| Hitachi   | HTS727575A9E364    | 750 GB | 9       | 214   | 121   | 0.52   |
| HGST      | HTS545032A7E680    | 320 GB | 8       | 220   | 2     | 0.52   |
| Hitachi   | HDS721050DLE630    | 500 GB | 26      | 439   | 373   | 0.52   |
| Hitachi   | HTS543225L9A300    | 250 GB | 16      | 559   | 351   | 0.52   |
| Seagate   | ST380211AS         | 80 GB  | 5       | 716   | 462   | 0.52   |
| Seagate   | ST9160827AS        | 160 GB | 24      | 464   | 379   | 0.52   |
| WDC       | WD5000LPVT-00G33T0 | 500 GB | 4       | 386   | 3     | 0.52   |
| WDC       | WD800BEVS-00RST0   | 80 GB  | 3       | 257   | 1     | 0.52   |
| WDC       | WD800JD-75JNA0     | 80 GB  | 2       | 1490  | 59    | 0.52   |
| Seagate   | ST96812A           | 60 GB  | 3       | 375   | 758   | 0.52   |
| WDC       | WD2500BJKT-00F4T0  | 250 GB | 2       | 187   | 0     | 0.51   |
| WDC       | WD7500BPKT-00PK4T0 | 750 GB | 1       | 187   | 0     | 0.51   |
| WDC       | WD1003FBYX-01Y7B1  | 1 TB   | 16      | 314   | 3     | 0.51   |
| WDC       | WD800BEVS-75RST0   | 80 GB  | 3       | 350   | 310   | 0.51   |
| Seagate   | ST9500420AS        | 500 GB | 45      | 525   | 415   | 0.51   |
| Hitachi   | HDT721064SLA360    | 640 GB | 2       | 1020  | 5     | 0.51   |
| Seagate   | ST3160812AS 41N... | 160 GB | 1       | 927   | 4     | 0.51   |
| WDC       | WD6400AADS-00M2B0  | 640 GB | 8       | 795   | 8     | 0.51   |
| WDC       | WD20EFRX-68EUZN0   | 2 TB   | 13      | 195   | 1     | 0.51   |
| WDC       | WD5000BEVT-80A0RT0 | 500 GB | 1       | 1662  | 8     | 0.51   |
| Seagate   | ST1000LM024 HN-... | 1 TB   | 280     | 249   | 53    | 0.51   |
| Hitachi   | HTS543232L9A300    | 320 GB | 12      | 542   | 553   | 0.50   |
| WDC       | WD7500BPVX-60JC3T0 | 750 GB | 3       | 247   | 2     | 0.50   |
| Quantum   | FIREBALLlct15 15   | 15 GB  | 1       | 183   | 0     | 0.50   |
| WDC       | WD3200AZRX-00A8LB0 | 320 GB | 2       | 183   | 0     | 0.50   |
| HGST      | HUS726040ALE611    | 4 TB   | 1       | 182   | 0     | 0.50   |
| Seagate   | ST750LX003-1AC154  | 750 GB | 8       | 257   | 132   | 0.50   |
| Seagate   | ST31000523AS       | 1 TB   | 2       | 2091  | 11    | 0.50   |
| HGST      | HDN724030ALE640    | 3 TB   | 2       | 182   | 0     | 0.50   |
| WDC       | WD1600AAJS-22WAA0  | 160 GB | 1       | 910   | 4     | 0.50   |
| WDC       | WD10EARX-00PASB0   | 1 TB   | 1       | 1636  | 8     | 0.50   |
| Samsung   | HM321HX            | 320 GB | 2       | 263   | 4     | 0.50   |
| Hitachi   | IC25N030ATMR04-0   | 30 GB  | 1       | 544   | 2     | 0.50   |
| Hitachi   | HTS541060G9AT00    | 60 GB  | 5       | 474   | 5     | 0.50   |
| WDC       | WD5000AAKS-22YGA0  | 500 GB | 2       | 526   | 228   | 0.50   |
| WDC       | WD7500BPKT-60PK4T0 | 750 GB | 2       | 343   | 4     | 0.49   |
| HGST      | HUS724040ALA640    | 4 TB   | 1       | 180   | 0     | 0.49   |
| Seagate   | ST3000VN000-1H4167 | 3 TB   | 1       | 179   | 0     | 0.49   |
| Hitachi   | HDT722525DLAT80    | 250 GB | 2       | 722   | 3     | 0.49   |
| Toshiba   | MK8009GAH          | 80 GB  | 2       | 360   | 43    | 0.49   |
| Samsung   | HE753LJ            | 750 GB | 2       | 374   | 51    | 0.49   |
| Seagate   | ST9120821A         | 120 GB | 3       | 490   | 26    | 0.49   |
| WDC       | WD5000BPKX-75HPJT0 | 500 GB | 1       | 178   | 0     | 0.49   |
| WDC       | WD1600BEVT-22A23T0 | 160 GB | 16      | 250   | 5     | 0.49   |
| WDC       | WD10JPVX-22JC3T0   | 1 TB   | 65      | 187   | 15    | 0.49   |
| Seagate   | ST9500423AS        | 500 GB | 16      | 233   | 8     | 0.49   |
| WDC       | WD5000LPVX-80V0TT0 | 500 GB | 26      | 185   | 1     | 0.48   |
| Seagate   | ST3120811AS        | 120 GB | 10      | 517   | 194   | 0.48   |
| Seagate   | ST3300822AS        | 300 GB | 1       | 176   | 0     | 0.48   |
| Seagate   | ST9500420ASG       | 500 GB | 1       | 351   | 1     | 0.48   |
| WDC       | WD60EFRX-68MYMN1   | 6 TB   | 5       | 294   | 3     | 0.48   |
| WDC       | WD3200AAJB-00J3A0  | 320 GB | 12      | 316   | 4     | 0.48   |
| Samsung   | HM080HC            | 72 GB  | 1       | 526   | 2     | 0.48   |
| WDC       | WD2005FBYZ-01YCBB2 | 2 TB   | 2       | 175   | 0     | 0.48   |
| WDC       | WD5000BPKT-75PK4T0 | 500 GB | 5       | 299   | 4     | 0.48   |
| WDC       | WD1003FBYX-01Y7B0  | 1 TB   | 3       | 973   | 5     | 0.48   |
| WDC       | WD5000BPKX-00HPJT0 | 500 GB | 2       | 174   | 0     | 0.48   |
| WDC       | WD3200BPVT-75ZEST0 | 320 GB | 3       | 275   | 3     | 0.48   |
| WDC       | WD10JUCT-63J6SY0   | 1 TB   | 3       | 173   | 0     | 0.48   |
| WDC       | WD3200BEVT-26ZCT0  | 320 GB | 2       | 243   | 1     | 0.48   |
| Samsung   | SP0812C            | 80 GB  | 12      | 499   | 178   | 0.47   |
| WDC       | WD3200BEVT-24A23T0 | 320 GB | 8       | 515   | 127   | 0.47   |
| WDC       | WD1600BEVT-35ZCT0  | 160 GB | 2       | 172   | 0     | 0.47   |
| WDC       | WD3200AAKS-22L6A0  | 320 GB | 3       | 378   | 5     | 0.47   |
| WDC       | WD30EZRX-00D8PB0   | 3 TB   | 7       | 274   | 2     | 0.47   |
| Toshiba   | MK2555GSXF         | 250 GB | 2       | 171   | 0     | 0.47   |
| Toshiba   | MK1237GSX          | 120 GB | 6       | 375   | 36    | 0.47   |
| WDC       | WD10JPVX-08JC3T2   | 1 TB   | 4       | 191   | 1     | 0.47   |
| Toshiba   | MK1234GSX          | 120 GB | 5       | 462   | 6     | 0.47   |
| Seagate   | ST250LT003-9YG14C  | 250 GB | 2       | 170   | 0     | 0.47   |
| Hitachi   | HCS5C1010DLE630    | 1 TB   | 1       | 169   | 0     | 0.47   |
| Toshiba   | MK8046GSX          | 80 GB  | 2       | 299   | 2     | 0.47   |
| WDC       | WD3200BJKT-00F4T0  | 320 GB | 1       | 169   | 0     | 0.46   |
| Samsung   | HM250HJ            | 250 GB | 2       | 337   | 17    | 0.46   |
| HGST      | HTS721010A9E630    | 1 TB   | 82      | 185   | 15    | 0.46   |
| Hitachi   | HTS545050A7E380    | 500 GB | 63      | 275   | 89    | 0.46   |
| Seagate   | ST1000DM000-9TS15E | 1 TB   | 1       | 168   | 0     | 0.46   |
| WDC       | WD10S21X-24R1BT... | 1 TB   | 5       | 168   | 0     | 0.46   |
| WDC       | WD1600JD-22HBB0    | 160 GB | 1       | 1010  | 5     | 0.46   |
| Seagate   | ST9500325ASG       | 500 GB | 2       | 432   | 58    | 0.46   |
| WDC       | WD5000LPCX-22VHAT0 | 500 GB | 7       | 168   | 0     | 0.46   |
| WDC       | WD7501AALS-00E8B0  | 750 GB | 1       | 1502  | 8     | 0.46   |
| WDC       | WD5000MPCK-60AWHT0 | 500 GB | 1       | 166   | 0     | 0.46   |
| Seagate   | ST3250820NS        | 250 GB | 2       | 695   | 1050  | 0.46   |
| WDC       | WD7500BPVT-08HXZT3 | 750 GB | 2       | 165   | 0     | 0.45   |
| WDC       | WD1200BEVS-75RST0  | 120 GB | 2       | 165   | 0     | 0.45   |
| WDC       | WD10SPCX-22HWST0   | 1 TB   | 1       | 165   | 0     | 0.45   |
| Maxtor    | 6G160E0            | 160 GB | 7       | 327   | 129   | 0.45   |
| Hitachi   | HDS721616PLAT80    | 164 GB | 2       | 1693  | 62    | 0.45   |
| WDC       | WD2500BPVT-22ZEST0 | 250 GB | 12      | 212   | 5     | 0.45   |
| WDC       | WD5000AAVS-00G9B0  | 500 GB | 1       | 1464  | 8     | 0.45   |
| Seagate   | ST320DM001 HD322GJ | 320 GB | 3       | 163   | 2     | 0.45   |
| Samsung   | HD080HJ-P          | 80 GB  | 3       | 461   | 3     | 0.44   |
| WDC       | WD1600BEVS-22VAT0  | 160 GB | 1       | 324   | 1     | 0.44   |
| Seagate   | ST920217AS         | 20 GB  | 1       | 162   | 0     | 0.44   |
| Hitachi   | HTS547564A9E384    | 640 GB | 22      | 461   | 534   | 0.44   |
| Toshiba   | DT01ACA050         | 500 GB | 168     | 180   | 29    | 0.44   |
| WDC       | WD3200AAKX-00ERMA0 | 320 GB | 7       | 201   | 3     | 0.44   |
| Toshiba   | MQ01ABC150         | 1.5 TB | 1       | 160   | 0     | 0.44   |
| WDC       | WD6400BEVT-22A0RT0 | 640 GB | 6       | 467   | 6     | 0.44   |
| WDC       | WD5000AADS-56S9B1  | 500 GB | 2       | 411   | 4     | 0.44   |
| Toshiba   | MK7575GSX          | 750 GB | 13      | 484   | 690   | 0.44   |
| WDC       | WD2000FYYZ-01UL1B1 | 2 TB   | 5       | 253   | 382   | 0.44   |
| Seagate   | ST500DM002-9YN14C  | 500 GB | 2       | 389   | 511   | 0.44   |
| WDC       | WD5000LPVX-28V0TT0 | 500 GB | 1       | 159   | 0     | 0.44   |
| WDC       | WD400BB-23FJA0     | 40 GB  | 1       | 796   | 4     | 0.44   |
| Hitachi   | HDS722512VLAT20    | 123 GB | 1       | 795   | 4     | 0.44   |
| Seagate   | ST910021AS         | 100 GB | 3       | 682   | 53    | 0.43   |
| Seagate   | ST4000DM000-1F2168 | 4 TB   | 7       | 186   | 1     | 0.43   |
| Hitachi   | HTS541075A9E680    | 750 GB | 4       | 325   | 764   | 0.43   |
| Hitachi   | HTS541616J9SA00    | 160 GB | 23      | 462   | 91    | 0.43   |
| WDC       | WD7500BPKX-75HPJT0 | 750 GB | 1       | 157   | 0     | 0.43   |
| Samsung   | HM250JI            | 250 GB | 3       | 491   | 11    | 0.43   |
| Hitachi   | HTS543232A7A384    | 320 GB | 114     | 278   | 298   | 0.43   |
| Toshiba   | MK3276GSXN         | 320 GB | 1       | 156   | 0     | 0.43   |
| WDC       | WD5000BPVT-60HXZT3 | 500 GB | 6       | 480   | 31    | 0.43   |
| Seagate   | ST98823AS          | 80 GB  | 5       | 365   | 830   | 0.43   |
| Maxtor    | STM3160215A        | 160 GB | 5       | 231   | 599   | 0.43   |
| WDC       | WD3200AVJS-63B6A0  | 320 GB | 3       | 1531  | 34    | 0.43   |
| WDC       | WD5000AAKX-75U6AA0 | 500 GB | 4       | 168   | 3     | 0.43   |
| WDC       | WD1600BEVT-80A23T0 | 160 GB | 16      | 204   | 3     | 0.43   |
| Hitachi   | HDP725032GLA380    | 320 GB | 5       | 878   | 41    | 0.43   |
| Seagate   | STM9120817AS       | 120 GB | 1       | 154   | 0     | 0.42   |
| Seagate   | ST2000DX001-1CM164 | 2 TB   | 11      | 250   | 265   | 0.42   |
| WDC       | WD5000AAKS-00WWPA0 | 500 GB | 3       | 336   | 20    | 0.42   |
| WDC       | WD10EZEX-07M2NA0   | 1 TB   | 1       | 152   | 0     | 0.42   |
| Seagate   | ST1000DX001-1CM162 | 1 TB   | 16      | 276   | 86    | 0.42   |
| WDC       | WD5000LPVT-24G33T1 | 500 GB | 13      | 213   | 1     | 0.42   |
| WDC       | WD400JB-00FMA0     | 40 GB  | 1       | 152   | 0     | 0.42   |
| Hitachi   | HTS542512K9SA00    | 120 GB | 38      | 456   | 113   | 0.42   |
| Toshiba   | HDWE140            | 4 TB   | 6       | 152   | 0     | 0.42   |
| WDC       | WD800JD-22LSA1     | 80 GB  | 3       | 627   | 232   | 0.42   |
| Seagate   | ST2000DM001-1ER164 | 2 TB   | 22      | 151   | 0     | 0.41   |
| Toshiba   | MK5059GSXP         | 500 GB | 18      | 297   | 339   | 0.41   |
| Fujitsu   | MHZ2250BH G2       | 250 GB | 9       | 504   | 577   | 0.41   |
| WDC       | WD10JPVT-75A1YT0   | 1 TB   | 4       | 443   | 4     | 0.41   |
| WDC       | WD7500BPVT-55HXZT4 | 750 GB | 1       | 150   | 0     | 0.41   |
| Samsung   | SP1634N            | 160 GB | 1       | 298   | 1     | 0.41   |
| WDC       | WD5001AALS-00LWTA0 | 500 GB | 3       | 495   | 80    | 0.41   |
| WDC       | WD10JPVX-80JC3T0   | 1 TB   | 7       | 148   | 0     | 0.41   |
| WDC       | WD5000LPVX-22V0TT0 | 500 GB | 100     | 176   | 3     | 0.41   |
| Seagate   | ST1500DM003-9YN16G | 1.5 TB | 14      | 449   | 446   | 0.41   |
| WDC       | WD5000BPVT-80HXZT1 | 500 GB | 5       | 575   | 67    | 0.41   |
| Fujitsu   | MHW2020BH          | 20 GB  | 1       | 148   | 0     | 0.41   |
| WDC       | WD800BB-75JHC0     | 80 GB  | 1       | 148   | 0     | 0.41   |
| WDC       | WD1600BEVT-75A23T0 | 160 GB | 3       | 244   | 1     | 0.41   |
| WDC       | WD1200JS-22NCB1    | 120 GB | 1       | 1184  | 7     | 0.41   |
| Hitachi   | HTS541680J9SA00    | 80 GB  | 34      | 468   | 43    | 0.40   |
| WDC       | WD5000BEVT-60ZAT1  | 500 GB | 4       | 344   | 15    | 0.40   |
| WDC       | WD2500BEVT-08A23T1 | 250 GB | 10      | 214   | 144   | 0.40   |
| Seagate   | ST9320325AS        | 320 GB | 144     | 429   | 383   | 0.40   |
| Hitachi   | HDS722525VLSA80    | 250 GB | 2       | 370   | 17    | 0.40   |
| WDC       | WD10EZRX-00D8PB0   | 1 TB   | 6       | 146   | 0     | 0.40   |
| WDC       | WD2500BEVT-00A0RT1 | 245 GB | 1       | 146   | 0     | 0.40   |
| Hitachi   | HTS543216L9A300    | 160 GB | 27      | 454   | 132   | 0.40   |
| WDC       | WD3000FYYZ-01UL1B0 | 3 TB   | 1       | 145   | 0     | 0.40   |
| Samsung   | SP0842N            | 80 GB  | 8       | 614   | 591   | 0.40   |
| Toshiba   | MK3265GSXN         | 320 GB | 12      | 412   | 298   | 0.40   |
| HGST      | HTS541010A9E680    | 1 TB   | 91      | 233   | 236   | 0.40   |
| Seagate   | ST9750423AS        | 750 GB | 7       | 274   | 288   | 0.40   |
| WDC       | WD3200BPVT-60JJ5T0 | 320 GB | 7       | 400   | 25    | 0.40   |
| WDC       | WD10PURX-64D85Y0   | 1 TB   | 4       | 213   | 2     | 0.40   |
| Fujitsu   | MHV2060BHPL        | 60 GB  | 1       | 144   | 0     | 0.40   |
| Seagate   | ST500LM000-1EJ1... | 500 GB | 1       | 144   | 0     | 0.40   |
| WDC       | WD3200BPVT-80ZEST0 | 320 GB | 18      | 342   | 12    | 0.39   |
| Seagate   | ST3750330NS        | 750 GB | 3       | 560   | 337   | 0.39   |
| Seagate   | ST9250827AS        | 250 GB | 14      | 379   | 308   | 0.39   |
| WDC       | WD5000AAKX-08U6AA0 | 500 GB | 24      | 157   | 1     | 0.39   |
| WDC       | WD3200AAJS-55VWA0  | 320 GB | 1       | 1006  | 6     | 0.39   |
| Seagate   | ST3250312CS        | 250 GB | 7       | 311   | 216   | 0.39   |
| Hitachi   | HTS545025B9SA02    | 250 GB | 4       | 184   | 507   | 0.39   |
| Samsung   | SP2004C            | 200 GB | 22      | 710   | 527   | 0.39   |
| Seagate   | ST3000NM0033-9Z... | 3 TB   | 2       | 577   | 9     | 0.39   |
| WDC       | WD2500BEVT-60ZCT1  | 250 GB | 2       | 142   | 0     | 0.39   |
| Toshiba   | MK2546GSX          | 250 GB | 9       | 560   | 41    | 0.39   |
| Toshiba   | MK2555GSX          | 250 GB | 18      | 391   | 119   | 0.39   |
| WDC       | WD2500AAJB-57WGA0  | 250 GB | 1       | 140   | 0     | 0.38   |
| IBM       | DTLA-305020        | 20 GB  | 2       | 1484  | 37    | 0.38   |
| WDC       | WD5000AAKB-00H8A0  | 500 GB | 12      | 509   | 9     | 0.38   |
| WDC       | WD400EB-11CPF0     | 40 GB  | 2       | 1019  | 31    | 0.38   |
| WDC       | WD800BB-00HEA0     | 80 GB  | 1       | 836   | 5     | 0.38   |
| WDC       | WD5000AAKS-60WWPA0 | 500 GB | 3       | 483   | 438   | 0.38   |
| WDC       | WD5000AZRZ-00HTKB0 | 500 GB | 4       | 138   | 0     | 0.38   |
| WDC       | WD10JPVX-75JC3T0   | 1 TB   | 20      | 178   | 3     | 0.38   |
| WDC       | WD2500BEVS-60UST0  | 250 GB | 6       | 425   | 338   | 0.38   |
| Hitachi   | HTS723232A7A364    | 320 GB | 18      | 255   | 455   | 0.38   |
| Seagate   | ST9250315AS        | 250 GB | 122     | 430   | 423   | 0.38   |
| Seagate   | ST9640320AS        | 640 GB | 6       | 395   | 340   | 0.38   |
| Seagate   | ST320LT022-1AE142  | 320 GB | 1       | 136   | 0     | 0.38   |
| WDC       | WD2500BPVT-24JJ5T0 | 250 GB | 1       | 136   | 0     | 0.37   |
| Samsung   | SP1654N            | 160 GB | 3       | 615   | 414   | 0.37   |
| WDC       | WD2500AAKX-603CA0  | 250 GB | 3       | 138   | 401   | 0.37   |
| Seagate   | ST3500312CS        | 500 GB | 7       | 815   | 484   | 0.37   |
| Hitachi   | HCT721050SLA380    | 500 GB | 1       | 136   | 0     | 0.37   |
| WDC       | WD800JD-00JNA0     | 80 GB  | 2       | 809   | 5     | 0.37   |
| Hitachi   | HTS725032A9A364    | 320 GB | 10      | 410   | 848   | 0.37   |
| WDC       | WD3201ABYS-01B9A0  | 320 GB | 2       | 926   | 278   | 0.37   |
| WDC       | WD3200AAKX-073CA1  | 320 GB | 2       | 342   | 4     | 0.37   |
| WDC       | WD6400BPVT-75HXZT1 | 640 GB | 2       | 385   | 3     | 0.37   |
| Fujitsu   | MHW2160BH          | 160 GB | 1       | 134   | 0     | 0.37   |
| WDC       | WD5000LPVX-55V0TT0 | 500 GB | 9       | 133   | 0     | 0.37   |
| WDC       | WD5000LPCX-24C6HT0 | 500 GB | 30      | 158   | 1     | 0.37   |
| Seagate   | ST3200822A         | 200 GB | 3       | 1660  | 14    | 0.36   |
| Toshiba   | MK1655GSX          | 160 GB | 10      | 266   | 36    | 0.36   |
| IBM/Hi... | IC35L040AVER07-0   | 41 GB  | 2       | 1050  | 7     | 0.36   |
| Samsung   | HD403LJ            | 400 GB | 10      | 1173  | 721   | 0.36   |
| HGST      | HTS545050A7E380    | 500 GB | 88      | 243   | 246   | 0.36   |
| Seagate   | ST9120822A         | 120 GB | 2       | 273   | 53    | 0.36   |
| Samsung   | HD752LJ            | 750 GB | 1       | 516   | 3     | 0.35   |
| Hitachi   | HTS541212H9AT00    | 120 GB | 3       | 335   | 5     | 0.35   |
| Seagate   | ST3120813AS        | 120 GB | 14      | 826   | 819   | 0.35   |
| Toshiba   | MG03ACA100         | 1 TB   | 7       | 153   | 1     | 0.35   |
| Hitachi   | HTS542525K9SA00    | 250 GB | 24      | 534   | 52    | 0.35   |
| WDC       | WD10EADS-98M2B0    | 1 TB   | 1       | 899   | 6     | 0.35   |
| WDC       | WD5000AZLX-00CL5A0 | 500 GB | 2       | 128   | 0     | 0.35   |
| WDC       | WD3200BPVT-16JJ5T0 | 320 GB | 2       | 231   | 1     | 0.35   |
| WDC       | WD3200AAJS-65M0A0  | 320 GB | 1       | 1152  | 8     | 0.35   |
| WDC       | WD5000BPKT-22PK4T0 | 500 GB | 1       | 127   | 0     | 0.35   |
| Seagate   | ST3500830SCE       | 500 GB | 1       | 126   | 0     | 0.35   |
| Seagate   | ST9120821AS        | 120 GB | 5       | 274   | 1101  | 0.35   |
| Samsung   | SP0812N            | 80 GB  | 4       | 546   | 6     | 0.35   |
| Toshiba   | MQ01ABD100         | 1 TB   | 95      | 173   | 58    | 0.35   |
| WDC       | WD400BB-60DGA0     | 40 GB  | 1       | 504   | 3     | 0.35   |
| Seagate   | ST3500410AS        | 500 GB | 19      | 1001  | 323   | 0.34   |
| Toshiba   | MQ01ABD050         | 500 GB | 63      | 283   | 312   | 0.34   |
| Toshiba   | MK1216GSG          | 120 GB | 3       | 272   | 4     | 0.34   |
| WDC       | WD10JPVX-00JC3T0   | 1 TB   | 23      | 128   | 1     | 0.34   |
| HGST      | HTS721075A9E630    | 750 GB | 5       | 124   | 0     | 0.34   |
| Samsung   | HD252KJ            | 250 GB | 5       | 551   | 406   | 0.34   |
| Toshiba   | MK3252GSX          | 320 GB | 15      | 557   | 261   | 0.34   |
| Toshiba   | DT01ABA200         | 2 TB   | 1       | 124   | 0     | 0.34   |
| WDC       | WD3200AAJS-56M0A0  | 320 GB | 5       | 408   | 3     | 0.34   |
| WDC       | WD20EARS-00J2GB0   | 2 TB   | 1       | 1120  | 8     | 0.34   |
| WDC       | WD3200AAKS-00C9A0  | 320 GB | 3       | 1079  | 8     | 0.34   |
| Seagate   | ST4000VN000-1H4168 | 4 TB   | 2       | 124   | 0     | 0.34   |
| HGST      | HTS725050A7E630    | 500 GB | 75      | 164   | 84    | 0.34   |
| WDC       | WD5000AZLX-00K2TA0 | 500 GB | 3       | 124   | 0     | 0.34   |
| WDC       | WD5000AAKS-60Z1A0  | 500 GB | 2       | 371   | 2     | 0.34   |
| Samsung   | HD200HJ            | 200 GB | 10      | 853   | 731   | 0.34   |
| HGST      | HTE725050A7E630    | 500 GB | 1       | 122   | 0     | 0.34   |
| Toshiba   | MK7559GSXP         | 750 GB | 11      | 416   | 441   | 0.34   |
| Seagate   | ST3160815SV        | 160 GB | 5       | 577   | 1240  | 0.34   |
| Seagate   | ST1000NM0011       | 1 TB   | 4       | 506   | 68    | 0.34   |
| WDC       | WD1600AVVS-63L2B0  | 160 GB | 2       | 121   | 0     | 0.33   |
| Toshiba   | MK1034GSX          | 100 GB | 4       | 385   | 464   | 0.33   |
| WDC       | WD5000AAKS-55V0A0  | 500 GB | 5       | 427   | 6     | 0.33   |
| Seagate   | ST9100827AS        | 100 GB | 1       | 838   | 6     | 0.33   |
| Seagate   | ST960821A          | 60 GB  | 1       | 358   | 2     | 0.33   |
| Toshiba   | MK5076GSX -63      | 500 GB | 2       | 119   | 0     | 0.33   |
| Toshiba   | MK6025GAS          | 60 GB  | 2       | 166   | 9     | 0.33   |
| WDC       | WD5000AAKX-221CA1  | 500 GB | 8       | 429   | 41    | 0.33   |
| HGST      | HTS545032A7E380    | 320 GB | 12      | 128   | 1     | 0.32   |
| WDC       | WD2500BPVT-75JJ5T0 | 250 GB | 2       | 117   | 0     | 0.32   |
| Toshiba   | MK1633GSG          | 160 GB | 2       | 116   | 0     | 0.32   |
| WDC       | WD10SPCX-80HWST0   | 1 TB   | 1       | 116   | 0     | 0.32   |
| WDC       | ZALMAN             | 500 GB | 1       | 1047  | 8     | 0.32   |
| WDC       | WD5000AZRX-00L4HB0 | 500 GB | 9       | 116   | 0     | 0.32   |
| Hitachi   | HTS543216L9SA00    | 160 GB | 8       | 291   | 12    | 0.32   |
| Seagate   | ST980811AS         | 80 GB  | 13      | 439   | 210   | 0.32   |
| Seagate   | ST640LM001 HN-M... | 640 GB | 1       | 116   | 0     | 0.32   |
| Seagate   | ST9160823AS        | 160 GB | 4       | 924   | 638   | 0.32   |
| Seagate   | ST320LT012-1DG14C  | 320 GB | 11      | 238   | 96    | 0.32   |
| WDC       | WD3200BEKX-00B7WT0 | 320 GB | 5       | 119   | 3     | 0.31   |
| WDC       | WD5000AAKS-00M9A0  | 500 GB | 4       | 580   | 569   | 0.31   |
| Samsung   | SP2504C            | 250 GB | 21      | 974   | 828   | 0.31   |
| Hitachi   | HTS725050A9A364    | 500 GB | 12      | 347   | 694   | 0.31   |
| Toshiba   | MK2565GSX          | 250 GB | 15      | 250   | 223   | 0.31   |
| WDC       | WD3200AVJS-63N9A0  | 320 GB | 1       | 114   | 0     | 0.31   |
| WDC       | WD3200LPVX-22V0TT0 | 320 GB | 10      | 148   | 2     | 0.31   |
| WDC       | WD1002F9YZ-09H1JL1 | 1 TB   | 1       | 112   | 0     | 0.31   |
| WDC       | WD2500BEVT-75A23T0 | 250 GB | 4       | 498   | 14    | 0.31   |
| Hitachi   | HUA722010CLA330    | 1 TB   | 5       | 242   | 12    | 0.31   |
| WDC       | WD3200BEVT-08A23T1 | 320 GB | 2       | 234   | 4     | 0.31   |
| WDC       | WD3200AAKS-00YGA0  | 320 GB | 1       | 562   | 4     | 0.31   |
| Toshiba   | MK1059GSMP         | 1 TB   | 11      | 467   | 334   | 0.31   |
| Seagate   | ST9100823A         | 95 GB  | 1       | 1007  | 8     | 0.31   |
| WDC       | WD5000AAKX-003CA0  | 500 GB | 10      | 463   | 54    | 0.31   |
| WDC       | WD1001FAES-55W7A0  | 1 TB   | 1       | 111   | 0     | 0.31   |
| Fujitsu   | MHV2060BH          | 60 GB  | 3       | 498   | 20    | 0.30   |
| Fujitsu   | MPE3064AT          | 6 GB   | 1       | 111   | 0     | 0.30   |
| WDC       | WD400EB-00CPF0     | 40 GB  | 2       | 534   | 11    | 0.30   |
| Toshiba   | MK6475GSX          | 640 GB | 15      | 296   | 448   | 0.30   |
| WDC       | WD10EZEX-75M2NA0   | 1 TB   | 6       | 109   | 0     | 0.30   |
| Apple     | HDD ST1000DM003    | 1 TB   | 1       | 109   | 0     | 0.30   |
| Seagate   | ST9320310AS        | 320 GB | 3       | 281   | 338   | 0.30   |
| Toshiba   | MK6465GSX          | 640 GB | 15      | 634   | 425   | 0.30   |
| Hitachi   | HTS541612J9SA00    | 120 GB | 40      | 510   | 33    | 0.30   |
| Toshiba   | MQ02ABD100H        | 1 TB   | 2       | 107   | 0     | 0.30   |
| WDC       | WD2500BEVT-00ZCT0  | 250 GB | 6       | 107   | 0     | 0.29   |
| WDC       | WD3200AAJS-60M0A1  | 320 GB | 3       | 586   | 1255  | 0.29   |
| Fujitsu   | MHW2040BH          | 40 GB  | 1       | 214   | 1     | 0.29   |
| Fujitsu   | MHV2100BH PL       | 100 GB | 3       | 291   | 4     | 0.29   |
| Hitachi   | HTS542520K9SA00    | 200 GB | 4       | 657   | 11    | 0.29   |
| Seagate   | ST320LT020-9YG142  | 320 GB | 86      | 286   | 491   | 0.29   |
| WDC       | WD3200LPCX-24C6HT0 | 320 GB | 16      | 106   | 0     | 0.29   |
| China     | TP00250GB          | 250 GB | 1       | 106   | 0     | 0.29   |
| WDC       | WD5000LPLX-75ZNTT0 | 500 GB | 1       | 106   | 0     | 0.29   |
| Seagate   | ST320LM010-1KJ15C  | 320 GB | 2       | 105   | 0     | 0.29   |
| WDC       | WD1500HLFS-01G6U0  | 150 GB | 1       | 211   | 1     | 0.29   |
| WDC       | WD6400BPVT-80HXZT1 | 640 GB | 4       | 422   | 6     | 0.29   |
| Hitachi   | HTS727550A9E364    | 500 GB | 7       | 273   | 438   | 0.29   |
| Seagate   | ST9500325AS        | 500 GB | 225     | 423   | 601   | 0.29   |
| Toshiba   | MQ01ABF032         | 320 GB | 14      | 104   | 0     | 0.29   |
| Seagate   | ST500LM000-SSHD... | 500 GB | 14      | 156   | 91    | 0.28   |
| WDC       | WD5000AAKX-19U6AA0 | 500 GB | 1       | 103   | 0     | 0.28   |
| WDC       | WD5000AAKX-22ERMA0 | 500 GB | 20      | 236   | 3     | 0.28   |
| WDC       | WD2500AAKX-221CA1  | 250 GB | 1       | 931   | 8     | 0.28   |
| Hitachi   | HTS542580K9SA00    | 80 GB  | 6       | 336   | 6     | 0.28   |
| WDC       | WD10JPVX-35JC3T0   | 1 TB   | 1       | 103   | 0     | 0.28   |
| Fujitsu   | MHT2040AH PL       | 40 GB  | 1       | 306   | 2     | 0.28   |
| Seagate   | ST1000DM003-1SB10C | 1 TB   | 31      | 102   | 0     | 0.28   |
| Hitachi   | HTS541040G9AT00    | 40 GB  | 2       | 206   | 3     | 0.28   |
| WDC       | WD5000BPVT-08HXZT1 | 500 GB | 1       | 100   | 0     | 0.28   |
| WDC       | WD5000LPVX-00V0TT0 | 500 GB | 14      | 152   | 54    | 0.28   |
| WDC       | WD5000HHTZ-04N21V1 | 500 GB | 1       | 100   | 0     | 0.27   |
| Samsung   | HN-M101MBB         | 1 TB   | 6       | 428   | 388   | 0.27   |
| Hitachi   | HUA723020ALA641    | 2 TB   | 2       | 100   | 0     | 0.27   |
| WDC       | WD5000BEVT-22ZAT0  | 500 GB | 4       | 310   | 2     | 0.27   |
| Seagate   | ST5000DM000-1FK178 | 5 TB   | 2       | 112   | 4     | 0.27   |
| WDC       | WD10SPCX-75HWST0   | 1 TB   | 1       | 100   | 0     | 0.27   |
| WDC       | WD10EZEX-21WN4A0   | 1 TB   | 5       | 99    | 0     | 0.27   |
| Seagate   | ST250LM004 HN-M... | 250 GB | 3       | 192   | 5     | 0.27   |
| Toshiba   | MQ01ACF050         | 500 GB | 6       | 127   | 173   | 0.27   |
| WDC       | WD5000BPKX-22HPJT0 | 500 GB | 7       | 99    | 0     | 0.27   |
| Toshiba   | MK1637GSX          | 160 GB | 21      | 537   | 45    | 0.27   |
| Seagate   | ST340014AS         | 40 GB  | 2       | 1218  | 1016  | 0.27   |
| Toshiba   | MQ01ABF050         | 500 GB | 142     | 116   | 81    | 0.27   |
| WDC       | WD7500BPVT-00HXZT3 | 750 GB | 7       | 496   | 16    | 0.27   |
| WDC       | WD3202ABYS-01B7A0  | 320 GB | 2       | 546   | 5     | 0.27   |
| WDC       | WD40EFRX-68WT0N0   | 4 TB   | 6       | 116   | 1     | 0.27   |
| Toshiba   | MK3276GSX -63      | 320 GB | 5       | 141   | 1     | 0.26   |
| Fujitsu   | MHY2160BH          | 160 GB | 5       | 191   | 241   | 0.26   |
| WDC       | WD5000LPVX-60V0TT0 | 500 GB | 7       | 159   | 25    | 0.26   |
| WDC       | WD5000BEKT-60KA9T0 | 500 GB | 1       | 383   | 3     | 0.26   |
| Samsung   | HM500JJ            | 500 GB | 2       | 299   | 5     | 0.26   |
| Samsung   | SP0401N            | 40 GB  | 1       | 95    | 0     | 0.26   |
| Seagate   | ST9120817AS        | 120 GB | 3       | 370   | 456   | 0.26   |
| Toshiba   | MK3259GSXP         | 320 GB | 32      | 217   | 153   | 0.26   |
| Seagate   | ST1000UM000-1EK164 | 1 TB   | 1       | 94    | 0     | 0.26   |
| WDC       | WD7500BPKX-22HPJT0 | 750 GB | 5       | 136   | 2     | 0.26   |
| WDC       | WD1600JS-22NCB1    | 160 GB | 2       | 478   | 5     | 0.26   |
| Toshiba   | MK1665GSX H        | 160 GB | 1       | 93    | 0     | 0.26   |
| WDC       | WD10EZRZ-00Z5HB0   | 1 TB   | 4       | 93    | 0     | 0.26   |
| Toshiba   | MK8037GSX          | 80 GB  | 11      | 414   | 206   | 0.25   |
| WDC       | WD2500JS-19NCB1    | 250 GB | 1       | 92    | 0     | 0.25   |
| Toshiba   | MK5065GSX          | 500 GB | 12      | 345   | 248   | 0.25   |
| WDC       | WD1600BPVT-22JJ5T0 | 160 GB | 1       | 91    | 0     | 0.25   |
| Toshiba   | HDWD130            | 3 TB   | 3       | 89    | 0     | 0.25   |
| Samsung   | HS082HB            | 80 GB  | 1       | 89    | 0     | 0.25   |
| Seagate   | ST340810A          | 40 GB  | 7       | 480   | 43    | 0.24   |
| Seagate   | ST380023A          | 80 GB  | 1       | 2752  | 30    | 0.24   |
| WDC       | WD5000AADS-00L4B1  | 500 GB | 4       | 283   | 7     | 0.24   |
| WDC       | WD1600AAJB-00J3A0  | 160 GB | 10      | 641   | 212   | 0.24   |
| WDC       | WD10EZEX-35WN4A0   | 1 TB   | 3       | 88    | 0     | 0.24   |
| Toshiba   | MK1246GSX          | 120 GB | 9       | 433   | 72    | 0.24   |
| WDC       | WD3200AAKX-753CA1  | 320 GB | 2       | 221   | 4     | 0.24   |
| Seagate   | ST380021A          | 80 GB  | 6       | 663   | 20    | 0.24   |
| Toshiba   | MK3265GSX          | 320 GB | 41      | 565   | 242   | 0.24   |
| Samsung   | HN-M750MBB         | 750 GB | 4       | 229   | 7     | 0.24   |
| WDC       | WD10EZEX-08Y20A0   | 1 TB   | 2       | 87    | 0     | 0.24   |
| WDC       | WD5000AAKS-65V0A0  | 500 GB | 2       | 786   | 8     | 0.24   |
| WDC       | WD2000JB-22GVA0    | 200 GB | 1       | 694   | 7     | 0.24   |
| Hitachi   | IC25N080ATMR04-0   | 80 GB  | 2       | 268   | 26    | 0.24   |
| Seagate   | ST320LT007-9ZV142  | 320 GB | 10      | 308   | 857   | 0.24   |
| Seagate   | ST2000LM007-1R8174 | 2 TB   | 3       | 99    | 23    | 0.24   |
| WDC       | WD2500BPVT-22JJ5T0 | 250 GB | 3       | 217   | 248   | 0.24   |
| WDC       | WD1600BEVT-00A1TT0 | 160 GB | 2       | 273   | 3     | 0.24   |
| Hitachi   | HTS541010G9SA00    | 100 GB | 8       | 391   | 15    | 0.24   |
| Seagate   | ST750LM030-1KKG62  | 750 GB | 1       | 85    | 0     | 0.23   |
| WDC       | WD1600AAJS-56M0A0  | 160 GB | 1       | 767   | 8     | 0.23   |
| WDC       | WD7500BPVT-22HXZT1 | 750 GB | 4       | 812   | 260   | 0.23   |
| Toshiba   | MK1629GSG          | 160 GB | 1       | 594   | 6     | 0.23   |
| Seagate   | ST3500412AS        | 500 GB | 14      | 723   | 570   | 0.23   |
| Samsung   | HD300LD            | 300 GB | 4       | 554   | 15    | 0.23   |
| Seagate   | ST1000LM014-SSH... | 1 TB   | 6       | 177   | 16    | 0.23   |
| Toshiba   | MK3263GSXN         | 320 GB | 5       | 582   | 15    | 0.23   |
| Toshiba   | MK3021GAS          | 30 GB  | 1       | 495   | 5     | 0.23   |
| Samsung   | SP2014N            | 200 GB | 4       | 313   | 18    | 0.23   |
| WDC       | WD2500AAKX-753CA1  | 250 GB | 2       | 104   | 4     | 0.23   |
| Seagate   | ST500LT012-1DG142  | 500 GB | 209     | 120   | 57    | 0.23   |
| WDC       | WD2500AAKX-193CA0  | 250 GB | 1       | 82    | 0     | 0.23   |
| WDC       | WD20EARS-22MVWB0   | 2 TB   | 1       | 739   | 8     | 0.23   |
| Seagate   | ST9160314AS        | 160 GB | 17      | 232   | 266   | 0.22   |
| WDC       | WD5000LPCX-00VHAT0 | 500 GB | 9       | 82    | 0     | 0.22   |
| Seagate   | ST9250410ASG       | 250 GB | 1       | 409   | 4     | 0.22   |
| WDC       | WD800BB-55JKC0     | 80 GB  | 5       | 751   | 31    | 0.22   |
| WDC       | WD50EFRX-68MYMN1   | 5 TB   | 2       | 81    | 0     | 0.22   |
| Seagate   | ST9160821AS        | 160 GB | 39      | 428   | 624   | 0.22   |
| WDC       | WD5000AAKS-00H2B0  | 499 GB | 1       | 731   | 8     | 0.22   |
| WDC       | WD10EURX-73C57Y0   | 1 TB   | 1       | 81    | 0     | 0.22   |
| HGST      | HTS545050A7E660    | 500 GB | 8       | 156   | 4     | 0.22   |
| WDC       | WD10J31X-00U3VT0   | 1 TB   | 1       | 80    | 0     | 0.22   |
| Magnet... | MD03200-AJDW-RO    | 320 GB | 1       | 79    | 0     | 0.22   |
| Toshiba   | MK4055GSX          | 400 GB | 1       | 557   | 6     | 0.22   |
| Seagate   | ST95005620AS       | 500 GB | 5       | 406   | 417   | 0.22   |
| WDC       | WD600BEVS-07LAT0   | 60 GB  | 1       | 635   | 7     | 0.22   |
| Seagate   | ST4000DM005-2DP166 | 4 TB   | 2       | 79    | 0     | 0.22   |
| Maxtor    | STM3160811AS       | 160 GB | 5       | 686   | 257   | 0.22   |
| WDC       | WD1003FZEX-00RLFA0 | 1 TB   | 1       | 79    | 0     | 0.22   |
| Toshiba   | MK3263GSX          | 320 GB | 4       | 536   | 25    | 0.22   |
| WDC       | WD3200BUCT-63TWBY0 | 320 GB | 2       | 79    | 0     | 0.22   |
| WDC       | WD3200BEVT-00ZCT0  | 320 GB | 2       | 501   | 6     | 0.22   |
| Hitachi   | HTS543225A7A384    | 250 GB | 14      | 264   | 365   | 0.22   |
| Hitachi   | HDP725016GLA380    | 160 GB | 4       | 863   | 389   | 0.22   |
| Samsung   | SP2514N            | 250 GB | 5       | 450   | 610   | 0.21   |
| Seagate   | ST2000DM006-2DM164 | 2 TB   | 3       | 78    | 0     | 0.21   |
| WDC       | WD1600BEVT-26ZCT0  | 160 GB | 1       | 78    | 0     | 0.21   |
| Seagate   | ST3320613AS        | 320 GB | 67      | 748   | 245   | 0.21   |
| WDC       | WD5000AZRX-00A3KB0 | 500 GB | 3       | 113   | 3     | 0.21   |
| Toshiba   | MK1665GSX          | 160 GB | 11      | 215   | 158   | 0.21   |
| WDC       | WD400JB-00ENA0     | 40 GB  | 1       | 1000  | 12    | 0.21   |
| HP        | GB0250EAFJF        | 250 GB | 1       | 535   | 6     | 0.21   |
| Seagate   | ST9160310AS        | 160 GB | 24      | 267   | 226   | 0.21   |
| Toshiba   | MK1646GSX          | 160 GB | 4       | 527   | 58    | 0.21   |
| WDC       | WD2502ABYS-50B7A1  | 250 GB | 1       | 1290  | 16    | 0.21   |
| Hitachi   | HTS543280L9A300    | 80 GB  | 2       | 99    | 1     | 0.21   |
| Hitachi   | HTS541060G9SA00    | 60 GB  | 2       | 329   | 4     | 0.21   |
| WDC       | WD10EARX-00NYB0    | 1 TB   | 1       | 75    | 0     | 0.21   |
| WDC       | WD7500BPKX-00HPJT0 | 750 GB | 3       | 75    | 0     | 0.21   |
| WDC       | WD1004FBYZ-01YCBB1 | 1 TB   | 1       | 75    | 0     | 0.21   |
| Toshiba   | MK6476GSXN         | 640 GB | 3       | 122   | 601   | 0.21   |
| WDC       | WD3200BPVT-00ZEST0 | 320 GB | 2       | 74    | 0     | 0.21   |
| WDC       | WD400VE-07HDT0     | 40 GB  | 1       | 74    | 0     | 0.20   |
| Seagate   | ST500LM000-1EJ162  | 500 GB | 31      | 156   | 56    | 0.20   |
| Seagate   | ST2000VX000-9YW164 | 2 TB   | 4       | 407   | 228   | 0.20   |
| Hitachi   | HTS541080G9AT00    | 80 GB  | 10      | 487   | 83    | 0.20   |
| WDC       | WD800VE-75HDT1     | 80 GB  | 1       | 369   | 4     | 0.20   |
| Seagate   | ST1000DM003-1SB102 | 1 TB   | 14      | 73    | 0     | 0.20   |
| Hitachi   | HDE721050SLA330    | 500 GB | 1       | 2416  | 32    | 0.20   |
| WDC       | WD1500BLHX-01V7BV0 | 150 GB | 1       | 72    | 0     | 0.20   |
| WDC       | WD20EADS-32S2B0    | 2 TB   | 1       | 1093  | 14    | 0.20   |
| WDC       | WD1600SD-01KCC0    | 160 GB | 1       | 2914  | 39    | 0.20   |
| WDC       | WD2500LPCX-24C6HT0 | 250 GB | 19      | 74    | 1     | 0.20   |
| Toshiba   | MK8034GSX          | 80 GB  | 6       | 356   | 51    | 0.20   |
| Fujitsu   | MJA2500BH G2       | 500 GB | 8       | 309   | 146   | 0.20   |
| Seagate   | ST9160412AS        | 160 GB | 4       | 449   | 256   | 0.20   |
| WDC       | WD1600AAJS-75PSA0  | 159 GB | 4       | 254   | 3     | 0.20   |
| Seagate   | ST500LM030-1RK17D  | 500 GB | 2       | 71    | 0     | 0.20   |
| HP        | MB1000EAMZE        | 1 TB   | 1       | 1919  | 26    | 0.19   |
| Toshiba   | MK2552GSX          | 250 GB | 4       | 357   | 33    | 0.19   |
| WDC       | WD7500BPVX-75JC3T0 | 750 GB | 1       | 349   | 4     | 0.19   |
| Seagate   | ST9160301AS        | 160 GB | 5       | 153   | 403   | 0.19   |
| WDC       | WD7500LPCX-60KHST0 | 750 GB | 3       | 69    | 0     | 0.19   |
| Hitachi   | HTS722020K9SA00    | 200 GB | 3       | 636   | 9     | 0.19   |
| Hitachi   | HTS542525K9A300    | 250 GB | 2       | 351   | 511   | 0.19   |
| Seagate   | ST3000DM001-9YN166 | 3 TB   | 10      | 482   | 1453  | 0.19   |
| WDC       | WD2500AAJS-22L7A0  | 250 GB | 3       | 625   | 9     | 0.19   |
| Seagate   | ST91608220AS       | 160 GB | 1       | 135   | 1     | 0.19   |
| Seagate   | ST4000DX001-1CE168 | 4 TB   | 3       | 96    | 8     | 0.19   |
| WDC       | WD200BB-60CJA0     | 20 GB  | 1       | 1417  | 20    | 0.18   |
| WDC       | WD3200JS-22PDB0    | 320 GB | 1       | 1538  | 22    | 0.18   |
| WDC       | WD3200BEVT-75A23T0 | 320 GB | 1       | 133   | 1     | 0.18   |
| Seagate   | ST3402111A         | 40 GB  | 2       | 117   | 36    | 0.18   |
| WDC       | WD3200BEVT-60A23T0 | 320 GB | 13      | 287   | 386   | 0.18   |
| WDC       | WD10JUCT-63CYNY0   | 1 TB   | 1       | 66    | 0     | 0.18   |
| WDC       | WD10PURX-64E5EY0   | 1 TB   | 3       | 69    | 1     | 0.18   |
| WDC       | WD30EZRX-22D8PB0   | 3 TB   | 1       | 65    | 0     | 0.18   |
| WDC       | WD1600AAJS         | 160 GB | 1       | 65    | 0     | 0.18   |
| HGST      | HTE721010A9E630    | 1 TB   | 2       | 65    | 0     | 0.18   |
| WDC       | WD10JPCX-24UE4T0   | 1 TB   | 16      | 78    | 1     | 0.18   |
| WDC       | WD3200BPVT-00HXZT1 | 320 GB | 4       | 331   | 295   | 0.18   |
| Hitachi   | HTS545032B9A302    | 320 GB | 2       | 228   | 13    | 0.18   |
| Seagate   | ST1000VX000-1ES162 | 1 TB   | 11      | 64    | 0     | 0.18   |
| Toshiba   | MK1011GAH          | 100 GB | 4       | 378   | 9     | 0.18   |
| Seagate   | ST9100824AS        | 100 GB | 2       | 129   | 3     | 0.18   |
| WDC       | WD5000AAKX-60U6AA0 | 500 GB | 18      | 144   | 77    | 0.18   |
| WDC       | WD10EZEX-00WN4A0   | 1 TB   | 20      | 63    | 0     | 0.17   |
| Samsung   | HD400LD            | 400 GB | 1       | 63    | 0     | 0.17   |
| WDC       | WD30EZRZ-00Z5HB0   | 3 TB   | 6       | 63    | 0     | 0.17   |
| WDC       | WD10EURX-73FH1Y0   | 1 TB   | 2       | 63    | 0     | 0.17   |
| WDC       | WD3200BEVT-22A0RT0 | 320 GB | 2       | 120   | 2     | 0.17   |
| WDC       | WD5000BPKT-80PK4T0 | 500 GB | 1       | 563   | 8     | 0.17   |
| Hitachi   | HTS424040M9AT00    | 40 GB  | 5       | 483   | 20    | 0.17   |
| HGST      | HTS725032A7E630    | 320 GB | 5       | 112   | 410   | 0.17   |
| WDC       | WD800AAJS-60B4A0   | 80 GB  | 1       | 3049  | 48    | 0.17   |
| WDC       | WD10EZRX-22L4HB0   | 1 TB   | 1       | 62    | 0     | 0.17   |
| Toshiba   | HDWJ105            | 500 GB | 3       | 61    | 0     | 0.17   |
| Maxtor    | 4K060H3            | 60 GB  | 1       | 927   | 14    | 0.17   |
| HGST      | HTS545050A7E680    | 500 GB | 130     | 116   | 295   | 0.17   |
| WDC       | WD5000LPVX-08V0TT5 | 500 GB | 8       | 83    | 1     | 0.17   |
| WDC       | WD10EZEX-07WN4A0   | 1 TB   | 1       | 61    | 0     | 0.17   |
| Hitachi   | HTS725016A9A362    | 160 GB | 1       | 61    | 0     | 0.17   |
| Seagate   | ST3120213A         | 120 GB | 8       | 494   | 773   | 0.17   |
| WDC       | WD1200BEVS-00UST0  | 120 GB | 1       | 61    | 0     | 0.17   |
| WDC       | WD5000LPCX-21VHAT0 | 500 GB | 19      | 60    | 0     | 0.17   |
| HGST      | HTS545025A7E330    | 250 GB | 1       | 60    | 0     | 0.17   |
| Seagate   | ST9402115AS        | 40 GB  | 1       | 60    | 0     | 0.17   |
| Fujitsu   | MHV2100AH PL       | 100 GB | 1       | 423   | 6     | 0.17   |
| Hitachi   | DK23FB-60          | 60 GB  | 1       | 960   | 15    | 0.16   |
| WDC       | WD2500AAJS-98B4A0  | 250 GB | 1       | 540   | 8     | 0.16   |
| Seagate   | ST9320320AS        | 320 GB | 16      | 670   | 156   | 0.16   |
| WDC       | WD1600BEVT-60ZCT0  | 160 GB | 3       | 101   | 336   | 0.16   |
| Samsung   | HM120JI            | 120 GB | 4       | 323   | 5     | 0.16   |
| WDC       | WD3200LPVT-22G33T0 | 320 GB | 1       | 58    | 0     | 0.16   |
| MediaMax  | WL250GPA872B       | 250 GB | 1       | 58    | 0     | 0.16   |
| WDC       | WD1600AAJS-08L7A0  | 160 GB | 4       | 415   | 317   | 0.16   |
| Hitachi   | HTS543225L9SA00    | 250 GB | 3       | 685   | 51    | 0.16   |
| Seagate   | ST9250311CS        | 250 GB | 1       | 2074  | 35    | 0.16   |
| Toshiba   | MK1059GSM          | 1 TB   | 15      | 303   | 1041  | 0.16   |
| WDC       | WD10EZEX-08WN4A0   | 1 TB   | 27      | 57    | 0     | 0.16   |
| Seagate   | ST1000LM014-1EJ... | 1 TB   | 4       | 145   | 1     | 0.16   |
| Seagate   | ST96812AS          | 60 GB  | 3       | 224   | 283   | 0.16   |
| WDC       | WD5000AACS-00G8B0  | 500 GB | 2       | 509   | 8     | 0.16   |
| WDC       | WD3200BEKT-60F3T1  | 320 GB | 4       | 294   | 262   | 0.15   |
| Toshiba   | HDWD110            | 1 TB   | 36      | 63    | 12    | 0.15   |
| WDC       | WD5000LPVX-75V0TT0 | 500 GB | 13      | 55    | 0     | 0.15   |
| Maxtor    | 6V250F0            | 250 GB | 2       | 163   | 1     | 0.15   |
| WDC       | WD1500HLHX-01JJPV0 | 150 GB | 1       | 498   | 8     | 0.15   |
| WDC       | WD5000AVCS-632DY1  | 500 GB | 1       | 55    | 0     | 0.15   |
| WDC       | WD10EALX-229BA1    | 1 TB   | 1       | 493   | 8     | 0.15   |
| WDC       | WD10EZEX-35M2NA0   | 1 TB   | 1       | 54    | 0     | 0.15   |
| WDC       | WD360GD-00FLA2     | 37 GB  | 3       | 912   | 19    | 0.15   |
| WDC       | WD3200BEVT-00A23T0 | 320 GB | 2       | 133   | 13    | 0.15   |
| WDC       | WD5000AZLX-22JKKA0 | 500 GB | 3       | 53    | 0     | 0.15   |
| Hitachi   | HDT725032VLAT80    | 320 GB | 3       | 1450  | 89    | 0.15   |
| Toshiba   | HDWD120            | 2 TB   | 7       | 53    | 0     | 0.15   |
| Seagate   | ST500LM021-1KJ152  | 500 GB | 28      | 80    | 96    | 0.15   |
| IBM/Hi... | IC25N030ATCS04-0   | 30 GB  | 1       | 52    | 0     | 0.14   |
| Seagate   | ST2000LX001-1RG174 | 2 TB   | 1       | 52    | 0     | 0.14   |
| WDC       | WD2500BEVT-22ZAT0  | 250 GB | 1       | 316   | 5     | 0.14   |
| WDC       | WD3200BEVT-11ZCT0  | 320 GB | 2       | 60    | 1     | 0.14   |
| Hitachi   | HTS722010K9SA00    | 100 GB | 1       | 468   | 8     | 0.14   |
| Fujitsu   | MJA2250BH G2       | 250 GB | 5       | 237   | 209   | 0.14   |
| WDC       | WD5000LPVX-16V0TT3 | 500 GB | 1       | 51    | 0     | 0.14   |
| WDC       | WD3200BEVT-60ZCT0  | 320 GB | 5       | 269   | 24    | 0.14   |
| WDC       | WD2500AAKS-00F0A0  | 250 GB | 3       | 538   | 10    | 0.14   |
| WDC       | WD1600AAJB-56R1A0  | 160 GB | 2       | 152   | 4     | 0.14   |
| Seagate   | ST96023AS          | 60 GB  | 1       | 554   | 10    | 0.14   |
| Fujitsu   | MHV2080BH          | 78 GB  | 1       | 400   | 7     | 0.14   |
| WDC       | WD20EZRZ-00Z5HB0   | 2 TB   | 6       | 49    | 0     | 0.14   |
| Hitachi   | HTS545050B9SA00    | 500 GB | 5       | 944   | 808   | 0.14   |
| Toshiba   | MK3265GSXF         | 320 GB | 3       | 155   | 5     | 0.14   |
| WDC       | WD1600BEKT-60V5T1  | 160 GB | 2       | 145   | 1     | 0.13   |
| WDC       | WD10JUCT-61CYNY0   | 1 TB   | 1       | 48    | 0     | 0.13   |
| WDC       | WD600UE-22KVT0     | 60 GB  | 1       | 243   | 4     | 0.13   |
| WDC       | WD10JPLX-00MBPT0   | 1 TB   | 7       | 56    | 9     | 0.13   |
| Seagate   | ST4000VM000-2AF166 | 4 TB   | 1       | 47    | 0     | 0.13   |
| Samsung   | SP1203N            | 120 GB | 6       | 485   | 31    | 0.13   |
| WDC       | WD5000AAKX-753CA1  | 500 GB | 3       | 564   | 26    | 0.13   |
| Hitachi   | HTS421210H9AT00    | 100 GB | 1       | 568   | 11    | 0.13   |
| WDC       | WD7500AACS-00D6B1  | 750 GB | 1       | 423   | 8     | 0.13   |
| Fujitsu   | MHV2080BH PL       | 80 GB  | 6       | 215   | 7     | 0.13   |
| WDC       | WD10EZRZ-00HTKB0   | 1 TB   | 13      | 46    | 0     | 0.13   |
| HGST      | HTS541010A7E630    | 1 TB   | 8       | 62    | 1     | 0.13   |
| WDC       | WD1200BEVS-07LAT0  | 120 GB | 3       | 391   | 164   | 0.13   |
| Samsung   | SP1213C            | 120 GB | 4       | 750   | 54    | 0.13   |
| WDC       | WD1600BB-00GUC0    | 160 GB | 3       | 761   | 81    | 0.13   |
| Hitachi   | HTS542512K9A300    | 120 GB | 3       | 364   | 6     | 0.13   |
| Toshiba   | MK2046GSX          | 200 GB | 7       | 418   | 25    | 0.12   |
| Samsung   | SV4012H            | 40 GB  | 2       | 1504  | 236   | 0.12   |
| WDC       | WD10EZEX-22MFCA0   | 1 TB   | 10      | 51    | 1     | 0.12   |
| WDC       | WD3200AAJS-00V4A0  | 320 GB | 3       | 396   | 9     | 0.12   |
| Toshiba   | MK3265GSX H        | 320 GB | 1       | 45    | 0     | 0.12   |
| WDC       | WD10EFRX-68FYTN0   | 1 TB   | 9       | 65    | 1     | 0.12   |
| WDC       | WD6001FSYZ-01SS7B1 | 6 TB   | 1       | 44    | 0     | 0.12   |
| ExcelStor | J880S              | 82 GB  | 1       | 44    | 0     | 0.12   |
| Toshiba   | MK6008GAH          | 60 GB  | 2       | 399   | 8     | 0.12   |
| Toshiba   | MK1652GSX          | 160 GB | 8       | 294   | 39    | 0.12   |
| WDC       | WD1003FZEX-00K3CA0 | 1 TB   | 5       | 44    | 0     | 0.12   |
| Hitachi   | HDP725025GLAT80    | 250 GB | 1       | 216   | 4     | 0.12   |
| Toshiba   | MK3276GSX H        | 320 GB | 1       | 43    | 0     | 0.12   |
| Seagate   | ST31500341AS       | 1.5 TB | 43      | 733   | 270   | 0.12   |
| Toshiba   | MK3275GSX          | 320 GB | 6       | 128   | 8     | 0.12   |
| WDC       | WD1503FYYS-02W0B0  | 1.5 TB | 1       | 382   | 8     | 0.12   |
| Hitachi   | IC25N060ATMR04-0   | 60 GB  | 5       | 215   | 10    | 0.11   |
| Seagate   | ST1000DX002-2DV162 | 1 TB   | 2       | 41    | 0     | 0.11   |
| WDC       | WD5000LPCX-24VHAT0 | 500 GB | 19      | 42    | 59    | 0.11   |
| Seagate   | ST3750330AS        | 750 GB | 8       | 713   | 295   | 0.11   |
| Hitachi   | HTS543232L9SA00    | 320 GB | 5       | 389   | 182   | 0.11   |
| Maxtor    | 7L250R0            | 251 GB | 1       | 40    | 0     | 0.11   |
| Fujitsu   | MHV2200BT PL       | 200 GB | 1       | 325   | 7     | 0.11   |
| WDC       | WD1600BEVE-00UYT0  | 160 GB | 1       | 40    | 0     | 0.11   |
| WDC       | WD3200LPVT-00G33T0 | 320 GB | 2       | 40    | 0     | 0.11   |
| Maxtor    | 6Y120M0            | 122 GB | 1       | 40    | 0     | 0.11   |
| WDC       | WD30EZRX-00AZ6B0   | 3 TB   | 1       | 40    | 0     | 0.11   |
| WDC       | WD6400AAKS-55A7B2  | 640 GB | 1       | 361   | 8     | 0.11   |
| WDC       | WD10EZEX-60WN4A0   | 1 TB   | 9       | 46    | 79    | 0.11   |
| WDC       | WD1600BEKT-60A25T1 | 160 GB | 1       | 79    | 1     | 0.11   |
| Toshiba   | MK5055GSX          | 500 GB | 6       | 546   | 111   | 0.11   |
| Hitachi   | HTS545012B9SA00    | 120 GB | 1       | 197   | 4     | 0.11   |
| WDC       | WD3200AAKX-32ERMA0 | 320 GB | 1       | 39    | 0     | 0.11   |
| WDC       | WD2000JS-22NCB1    | 200 GB | 1       | 1921  | 48    | 0.11   |
| WDC       | WD5000AVCS-612DY1  | 500 GB | 1       | 582   | 14    | 0.11   |
| Toshiba   | MK1252GSX          | 120 GB | 6       | 332   | 128   | 0.11   |
| Hitachi   | HTS421280H9AT00    | 80 GB  | 2       | 776   | 30    | 0.11   |
| Seagate   | ST2000DX002-2DV164 | 2 TB   | 2       | 38    | 0     | 0.11   |
| Samsung   | HM100JC            | 100 GB | 1       | 383   | 9     | 0.10   |
| Samsung   | SP1213N            | 120 GB | 2       | 1093  | 515   | 0.10   |
| WDC       | WD1500ADFD-00NLR5  | 150 GB | 1       | 344   | 8     | 0.10   |
| Seagate   | ST500VT000-1DK142  | 500 GB | 1       | 38    | 0     | 0.10   |
| Hitachi   | HTS541020G9SA00    | 20 GB  | 1       | 38    | 0     | 0.10   |
| WDC       | WD15EADS-22P8B0    | 1.5 TB | 1       | 339   | 8     | 0.10   |
| WDC       | WD3200BEVS-16VAT0  | 320 GB | 1       | 37    | 0     | 0.10   |
| HGST      | HTS541515A9E630    | 1.5 TB | 2       | 541   | 14    | 0.10   |
| WDC       | WD1002FBYS-18W8B0  | 1 TB   | 1       | 36    | 0     | 0.10   |
| WDC       | WD5000BEVT-80A0RT1 | 500 GB | 2       | 284   | 7     | 0.10   |
| Hitachi   | HTS543212L9A300    | 120 GB | 2       | 232   | 72    | 0.10   |
| WDC       | WD5000LPLX-00ZNTT0 | 500 GB | 15      | 35    | 0     | 0.10   |
| WDC       | WD2500AAJS-75B4A0  | 250 GB | 2       | 348   | 9     | 0.10   |
| Maxtor    | 6L120P0            | 122 GB | 2       | 35    | 0     | 0.10   |
| Seagate   | ST3000DM008-2DM166 | 3 TB   | 3       | 35    | 0     | 0.10   |
| WDC       | WD30EZRS-00J99B0   | 3 TB   | 4       | 643   | 759   | 0.10   |
| WDC       | WD10SPZX-22Z10T0   | 1 TB   | 3       | 35    | 0     | 0.10   |
| Samsung   | HM160HC            | 160 GB | 4       | 233   | 17    | 0.10   |
| WDC       | WD2500BPVT-26JJ5T0 | 250 GB | 1       | 35    | 0     | 0.10   |
| Seagate   | ST980411ASG        | 80 GB  | 1       | 490   | 13    | 0.10   |
| Hitachi   | HTS725025A9A361... | 250 GB | 1       | 34    | 0     | 0.09   |
| WDC       | WD5000LPVX-08V0TT2 | 500 GB | 1       | 274   | 7     | 0.09   |
| Toshiba   | HDWD105            | 500 GB | 30      | 33    | 5     | 0.09   |
| WDC       | WD10EZEX-75WN4A0   | 1 TB   | 5       | 83    | 2     | 0.09   |
| Hitachi   | HDS722580VLAT20    | 82 GB  | 2       | 577   | 267   | 0.09   |
| Maxtor    | STM380211AS        | 80 GB  | 3       | 290   | 1165  | 0.09   |
| WDC       | WD5000BEKT-22KA9T0 | 500 GB | 1       | 302   | 8     | 0.09   |
| HGST      | HTS541050A9E680    | 500 GB | 3       | 33    | 0     | 0.09   |
| Seagate   | ST1000LM010-9YH146 | 1 TB   | 4       | 135   | 646   | 0.09   |
| WDC       | WD1600BB-55GUA0    | 160 GB | 1       | 668   | 19    | 0.09   |
| WDC       | WD2500AAJS-00YZCA0 | 250 GB | 1       | 33    | 0     | 0.09   |
| Seagate   | ST1000DM010-2EP102 | 1 TB   | 36      | 32    | 0     | 0.09   |
| Toshiba   | HDWM105            | 500 GB | 1       | 32    | 0     | 0.09   |
| Maxtor    | STM3320613AS       | 320 GB | 8       | 1132  | 157   | 0.09   |
| HGST      | HUS726020ALE614    | 2 TB   | 1       | 31    | 0     | 0.09   |
| WDC       | WD1600BEVS-00VAT0  | 160 GB | 1       | 31    | 0     | 0.09   |
| WDC       | WD800JB-00FSA0     | 80 GB  | 1       | 1366  | 43    | 0.09   |
| Maxtor    | 2F030J1            | 30 GB  | 1       | 185   | 5     | 0.08   |
| WDC       | WD2500JD-00HBC0    | 250 GB | 1       | 618   | 19    | 0.08   |
| WDC       | WD5000AAJS-00YFA0  | 500 GB | 2       | 469   | 81    | 0.08   |
| WDC       | WD2000JS-60NCB1    | 200 GB | 1       | 275   | 8     | 0.08   |
| Fujitsu   | MHV2060AT PL       | 60 GB  | 2       | 689   | 21    | 0.08   |
| WDC       | WD1600BEVT-00A23T0 | 160 GB | 2       | 111   | 5     | 0.08   |
| Seagate   | ST3320311CS        | 320 GB | 2       | 30    | 0     | 0.08   |
| Seagate   | ST38410A           | 8 GB   | 1       | 754   | 24    | 0.08   |
| WDC       | WD5000LPLX-22ZNTT0 | 500 GB | 1       | 30    | 0     | 0.08   |
| WDC       | WD2500AAJS-55M0A0  | 250 GB | 1       | 269   | 8     | 0.08   |
| Samsung   | SV0401N            | 40 GB  | 1       | 952   | 31    | 0.08   |
| Seagate   | ST750LM028-1KK162  | 750 GB | 1       | 29    | 0     | 0.08   |
| WDC       | WD1600JS-00MHB1    | 160 GB | 1       | 1060  | 35    | 0.08   |
| WDC       | WD5000AAKX-00KJ3A0 | 500 GB | 1       | 262   | 8     | 0.08   |
| Samsung   | MP0804H            | 80 GB  | 2       | 198   | 7     | 0.08   |
| WDC       | WD3200JB-00KFA0    | 320 GB | 1       | 29    | 0     | 0.08   |
| Maxtor    | 6L080M0            | 80 GB  | 3       | 28    | 0     | 0.08   |
| Hitachi   | HTS543212L9SA02    | 120 GB | 1       | 27    | 0     | 0.08   |
| MARSHAL   | MAL2500SA-T54      | 500 GB | 1       | 279   | 9     | 0.08   |
| Hitachi   | HTS541040G9SA00    | 40 GB  | 1       | 415   | 14    | 0.08   |
| Seagate   | ST3500320AS        | 500 GB | 49      | 803   | 558   | 0.07   |
| HGST      | HTS545050B7E660    | 500 GB | 7       | 26    | 0     | 0.07   |
| HGST      | HTS541010B7E610    | 1 TB   | 2       | 26    | 0     | 0.07   |
| WDC       | WD2000JD-55HBC0    | 200 GB | 1       | 26    | 0     | 0.07   |
| WDC       | WD3200AVVS-63L2B0  | 320 GB | 3       | 56    | 4     | 0.07   |
| WDC       | WD5000AZLX-21K2TA0 | 500 GB | 3       | 26    | 0     | 0.07   |
| Toshiba   | HDWJ110            | 1 TB   | 3       | 26    | 0     | 0.07   |
| WDC       | WD2502ABYS-02B7A0  | 251 GB | 1       | 316   | 11    | 0.07   |
| WDC       | WD3200AAJS-00VWA1  | 320 GB | 1       | 708   | 26    | 0.07   |
| Hitachi   | HTS548040M9AT00    | 40 GB  | 1       | 470   | 17    | 0.07   |
| Seagate   | ST9250320AS        | 250 GB | 10      | 279   | 315   | 0.07   |
| Seagate   | ST2000LM015-2E8174 | 2 TB   | 2       | 25    | 0     | 0.07   |
| WDC       | WD15EADS-00S2B0    | 1.5 TB | 1       | 483   | 18    | 0.07   |
| Fujitsu   | MHT2080BH          | 80 GB  | 1       | 403   | 15    | 0.07   |
| Samsung   | HM320JI            | 320 GB | 3       | 324   | 10    | 0.07   |
| Toshiba   | MK5059GSX          | 500 GB | 1       | 932   | 36    | 0.07   |
| Toshiba   | MQ01ABD100M        | 1 TB   | 1       | 25    | 0     | 0.07   |
| WDC       | WD4003FZEX-00Z4SA0 | 4 TB   | 1       | 25    | 0     | 0.07   |
| Samsung   | HM251JI            | 250 GB | 5       | 349   | 624   | 0.07   |
| Seagate   | ST3320820SCE       | 320 GB | 1       | 24    | 0     | 0.07   |
| WDC       | WD6400BEVT-80A0RT1 | 640 GB | 1       | 664   | 26    | 0.07   |
| Hitachi   | HTS725032A9A360    | 320 GB | 1       | 24    | 0     | 0.07   |
| WDC       | WD2500AAJS-52B4A0  | 250 GB | 2       | 942   | 45    | 0.07   |
| Seagate   | ST3640323AS        | 640 GB | 5       | 1118  | 735   | 0.07   |
| WDC       | WD10SPCX-75KHST0   | 1 TB   | 1       | 24    | 0     | 0.07   |
| WDC       | WD5000AZLX-00JKKA0 | 500 GB | 2       | 23    | 0     | 0.07   |
| Hitachi   | HTS541616J9AT00    | 160 GB | 2       | 224   | 7     | 0.07   |
| WDC       | WD400VE-75HDT1     | 40 GB  | 1       | 23    | 0     | 0.06   |
| WDC       | WD800JD-32LSA0     | 80 GB  | 1       | 2499  | 105   | 0.06   |
| WDC       | WD30EZRX-00SPEB0   | 3 TB   | 1       | 23    | 0     | 0.06   |
| Samsung   | HD160HJ            | 160 GB | 13      | 552   | 732   | 0.06   |
| Apple     | HDD HTS547550A9... | 500 GB | 1       | 23    | 0     | 0.06   |
| Toshiba   | MK6032GAX          | 60 GB  | 1       | 23    | 0     | 0.06   |
| Seagate   | ST4000VX000-2AG166 | 4 TB   | 1       | 23    | 0     | 0.06   |
| Fujitsu   | MJA2320BH G2       | 320 GB | 3       | 737   | 694   | 0.06   |
| Toshiba   | MK6465GSXW         | 640 GB | 1       | 552   | 23    | 0.06   |
| Seagate   | ST1000VM002-1ET162 | 1 TB   | 1       | 23    | 0     | 0.06   |
| Toshiba   | MK2529GSG          | 250 GB | 2       | 313   | 1127  | 0.06   |
| Toshiba   | MQ01ABF050M        | 500 GB | 3       | 22    | 0     | 0.06   |
| WDC       | WD3200BEKX-22B7WT0 | 320 GB | 1       | 21    | 0     | 0.06   |
| WDC       | WD10JPVX-60JC3T1   | 1 TB   | 5       | 21    | 0     | 0.06   |
| Maxtor    | 6L200P0            | 203 GB | 1       | 21    | 0     | 0.06   |
| WDC       | WD5000LPCX-75VHAT0 | 500 GB | 6       | 21    | 0     | 0.06   |
| Seagate   | ST3300831A         | 300 GB | 1       | 347   | 15    | 0.06   |
| Seagate   | ST3250824SCE       | 250 GB | 1       | 21    | 0     | 0.06   |
| Hitachi   | HTS722016K9A300    | 160 GB | 1       | 236   | 10    | 0.06   |
| WDC       | WD5000AVDS-73U7B1  | 500 GB | 2       | 189   | 7     | 0.06   |
| Samsung   | HM160HI            | 160 GB | 38      | 306   | 250   | 0.06   |
| Samsung   | HD103UI            | 1 TB   | 1       | 385   | 17    | 0.06   |
| Toshiba   | MK1656GSY          | 160 GB | 1       | 379   | 17    | 0.06   |
| Hitachi   | HTS721060G9SA00    | 60 GB  | 2       | 335   | 17    | 0.06   |
| Maxtor    | STM3160613AS       | 160 GB | 1       | 41    | 1     | 0.06   |
| WDC       | WD400BB-22DEA0     | 40 GB  | 1       | 831   | 39    | 0.06   |
| Maxtor    | 6B200M0            | 200 GB | 3       | 26    | 13    | 0.06   |
| WDC       | WD5000BPVT-75A1YT0 | 500 GB | 1       | 20    | 0     | 0.06   |
| WDC       | WD2500BPVT-00ZEST0 | 250 GB | 3       | 135   | 74    | 0.06   |
| Fujitsu   | MHZ2080BH G1       | 80 GB  | 1       | 20    | 0     | 0.06   |
| Maxtor    | STM3160813AS       | 160 GB | 3       | 745   | 370   | 0.06   |
| Toshiba   | MK5076GSX          | 500 GB | 21      | 56    | 216   | 0.05   |
| WDC       | WD5000LPCX-60VHAT0 | 500 GB | 6       | 66    | 1     | 0.05   |
| Seagate   | ST1000LM048-2E7172 | 1 TB   | 7       | 19    | 0     | 0.05   |
| Maxtor    | STM3500320AS       | 500 GB | 9       | 738   | 402   | 0.05   |
| Seagate   | ST3160215SCE       | 160 GB | 1       | 98    | 4     | 0.05   |
| Hitachi   | IC25N040ATMR04-0   | 40 GB  | 2       | 628   | 181   | 0.05   |
| WDC       | WD5000AZLX-08K2TA0 | 500 GB | 5       | 19    | 0     | 0.05   |
| Seagate   | ST9250610NS        | 250 GB | 2       | 19    | 0     | 0.05   |
| WDC       | WD200EB-75CPF0     | 20 GB  | 2       | 402   | 20    | 0.05   |
| Toshiba   | MK1032GAX          | 100 GB | 1       | 19    | 0     | 0.05   |
| WDC       | WD2000BB-00GUC0    | 200 GB | 1       | 594   | 30    | 0.05   |
| WDC       | WD1600JD-00GBB0    | 160 GB | 1       | 727   | 37    | 0.05   |
| HGST      | HTS541075A7E630    | 750 GB | 6       | 38    | 169   | 0.05   |
| WDC       | WD3200BPVT-00HXZT3 | 320 GB | 2       | 229   | 12    | 0.05   |
| Seagate   | ST31000340NS       | 1 TB   | 7       | 1003  | 468   | 0.05   |
| Samsung   | HM080HI            | 80 GB  | 2       | 473   | 405   | 0.05   |
| WDC       | WD2500BEVT-60A23T0 | 250 GB | 2       | 101   | 24    | 0.05   |
| Seagate   | ST31000340AS       | 1 TB   | 3       | 1146  | 386   | 0.05   |
| WDC       | WD5000LPVX-16V0TT0 | 500 GB | 1       | 71    | 3     | 0.05   |
| Quantum   | FIREBALLlct15 10   | 10 GB  | 1       | 105   | 5     | 0.05   |
| Samsung   | HM121HC            | 120 GB | 2       | 179   | 26    | 0.05   |
| WDC       | WD2500JS-75NCB1    | 250 GB | 1       | 2681  | 153   | 0.05   |
| WDC       | WD1600JS-55MHB0    | 160 GB | 1       | 761   | 43    | 0.05   |
| WDC       | WD5000AAKS-00V6A0  | 500 GB | 1       | 503   | 29    | 0.05   |
| Seagate   | ST3320310CS        | 320 GB | 3       | 576   | 32    | 0.05   |
| Samsung   | HN-M250MBB         | 250 GB | 1       | 292   | 17    | 0.04   |
| Maxtor    | 2F040L0            | 41 GB  | 3       | 25    | 2     | 0.04   |
| Seagate   | ST1000DX001-1NS162 | 1 TB   | 1       | 161   | 9     | 0.04   |
| WDC       | WD800BB-88JHC0     | 80 GB  | 1       | 1625  | 101   | 0.04   |
| Hitachi   | HDT721050SLA360    | 500 GB | 2       | 1336  | 95    | 0.04   |
| Hitachi   | HTS545025A7E380    | 250 GB | 1       | 15    | 0     | 0.04   |
| WDC       | WD5000LPLX-66ZNTT1 | 500 GB | 1       | 31    | 1     | 0.04   |
| Samsung   | SP1604N            | 80 GB  | 2       | 454   | 93    | 0.04   |
| Samsung   | SP1253N            | 120 GB | 1       | 286   | 18    | 0.04   |
| Maxtor    | 6L160M0            | 160 GB | 4       | 26    | 1     | 0.04   |
| Samsung   | SP1614C            | 160 GB | 2       | 124   | 22    | 0.04   |
| Hitachi   | HTS723225L9A360    | 250 GB | 3       | 322   | 1301  | 0.04   |
| Seagate   | ST31000333AS       | 1 TB   | 10      | 591   | 163   | 0.04   |
| WDC       | WD3200KS-00PFB0    | 320 GB | 1       | 1354  | 92    | 0.04   |
| Toshiba   | MK6034GSX          | 60 GB  | 2       | 376   | 29    | 0.04   |
| WDC       | WD10SPCX-21KHST0   | 1 TB   | 1       | 14    | 0     | 0.04   |
| Seagate   | ST9120310AS        | 120 GB | 1       | 14    | 0     | 0.04   |
| WDC       | WD2500BEKX-00B7WT0 | 250 GB | 1       | 13    | 0     | 0.04   |
| WDC       | WD40EZRX-00SPEB0   | 4 TB   | 2       | 141   | 10    | 0.04   |
| Seagate   | ST91000640NS       | 1 TB   | 1       | 13    | 0     | 0.04   |
| Seagate   | ST500DM002-1SB10A  | 500 GB | 14      | 17    | 1     | 0.04   |
| Seagate   | ST310212A          | 10 GB  | 1       | 380   | 27    | 0.04   |
| WDC       | WD5000AADS-98S9B1  | 500 GB | 1       | 120   | 8     | 0.04   |
| Hitachi   | HTS543232L9SA02    | 320 GB | 1       | 989   | 74    | 0.04   |
| Fujitsu   | MHV2120BH PL       | 120 GB | 6       | 38    | 3     | 0.03   |
| WDC       | WD3200AAJS-00RYA0  | 320 GB | 2       | 1320  | 143   | 0.03   |
| Fujitsu   | MPG3204AT E        | 20 GB  | 1       | 138   | 10    | 0.03   |
| Seagate   | ST3250412CS        | 250 GB | 1       | 12    | 0     | 0.03   |
| Toshiba   | MK2565GSXV         | 250 GB | 2       | 275   | 34    | 0.03   |
| WDC       | WD2500JS-75NCB3    | 250 GB | 1       | 1194  | 98    | 0.03   |
| WDC       | WD7500LPCX-22HWST0 | 750 GB | 1       | 129   | 10    | 0.03   |
| WDC       | WD2500AAJS-60M0A0  | 250 GB | 2       | 705   | 533   | 0.03   |
| IBM/Hi... | IC35L060AVV207-0   | 40 GB  | 1       | 325   | 27    | 0.03   |
| Maxtor    | 2F030J0            | 30 GB  | 2       | 33    | 2     | 0.03   |
| Hitachi   | HDS722525VLAT80    | 250 GB | 1       | 11    | 0     | 0.03   |
| Toshiba   | HDWM110            | 1 TB   | 2       | 11    | 0     | 0.03   |
| Maxtor    | STM3320820A        | 320 GB | 1       | 11    | 0     | 0.03   |
| Seagate   | STM31000528AS      | 1 TB   | 2       | 10    | 0     | 0.03   |
| Hitachi   | HTS541660J9SA00    | 60 GB  | 2       | 112   | 12    | 0.03   |
| Maxtor    | 6E040L0            | 40 GB  | 6       | 34    | 29    | 0.03   |
| WDC       | WD7500BPVT-60HXZT1 | 750 GB | 2       | 815   | 84    | 0.03   |
| WDC       | WD1002FBYS-43P1B0  | 1 TB   | 1       | 783   | 77    | 0.03   |
| Samsung   | HM160JI            | 160 GB | 1       | 739   | 76    | 0.03   |
| Seagate   | ST9808210A         | 80 GB  | 1       | 344   | 37    | 0.02   |
| WDC       | WD3200AAJS-40VWA1  | 320 GB | 1       | 375   | 41    | 0.02   |
| Maxtor    | 6E030L0            | 30 GB  | 4       | 17    | 1     | 0.02   |
| WDC       | WD10EZRX-00A3KB0   | 1 TB   | 1       | 8     | 0     | 0.02   |
| WDC       | WD2500AVJS-63B6A0  | 250 GB | 1       | 77    | 8     | 0.02   |
| WDC       | WD2500JS-60MHB1    | 250 GB | 1       | 124   | 14    | 0.02   |
| Toshiba   | MK7559GSXF         | 750 GB | 1       | 8     | 0     | 0.02   |
| Seagate   | ST4000DM004-2CV104 | 4 TB   | 2       | 8     | 0     | 0.02   |
| Maxtor    | 6Y120L0            | 122 GB | 6       | 29    | 16    | 0.02   |
| Hitachi   | HTS548080M9AT00    | 80 GB  | 1       | 136   | 16    | 0.02   |
| ExcelStor | J9250              | 250 GB | 1       | 1348  | 167   | 0.02   |
| Seagate   | ST9320421AS        | 320 GB | 2       | 709   | 98    | 0.02   |
| Toshiba   | MK5061GSYN         | 500 GB | 5       | 219   | 77    | 0.02   |
| Maxtor    | 6Y060L2            | 61 GB  | 1       | 542   | 71    | 0.02   |
| Maxtor    | 6K040L0            | 41 GB  | 1       | 29    | 3     | 0.02   |
| Seagate   | ST1000LM035-1RK172 | 1 TB   | 15      | 7     | 0     | 0.02   |
| Maxtor    | 6L160P0            | 163 GB | 1       | 29    | 3     | 0.02   |
| Seagate   | ST500DM009-2F110A  | 500 GB | 3       | 20    | 10    | 0.02   |
| WDC       | WD2000JS-00NCB1    | 200 GB | 1       | 537   | 73    | 0.02   |
| WDC       | WD3200BEKT-75PVMT0 | 320 GB | 1       | 208   | 28    | 0.02   |
| WDC       | WD5000LPLX-60ZNTT1 | 500 GB | 3       | 7     | 1     | 0.02   |
| HP        | GB0250C8045        | 250 GB | 1       | 1405  | 198   | 0.02   |
| WDC       | WD2500AAJS-41RYA0  | 250 GB | 1       | 76    | 10    | 0.02   |
| Maxtor    | 6B250S0            | 250 GB | 1       | 6     | 0     | 0.02   |
| WDC       | WD5000LPCX-08VHA   | 500 GB | 5       | 6     | 0     | 0.02   |
| WDC       | WD360ADFD-00NLR4   | 37 GB  | 1       | 499   | 77    | 0.02   |
| Seagate   | ST9160821A         | 160 GB | 1       | 182   | 28    | 0.02   |
| Toshiba   | MQ01ACF032         | 320 GB | 1       | 6     | 0     | 0.02   |
| Seagate   | ST500LM030-2E717D  | 500 GB | 4       | 6     | 0     | 0.02   |
| Maxtor    | 6L120M0            | 122 GB | 1       | 43    | 6     | 0.02   |
| WDC       | WD20NPVT-00Z2TT0   | 2 TB   | 1       | 171   | 27    | 0.02   |
| Samsung   | HM121HI            | 120 GB | 5       | 367   | 1365  | 0.02   |
| Maxtor    | 6L080P0            | 81 GB  | 2       | 10    | 10    | 0.02   |
| MediaMax  | WL250GLSA6410000   | 250 GB | 2       | 17    | 4     | 0.02   |
| WDC       | WD10TMVW-11ZSMS5   | 1 TB   | 1       | 59    | 9     | 0.02   |
| Samsung   | HM120JC            | 120 GB | 1       | 605   | 102   | 0.02   |
| Hitachi   | HTS541612J9AT00    | 120 GB | 1       | 116   | 19    | 0.02   |
| Seagate   | ST3500320SV        | 500 GB | 1       | 45    | 7     | 0.02   |
| Samsung   | SV0412H            | 40 GB  | 3       | 733   | 124   | 0.02   |
| Seagate   | ST3000VX010-2E3166 | 3 TB   | 1       | 5     | 0     | 0.01   |
| Toshiba   | MQ02ABF050H-SSH... | 500 GB | 1       | 5     | 0     | 0.01   |
| WDC       | WD15EARS-22MVWB0   | 1.5 TB | 3       | 818   | 514   | 0.01   |
| WDC       | WD1200AAJS-00VTA0  | 120 GB | 1       | 995   | 203   | 0.01   |
| Maxtor    | 6Y080M0            | 80 GB  | 6       | 30    | 38    | 0.01   |
| Hitachi   | HTE721060G9AT00    | 60 GB  | 1       | 4     | 0     | 0.01   |
| Seagate   | ST320LT012-9WS14C  | 320 GB | 39      | 201   | 967   | 0.01   |
| Fujitsu   | MHZ2160BJ G1       | 160 GB | 1       | 4     | 0     | 0.01   |
| Seagate   | ST3500820AS        | 500 GB | 2       | 268   | 56    | 0.01   |
| Seagate   | ST500LT012-9WS142  | 500 GB | 111     | 256   | 1031  | 0.01   |
| Maxtor    | 6Y120P0            | 122 GB | 2       | 23    | 8     | 0.01   |
| WDC       | WD800JD-55JRC0     | 80 GB  | 1       | 243   | 62    | 0.01   |
| Samsung   | HM500LI            | 500 GB | 1       | 7     | 1     | 0.01   |
| Maxtor    | 6Y200P0            | 203 GB | 1       | 30    | 7     | 0.01   |
| WDC       | WD2500BEKT-66F3T2  | 250 GB | 1       | 193   | 50    | 0.01   |
| WDC       | WD3200BEVT-75ZCT0  | 320 GB | 1       | 630   | 167   | 0.01   |
| Seagate   | ST3250310SV        | 250 GB | 1       | 287   | 79    | 0.01   |
| WDC       | WD10JPVX-08JC3T6   | 1 TB   | 1       | 3     | 0     | 0.01   |
| WDC       | WD5000AVJS-63TRA0  | 500 GB | 1       | 2013  | 578   | 0.01   |
| Hitachi   | HTS541640J9AT00    | 40 GB  | 1       | 283   | 82    | 0.01   |
| WDC       | WD10EADS-00R6B0    | 1 TB   | 1       | 1856  | 560   | 0.01   |
| Toshiba   | MK5056GSY          | 500 GB | 1       | 3     | 0     | 0.01   |
| Apple     | HDD HTS547575A9... | 750 GB | 1       | 506   | 153   | 0.01   |
| IBM/Hi... | IC35L060AVER07-0   | 61 GB  | 1       | 997   | 304   | 0.01   |
| Maxtor    | 2F020J0            | 20 GB  | 1       | 41    | 12    | 0.01   |
| WDC       | WD5002AALX-32Z3A0  | 500 GB | 1       | 3     | 0     | 0.01   |
| Maxtor    | 6E020L0            | 20 GB  | 1       | 22    | 6     | 0.01   |
| Seagate   | ST3500620AS        | 500 GB | 2       | 429   | 996   | 0.01   |
| WDC       | WD2004FBYZ-01YCBB0 | 2 TB   | 1       | 12    | 3     | 0.01   |
| WDC       | WD1600BEVS-22UST0  | 160 GB | 1       | 585   | 189   | 0.01   |
| Maxtor    | 6B160M0            | 163 GB | 1       | 3     | 0     | 0.01   |
| WDC       | WD2004FBYZ-01YCBB1 | 2 TB   | 1       | 2     | 0     | 0.01   |
| Seagate   | ST1000VM002-1SD102 | 1 TB   | 1       | 2     | 0     | 0.01   |
| Hitachi   | HTS722080K9A300    | 80 GB  | 1       | 2     | 0     | 0.01   |
| WDC       | WD40PURX-64NZ6Y0   | 4 TB   | 1       | 2     | 0     | 0.01   |
| Maxtor    | 6Y160P0            | 163 GB | 2       | 23    | 11    | 0.01   |
| Maxtor    | 6L080L0            | 81 GB  | 1       | 19    | 6     | 0.01   |
| Toshiba   | MK2556GSY          | 250 GB | 2       | 3     | 1     | 0.01   |
| Seagate   | ST500LM020-1G1162  | 500 GB | 3       | 2     | 0     | 0.01   |
| Toshiba   | MK8052GSX          | 80 GB  | 1       | 208   | 79    | 0.01   |
| Maxtor    | 7L250S0            | 250 GB | 1       | 7     | 2     | 0.01   |
| Samsung   | SV0802N            | 80 GB  | 1       | 554   | 215   | 0.01   |
| WDC       | WD5000LPLX-21ZNTT0 | 500 GB | 2       | 2     | 0     | 0.01   |
| Seagate   | ST1000VX005-2EZ102 | 1 TB   | 1       | 2     | 0     | 0.01   |
| Maxtor    | 6Y080P0            | 81 GB  | 6       | 14    | 7     | 0.01   |
| WDC       | WD3200AADS-00S9B0  | 320 GB | 1       | 26    | 10    | 0.01   |
| Toshiba   | MK6459GSX          | 640 GB | 4       | 481   | 839   | 0.01   |
| Toshiba   | MK3259GSX          | 320 GB | 1       | 192   | 82    | 0.01   |
| Toshiba   | MK5065GSXN         | 500 GB | 3       | 445   | 759   | 0.01   |
| Toshiba   | MK3276GSX          | 320 GB | 11      | 3     | 103   | 0.01   |
| Toshiba   | MK6476GSX          | 640 GB | 10      | 5     | 201   | 0.01   |
| WDC       | WD2500BEVT-35ZCT0  | 250 GB | 1       | 949   | 450   | 0.01   |
| Toshiba   | MK3261GSYN         | 320 GB | 4       | 7     | 182   | 0.01   |
| Maxtor    | 4D040H2            | 40 GB  | 2       | 27    | 328   | 0.01   |
| Hitachi   | HDS722516VLAT20    | 164 GB | 1       | 2242  | 1102  | 0.01   |
| WDC       | WD10EURX-63UHWY0   | 1 TB   | 1       | 644   | 338   | 0.01   |
| WDC       | WD4000AAKS-22TMA0  | 400 GB | 1       | 820   | 431   | 0.01   |
| WDC       | WD10TPVT-00U4RT1   | 1 TB   | 1       | 852   | 463   | 0.01   |
| Toshiba   | MQ02ABF100         | 1 TB   | 1       | 1     | 0     | 0.01   |
| WDC       | WD20EARS-19MVWB0   | 2 TB   | 1       | 713   | 392   | 0.00   |
| Toshiba   | MK2533GSG          | 250 GB | 1       | 1671  | 948   | 0.00   |
| Hitachi   | HTS723216L9A360    | 160 GB | 3       | 454   | 1491  | 0.00   |
| Hitachi   | HUA5C3020ALA640    | 2 TB   | 1       | 1045  | 595   | 0.00   |
| CLOVER    | CD155UI            | 1.5 TB | 1       | 1     | 0     | 0.00   |
| Maxtor    | 6L250S0            | 250 GB | 1       | 39    | 23    | 0.00   |
| Seagate   | ST3750630AS        | 750 GB | 1       | 1122  | 686   | 0.00   |
| WDC       | WD3200BEVT-26A23T0 | 320 GB | 1       | 352   | 218   | 0.00   |
| WDC       | WD5003ABYZ-011FA0  | 500 GB | 2       | 13    | 4     | 0.00   |
| WDC       | WD2500JS-58NCB1    | 250 GB | 1       | 900   | 615   | 0.00   |
| Seagate   | ST500VT000-1BS142  | 500 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WD20EZRZ-60Z5HB0   | 2 TB   | 1       | 1     | 0     | 0.00   |
| WDC       | WD2500JD-98GBB0    | 250 GB | 1       | 875   | 628   | 0.00   |
| Maxtor    | 4R060J0            | 61 GB  | 1       | 22    | 16    | 0.00   |
| Fujitsu   | MHZ2320BH G2       | 320 GB | 5       | 489   | 543   | 0.00   |
| Maxtor    | 2B020H1            | 20 GB  | 5       | 20    | 89    | 0.00   |
| WDC       | WD3200LPCX-60VHAT0 | 320 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WD1200             | 120 GB | 1       | 11    | 8     | 0.00   |
| Samsung   | HD251KJ            | 250 GB | 1       | 1236  | 1019  | 0.00   |
| WDC       | WD30EZRS-11J99B1   | 3 TB   | 1       | 794   | 663   | 0.00   |
| WDC       | WD400BB-00CAA0     | 40 GB  | 1       | 194   | 163   | 0.00   |
| WDC       | WD800UE-22HCT0     | 80 GB  | 1       | 436   | 395   | 0.00   |
| Toshiba   | MK5061GSY          | 500 GB | 1       | 1     | 0     | 0.00   |
| Maxtor    | 6Y080L0            | 80 GB  | 22      | 21    | 287   | 0.00   |
| WDC       | WD3200JS-63PDB1    | 320 GB | 1       | 343   | 342   | 0.00   |
| Maxtor    | 6Y160M0            | 160 GB | 3       | 12    | 184   | 0.00   |
| WDC       | WD2500AVVS-62L2B0  | 250 GB | 1       | 9     | 9     | 0.00   |
| Fujitsu   | MHV2160BT          | 160 GB | 1       | 483   | 535   | 0.00   |
| Maxtor    | STM3750330AS       | 750 GB | 1       | 995   | 1293  | 0.00   |
| Toshiba   | MK3256GSY          | 320 GB | 4       | 5     | 276   | 0.00   |
| MediaMax  | WL400GSA6454G      | 400 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD3200LPCX-22VHAT0 | 320 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD5000BPVX-00JC3T0 | 500 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD5000LPCX-75VHAT1 | 500 GB | 1       | 0     | 0     | 0.00   |
| Maxtor    | 6Y060L0            | 61 GB  | 3       | 19    | 76    | 0.00   |
| Seagate   | ST3320620SV        | 320 GB | 1       | 564   | 835   | 0.00   |
| Fujitsu   | MHZ2120BH G2       | 120 GB | 1       | 693   | 1028  | 0.00   |
| Hitachi   | DK23EA-40          | 40 GB  | 1       | 287   | 470   | 0.00   |
| WDC       | WD800AAJS-60PSA0   | 80 GB  | 1       | 614   | 1007  | 0.00   |
| Maxtor    | 4D060H3            | 60 GB  | 1       | 18    | 31    | 0.00   |
| WDC       | WD800JD-60LSA0     | 80 GB  | 1       | 437   | 783   | 0.00   |
| WDC       | WD6400BPVT-24HXZT1 | 640 GB | 1       | 560   | 1013  | 0.00   |
| Hitachi   | HUA722010CLA630    | 1 TB   | 1       | 0     | 0     | 0.00   |
| WDC       | WD15EARS-19MVWB0   | 1.5 TB | 1       | 696   | 1306  | 0.00   |
| Hitachi   | HTS723212L9A360    | 120 GB | 1       | 535   | 1012  | 0.00   |
| China     | OOS500G            | 500 GB | 1       | 453   | 1024  | 0.00   |
| WDC       | WD15EURS-63S48Y0   | 1.5 TB | 1       | 11    | 26    | 0.00   |
| Hitachi   | HTS725025A9A364    | 250 GB | 10      | 447   | 1148  | 0.00   |
| Toshiba   | MK8025GAS          | 80 GB  | 1       | 22    | 58    | 0.00   |
| HGST      | HUS722T1TALA604    | 1 TB   | 1       | 0     | 0     | 0.00   |
| Seagate   | ST3500321CS        | 500 GB | 1       | 48    | 137   | 0.00   |
| WDC       | WD3200L22X-00JVPT0 | 320 GB | 1       | 0     | 0     | 0.00   |
| Seagate   | ST980817AS         | 80 GB  | 1       | 310   | 1009  | 0.00   |
| Hitachi   | HTS723232L9A360    | 320 GB | 1       | 301   | 1020  | 0.00   |
| WDC       | WD5000LPLX-60ZNTT0 | 500 GB | 1       | 0     | 0     | 0.00   |
| Samsung   | SV2011H            | 20 GB  | 1       | 0     | 3     | 0.00   |
| WDC       | WD2500AAJS-55B4A0  | 250 GB | 1       | 476   | 2020  | 0.00   |
| Toshiba   | MQ01ABB200         | 2 TB   | 1       | 152   | 704   | 0.00   |
| Seagate   | ST250LT012-9WS141  | 250 GB | 3       | 217   | 1099  | 0.00   |
| Seagate   | ST9500424AS        | 500 GB | 1       | 200   | 1009  | 0.00   |
| Maxtor    | 7L300S0            | 300 GB | 1       | 5     | 33    | 0.00   |
| Seagate   | ST1000LX015-1U7172 | 1 TB   | 1       | 0     | 0     | 0.00   |
| Seagate   | ST3160316CS        | 159 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD3200BEKX-60B7WT0 | 320 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD5000LPLX-08ZNTT0 | 500 GB | 2       | 0     | 0     | 0.00   |
| Seagate   | ST980829A          | 80 GB  | 1       | 222   | 2022  | 0.00   |
| Toshiba   | MK1214GAH          | 120 GB | 1       | 44    | 417   | 0.00   |
| WDC       | WD10EZEX-00MFCA0   | 1 TB   | 1       | 0     | 0     | 0.00   |
| Fujitsu   | MHV2060BH PL       | 60 GB  | 2       | 0     | 4     | 0.00   |
| Seagate   | ST9320312AS        | 320 GB | 1       | 69    | 1193  | 0.00   |
| Hitachi   | HTS548060M9AT00    | 60 GB  | 1       | 35    | 655   | 0.00   |
| Maxtor    | 6L200S0            | 203 GB | 1       | 2     | 39    | 0.00   |
| CLOVER    | CN-M500MBB         | 500 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD60PURX-64T0ZY0   | 6 TB   | 1       | 0     | 0     | 0.00   |
| WDC       | WD60PURX-64T0ZY1   | 6 TB   | 1       | 0     | 0     | 0.00   |
| Toshiba   | MK1676GSX          | 160 GB | 1       | 20    | 893   | 0.00   |
| Maxtor    | 6L300S0            | 300 GB | 1       | 27    | 1774  | 0.00   |
| Seagate   | ST380020A          | 80 GB  | 1       | 2     | 225   | 0.00   |
| Hitachi   | HTS721060G9AT00    | 60 GB  | 1       | 0     | 37    | 0.00   |

HDD by Family
--------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

| MFG       | Family                 | Models | Samples | Days  | Err   | Rating |
|-----------|------------------------|--------|---------|-------|-------|--------|
| Samsung   | SpinPoint V20400       | 1      | 1       | 5713  | 0     | 15.65  |
| Seagate   | Barracuda ES+          | 1      | 1       | 1968  | 0     | 5.39   |
| WDC       | RE4-GP                 | 3      | 6       | 1733  | 1     | 4.22   |
| Hitachi   | CinemaStar 5K320       | 1      | 1       | 1281  | 0     | 3.51   |
| WDC       | Raptor X               | 1      | 1       | 1164  | 0     | 3.19   |
| Samsung   | SpinPoint              | 2      | 3       | 1164  | 3     | 3.04   |
| WDC       | RE2                    | 5      | 8       | 1282  | 70    | 2.84   |
| WDC       | RE2-GP                 | 1      | 1       | 989   | 0     | 2.71   |
| Hitachi   | Ultrastar 7K3000       | 3      | 13      | 903   | 0     | 2.47   |
| Hitachi   | Ultrastar A7K1000      | 3      | 5       | 1208  | 1     | 2.46   |
| Seagate   | Constellation.2        | 1      | 1       | 878   | 0     | 2.41   |
| Seagate   | U5                     | 2      | 2       | 875   | 0     | 2.40   |
| Quantum   | Fireball Plus AS       | 2      | 2       | 845   | 0     | 2.32   |
| WDC       | Red Pro                | 1      | 1       | 782   | 0     | 2.14   |
| HP        | Proliant HardDrive     | 5      | 5       | 1503  | 46    | 2.09   |
| WDC       | Caviar SE16            | 4      | 19      | 957   | 23    | 1.97   |
| Seagate   | Barracuda 7200.8       | 6      | 25      | 1053  | 118   | 1.96   |
| WDC       | Scorpio Blue EIDE      | 3      | 5       | 686   | 0     | 1.88   |
| WDC       | Raptor                 | 12     | 15      | 1181  | 11    | 1.83   |
| Hitachi   | Deskstar 7K80          | 6      | 45      | 872   | 8     | 1.82   |
| Hitachi   | Deskstar 7K2000        | 1      | 9       | 1034  | 9     | 1.78   |
| Toshiba   | 3.5" HDD DT01ABA..V    | 1      | 1       | 644   | 0     | 1.77   |
| Toshiba   | 2.5" HDD MK..32GSX     | 1      | 3       | 628   | 0     | 1.72   |
| Hitachi   | Deskstar 5K3000        | 3      | 11      | 665   | 30    | 1.69   |
| Hitachi   | Deskstar 7K1000        | 2      | 11      | 953   | 14    | 1.67   |
| Hitachi   | Deskstar 7K3000        | 4      | 29      | 721   | 37    | 1.66   |
| Hitachi   | Deskstar T7K250        | 5      | 21      | 1078  | 29    | 1.65   |
| Hitachi   | Deskstar T7K500        | 8      | 34      | 1065  | 39    | 1.64   |
| Samsung   | SpinPoint F4 EG (AF)   | 1      | 10      | 751   | 10    | 1.60   |
| WDC       | Caviar SE              | 118    | 330     | 842   | 26    | 1.60   |
| Hitachi   | CinemaStar 5K1000      | 2      | 2       | 569   | 0     | 1.56   |
| Seagate   | Constellation ES.2 ... | 1      | 4       | 553   | 0     | 1.52   |
| Seagate   | Barracuda ES           | 5      | 26      | 976   | 386   | 1.51   |
| MediaMax  | WL1000                 | 1      | 1       | 543   | 0     | 1.49   |
| WDC       | Caviar Black           | 33     | 233     | 726   | 48    | 1.49   |
| WDC       | RE3                    | 12     | 31      | 823   | 6     | 1.47   |
| Seagate   | Momentus               | 4      | 6       | 646   | 194   | 1.46   |
| WDC       | RE                     | 12     | 25      | 745   | 79    | 1.45   |
| Toshiba   | 2.5" HDD MK..59GSXP... | 1      | 3       | 506   | 0     | 1.39   |
| Seagate   | Barracuda 5400.1       | 1      | 3       | 763   | 45    | 1.38   |
| Hitachi   | Deskstar 5K1000        | 3      | 20      | 638   | 69    | 1.37   |
| Seagate   | Barracuda ATA V        | 2      | 2       | 1819  | 15    | 1.34   |
| WDC       | Elements / My Passport | 2      | 2       | 513   | 5     | 1.33   |
| Seagate   | U9                     | 2      | 4       | 485   | 0     | 1.33   |
| Samsung   | SpinPoint F3           | 4      | 125     | 653   | 35    | 1.33   |
| Seagate   | Barracuda Green (AF)   | 3      | 81      | 745   | 208   | 1.30   |
| Fujitsu   | MHW BH                 | 9      | 27      | 610   | 3     | 1.28   |
| Seagate   | Constellation ES.2     | 1      | 1       | 467   | 0     | 1.28   |
| Samsung   | SpinPoint VL40         | 1      | 1       | 2328  | 4     | 1.28   |
| Seagate   | SpinPoint M7E          | 2      | 9       | 486   | 2     | 1.27   |
| Seagate   | Barracuda 7200.10      | 27     | 786     | 787   | 287   | 1.24   |
| WDC       | Caviar                 | 50     | 103     | 744   | 38    | 1.23   |
| HGST      | Deskstar NAS           | 3      | 5       | 443   | 0     | 1.21   |
| Seagate   | Barracuda 7200.7 an... | 18     | 378     | 799   | 92    | 1.21   |
| Seagate   | Constellation ES (S... | 3      | 11      | 1015  | 83    | 1.20   |
| Seagate   | DB35.3                 | 6      | 11      | 559   | 211   | 1.19   |
| Hitachi   | Deskstar P7K500        | 8      | 103     | 858   | 82    | 1.17   |
| Toshiba   | 2.5" HDD MK..58GSX     | 1      | 1       | 425   | 0     | 1.16   |
| Hitachi   | Travelstar 5K500       | 1      | 1       | 834   | 1     | 1.14   |
| Hitachi   | Deskstar 7K1000.C      | 13     | 279     | 611   | 42    | 1.14   |
| WDC       | VelociRaptor           | 20     | 35      | 490   | 2     | 1.14   |
| Seagate   | SV35.5                 | 1      | 2       | 782   | 2     | 1.13   |
| WDC       | Caviar Green           | 105    | 761     | 660   | 69    | 1.11   |
| Samsung   | SpinPoint T133         | 5      | 14      | 742   | 249   | 1.10   |
| Hitachi   | Ultrastar A7K2000      | 4      | 9       | 464   | 7     | 1.07   |
| Seagate   | Barracuda 7200.9       | 27     | 323     | 726   | 387   | 1.07   |
| Samsung   | SpinPoint F2 EG        | 3      | 55      | 739   | 217   | 1.07   |
| Seagate   | Pipeline HD Mini       | 3      | 6       | 962   | 289   | 1.07   |
| Samsung   | SpinPoint F1 DT        | 11     | 137     | 758   | 211   | 1.05   |
| Seagate   | Barracuda 7200.7       | 1      | 2       | 1049  | 105   | 1.04   |
| Samsung   | SpinPoint F3 EG        | 3      | 20      | 602   | 207   | 1.03   |
| Seagate   | Video 3.5 HDD          | 7      | 12      | 428   | 1     | 1.03   |
| Maxtor    | MaXLine III (SATA/300) | 1      | 1       | 738   | 1     | 1.01   |
| Seagate   | Constellation CS       | 2      | 6       | 367   | 0     | 1.01   |
| Seagate   | Barracuda 7200.12      | 14     | 788     | 647   | 163   | 1.00   |
| WDC       | Caviar Blue            | 255    | 1666    | 562   | 46    | 0.99   |
| Hitachi   | Deskstar 7K160         | 6      | 98      | 810   | 121   | 0.99   |
| Toshiba   | 2.5" HDD MK..61GSY     | 1      | 1       | 354   | 0     | 0.97   |
| WDC       | Green                  | 1      | 1       | 1049  | 2     | 0.96   |
| Hitachi   | CinemaStar P7K500      | 1      | 2       | 1006  | 2     | 0.96   |
| WDC       | Caviar Blue EIDE       | 16     | 69      | 651   | 76    | 0.94   |
| Hitachi   | Deskstar 7K1000.B      | 10     | 61      | 735   | 50    | 0.92   |
| Hitachi   | Deskstar 7K500         | 1      | 1       | 1941  | 5     | 0.89   |
| Hitachi   | Travelstar Z7K500      | 1      | 5       | 419   | 1017  | 0.89   |
| Seagate   | Barracuda SpinPoint F3 | 2      | 33      | 429   | 3     | 0.88   |
| HGST      | Ultrastar 7K4000       | 2      | 7       | 313   | 0     | 0.86   |
| ExcelStor | Jupiter                | 6      | 9       | 710   | 21    | 0.85   |
| Seagate   | Barracuda ATA IV       | 4      | 34      | 646   | 25    | 0.85   |
| Seagate   | Constellation ES.3     | 4      | 22      | 354   | 47    | 0.84   |
| Seagate   | Barracuda              | 1      | 5       | 304   | 0     | 0.83   |
| WDC       | Scorpio                | 1      | 1       | 300   | 0     | 0.82   |
| Fujitsu   | MHY BH                 | 4      | 32      | 533   | 212   | 0.82   |
| Samsung   | SpinPoint P80 SD       | 7      | 145     | 815   | 375   | 0.82   |
| Samsung   | SpinPoint M7E (AF)     | 4      | 67      | 423   | 49    | 0.81   |
| Maxtor    | DiamondMax 21          | 14     | 114     | 602   | 405   | 0.81   |
| Seagate   | SpinPoint M9T          | 2      | 11      | 292   | 0     | 0.80   |
| Maxtor    | DiamondMax D540X-4K    | 2      | 2       | 724   | 7     | 0.80   |
| WDC       | AV-GP                  | 22     | 40      | 385   | 63    | 0.80   |
| IBM/Hi... | Deskstar 120GXP        | 2      | 5       | 657   | 3     | 0.80   |
| Seagate   | Barracuda LP           | 4      | 46      | 839   | 456   | 0.79   |
| Fujitsu   | MHW BJ                 | 2      | 2       | 289   | 0     | 0.79   |
| Hitachi   | Travelstar 7K200       | 5      | 9       | 574   | 119   | 0.79   |
| Seagate   | NAS HDD                | 4      | 5       | 284   | 0     | 0.78   |
| Fujitsu   | MHZ BH                 | 9      | 47      | 495   | 324   | 0.78   |
| Fujitsu   | MHX BT                 | 2      | 5       | 619   | 30    | 0.77   |
| WDC       | Scorpio Black          | 38     | 98      | 379   | 74    | 0.76   |
| Maxtor    | DiamondMax 10 (SATA... | 5      | 19      | 555   | 103   | 0.75   |
| Seagate   | Barracuda ES.2         | 4      | 19      | 885   | 405   | 0.75   |
| WDC       | Scorpio Blue           | 175    | 1215    | 395   | 49    | 0.74   |
| WDC       | Red                    | 10     | 87      | 313   | 13    | 0.73   |
| Toshiba   | 3.5" HDD E300          | 2      | 2       | 265   | 0     | 0.73   |
| WDC       | RE4                    | 10     | 42      | 459   | 3     | 0.72   |
| Seagate   | SV35                   | 13     | 61      | 310   | 51    | 0.71   |
| IBM/Hi... | Deskstar GXP-180       | 4      | 5       | 603   | 7     | 0.70   |
| Samsung   | SpinPoint T166         | 7      | 95      | 744   | 436   | 0.70   |
| Toshiba   | 3.5" MD04ACA Enterp... | 1      | 1       | 253   | 0     | 0.69   |
| HP        | 250GB SATA disk VB0... | 1      | 2       | 252   | 0     | 0.69   |
| Hitachi   | Travelstar 5K1000      | 3      | 13      | 374   | 478   | 0.69   |
| Fujitsu   | MHV                    | 21     | 45      | 426   | 17    | 0.69   |
| Maxtor    | DiamondMax Plus D740X  | 1      | 2       | 463   | 3     | 0.69   |
| Seagate   | Momentus 7200.2        | 5      | 11      | 620   | 325   | 0.68   |
| Apple     | HGST Travelstar Z5K500 | 1      | 5       | 293   | 3     | 0.68   |
| Seagate   | Barracuda 7200.14 (AF) | 22     | 1015    | 345   | 96    | 0.68   |
| Hitachi   | Travelstar 7K320       | 9      | 15      | 466   | 695   | 0.68   |
| Hitachi   | Travelstar 5K500.B     | 11     | 238     | 462   | 161   | 0.67   |
| Samsung   | SpinPoint PL40         | 1      | 1       | 4382  | 17    | 0.67   |
| Fujitsu   | MHW AT                 | 1      | 1       | 241   | 0     | 0.66   |
| Seagate   | Maxtor DiamondMax 23   | 4      | 44      | 563   | 226   | 0.65   |
| Seagate   | Pipeline HD 5900.2     | 6      | 24      | 493   | 209   | 0.65   |
| Samsung   | SpinPoint M8 (AF)      | 5      | 36      | 381   | 68    | 0.64   |
| Samsung   | SpinPoint M7           | 3      | 75      | 351   | 61    | 0.64   |
| Hitachi   | Travelstar 5K750       | 3      | 184     | 386   | 350   | 0.64   |
| WDC       | AV                     | 10     | 16      | 619   | 43    | 0.64   |
| Toshiba   | 2.5" HDD               | 13     | 31      | 420   | 51    | 0.63   |
| Samsung   | SpinPoint S250         | 2      | 36      | 817   | 687   | 0.63   |
| Apple     | Hitachi-HGST Travel... | 1      | 8       | 271   | 253   | 0.62   |
| Hitachi   | Travelstar 7K100       | 4      | 6       | 325   | 12    | 0.61   |
| WDC       | Black                  | 11     | 43      | 233   | 1     | 0.61   |
| Hitachi   | CinemaStar 7K1000.B    | 2      | 4       | 218   | 0     | 0.60   |
| Seagate   | Momentus 7200.4        | 6      | 96      | 459   | 290   | 0.60   |
| Samsung   | SpinPoint S166         | 3      | 34      | 758   | 456   | 0.59   |
| Hitachi   | Deskstar 7K250         | 6      | 9       | 842   | 410   | 0.58   |
| Seagate   | Constellation ES (S... | 3      | 13      | 747   | 68    | 0.58   |
| Seagate   | UX                     | 1      | 5       | 626   | 16    | 0.58   |
| Seagate   | Desktop HDD.15         | 3      | 10      | 231   | 2     | 0.57   |
| Seagate   | Barracuda XT           | 2      | 7       | 435   | 229   | 0.57   |
| Hitachi   | Deskstar 7K1000.D      | 2      | 47      | 494   | 368   | 0.57   |
| Samsung   | SpinPoint F4           | 1      | 14      | 333   | 22    | 0.56   |
| Fujitsu   | MPA..MPG               | 3      | 3       | 247   | 4     | 0.56   |
| Toshiba   | 3.5" HDD DT01ACA       | 4      | 377     | 232   | 28    | 0.56   |
| Seagate   | Momentus 7200.5        | 4      | 50      | 337   | 71    | 0.56   |
| Fujitsu   | MHT                    | 3      | 3       | 398   | 6     | 0.56   |
| Maxtor    | DiamondMax 20          | 5      | 16      | 551   | 300   | 0.56   |
| Hitachi   | Deskstar E7K1000       | 2      | 2       | 1369  | 16    | 0.54   |
| Toshiba   | N300                   | 1      | 1       | 198   | 0     | 0.54   |
| Seagate   | Momentus 5400 PSD      | 2      | 3       | 352   | 338   | 0.53   |
| Seagate   | Barracuda ATA III      | 1      | 1       | 194   | 0     | 0.53   |
| Seagate   | SpinPoint M8 (AF)      | 6      | 486     | 262   | 46    | 0.53   |
| WDC       | Protege                | 6      | 9       | 652   | 14    | 0.52   |
| Seagate   | Momentus 5400.2        | 12     | 31      | 403   | 490   | 0.52   |
| Magnet... | Unknown                | 2      | 2       | 185   | 0     | 0.51   |
| Seagate   | Momentus XT (AF)       | 1      | 8       | 257   | 132   | 0.50   |
| Samsung   | SpinPoint MP5          | 3      | 7       | 359   | 187   | 0.50   |
| Samsung   | SpinPoint F1 RE        | 1      | 2       | 374   | 51    | 0.49   |
| Maxtor    | DiamondMax 17          | 2      | 9       | 303   | 101   | 0.48   |
| WDC       | Gold                   | 1      | 2       | 175   | 0     | 0.48   |
| Samsung   | SpinPoint P80          | 17     | 71      | 575   | 174   | 0.48   |
| Hitachi   | Travelstar Z5K500      | 3      | 81      | 271   | 95    | 0.47   |
| Toshiba   | 2.5" HDD MQ01ABD       | 4      | 266     | 251   | 108   | 0.47   |
| Hitachi   | CinemaStar 5K1000.B    | 1      | 1       | 169   | 0     | 0.47   |
| WDC       | Black SSHD             | 1      | 5       | 168   | 0     | 0.46   |
| Seagate   | Momentus 5400.4        | 3      | 41      | 428   | 361   | 0.46   |
| WDC       | Blue UltraSlim         | 1      | 1       | 166   | 0     | 0.46   |
| HGST      | Travelstar 7K1000      | 3      | 89      | 179   | 14    | 0.45   |
| Seagate   | SpinPoint F4           | 1      | 3       | 163   | 2     | 0.45   |
| Toshiba   | 2.5" HDD MQ01ABC       | 1      | 1       | 160   | 0     | 0.44   |
| Hitachi   | Travelstar 5K250       | 8      | 111     | 513   | 126   | 0.44   |
| Seagate   | Momentus 5400.3        | 7      | 82      | 445   | 375   | 0.43   |
| Seagate   | MobileMax-2            | 1      | 1       | 154   | 0     | 0.42   |
| Samsung   | SpinPoint V80          | 3      | 4       | 597   | 63    | 0.42   |
| Hitachi   | Travelstar 7K750       | 2      | 16      | 240   | 260   | 0.42   |
| Hitachi   | Travelstar Z5K320      | 3      | 130     | 279   | 301   | 0.42   |
| Toshiba   | 1.8" HDD               | 3      | 5       | 366   | 21    | 0.42   |
| Toshiba   | X300                   | 1      | 6       | 152   | 0     | 0.42   |
| HGST      | Travelstar 5K1000      | 4      | 113     | 228   | 254   | 0.41   |
| Seagate   | Desktop SSHD           | 5      | 33      | 248   | 131   | 0.41   |
| Samsung   | SpinPoint M            | 2      | 5       | 237   | 4     | 0.39   |
| Seagate   | Momentus 7200.3        | 4      | 6       | 533   | 40    | 0.39   |
| Toshiba   | 2.5" HDD MK..75GSX     | 4      | 42      | 334   | 405   | 0.39   |
| IBM       | Deskstar 40GV & 75G... | 1      | 2       | 1484  | 37    | 0.38   |
| Hitachi   | Travelstar 5K320       | 10     | 77      | 464   | 223   | 0.38   |
| Hitachi   | Travelstar Z7K320      | 1      | 18      | 255   | 455   | 0.38   |
| WDC       | Blue Mobile            | 63     | 567     | 156   | 10    | 0.37   |
| WDC       | Purple                 | 8      | 17      | 149   | 1     | 0.36   |
| Quantum   | Fireball lct15         | 3      | 3       | 226   | 2     | 0.36   |
| Seagate   | Momentus 7200.1        | 2      | 4       | 650   | 43    | 0.36   |
| Hitachi   | Travelstar 5K120       | 1      | 3       | 335   | 5     | 0.35   |
| Hitachi   | Travelstar 5K160       | 8      | 104     | 465   | 48    | 0.35   |
| Toshiba   | 3.5" MG03ACAxxx(Y) ... | 1      | 7       | 153   | 1     | 0.35   |
| Toshiba   | 2.5" HDD MK..59GSXP    | 7      | 75      | 309   | 297   | 0.35   |
| Seagate   | Momentus 4200.2        | 3      | 3       | 561   | 687   | 0.35   |
| Seagate   | Momentus 5400.7 (AF)   | 2      | 8       | 248   | 401   | 0.35   |
| Samsung   | SpinPoint P120         | 5      | 53      | 767   | 606   | 0.34   |
| Seagate   | Momentus 5400.6        | 9      | 523     | 418   | 479   | 0.34   |
| Toshiba   | 1.8" HDD MK..16GSG     | 1      | 3       | 272   | 4     | 0.34   |
| Toshiba   | 3.5" DT01ABA Deskto... | 1      | 1       | 124   | 0     | 0.34   |
| WDC       | Blue                   | 15     | 63      | 123   | 0     | 0.34   |
| Toshiba   | 2.5" HDD MK..55GSX     | 5      | 37      | 375   | 86    | 0.34   |
| Seagate   | U6                     | 3      | 11      | 584   | 52    | 0.33   |
| HGST      | Travelstar Z7K500      | 3      | 81      | 161   | 104   | 0.33   |
| Fujitsu   | MJA BH                 | 6      | 22      | 365   | 206   | 0.33   |
| Seagate   | Laptop SSHD            | 7      | 83      | 195   | 93    | 0.33   |
| WDC       | ZALMAN                 | 1      | 1       | 1047  | 8     | 0.32   |
| Toshiba   | 2.5" HDD MK..37GSX     | 2      | 27      | 501   | 43    | 0.31   |
| Toshiba   | 2.5" HDD MK..65GSX     | 12     | 125     | 439   | 251   | 0.31   |
| Toshiba   | 2.5" HDD MK..46GSX     | 4      | 24      | 485   | 52    | 0.31   |
| Hitachi   | Travelstar 5K100       | 9      | 34      | 419   | 30    | 0.31   |
| WDC       | Se                     | 1      | 1       | 112   | 0     | 0.31   |
| Toshiba   | 2.5" HDD MK..59GSM     | 1      | 11      | 467   | 334   | 0.31   |
| Hitachi   | Travelstar 7K500       | 7      | 40      | 367   | 733   | 0.31   |
| Seagate   | LD25 Series            | 2      | 2       | 111   | 0     | 0.30   |
| Apple     | Seagate Barracuda      | 1      | 1       | 109   | 0     | 0.30   |
| Seagate   | Momentus 5400.7        | 1      | 3       | 281   | 338   | 0.30   |
| WDC       | Green Mobile           | 2      | 2       | 191   | 14    | 0.30   |
| Toshiba   | 2.5" HDD MQ02ABD..H    | 1      | 2       | 107   | 0     | 0.30   |
| HGST      | Ultrastar 7K6000       | 2      | 2       | 107   | 0     | 0.29   |
| Seagate   | Momentus Thin          | 3      | 98      | 286   | 518   | 0.29   |
| Toshiba   | 2.5" HDD MK..76GSX     | 6      | 13      | 133   | 139   | 0.29   |
| Seagate   | SV35.2                 | 2      | 6       | 574   | 1173  | 0.28   |
| WDC       | Black Mobile           | 23     | 66      | 103   | 2     | 0.27   |
| Toshiba   | 2.5" HDD MQ01ABF       | 1      | 142     | 116   | 81    | 0.27   |
| Seagate   | Laptop Thin SSHD       | 1      | 1       | 94    | 0     | 0.26   |
| HGST      | Travelstar Z5K500      | 5      | 246     | 167   | 244   | 0.26   |
| Toshiba   | 2.5" HDD MK..37GSX     | 1      | 11      | 414   | 206   | 0.25   |
| Toshiba   | 2.5" HDD MK..34GSX     | 2      | 10      | 368   | 216   | 0.25   |
| Toshiba   | 2.5" HDD L200          | 3      | 8       | 90    | 0     | 0.25   |
| Toshiba   | 2.5" HDD MQ01ABF       | 2      | 17      | 89    | 0     | 0.25   |
| Samsung   | SpinPoint N2           | 1      | 1       | 89    | 0     | 0.25   |
| IBM/Hi... | Deskstar 60GXP         | 2      | 3       | 1032  | 106   | 0.24   |
| Toshiba   | 2.5" HDD MQ01ACF       | 2      | 7       | 109   | 149   | 0.24   |
| Toshiba   | 2.5" HDD MK..63GSX     | 2      | 9       | 562   | 20    | 0.22   |
| Toshiba   | 2.5" HDD MK..52GSX     | 5      | 34      | 421   | 153   | 0.22   |
| WDC       | Blue SSHD              | 1      | 1       | 80    | 0     | 0.22   |
| Seagate   | Momentus XT            | 1      | 5       | 406   | 417   | 0.22   |
| Toshiba   | 1.8" HDD MK..33GSG     | 2      | 3       | 634   | 316   | 0.21   |
| Toshiba   | 2.5" HDD MK..61GSY[N]  | 4      | 12      | 163   | 93    | 0.20   |
| Seagate   | Barracuda 7200.11      | 11     | 213     | 768   | 335   | 0.18   |
| Hitachi   | Travelstar 4K40        | 1      | 5       | 483   | 20    | 0.17   |
| Hitachi   | Travelstar 80GN        | 4      | 10      | 341   | 47    | 0.17   |
| Seagate   | Momentus 5400.5        | 4      | 51      | 391   | 217   | 0.16   |
| Toshiba   | 2.5" HDD MK..56GSY     | 5      | 9       | 101   | 125   | 0.16   |
| Toshiba   | 2.5" HDD MK..59GSM     | 1      | 15      | 303   | 1041  | 0.16   |
| Seagate   | Ultra Mobile HDD       | 2      | 2       | 57    | 0     | 0.16   |
| China     | Unknown                | 2      | 2       | 279   | 512   | 0.15   |
| IBM/Hi... | Travelstar 60GH and... | 1      | 1       | 52    | 0     | 0.14   |
| Toshiba   | 1.8" HDD               | 2      | 5       | 312   | 91    | 0.14   |
| Seagate   | Laptop Thin HDD        | 7      | 403     | 166   | 425   | 0.14   |
| Samsung   | SpinPoint M40/60/80    | 6      | 10      | 449   | 102   | 0.14   |
| Toshiba   | P300                   | 4      | 76      | 52    | 8     | 0.13   |
| Toshiba   | 2.5" HDD MK..46GSX     | 1      | 7       | 418   | 25    | 0.12   |
| WDC       | Scorpio EIDE           | 5      | 5       | 229   | 81    | 0.12   |
| Toshiba   | 1.8" HDD MK..29GSG     | 2      | 3       | 407   | 753   | 0.12   |
| Hitachi   | Travelstar 4K120       | 2      | 3       | 707   | 24    | 0.11   |
| Seagate   | FireCuda 3.5           | 2      | 4       | 40    | 0     | 0.11   |
| HGST      | Travelstar 5K1500      | 1      | 2       | 541   | 14    | 0.10   |
| Seagate   | Barracuda 3.5          | 6      | 49      | 35    | 1     | 0.10   |
| HGST      | Travelstar Z5K1000     | 2      | 14      | 52    | 73    | 0.09   |
| Seagate   | FreePlay               | 1      | 4       | 135   | 646   | 0.09   |
| Hitachi   | Travelstar DK23XX/D... | 2      | 2       | 624   | 243   | 0.08   |
| Samsung   | SpinPoint V40+         | 2      | 3       | 1003  | 159   | 0.08   |
| Seagate   | U8                     | 1      | 1       | 754   | 24    | 0.08   |
| Samsung   | SpinPoint M5           | 5      | 52      | 312   | 317   | 0.08   |
| MARSHAL   | Unknown                | 1      | 1       | 279   | 9     | 0.08   |
| HGST      | Travelstar Z5K500.B    | 1      | 7       | 26    | 0     | 0.07   |
| HGST      | Travelstar Z5K1        | 1      | 2       | 26    | 0     | 0.07   |
| Seagate   | FireCuda 2.5           | 2      | 2       | 26    | 0     | 0.07   |
| Toshiba   | 2.5" HDD MQ01ABD       | 1      | 1       | 25    | 0     | 0.07   |
| Seagate   | Barracuda 2.5 5400     | 4      | 15      | 23    | 0     | 0.07   |
| Maxtor    | DiamondMax 22          | 4      | 21      | 901   | 346   | 0.07   |
| MediaMax  | WL250                  | 2      | 3       | 30    | 3     | 0.06   |
| Toshiba   | 2.5" HDD               | 1      | 1       | 23    | 0     | 0.06   |
| Seagate   | Surveillance           | 1      | 1       | 23    | 0     | 0.06   |
| Samsung   | SpinPoint M6           | 3      | 9       | 303   | 350   | 0.06   |
| Seagate   | DB35.2                 | 1      | 1       | 21    | 0     | 0.06   |
| Samsung   | SpinPoint F1 EG        | 1      | 1       | 385   | 17    | 0.06   |
| Seagate   | Mobile HDD             | 2      | 18      | 22    | 4     | 0.06   |
| Seagate   | Video 2.5              | 2      | 2       | 19    | 0     | 0.05   |
| Toshiba   | 2.5" HDD H200          | 2      | 3       | 18    | 0     | 0.05   |
| Seagate   | Constellation.2 (SATA) | 2      | 3       | 17    | 0     | 0.05   |
| Toshiba   | 2.5" HDD MK..65GSX     | 2      | 3       | 368   | 31    | 0.04   |
| Maxtor    | Fireball 3             | 4      | 7       | 53    | 4     | 0.04   |
| Maxtor    | DiamondMax 10 (ATA/... | 14     | 23      | 24    | 84    | 0.04   |
| Maxtor    | MaXLine III (ATA/13... | 3      | 3       | 17    | 12    | 0.04   |
| Seagate   | U10                    | 1      | 1       | 380   | 27    | 0.04   |
| Apple     | HGST Travelstar 5K750  | 2      | 2       | 265   | 77    | 0.04   |
| Seagate   | Pipeline HD 5900.1     | 2      | 4       | 444   | 58    | 0.03   |
| Hitachi   | Travelstar 5K80        | 3      | 3       | 214   | 230   | 0.03   |
| Toshiba   | 2.5" HDD MK..76GSX     | 4      | 43      | 30    | 199   | 0.03   |
| Maxtor    | DiamondMax Plus 8      | 4      | 12      | 27    | 16    | 0.02   |
| Toshiba   | 2.5" HDD MK..59GSX     | 1      | 1       | 8     | 0     | 0.02   |
| Seagate   | SV35.3                 | 1      | 1       | 45    | 7     | 0.02   |
| Samsung   | SpinPoint V60          | 1      | 3       | 733   | 124   | 0.02   |
| Toshiba   | 2.5" HDD MQ02ABF..H    | 1      | 1       | 5     | 0     | 0.01   |
| Hitachi   | Travelstar E7K100      | 1      | 1       | 4     | 0     | 0.01   |
| Fujitsu   | MHZ BJ                 | 1      | 1       | 4     | 0     | 0.01   |
| Seagate   | SkyHawk                | 2      | 2       | 3     | 0     | 0.01   |
| Maxtor    | DiamondMax Plus 9      | 11     | 53      | 32    | 143   | 0.01   |
| Toshiba   | 2.5" HDD MQ02ABF       | 1      | 1       | 1     | 0     | 0.01   |
| Hitachi   | Ultrastar 5K3000       | 1      | 1       | 1045  | 595   | 0.00   |
| Maxtor    | DiamondMax D540X-4D    | 2      | 3       | 24    | 229   | 0.00   |
| Maxtor    | DiamondMax 16          | 1      | 1       | 22    | 16    | 0.00   |
| Maxtor    | Fireball 541DX         | 1      | 5       | 20    | 89    | 0.00   |
| CLOVER    | Hightech Utania        | 2      | 2       | 0     | 0     | 0.00   |
| MediaMax  | WL400                  | 1      | 1       | 0     | 0     | 0.00   |
| HGST      | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| Toshiba   | 2.5" HDD MQ01ABB       | 1      | 1       | 152   | 704   | 0.00   |

HDD by Vendor
-------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

| MFG         | Models | Samples | Days  | Err   | Rating |
|-------------|--------|---------|-------|-------|--------|
| HP          | 6      | 7       | 1146  | 33    | 1.69   |
| Quantum     | 5      | 5       | 474   | 2     | 1.14   |
| WDC         | 1059   | 5594    | 509   | 43    | 0.93   |
| ExcelStor   | 6      | 9       | 710   | 21    | 0.85   |
| Hitachi     | 200    | 1927    | 548   | 163   | 0.81   |
| Samsung     | 114    | 1090    | 648   | 245   | 0.80   |
| Fujitsu     | 61     | 188     | 478   | 147   | 0.77   |
| Seagate     | 367    | 6220    | 511   | 226   | 0.74   |
| IBM/Hitachi | 9      | 14      | 675   | 26    | 0.60   |
| Apple       | 5      | 16      | 267   | 137   | 0.55   |
| Magnetic... | 2      | 2       | 185   | 0     | 0.51   |
| Maxtor      | 74     | 291     | 398   | 248   | 0.44   |
| Toshiba     | 133    | 1489    | 258   | 119   | 0.39   |
| IBM         | 1      | 2       | 1484  | 37    | 0.38   |
| MediaMax    | 4      | 5       | 127   | 2     | 0.34   |
| HGST        | 28     | 569     | 180   | 175   | 0.34   |
| China       | 2      | 2       | 279   | 512   | 0.15   |
| MARSHAL     | 1      | 1       | 279   | 9     | 0.08   |
| CLOVER      | 2      | 2       | 0     | 0     | 0.00   |

SSD by Model
------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

See complete list of tested SSD samples in the Appendix 2 (All_SSD.md).

| MFG       | Model              | Size   | Samples | Days  | Err   | Rating |
|-----------|--------------------|--------|---------|-------|-------|--------|
| OCZ       | VERTEX PLUS R2     | 61 GB  | 1       | 1202  | 0     | 3.29   |
| Mushkin   | MKNSSDCR120GB      | 120 GB | 1       | 1164  | 0     | 3.19   |
| Samsung   | MZ7WD240HCFV-00003 | 240 GB | 1       | 1154  | 0     | 3.16   |
| Toshiba   | THNS064GG2BNAA     | 64 GB  | 2       | 1079  | 0     | 2.96   |
| OCZ       | VERTEX2 3.5        | 120 GB | 1       | 1040  | 0     | 2.85   |
| Kingston  | SVP100S296G        | 96 GB  | 1       | 918   | 0     | 2.52   |
| Samsung   | SSD PM800 2.5"     | 256 GB | 1       | 871   | 0     | 2.39   |
| Corsair   | Force GS           | 180 GB | 2       | 854   | 0     | 2.34   |
| OCZ       | VERTEX2            | 40 GB  | 1       | 850   | 0     | 2.33   |
| Corsair   | Force GT           | 180 GB | 1       | 838   | 0     | 2.30   |
| OCZ       | AGILITY4           | 128 GB | 3       | 803   | 0     | 2.20   |
| OCZ       | DENRSTE251M45-0... | 100 GB | 1       | 800   | 0     | 2.19   |
| OCZ       | VERTEX PLUS R2     | 247 GB | 1       | 797   | 0     | 2.18   |
| Micron    | MTFDDAT128MAM-1J2  | 128 GB | 1       | 783   | 0     | 2.15   |
| Corsair   | Force GS           | 90 GB  | 1       | 776   | 0     | 2.13   |
| SanDisk   | SD5SE2128G1002E    | 128 GB | 2       | 724   | 0     | 1.98   |
| ADATA     | SSD S510           | 120 GB | 3       | 717   | 0     | 1.97   |
| Samsung   | SSD 840 EVO        | 750 GB | 1       | 713   | 0     | 1.96   |
| OCZ       | NOCTI              | 60 GB  | 1       | 704   | 0     | 1.93   |
| Corsair   | Force 3 SSD        | 240 GB | 2       | 697   | 0     | 1.91   |
| Corsair   | Force 3 SSD        | 60 GB  | 8       | 695   | 0     | 1.91   |
| Kingston  | SVP200S390G        | 90 GB  | 1       | 686   | 0     | 1.88   |
| Intel     | SSDSC2CT080A4      | 80 GB  | 2       | 675   | 0     | 1.85   |
| Kingston  | SVP200S37A480G     | 480 GB | 1       | 674   | 0     | 1.85   |
| Kingston  | SNVP325S2128GB     | 128 GB | 1       | 674   | 0     | 1.85   |
| Toshiba   | THNSNH060GMCT      | 60 GB  | 1       | 666   | 0     | 1.82   |
| OCZ       | AGILITY3           | 120 GB | 19      | 753   | 88    | 1.82   |
| Samsung   | SSD 840 EVO 120... | 120 GB | 1       | 641   | 0     | 1.76   |
| Samsung   | SSD 850 PRO        | 1 TB   | 1       | 626   | 0     | 1.72   |
| Kingston  | SVP200S37A240G     | 240 GB | 1       | 623   | 0     | 1.71   |
| Intel     | SSDSA2M040G2GC     | 40 GB  | 2       | 1007  | 3     | 1.69   |
| Samsung   | MZMPA128HMFU-00000 | 128 GB | 1       | 616   | 0     | 1.69   |
| Crucial   | M4-CT064M4SSD2     | 64 GB  | 7       | 600   | 0     | 1.65   |
| Samsung   | SSD 830 Series     | 512 GB | 1       | 599   | 0     | 1.64   |
| Kingston  | SKC300S37A480G     | 480 GB | 1       | 597   | 0     | 1.64   |
| OCZ       | DENCSTE351M16-0... | 240 GB | 1       | 585   | 0     | 1.60   |
| Corsair   | Force 3 SSD        | 120 GB | 8       | 707   | 89    | 1.58   |
| OCZ       | VERTEX2            | 120 GB | 2       | 568   | 0     | 1.56   |
| OCZ       | REVODRIVE3         | 60 GB  | 4       | 564   | 0     | 1.55   |
| Crucial   | M4-CT128M4SSD2     | 128 GB | 14      | 585   | 73    | 1.54   |
| Samsung   | MZMPC128HBFU-000L1 | 128 GB | 1       | 559   | 0     | 1.53   |
| Kingston  | SVP200S360G        | 60 GB  | 4       | 550   | 0     | 1.51   |
| Toshiba   | THNSNH128GCST      | 128 GB | 1       | 549   | 0     | 1.51   |
| SanDisk   | SD6SB1M256G1002    | 256 GB | 1       | 548   | 0     | 1.50   |
| Apple     | SSD SM1024F        | 1 TB   | 1       | 545   | 0     | 1.49   |
| Intel     | SSDSA2CW120G3      | 120 GB | 4       | 544   | 0     | 1.49   |
| OCZ       | VERTEX2 3.5        | 115 GB | 1       | 541   | 0     | 1.48   |
| Toshiba   | THNSFC256GAMJ      | 256 GB | 1       | 539   | 0     | 1.48   |
| Samsung   | MZ7PC128HAFU-000   | 128 GB | 1       | 517   | 0     | 1.42   |
| OCZ       | VERTEX2            | 60 GB  | 2       | 511   | 0     | 1.40   |
| OCZ       | D2RSTK251E14-0400  | 400 GB | 1       | 502   | 0     | 1.38   |
| Samsung   | SSD 840 EVO        | 1 TB   | 2       | 496   | 0     | 1.36   |
| Transcend | TS128GSSD320       | 128 GB | 1       | 493   | 0     | 1.35   |
| Crucial   | CT500MX200SSD1     | 500 GB | 1       | 489   | 0     | 1.34   |
| OCZ       | VERTEX3            | 60 GB  | 24      | 553   | 2     | 1.32   |
| Intel     | SSDSC2BW240A3L     | 240 GB | 1       | 480   | 0     | 1.32   |
| Toshiba   | THNSNF128GMCS      | 128 GB | 2       | 471   | 0     | 1.29   |
| Verbatim  | SATA-III SSD       | 128 GB | 1       | 470   | 0     | 1.29   |
| Plextor   | PX-64M2S           | 64 GB  | 2       | 467   | 0     | 1.28   |
| SPCC      | SSD110             | 120 GB | 3       | 466   | 0     | 1.28   |
| OCZ       | AGILITY3           | 60 GB  | 16      | 499   | 1     | 1.25   |
| Corsair   | Performance Pro    | 128 GB | 1       | 450   | 0     | 1.23   |
| Plextor   | PX-128M2S          | 128 GB | 1       | 447   | 0     | 1.23   |
| Samsung   | SSD 830 Series     | 64 GB  | 3       | 447   | 0     | 1.23   |
| Foxline   | FLDMMS128G         | 128 GB | 1       | 443   | 0     | 1.22   |
| Corsair   | Force GT           | 60 GB  | 5       | 690   | 7     | 1.21   |
| OCZ       | VECTOR             | 128 GB | 2       | 439   | 0     | 1.20   |
| Samsung   | MZNTE128HMGR-000SO | 128 GB | 1       | 436   | 0     | 1.20   |
| OCZ       | REVODRIVE X2       | 25 GB  | 4       | 435   | 0     | 1.19   |
| Corsair   | Force GT           | 120 GB | 6       | 506   | 1     | 1.19   |
| Kingston  | SV200S3128G        | 128 GB | 6       | 432   | 0     | 1.19   |
| Crucial   | M4-CT128M4SSD1     | 128 GB | 3       | 430   | 0     | 1.18   |
| Corsair   | CSSD-F60GB2        | 60 GB  | 1       | 420   | 0     | 1.15   |
| Kingston  | SKC380S360G        | 60 GB  | 1       | 420   | 0     | 1.15   |
| OCZ       | SOLID3             | 120 GB | 1       | 418   | 0     | 1.15   |
| Apple     | SSD TS128C         | 121 GB | 1       | 416   | 0     | 1.14   |
| Smartbuy  | SSD                | 60 GB  | 4       | 414   | 0     | 1.13   |
| SanDisk   | SD6SB2M128G1022I   | 128 GB | 1       | 412   | 0     | 1.13   |
| Samsung   | MMCRE28G5MXP-0VBH1 | 128 GB | 1       | 410   | 0     | 1.12   |
| Samsung   | MZRPA128HMCD-000SO | 64 GB  | 4       | 405   | 0     | 1.11   |
| Toshiba   | THNSNH060GBST      | 60 GB  | 2       | 399   | 0     | 1.10   |
| Crucial   | M4-CT256M4SSD2     | 256 GB | 2       | 399   | 0     | 1.09   |
| SanDisk   | SDSSDXP240G        | 240 GB | 2       | 398   | 0     | 1.09   |
| OCZ       | AGILITY3           | 64 GB  | 2       | 397   | 0     | 1.09   |
| OCZ       | VERTEX3 MI         | 120 GB | 13      | 468   | 74    | 1.07   |
| Kingston  | SNV425S264GB       | 64 GB  | 1       | 386   | 0     | 1.06   |
| Samsung   | MZ7TD256HAFV-000L9 | 256 GB | 1       | 385   | 0     | 1.06   |
| Samsung   | MMCRE28GFMXP-MVB   | 128 GB | 2       | 383   | 0     | 1.05   |
| Samsung   | MZ7TE128HMGR-00000 | 128 GB | 2       | 382   | 0     | 1.05   |
| OCZ       | VERTEX4            | 128 GB | 49      | 399   | 1     | 1.04   |
| KingSpec  | SPK-SF12-M120      | 120 GB | 1       | 373   | 0     | 1.02   |
| ADATA     | SSD S511           | 120 GB | 1       | 372   | 0     | 1.02   |
| Samsung   | MZMPC032HBCD-00000 | 32 GB  | 5       | 372   | 0     | 1.02   |
| Samsung   | MZ7TD256HAFV-000L7 | 256 GB | 2       | 370   | 0     | 1.02   |
| Samsung   | SSD 850 EVO mSATA  | 120 GB | 2       | 369   | 0     | 1.01   |
| Toshiba   | THNSNC128GCSJ      | 128 GB | 1       | 367   | 0     | 1.01   |
| Samsung   | MZMPC032HBCD-000H1 | 32 GB  | 4       | 367   | 0     | 1.01   |
| Corsair   | Force GS           | 240 GB | 1       | 365   | 0     | 1.00   |
| Samsung   | SSD 840 Series     | 500 GB | 1       | 365   | 0     | 1.00   |
| OCZ       | VERTEX3            | 120 GB | 36      | 516   | 48    | 1.00   |
| Kingston  | SVP200S37A60G      | 60 GB  | 5       | 360   | 0     | 0.99   |
| China     | SSD                | 60 GB  | 2       | 367   | 1     | 0.99   |
| KingShare | 230120SSD          | 128 GB | 1       | 358   | 0     | 0.98   |
| SanDisk   | SDSSDH2128G        | 128 GB | 1       | 356   | 0     | 0.98   |
| KingSpec  | KSD-SA25.5-016MJ   | 16 GB  | 1       | 353   | 0     | 0.97   |
| Toshiba   | THNSNX024GMNT      | 24 GB  | 2       | 346   | 0     | 0.95   |
| OCZ       | VERTEX3            | 240 GB | 7       | 399   | 6     | 0.94   |
| Toshiba   | THNS064GE4BBDC     | 64 GB  | 1       | 338   | 0     | 0.93   |
| KingFast  | SSD                | 32 GB  | 1       | 332   | 0     | 0.91   |
| Plextor   | PX-128M3           | 128 GB | 2       | 331   | 0     | 0.91   |
| Crucial   | C300-CTFDDAC128MAG | 128 GB | 3       | 330   | 0     | 0.91   |
| China     | SATA SSD           | 20 GB  | 6       | 382   | 1     | 0.90   |
| Kingston  | SV200S364G         | 64 GB  | 1       | 327   | 0     | 0.90   |
| Samsung   | SSD 840 PRO Series | 512 GB | 2       | 326   | 0     | 0.90   |
| Kingston  | SH100S3240G        | 240 GB | 1       | 1628  | 4     | 0.89   |
| Samsung   | SSD 840 EVO        | 250 GB | 20      | 329   | 51    | 0.89   |
| Kingston  | SMS100S264G        | 64 GB  | 1       | 323   | 0     | 0.89   |
| OCZ       | VERTEX3 LP         | 60 GB  | 1       | 320   | 0     | 0.88   |
| SanDisk   | SD5SG2256G1052E    | 256 GB | 1       | 313   | 0     | 0.86   |
| OCZ       | AGILITY3           | 128 GB | 2       | 313   | 0     | 0.86   |
| Intel     | SSDSC2MH120A2      | 120 GB | 1       | 311   | 0     | 0.85   |
| OCZ       | VERTEX4            | 256 GB | 9       | 333   | 1     | 0.84   |
| Crucial   | C300-CTFDDAC064MAG | 64 GB  | 1       | 307   | 0     | 0.84   |
| Kingston  | SVP200S3240G       | 240 GB | 2       | 307   | 0     | 0.84   |
| Toshiba   | THNSNC128GBSJ      | 128 GB | 1       | 303   | 0     | 0.83   |
| Samsung   | SSD PM830 2.5" 7mm | 128 GB | 1       | 302   | 0     | 0.83   |
| OCZ       | AGILITY2           | 60 GB  | 2       | 302   | 0     | 0.83   |
| SanDisk   | SDSSDX120GG25      | 120 GB | 4       | 301   | 0     | 0.83   |
| Mushkin   | MKNSSDAT240GB-DX   | 240 GB | 1       | 299   | 0     | 0.82   |
| Samsung   | SSD PM830 mSATA    | 32 GB  | 4       | 299   | 0     | 0.82   |
| Kingston  | SH103S3120G        | 120 GB | 31      | 299   | 0     | 0.82   |
| China     | SATA SSD           | 128 GB | 2       | 298   | 0     | 0.82   |
| Intel     | SSDSC2CT240A4      | 240 GB | 4       | 297   | 0     | 0.82   |
| Ramaxel   | RDM-II XM020C024G  | 24 GB  | 2       | 295   | 0     | 0.81   |
| SanDisk   | SDSSDHII480G       | 480 GB | 3       | 295   | 0     | 0.81   |
| OCZ       | VERTEX3            | 90 GB  | 11      | 611   | 7     | 0.81   |
| Kingston  | SNVP325S2256GB     | 256 GB | 1       | 293   | 0     | 0.80   |
| Kingston  | SKC300S37A60G      | 60 GB  | 10      | 324   | 4     | 0.80   |
| OCZ       | SOLID3             | 60 GB  | 2       | 549   | 7     | 0.80   |
| Samsung   | MZMPA064HMDR-00000 | 64 GB  | 1       | 290   | 0     | 0.79   |
| OCZ       | AGILITY3           | 90 GB  | 3       | 476   | 1     | 0.79   |
| OCZ       | CACHE-SYNAPSE      | 32 GB  | 1       | 286   | 0     | 0.79   |
| Corsair   | Force 3 SSD        | 90 GB  | 4       | 284   | 0     | 0.78   |
| OCZ       | AGILITY3           | 240 GB | 2       | 284   | 0     | 0.78   |
| Samsung   | MZMPA024HMCD-000L1 | 24 GB  | 1       | 283   | 0     | 0.78   |
| Apacer    | AST680S            | 128 GB | 1       | 280   | 0     | 0.77   |
| OCZ       | VERTEX             | 64 GB  | 1       | 280   | 0     | 0.77   |
| Kingston  | SMS100S232G        | 32 GB  | 1       | 279   | 0     | 0.76   |
| Intel     | SSDSC2BW180A4      | 180 GB | 5       | 275   | 0     | 0.76   |
| Samsung   | SSD 830 Series     | 128 GB | 6       | 274   | 0     | 0.75   |
| Goodram   | C40                | 120 GB | 3       | 266   | 0     | 0.73   |
| Plextor   | PX-256M5Pro        | 256 GB | 3       | 262   | 0     | 0.72   |
| Apacer    | A7202              | 64 GB  | 1       | 262   | 0     | 0.72   |
| Samsung   | SSD PM830 mSATA    | 128 GB | 1       | 261   | 0     | 0.72   |
| SanDisk   | SDSSDHP064G        | 64 GB  | 6       | 260   | 0     | 0.71   |
| Intel     | SSDSA2M080G2GC     | 80 GB  | 4       | 587   | 4     | 0.71   |
| Samsung   | MMCQE28GFMUP-MVA   | 128 GB | 2       | 298   | 13    | 0.71   |
| Samsung   | SSD PM810 TM       | 64 GB  | 1       | 257   | 0     | 0.70   |
| SanDisk   | SD6SB1M128G        | 128 GB | 1       | 256   | 0     | 0.70   |
| OCZ       | VERTEX PLUS R2     | 123 GB | 2       | 251   | 0     | 0.69   |
| Samsung   | SSD 840 EVO        | 120 GB | 32      | 250   | 0     | 0.69   |
| Samsung   | SSD 840 PRO Series | 128 GB | 10      | 249   | 0     | 0.68   |
| ADATA     | SX900              | 64 GB  | 3       | 500   | 339   | 0.68   |
| Samsung   | SSD 840 Series     | 120 GB | 9       | 266   | 1     | 0.68   |
| Intel     | SSDSA2M080G2HP     | 80 GB  | 1       | 245   | 0     | 0.67   |
| Intel     | SSDSA1MH080G1GN    | 80 GB  | 1       | 244   | 0     | 0.67   |
| Intel     | SSDSA2BW160G3L     | 160 GB | 1       | 239   | 0     | 0.66   |
| OCZ       | VECTOR150          | 120 GB | 7       | 239   | 0     | 0.66   |
| HP        | VK0240GDJXU        | 240 GB | 1       | 238   | 0     | 0.65   |
| Samsung   | SSD 830 Series     | 256 GB | 2       | 238   | 0     | 0.65   |
| Crucial   | M4-CT128M4SSD3     | 128 GB | 1       | 238   | 0     | 0.65   |
| Kingston  | SV200S3256G        | 256 GB | 2       | 237   | 0     | 0.65   |
| Plextor   | PX-64M3            | 64 GB  | 3       | 408   | 346   | 0.64   |
| Corsair   | Force GS           | 128 GB | 13      | 232   | 0     | 0.64   |
| Kingston  | SM2280S3120G       | 120 GB | 3       | 230   | 0     | 0.63   |
| SanDisk   | SDSSDHP128G        | 128 GB | 16      | 229   | 0     | 0.63   |
| Kingston  | SV100S264G         | 64 GB  | 6       | 391   | 4     | 0.63   |
| TEAM      | L3 SSD             | 120 GB | 1       | 227   | 0     | 0.62   |
| Corsair   | Force 3 SSD        | 480 GB | 1       | 226   | 0     | 0.62   |
| OCZ       | OCTANE S2          | 64 GB  | 1       | 224   | 0     | 0.61   |
| ADATA     | SP900              | 128 GB | 18      | 256   | 19    | 0.61   |
| Kingston  | SV300S37A60G       | 60 GB  | 83      | 225   | 1     | 0.61   |
| Toshiba   | TR150              | 120 GB | 2       | 222   | 0     | 0.61   |
| Samsung   | MMDPE56GFDXP-MVB   | 256 GB | 1       | 218   | 0     | 0.60   |
| Goodram   | C50                | 60 GB  | 2       | 214   | 0     | 0.59   |
| Samsung   | SSD 840 Series     | 250 GB | 6       | 214   | 0     | 0.59   |
| Kingston  | SVP200S37A120G     | 120 GB | 6       | 283   | 179   | 0.58   |
| Toshiba   | THNSNJ128GCST      | 128 GB | 3       | 208   | 0     | 0.57   |
| Samsung   | SSD 840 EVO        | 500 GB | 9       | 208   | 0     | 0.57   |
| OCZ       | VERTEX2            | 50 GB  | 2       | 309   | 320   | 0.57   |
| Toshiba   | THNSNH128GBST      | 128 GB | 2       | 207   | 0     | 0.57   |
| Intel     | SSDSC2BP240G4      | 240 GB | 1       | 206   | 0     | 0.56   |
| ADATA     | SP900              | 256 GB | 6       | 333   | 2     | 0.56   |
| Samsung   | SSD 840 PRO Series | 256 GB | 13      | 204   | 0     | 0.56   |
| SPCC      | SSD B29            | 32 GB  | 1       | 204   | 0     | 0.56   |
| SanDisk   | SD5SF2128G1014E    | 128 GB | 2       | 200   | 0     | 0.55   |
| ADATA     | SP600              | 256 GB | 1       | 198   | 0     | 0.55   |
| OCZ       | TRION100           | 240 GB | 6       | 197   | 0     | 0.54   |
| Toshiba   | THNSNJ128GCSU      | 128 GB | 2       | 195   | 0     | 0.54   |
| Samsung   | MZMPC032HBCD-000L1 | 32 GB  | 1       | 195   | 0     | 0.53   |
| Plextor   | PX-128M7VC         | 128 GB | 5       | 194   | 0     | 0.53   |
| OCZ       | VERTEX4            | 512 GB | 1       | 573   | 2     | 0.52   |
| ADATA     | SX900              | 128 GB | 6       | 436   | 512   | 0.52   |
| Kingston  | SV100S2128G        | 128 GB | 2       | 359   | 2     | 0.52   |
| Samsung   | SSD 850 PRO        | 128 GB | 9       | 188   | 0     | 0.52   |
| Samsung   | SG9MSM6D024GPM00   | 22 GB  | 1       | 188   | 0     | 0.52   |
| Transcend | TS128GSSD720       | 128 GB | 2       | 187   | 0     | 0.51   |
| SanDisk   | SSD i100           | 16 GB  | 5       | 187   | 0     | 0.51   |
| Toshiba   | THNSNH128GMCT      | 128 GB | 2       | 186   | 0     | 0.51   |
| Crucial   | CT256MX100SSD1     | 256 GB | 8       | 186   | 0     | 0.51   |
| OCZ       | VERTEX PLUS        | 60 GB  | 1       | 372   | 1     | 0.51   |
| Smartbuy  | mSata              | 64 GB  | 1       | 186   | 0     | 0.51   |
| Crucial   | M4-CT512M4SSD2     | 512 GB | 1       | 184   | 0     | 0.51   |
| Kingston  | SKC300S37A120G     | 120 GB | 10      | 184   | 0     | 0.51   |
| Crucial   | CT240M500SSD1      | 240 GB | 8       | 259   | 271   | 0.50   |
| Crucial   | CT960M500SSD1      | 960 GB | 4       | 419   | 517   | 0.49   |
| Toshiba   | Q300 Pro           | 256 GB | 1       | 178   | 0     | 0.49   |
| ADATA     | SSD S599           | 60 GB  | 1       | 178   | 0     | 0.49   |
| Samsung   | SSD PM800 Serie... | 256 GB | 1       | 178   | 0     | 0.49   |
| Kingston  | SVP200S37A90G      | 90 GB  | 2       | 176   | 0     | 0.48   |
| PNY       | CS900 120GB SSD    | 120 GB | 1       | 175   | 0     | 0.48   |
| Toshiba   | THNSNH060GCST      | 60 GB  | 1       | 175   | 0     | 0.48   |
| Plextor   | PX-128M7VG         | 128 GB | 1       | 171   | 0     | 0.47   |
| SPCC      | SSD110             | 60 GB  | 4       | 441   | 509   | 0.47   |
| OCZ       | VERTEX460          | 120 GB | 1       | 169   | 0     | 0.46   |
| SanDisk   | SDSSDP256G         | 256 GB | 2       | 169   | 0     | 0.46   |
| ADATA     | SP900              | 64 GB  | 12      | 230   | 2     | 0.46   |
| ADATA     | SP600              | 32 GB  | 3       | 168   | 0     | 0.46   |
| Intel     | SSDSA2CT040G3      | 40 GB  | 3       | 167   | 0     | 0.46   |
| Intel     | SSDSC2CT180A4      | 180 GB | 5       | 166   | 0     | 0.46   |
| Kingston  | SV300S37A120G      | 120 GB | 212     | 183   | 23    | 0.45   |
| SanDisk   | iSSD P4            | 8 GB   | 3       | 245   | 1     | 0.44   |
| Intel     | SSDSCMMW180A3L     | 180 GB | 1       | 160   | 0     | 0.44   |
| Plextor   | PX-256S2C          | 256 GB | 2       | 153   | 0     | 0.42   |
| SPCC      | SSD162             | 120 GB | 5       | 412   | 407   | 0.42   |
| Samsung   | MZNLN128HCGR-000L2 | 128 GB | 1       | 153   | 0     | 0.42   |
| Samsung   | MZNTY128HDHP-000L1 | 128 GB | 1       | 153   | 0     | 0.42   |
| Intel     | SSDSA2CW080G3      | 80 GB  | 4       | 152   | 0     | 0.42   |
| Samsung   | SSD 840 EVO 500... | 500 GB | 1       | 152   | 0     | 0.42   |
| Intel     | SSDSC2BW180A3L     | 180 GB | 1       | 149   | 0     | 0.41   |
| SPCC      | SSD                | 60 GB  | 48      | 162   | 43    | 0.41   |
| Kingston  | SHSS37A120G        | 120 GB | 6       | 147   | 0     | 0.40   |
| SanDisk   | SDSSDHII120G       | 120 GB | 13      | 146   | 0     | 0.40   |
| Toshiba   | THNSNJ256GCSU      | 256 GB | 2       | 144   | 0     | 0.40   |
| Intel     | SSDSC2BB120G4      | 120 GB | 1       | 143   | 0     | 0.39   |
| QUMO      | SSD                | 60 GB  | 1       | 143   | 0     | 0.39   |
| KingSpec  | KSD-SA25.5-064MJ   | 64 GB  | 1       | 141   | 0     | 0.39   |
| Smartbuy  | SSD                | 120 GB | 35      | 141   | 0     | 0.39   |
| Samsung   | SSD 850 EVO        | 120 GB | 28      | 138   | 0     | 0.38   |
| ADATA     | SX930              | 120 GB | 1       | 138   | 0     | 0.38   |
| China     | SATA SSD           | 64 GB  | 2       | 138   | 0     | 0.38   |
| Intel     | SSDSC2BB080G4      | 80 GB  | 1       | 135   | 0     | 0.37   |
| Samsung   | SSD 850 PRO        | 256 GB | 23      | 134   | 0     | 0.37   |
| Corsair   | Force GT           | 90 GB  | 2       | 361   | 1     | 0.37   |
| SanDisk   | SDSSDHP256G        | 256 GB | 5       | 134   | 0     | 0.37   |
| SanDisk   | SDSSDP128G         | 126 GB | 18      | 133   | 1     | 0.36   |
| SanDisk   | SDSSDP064G         | 63 GB  | 4       | 172   | 256   | 0.36   |
| OCZ       | AGILITY4           | 256 GB | 4       | 141   | 61    | 0.36   |
| Smartbuy  | SSD                | 60 GB  | 16      | 128   | 0     | 0.35   |
| Transcend | TS64GMSA370        | 64 GB  | 1       | 127   | 0     | 0.35   |
| OCZ       | VECTOR150          | 240 GB | 2       | 127   | 0     | 0.35   |
| Kingston  | SH103S3240G        | 240 GB | 9       | 299   | 237   | 0.35   |
| Chiprex   | S10T3120GB         | 120 GB | 1       | 126   | 0     | 0.35   |
| Transcend | TS128GSSD340       | 128 GB | 3       | 126   | 0     | 0.35   |
| KingFast  | SSD                | 29 GB  | 1       | 125   | 0     | 0.34   |
| Samsung   | MZMTD128HAFV-000L1 | 128 GB | 6       | 132   | 24    | 0.34   |
| Kingston  | SV100S232G         | 32 GB  | 2       | 122   | 0     | 0.33   |
| Corsair   | Neutron GTX SSD    | 240 GB | 3       | 165   | 98    | 0.33   |
| Samsung   | SSD PM830 2.5" 7mm | 256 GB | 1       | 121   | 0     | 0.33   |
| ADATA     | SSD SX900 512GB... | 512 GB | 1       | 120   | 0     | 0.33   |
| SanDisk   | SDSSDHII240G       | 240 GB | 6       | 119   | 0     | 0.33   |
| OCZ       | VERTEX4            | 64 GB  | 5       | 121   | 1     | 0.33   |
| OCZ       | TRION100           | 120 GB | 2       | 121   | 1     | 0.32   |
| ADATA     | XM13               | 32 GB  | 1       | 116   | 0     | 0.32   |
| Plextor   | PX-128M5S          | 128 GB | 34      | 115   | 0     | 0.32   |
| Corsair   | Force LE SSD       | 120 GB | 2       | 114   | 0     | 0.31   |
| OCZ       | D2CSTK181M11-0180  | 180 GB | 3       | 114   | 0     | 0.31   |
| OCZ       | VERTEX2            | 90 GB  | 1       | 113   | 0     | 0.31   |
| Samsung   | SSD 840 EVO 250... | 250 GB | 2       | 112   | 0     | 0.31   |
| Samsung   | SSD 850 EVO        | 500 GB | 31      | 112   | 0     | 0.31   |
| SanDisk   | SSD i100           | 24 GB  | 9       | 112   | 0     | 0.31   |
| Samsung   | SSD 850 EVO M.2    | 500 GB | 5       | 112   | 0     | 0.31   |
| OCZ       | VERTEX3            | 128 GB | 1       | 111   | 0     | 0.31   |
| SanDisk   | SD6SB1M128G1002    | 128 GB | 1       | 110   | 0     | 0.30   |
| Samsung   | MZNTD128HAGM-00000 | 128 GB | 1       | 110   | 0     | 0.30   |
| OCZ       | ARC100             | 120 GB | 7       | 109   | 0     | 0.30   |
| Samsung   | MZNLF128HCHP-000H1 | 128 GB | 1       | 109   | 0     | 0.30   |
| SanDisk   | Ultra II           | 480 GB | 2       | 109   | 0     | 0.30   |
| Corsair   | Force LS SSD       | 120 GB | 7       | 166   | 433   | 0.30   |
| OCZ       | ARC100             | 240 GB | 3       | 107   | 0     | 0.29   |
| Transcend | TS128GMSA740       | 128 GB | 1       | 106   | 0     | 0.29   |
| ADATA     | SP920SS            | 128 GB | 4       | 236   | 4     | 0.29   |
| Intel     | SSDMCEAC180B3      | 180 GB | 2       | 105   | 0     | 0.29   |
| SanDisk   | SSD U100           | 16 GB  | 1       | 104   | 0     | 0.29   |
| Samsung   | MZ7PD256HCGM-000H7 | 256 GB | 1       | 104   | 0     | 0.29   |
| ADATA     | SP600              | 64 GB  | 7       | 113   | 2     | 0.28   |
| Transcend | TS120GSSD25D-M     | 128 GB | 1       | 309   | 2     | 0.28   |
| Toshiba   | THNSNH256GBST      | 256 GB | 1       | 102   | 0     | 0.28   |
| Smartbuy  | mSata              | 256 GB | 1       | 102   | 0     | 0.28   |
| KingFast  | SSD                | 30 GB  | 1       | 102   | 0     | 0.28   |
| TEAM      | L3 EVO SSD         | 120 GB | 1       | 101   | 0     | 0.28   |
| Samsung   | SSD 850 EVO        | 250 GB | 59      | 101   | 0     | 0.28   |
| ADATA     | SP310              | 128 GB | 1       | 101   | 0     | 0.28   |
| ADATA     | SSD S511           | 60 GB  | 3       | 430   | 679   | 0.28   |
| Toshiba   | THNSNJ128G8NY      | 128 GB | 1       | 98    | 0     | 0.27   |
| SPCC      | SSD A20            | 60 GB  | 1       | 97    | 0     | 0.27   |
| Lite-On   | CV3-8D128          | 128 GB | 1       | 97    | 0     | 0.27   |
| Crucial   | CT128M550SSD3      | 128 GB | 2       | 126   | 8     | 0.27   |
| Crucial   | CT120M500SSD1      | 120 GB | 8       | 325   | 9     | 0.26   |
| Plextor   | PX-128M5M          | 128 GB | 7       | 95    | 0     | 0.26   |
| SanDisk   | SSD U100           | 256 GB | 1       | 94    | 0     | 0.26   |
| Kingston  | SV300S37A240G      | 240 GB | 34      | 94    | 1     | 0.26   |
| SPCC      | SSD170             | 120 GB | 3       | 237   | 341   | 0.26   |
| Patriot   | Blast              | 120 GB | 3       | 94    | 0     | 0.26   |
| Transcend | TS256GMTS800       | 256 GB | 1       | 93    | 0     | 0.26   |
| Crucial   | CT525MX300SSD1     | 525 GB | 2       | 93    | 0     | 0.26   |
| Plextor   | PX-512M7VC         | 512 GB | 1       | 91    | 0     | 0.25   |
| OCZ       | VERTEX460A         | 120 GB | 4       | 91    | 0     | 0.25   |
| SanDisk   | SDSSDXPS240G       | 240 GB | 3       | 99    | 345   | 0.24   |
| Lite-On   | PH2-CJ120          | 120 GB | 1       | 88    | 0     | 0.24   |
| Kingston  | RBU-SNS8151S396GG  | 96 GB  | 1       | 88    | 0     | 0.24   |
| Patriot   | Blast              | 240 GB | 3       | 87    | 0     | 0.24   |
| OCZ       | ONYX               | 32 GB  | 1       | 87    | 0     | 0.24   |
| Plextor   | PX-256M5S          | 256 GB | 7       | 87    | 0     | 0.24   |
| Kingston  | SKC380S3120G       | 120 GB | 1       | 86    | 0     | 0.24   |
| Samsung   | SSD 850 EVO M.2    | 250 GB | 7       | 86    | 0     | 0.24   |
| Crucial   | CT250MX200SSD1     | 250 GB | 3       | 85    | 0     | 0.24   |
| Plextor   | PX-256M3           | 256 GB | 1       | 256   | 2     | 0.23   |
| ADATA     | SP900NS38          | 128 GB | 2       | 85    | 0     | 0.23   |
| Patriot   | Blaze              | 240 GB | 1       | 85    | 0     | 0.23   |
| SPCC      | SSD                | 120 GB | 71      | 129   | 145   | 0.23   |
| PNY       | CS1311 240GB SSD   | 240 GB | 1       | 84    | 0     | 0.23   |
| Transcend | TS256GSSD320       | 256 GB | 2       | 84    | 0     | 0.23   |
| Apple     | SSD SM0256G        | 251 GB | 1       | 83    | 0     | 0.23   |
| SPCC      | SSD                | 55 GB  | 6       | 174   | 339   | 0.23   |
| OCZ       | VECTOR180          | 120 GB | 2       | 81    | 0     | 0.22   |
| Intel     | SSDSA2M160G2LE     | 160 GB | 1       | 1872  | 22    | 0.22   |
| Samsung   | MZMPC128HBFU-000   | 128 GB | 1       | 81    | 0     | 0.22   |
| Plextor   | PX-128M5Pro        | 128 GB | 38      | 80    | 0     | 0.22   |
| Kingston  | SUV300S37A120G     | 120 GB | 15      | 79    | 0     | 0.22   |
| Corsair   | Force LS SSD       | 480 GB | 1       | 79    | 0     | 0.22   |
| Seagate   | ST120HM000-1G5142  | 120 GB | 1       | 79    | 0     | 0.22   |
| Toshiba   | Q300 Pro           | 128 GB | 1       | 79    | 0     | 0.22   |
| Kingston  | SMS200S330G        | 30 GB  | 1       | 78    | 0     | 0.22   |
| SanDisk   | SSD i100           | 8 GB   | 2       | 77    | 0     | 0.21   |
| Samsung   | SSD 750 EVO        | 120 GB | 18      | 77    | 0     | 0.21   |
| SK hynix  | SC311 SATA         | 512 GB | 1       | 77    | 0     | 0.21   |
| OCZ       | VECTOR180          | 240 GB | 1       | 76    | 0     | 0.21   |
| Patriot   | Flare              | 60 GB  | 1       | 75    | 0     | 0.21   |
| Corsair   | Neutron SSD        | 64 GB  | 2       | 174   | 6     | 0.21   |
| Intel     | SSDSC2BW240A4      | 240 GB | 7       | 74    | 0     | 0.21   |
| China     | 120GB SSD          | 120 GB | 16      | 74    | 0     | 0.21   |
| China     | 64GB SSD           | 64 GB  | 6       | 72    | 0     | 0.20   |
| Lite-On   | L8H-256V2G-HP      | 256 GB | 1       | 71    | 0     | 0.20   |
| Crucial   | CT512MX100SSD1     | 512 GB | 5       | 71    | 0     | 0.20   |
| Samsung   | SSD 650            | 120 GB | 3       | 71    | 0     | 0.19   |
| Kingston  | SS200S330G         | 30 GB  | 1       | 70    | 0     | 0.19   |
| Patriot   | Spark              | 128 GB | 3       | 70    | 0     | 0.19   |
| Toshiba   | VX500              | 256 GB | 1       | 69    | 0     | 0.19   |
| SanDisk   | PLUS               | 480 GB | 2       | 68    | 0     | 0.19   |
| ADATA     | S596               | 128 GB | 1       | 68    | 0     | 0.19   |
| Toshiba   | TR150              | 240 GB | 7       | 67    | 0     | 0.19   |
| SanDisk   | SSD U110           | 16 GB  | 8       | 67    | 0     | 0.18   |
| OCZ       | VERTEX460A         | 240 GB | 2       | 66    | 0     | 0.18   |
| Kingston  | SUV400S37120G      | 120 GB | 21      | 82    | 16    | 0.18   |
| Kingston  | SVP200S3120G       | 120 GB | 3       | 405   | 665   | 0.18   |
| Transcend | TS256GSSD340       | 256 GB | 2       | 65    | 0     | 0.18   |
| Plextor   | PX-128M6M          | 128 GB | 4       | 65    | 0     | 0.18   |
| PNY       | SSD2SC240G1LC70... | 240 GB | 1       | 64    | 0     | 0.18   |
| Intel     | SSDSA2M160G2GC     | 160 GB | 1       | 578   | 8     | 0.18   |
| Apple     | SSD SM0128G        | 121 GB | 1       | 64    | 0     | 0.18   |
| Kingston  | SKC400S37256G      | 256 GB | 1       | 64    | 0     | 0.18   |
| Intel     | SSDSC2BW120A4      | 120 GB | 20      | 70    | 1     | 0.17   |
| Intel     | SSDSC2BW080A4      | 80 GB  | 1       | 63    | 0     | 0.17   |
| Crucial   | CT128M550SSD1      | 128 GB | 3       | 88    | 30    | 0.17   |
| Fordisk   | S860 256G 6Gbps    | 256 GB | 1       | 62    | 0     | 0.17   |
| PHISON    | 128GB PS3109-S9    | 128 GB | 1       | 121   | 1     | 0.17   |
| Samsung   | MZNLN256HCHP-00000 | 256 GB | 1       | 60    | 0     | 0.17   |
| China     | SATA SSD           | 120 GB | 2       | 59    | 0     | 0.16   |
| Plextor   | PX-128M6S          | 128 GB | 20      | 65    | 56    | 0.16   |
| Crucial   | CT256M550SSD1      | 256 GB | 3       | 236   | 6     | 0.16   |
| Transcend | TS128GSSD370       | 128 GB | 5       | 58    | 0     | 0.16   |
| OCZ       | VERTEX2            | 180 GB | 1       | 58    | 0     | 0.16   |
| Kingston  | SM2280S3G2240G     | 240 GB | 1       | 57    | 0     | 0.16   |
| Samsung   | SSD 750 EVO        | 250 GB | 13      | 57    | 0     | 0.16   |
| SanDisk   | SSD U100           | 128 GB | 5       | 148   | 39    | 0.16   |
| Intel     | SSDSC2BW120H6      | 120 GB | 6       | 56    | 0     | 0.15   |
| OCZ       | VERTEX460          | 240 GB | 1       | 56    | 0     | 0.15   |
| Radeon    | R7                 | 120 GB | 1       | 56    | 0     | 0.15   |
| SanDisk   | SSD U100           | 24 GB  | 14      | 66    | 20    | 0.15   |
| Crucial   | CT250BX100SSD1     | 250 GB | 2       | 55    | 0     | 0.15   |
| Transcend | TS64GSSD340        | 64 GB  | 1       | 54    | 0     | 0.15   |
| Samsung   | SSD 850 EVO        | 1 TB   | 6       | 54    | 0     | 0.15   |
| PNY       | CS1311 120GB SSD   | 120 GB | 2       | 54    | 0     | 0.15   |
| Goodram   | SSD                | 240 GB | 2       | 53    | 0     | 0.15   |
| Samsung   | MZMPC128HBFU-000MV | 128 GB | 1       | 53    | 0     | 0.15   |
| Kingston  | SUV300S37A240G     | 240 GB | 5       | 52    | 0     | 0.14   |
| Goodram   | CX100              | 120 GB | 4       | 63    | 2     | 0.14   |
| Intel     | SSDSC2BB240G4      | 240 GB | 1       | 52    | 0     | 0.14   |
| Apple     | SSD TS256C         | 251 GB | 1       | 51    | 0     | 0.14   |
| Lite-On   | LMT-19nmBGA-128G   | 128 GB | 1       | 51    | 0     | 0.14   |
| Kingston  | SUV400S37240G      | 240 GB | 22      | 56    | 48    | 0.14   |
| Kingston  | SMS200S360G        | 60 GB  | 3       | 67    | 1     | 0.14   |
| Samsung   | SSD PB22-CS3 FD... | 256 GB | 1       | 50    | 0     | 0.14   |
| Samsung   | MZ7LF128HCHP-00004 | 128 GB | 1       | 50    | 0     | 0.14   |
| Corsair   | Neutron GTX SSD    | 480 GB | 1       | 49    | 0     | 0.14   |
| Kingston  | SA400S37240G       | 240 GB | 2       | 52    | 1     | 0.14   |
| Kingston  | SHFS37A240G        | 240 GB | 11      | 79    | 555   | 0.14   |
| Corsair   | Force LS SSD       | 60 GB  | 12      | 150   | 250   | 0.13   |
| SanDisk   | SD8SB8U256G1122    | 256 GB | 1       | 48    | 0     | 0.13   |
| SPCC      | SSD                | 64 GB  | 1       | 48    | 0     | 0.13   |
| WDC       | WDS250G1B0B-00AS40 | 250 GB | 1       | 48    | 0     | 0.13   |
| SK hynix  | HFS128G32MND-3212A | 128 GB | 1       | 48    | 0     | 0.13   |
| Micron    | 1100_MTFDDAV256TBN | 256 GB | 1       | 47    | 0     | 0.13   |
| Samsung   | MZMTD128HAFV-000   | 128 GB | 3       | 46    | 0     | 0.13   |
| SanDisk   | SD5SF2032G1010E    | 32 GB  | 1       | 45    | 0     | 0.13   |
| Micron    | MTFDDAK256MAM-1K12 | 256 GB | 2       | 64    | 505   | 0.13   |
| Crucial   | CT240BX300SSD1     | 240 GB | 1       | 45    | 0     | 0.12   |
| Kingston  | RBU-SC152S37128GG2 | 128 GB | 1       | 45    | 0     | 0.12   |
| Samsung   | MZ7TE256HMHP-000L7 | 256 GB | 1       | 45    | 0     | 0.12   |
| PRETEC    | G2000 SSD          | 29 GB  | 1       | 44    | 0     | 0.12   |
| Kingston  | SM2280S3G2120G     | 120 GB | 1       | 42    | 0     | 0.12   |
| China     | SSD128G            | 128 GB | 1       | 42    | 0     | 0.12   |
| Samsung   | SSD 850 PRO        | 512 GB | 6       | 174   | 173   | 0.12   |
| China     | 240GB SSD          | 240 GB | 1       | 41    | 0     | 0.11   |
| Samsung   | MZNLF128HCHP-00004 | 128 GB | 1       | 40    | 0     | 0.11   |
| Plextor   | PX-256M6S          | 256 GB | 7       | 44    | 145   | 0.11   |
| ADATA     | SP610              | 128 GB | 1       | 39    | 0     | 0.11   |
| Kingston  | SHSS37A240G        | 240 GB | 9       | 39    | 0     | 0.11   |
| SPCC      | SSD                | 240 GB | 19      | 92    | 518   | 0.10   |
| Toshiba   | Q300               | 120 GB | 1       | 37    | 0     | 0.10   |
| Samsung   | SSD 850 EVO mSATA  | 250 GB | 2       | 37    | 0     | 0.10   |
| SanDisk   | SD6SB1M128G1022I   | 128 GB | 2       | 37    | 0     | 0.10   |
| Crucial   | CT1024MX200SSD1    | 1 TB   | 1       | 37    | 0     | 0.10   |
| SanDisk   | SD8SN8U512G1002    | 512 GB | 1       | 37    | 0     | 0.10   |
| Micron    | MTFDDAK512MAY-1... | 512 GB | 1       | 624   | 16    | 0.10   |
| Intel     | SSDSA1M080G2HP     | 80 GB  | 1       | 476   | 12    | 0.10   |
| Patriot   | Blaze              | 60 GB  | 2       | 36    | 0     | 0.10   |
| SanDisk   | SDSSDA240G         | 240 GB | 21      | 35    | 0     | 0.10   |
| China     | SSD                | 126 GB | 1       | 34    | 0     | 0.10   |
| ZOTAC     | SATA SSD           | 120 GB | 2       | 34    | 0     | 0.09   |
| SanDisk   | SSD U110           | 63 GB  | 1       | 34    | 0     | 0.09   |
| AMD       | R5S240GBSF         | 240 GB | 1       | 33    | 0     | 0.09   |
| Intel     | SSDSA1MH080G1HP    | 80 GB  | 1       | 33    | 0     | 0.09   |
| Kingmax   | SSD                | 60 GB  | 16      | 244   | 586   | 0.09   |
| Intel     | SSDSC2BW480A4      | 480 GB | 1       | 32    | 0     | 0.09   |
| Samsung   | MZMTD128HAFV-000H1 | 128 GB | 1       | 32    | 0     | 0.09   |
| OCZ       | VERTEX4            | 79 GB  | 1       | 129   | 3     | 0.09   |
| SanDisk   | SDSSDXP120G        | 120 GB | 1       | 32    | 0     | 0.09   |
| Micron    | C400-MTFDDAK256MAM | 256 GB | 1       | 32    | 0     | 0.09   |
| Toshiba   | THNSNB062GMCJ      | 62 GB  | 1       | 32    | 0     | 0.09   |
| GLOWAY    | FER120GS3-S7       | 120 GB | 1       | 31    | 0     | 0.09   |
| OCZ       | TRION150           | 480 GB | 1       | 31    | 0     | 0.09   |
| KingSpec  | KSD-SA25.7-016MJ   | 16 GB  | 2       | 30    | 0     | 0.08   |
| Toshiba   | VT180              | 480 GB | 1       | 30    | 0     | 0.08   |
| SanDisk   | SSD i100           | 32 GB  | 2       | 30    | 0     | 0.08   |
| ADATA     | SP900NS34          | 128 GB | 1       | 30    | 0     | 0.08   |
| Micron    | MTFDDAK128MAM-1J1  | 128 GB | 1       | 29    | 0     | 0.08   |
| KingPower | 1108 SSD           | 64 GB  | 1       | 29    | 0     | 0.08   |
| Apple     | SSD SD0128F        | 121 GB | 1       | 29    | 0     | 0.08   |
| Samsung   | MZ7TY256HDHP-00000 | 256 GB | 1       | 29    | 0     | 0.08   |
| Transcend | TS120GSSD220S      | 120 GB | 3       | 29    | 0     | 0.08   |
| ADATA     | SU800NS38          | 256 GB | 1       | 29    | 0     | 0.08   |
| WDC       | WDS250G1B0A-00H9H0 | 250 GB | 4       | 29    | 0     | 0.08   |
| Samsung   | SSD Thin uSATA ... | 128 GB | 1       | 378   | 12    | 0.08   |
| SanDisk   | SDSSDA480G         | 480 GB | 1       | 28    | 0     | 0.08   |
| KingDian  | S280-240GB         | 240 GB | 5       | 27    | 0     | 0.08   |
| Samsung   | MZ7TY128HDHP-000L1 | 128 GB | 2       | 27    | 0     | 0.08   |
| AMD       | R3S60GBSM          | 60 GB  | 1       | 27    | 0     | 0.08   |
| Intel     | SSDSA1M160G2HP     | 160 GB | 3       | 73    | 4     | 0.08   |
| KingDian  | S180               | 60 GB  | 8       | 27    | 0     | 0.07   |
| KingSpec  | CHA-M2B7-M256      | 256 GB | 2       | 27    | 0     | 0.07   |
| Crucial   | CT275MX300SSD1     | 275 GB | 7       | 26    | 0     | 0.07   |
| Transcend | TS64GSSD720        | 64 GB  | 1       | 26    | 0     | 0.07   |
| ADATA     | SP900              | 512 GB | 2       | 26    | 0     | 0.07   |
| Kingston  | SHSS37A480G        | 480 GB | 3       | 26    | 0     | 0.07   |
| Smartbuy  | SSD                | 240 GB | 9       | 46    | 1     | 0.07   |
| Toshiba   | THNSNH128G8NT      | 128 GB | 1       | 25    | 0     | 0.07   |
| Smartbuy  | mSata              | 128 GB | 1       | 25    | 0     | 0.07   |
| Intenso   | SSD                | 128 GB | 2       | 48    | 1     | 0.07   |
| WDC       | WDS240G1G0A-00SS50 | 240 GB | 6       | 25    | 0     | 0.07   |
| SanDisk   | SDSA5DK-016G-1006  | 16 GB  | 1       | 24    | 0     | 0.07   |
| Corsair   | CSSD-V32GB2        | 32 GB  | 1       | 99    | 3     | 0.07   |
| SK hynix  | HFS128G39TND-N210A | 128 GB | 3       | 24    | 0     | 0.07   |
| Plextor   | PX-128M6Pro        | 128 GB | 7       | 24    | 0     | 0.07   |
| Patriot   | Spark              | 256 GB | 1       | 24    | 0     | 0.07   |
| Kingston  | SHFS37A120G        | 120 GB | 39      | 48    | 444   | 0.07   |
| Plextor   | PX-256M5M          | 256 GB | 1       | 24    | 0     | 0.07   |
| Goodram   | SSD                | 120 GB | 5       | 23    | 0     | 0.06   |
| LDLC      | SSD                | 120 GB | 2       | 23    | 0     | 0.06   |
| Intel     | SSDSA2BW160G3H     | 160 GB | 2       | 98    | 4     | 0.06   |
| Intel     | SSDSCKKW240H6      | 240 GB | 1       | 46    | 1     | 0.06   |
| GLOWAY    | FER240GS3-S7       | 240 GB | 1       | 23    | 0     | 0.06   |
| Kingston  | SV300S37A480G      | 480 GB | 5       | 34    | 202   | 0.06   |
| Toshiba   | THNSNS060GBSP      | 60 GB  | 1       | 22    | 0     | 0.06   |
| Plextor   | PX-128M6V          | 128 GB | 1       | 22    | 0     | 0.06   |
| Kingston  | SKC300S37A180G     | 180 GB | 2       | 166   | 1025  | 0.06   |
| Intel     | SSDSC2BW180A3H     | 180 GB | 1       | 22    | 0     | 0.06   |
| Samsung   | MZNLF128HCHP-00000 | 128 GB | 1       | 22    | 0     | 0.06   |
| Plextor   | PX-256M6M          | 256 GB | 3       | 29    | 1     | 0.06   |
| Kingston  | SKC400S37512G      | 512 GB | 1       | 21    | 0     | 0.06   |
| AMD       | R3SL120G           | 120 GB | 17      | 21    | 0     | 0.06   |
| ADATA     | SP600              | 128 GB | 2       | 20    | 0     | 0.06   |
| Transcend | TS128GSSD370S      | 128 GB | 10      | 20    | 0     | 0.06   |
| KingSpec  | MT-128             | 128 GB | 3       | 20    | 0     | 0.06   |
| Transcend | TS32GSSD370S       | 32 GB  | 3       | 20    | 0     | 0.06   |
| Plextor   | PX-512M5Pro        | 512 GB | 1       | 20    | 0     | 0.06   |
| SanDisk   | SDSSDH240GG25      | 240 GB | 1       | 20    | 0     | 0.06   |
| AMD       | R3SL240G           | 240 GB | 4       | 44    | 1     | 0.06   |
| SanDisk   | SSD PLUS 240 GB    | 240 GB | 2       | 20    | 0     | 0.06   |
| Samsung   | MZYLF128HCHP-000L2 | 128 GB | 1       | 20    | 0     | 0.05   |
| Netac     | SSD 120G           | 120 GB | 1       | 19    | 0     | 0.05   |
| Intel     | SSDSCKGF256A5 SATA | 256 GB | 1       | 19    | 0     | 0.05   |
| Crucial   | CT480BX200SSD1     | 480 GB | 1       | 19    | 0     | 0.05   |
| SK hynix  | SC308 SATA         | 256 GB | 1       | 18    | 0     | 0.05   |
| ADATA     | SP610              | 256 GB | 1       | 18    | 0     | 0.05   |
| Hyperdisk | SDOM               | 16 GB  | 1       | 18    | 0     | 0.05   |
| OCZ       | TRION150           | 240 GB | 1       | 18    | 0     | 0.05   |
| Apacer    | AS510S             | 64 GB  | 1       | 17    | 0     | 0.05   |
| WDC       | WDS240G1G0B-00RC30 | 240 GB | 2       | 17    | 0     | 0.05   |
| KingFast  | SSD                | 120 GB | 2       | 17    | 0     | 0.05   |
| Kingston  | SA400S37120G       | 120 GB | 6       | 17    | 0     | 0.05   |
| SanDisk   | SD6SB1M-032G-1006  | 32 GB  | 1       | 17    | 0     | 0.05   |
| Kingrich  | SSD 120G           | 120 GB | 1       | 17    | 0     | 0.05   |
| ADATA     | SX950              | 240 GB | 1       | 16    | 0     | 0.05   |
| Toshiba   | A100               | 240 GB | 1       | 16    | 0     | 0.05   |
| SanDisk   | SD6SB1M-128G-1006  | 128 GB | 1       | 16    | 0     | 0.05   |
| Transcend | TS64GSSD25S-M      | 64 GB  | 1       | 16    | 0     | 0.04   |
| China     | RTMMB256VBV4KFY    | 256 GB | 1       | 16    | 0     | 0.04   |
| Apple     | SSD SM256E         | 251 GB | 1       | 15    | 0     | 0.04   |
| SanDisk   | SD8SBAT128G1122    | 128 GB | 1       | 15    | 0     | 0.04   |
| FASTDISK  | FASTDISK120G       | 120 GB | 1       | 15    | 0     | 0.04   |
| Kingmax   | SSD                | 120 GB | 12      | 75    | 426   | 0.04   |
| FORESEE   | 240GB SSD          | 240 GB | 1       | 15    | 0     | 0.04   |
| SPCC      | SSD                | 480 GB | 1       | 15    | 0     | 0.04   |
| Samsung   | SSD 850 EVO mSATA  | 500 GB | 3       | 14    | 0     | 0.04   |
| FASTDISK  | SSD 60G            | 60 GB  | 1       | 14    | 0     | 0.04   |
| Seagate   | ST480FP0021        | 480 GB | 1       | 14    | 0     | 0.04   |
| Transcend | TS256GSSD370S      | 256 GB | 1       | 14    | 0     | 0.04   |
| KingFast  | SSD                | 128 GB | 6       | 14    | 0     | 0.04   |
| Micron    | M600_MTFDDAK1T0MBF | 1 TB   | 1       | 13    | 0     | 0.04   |
| Samsung   | MZNTY128HDHP-00000 | 128 GB | 1       | 13    | 0     | 0.04   |
| OCZ       | VECTOR180          | 960 GB | 1       | 13    | 0     | 0.04   |
| Intel     | SSDSC2BB240G7      | 240 GB | 1       | 13    | 0     | 0.04   |
| Samsung   | MZYTY128HDHP-000L2 | 128 GB | 1       | 13    | 0     | 0.04   |
| SanDisk   | SSD U100           | 64 GB  | 2       | 13    | 0     | 0.04   |
| SanDisk   | SDSSDA120G         | 120 GB | 18      | 13    | 0     | 0.04   |
| China     | 128GB SSD          | 128 GB | 2       | 13    | 0     | 0.04   |
| Transcend | TS512GMSA370       | 512 GB | 1       | 12    | 0     | 0.03   |
| KingDian  | S400               | 120 GB | 2       | 12    | 0     | 0.03   |
| KingDian  | S280               | 240 GB | 2       | 11    | 0     | 0.03   |
| WDC       | WDS120G1G0A-00SS50 | 120 GB | 8       | 11    | 0     | 0.03   |
| China     | SSD                | 120 GB | 2       | 11    | 0     | 0.03   |
| ADATA     | IM2S3138E-128GM-B  | 128 GB | 1       | 11    | 0     | 0.03   |
| Crucial   | CT250MX500SSD1     | 250 GB | 1       | 11    | 0     | 0.03   |
| Crucial   | V4-CT128V4SSD2     | 128 GB | 1       | 11    | 0     | 0.03   |
| Crucial   | CT2050MX300SSD1    | 2 TB   | 1       | 33    | 2     | 0.03   |
| ADATA     | SU800              | 128 GB | 9       | 15    | 10    | 0.03   |
| AMD       | R5SL240G           | 240 GB | 1       | 10    | 0     | 0.03   |
| ADATA     | SX300              | 128 GB | 1       | 10    | 0     | 0.03   |
| KingSpec  | T-60               | 60 GB  | 2       | 10    | 0     | 0.03   |
| Intel     | SSDSA2CW160G3      | 160 GB | 1       | 10    | 0     | 0.03   |
| TEAM      | L5 LITE SSD        | 120 GB | 1       | 10    | 0     | 0.03   |
| Intel     | SSDSA2M080G2GN     | 80 GB  | 1       | 152   | 14    | 0.03   |
| Samsung   | MZ7TE512HMHP-000L2 | 512 GB | 1       | 10    | 0     | 0.03   |
| WDC       | WDS500G1B0A-00H9H0 | 500 GB | 1       | 10    | 0     | 0.03   |
| LDLC      | SSD                | 128 GB | 2       | 9     | 0     | 0.03   |
| Plextor   | PX-AG128M6e        | 128 GB | 2       | 9     | 0     | 0.03   |
| Crucial   | CT480M500SSD1      | 480 GB | 1       | 166   | 16    | 0.03   |
| Crucial   | CT240M500SSD3      | 240 GB | 2       | 166   | 16    | 0.03   |
| SPCC      | SSD162             | 240 GB | 1       | 203   | 20    | 0.03   |
| Lite-On   | CV1-8B128          | 128 GB | 2       | 9     | 0     | 0.03   |
| Faspeed   | H5-120G PLUS       | 120 GB | 1       | 9     | 0     | 0.03   |
| KingSpec  | ACSC2M064mSA       | 63 GB  | 1       | 9     | 0     | 0.03   |
| Intel     | SSDSC2BW240H6      | 240 GB | 2       | 9     | 0     | 0.03   |
| Patriot   | Blaze              | 120 GB | 3       | 9     | 0     | 0.03   |
| Intel     | SSDMCEAW180A4      | 180 GB | 1       | 9     | 0     | 0.02   |
| KingDian  | S280               | 480 GB | 1       | 9     | 0     | 0.02   |
| Kingston  | SKC400S37128G      | 128 GB | 1       | 8     | 0     | 0.02   |
| KingDian  | N400 60G           | 60 GB  | 1       | 8     | 0     | 0.02   |
| SanDisk   | SD7SN6S-128G-1006  | 128 GB | 1       | 8     | 0     | 0.02   |
| FORESEE   | 64GB SSD           | 64 GB  | 1       | 8     | 0     | 0.02   |
| Kingston  | RBU-SNS8100S312... | 128 GB | 2       | 8     | 0     | 0.02   |
| ADATA     | SP550              | 120 GB | 13      | 8     | 0     | 0.02   |
| SanDisk   | Ultra II           | 240 GB | 4       | 7     | 0     | 0.02   |
| PNY       | SSD2SC256GM1P3D... | 256 GB | 1       | 7     | 0     | 0.02   |
| Transcend | TS128GMTS800       | 128 GB | 3       | 7     | 0     | 0.02   |
| ADATA     | SU900              | 256 GB | 1       | 7     | 0     | 0.02   |
| FASTDISK  | SSD 120G           | 120 GB | 1       | 7     | 0     | 0.02   |
| ADATA     | SP580              | 120 GB | 3       | 7     | 0     | 0.02   |
| Toshiba   | TL100              | 240 GB | 1       | 7     | 0     | 0.02   |
| ADATA     | SP920SS            | 256 GB | 3       | 81    | 11    | 0.02   |
| Toshiba   | THNSNS128GMCP      | 128 GB | 1       | 7     | 0     | 0.02   |
| Crucial   | CT240BX200SSD1     | 240 GB | 3       | 7     | 0     | 0.02   |
| Kingston  | SMS200S3120G       | 120 GB | 3       | 17    | 254   | 0.02   |
| FORESEE   | 128GB SSD          | 128 GB | 1       | 6     | 0     | 0.02   |
| Patriot   | Ignite             | 240 GB | 1       | 6     | 0     | 0.02   |
| Kingston  | SH103S3480G        | 480 GB | 1       | 6     | 0     | 0.02   |
| Samsung   | SSD PM871b 2.5 7mm | 128 GB | 1       | 6     | 0     | 0.02   |
| Lite-On   | LMT-32L3M-HP       | 32 GB  | 1       | 6     | 0     | 0.02   |
| Lite-On   | CV5-8Q512-HP       | 512 GB | 1       | 6     | 0     | 0.02   |
| Toshiba   | A100               | 120 GB | 2       | 6     | 0     | 0.02   |
| Lite-On   | L8H-256V2G-11 M... | 256 GB | 1       | 6     | 0     | 0.02   |
| Smartbuy  | SSD                | 240 GB | 1       | 6     | 0     | 0.02   |
| ADATA     | SP550              | 240 GB | 5       | 6     | 0     | 0.02   |
| GeIL      | Zenith A3-PRO      | 240 GB | 1       | 6     | 0     | 0.02   |
| GeIL      | Zenith A3          | 120 GB | 1       | 6     | 0     | 0.02   |
| Plextor   | PX-G256M6e         | 256 GB | 1       | 5     | 0     | 0.02   |
| SanDisk   | SD7SB3Q128G1002    | 128 GB | 1       | 17    | 2     | 0.02   |
| OCZ       | ARC100             | 480 GB | 1       | 11    | 1     | 0.02   |
| MicroData | MD500 120G         | 120 GB | 1       | 5     | 0     | 0.01   |
| Mushkin   | MKNSSDCG480GB      | 480 GB | 2       | 116   | 508   | 0.01   |
| Plextor   | PX-AG256M6e        | 256 GB | 1       | 4     | 0     | 0.01   |
| BIWIN     | SSD                | 128 GB | 2       | 4     | 0     | 0.01   |
| Transcend | TS128GSSD360S      | 128 GB | 3       | 4     | 0     | 0.01   |
| SanDisk   | SD8SB8U512G1122    | 512 GB | 1       | 4     | 0     | 0.01   |
| Samsung   | MZNLN256HCHP-000L7 | 256 GB | 1       | 4     | 0     | 0.01   |
| Samsung   | SSD 750 EVO        | 500 GB | 2       | 4     | 0     | 0.01   |
| Crucial   | CT525MX300SSD4     | 525 GB | 1       | 4     | 0     | 0.01   |
| AMD       | R5SL120G           | 120 GB | 2       | 4     | 0     | 0.01   |
| SanDisk   | SD8SNAT256G1002    | 256 GB | 1       | 4     | 0     | 0.01   |
| GeIL      | ZENITH-A3 120G     | 120 GB | 1       | 3     | 0     | 0.01   |
| Crucial   | CT512M550SSD1      | 512 GB | 1       | 63    | 16    | 0.01   |
| KingSpec  | ACJC2M032mSH       | 32 GB  | 1       | 3     | 0     | 0.01   |
| Toshiba   | Q300               | 240 GB | 1       | 32    | 8     | 0.01   |
| CHN       | 25SATA01M 060      | 60 GB  | 1       | 3     | 0     | 0.01   |
| Intel     | SSDSA1M080G2LE     | 80 GB  | 1       | 87    | 24    | 0.01   |
| OCZ       | REVODRIVE X2       | 60 GB  | 4       | 1204  | 516   | 0.01   |
| SPCC      | SSDB27             | 32 GB  | 1       | 23    | 6     | 0.01   |
| SanDisk   | SD8SBAT256G1122    | 256 GB | 2       | 3     | 0     | 0.01   |
| SanDisk   | SSD i110           | 16 GB  | 1       | 3     | 0     | 0.01   |
| Transcend | TS256GMTS400       | 256 GB | 1       | 2     | 0     | 0.01   |
| Samsung   | MZ7LN256HMJP-000H1 | 256 GB | 2       | 2     | 0     | 0.01   |
| Transcend | TS128GSSD230S      | 128 GB | 3       | 2     | 0     | 0.01   |
| KingSpec  | ACSC2M128S25       | 126 GB | 1       | 2     | 0     | 0.01   |
| SanDisk   | SSD i110           | 126 GB | 1       | 2     | 0     | 0.01   |
| Fordisk   | SATA SSD           | 120 GB | 1       | 2     | 0     | 0.01   |
| Samsung   | MZNLN512HCJH-000H1 | 512 GB | 1       | 2     | 0     | 0.01   |
| SanDisk   | SDSA5GK-016G-1006  | 16 GB  | 1       | 276   | 106   | 0.01   |
| Intel     | SSDSC2KW240H6      | 240 GB | 1       | 2     | 0     | 0.01   |
| Transcend | TS64GSSD370        | 64 GB  | 2       | 2     | 0     | 0.01   |
| SanDisk   | SSD i110           | 24 GB  | 1       | 2     | 0     | 0.01   |
| Transcend | TS64GMTS800        | 64 GB  | 1       | 2     | 0     | 0.01   |
| SanDisk   | SSD P4             | 32 GB  | 8       | 79    | 151   | 0.01   |
| Samsung   | SSD 850            | 120 GB | 3       | 2     | 0     | 0.01   |
| SanDisk   | SDSSDH120GG25      | 120 GB | 1       | 112   | 55    | 0.01   |
| Kingrich  | 64GB K9 SATA3 SSD  | 63 GB  | 1       | 2     | 0     | 0.01   |
| Intel     | SSDSC2BP480G4      | 480 GB | 1       | 1     | 0     | 0.01   |
| Samsung   | SSD 860 PRO        | 512 GB | 1       | 1     | 0     | 0.01   |
| Transcend | TS32GMSA370        | 32 GB  | 1       | 1     | 0     | 0.01   |
| Kingston  | SKC300S37A240G     | 240 GB | 2       | 1     | 0     | 0.01   |
| China     | SSD 120G           | 120 GB | 1       | 1     | 0     | 0.01   |
| KingSpec  | P3D-240            | 240 GB | 1       | 1     | 0     | 0.01   |
| FASTDISK  | SSD                | 64 GB  | 1       | 1     | 0     | 0.00   |
| Plextor   | PX-128S2C          | 128 GB | 1       | 1     | 0     | 0.00   |
| FASTDISK  | SSD 30G            | 30 GB  | 1       | 1     | 0     | 0.00   |
| KingSpec  | ACJC2M064S25       | 63 GB  | 1       | 1     | 0     | 0.00   |
| Micron    | C400-MTFDDAT064MAM | 64 GB  | 1       | 1     | 0     | 0.00   |
| ADATA     | SU700              | 120 GB | 1       | 1     | 0     | 0.00   |
| China     | SSD 256G           | 256 GB | 1       | 1     | 0     | 0.00   |
| Samsung   | SSD 850 EVO mSATA  | 1 TB   | 1       | 1     | 0     | 0.00   |
| SanDisk   | SD8SN8U-128G-1006  | 128 GB | 4       | 5     | 1     | 0.00   |
| SK hynix  | SC210 mSATA        | 128 GB | 1       | 5     | 3     | 0.00   |
| Samsung   | MZ7LF120HCHP-000L1 | 120 GB | 1       | 1     | 0     | 0.00   |
| Plextor   | PX-256M6Pro        | 256 GB | 1       | 1     | 0     | 0.00   |
| Plextor   | PX-512M6M          | 512 GB | 1       | 1     | 0     | 0.00   |
| SanDisk   | SD8SNAT256G1122    | 256 GB | 1       | 1     | 0     | 0.00   |
| KingDian  | S280-120GB         | 120 GB | 2       | 1     | 0     | 0.00   |
| China     | SSD60G             | 60 GB  | 2       | 1     | 0     | 0.00   |
| Samsung   | MZNTY128HDHP-000H1 | 128 GB | 1       | 1     | 0     | 0.00   |
| GeIL      | ZENITH R3_120GB    | 120 GB | 1       | 1     | 0     | 0.00   |
| Micron    | 1100_MTFDDAK256TBN | 256 GB | 1       | 1     | 0     | 0.00   |
| KingSpec  | ACJC2M128S25       | 126 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WDS120G1G0B-00RC30 | 120 GB | 1       | 1     | 0     | 0.00   |
| Samsung   | MZMTD512HAGL-000L1 | 512 GB | 1       | 107   | 97    | 0.00   |
| SanDisk   | SSD P4             | 64 GB  | 1       | 14    | 14    | 0.00   |
| SK hynix  | SC210 2.5 7MM      | 128 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD6SB1M256G1022I   | 256 GB | 1       | 400   | 474   | 0.00   |
| SK hynix  | HFS060G32MNM-1010U | 60 GB  | 1       | 822   | 1016  | 0.00   |
| Golden... | GDSA25-120MS       | 120 GB | 1       | 0     | 0     | 0.00   |
| Plextor   | PX-128M6MV         | 128 GB | 1       | 0     | 0     | 0.00   |
| China     | SATA SSD           | 240 GB | 2       | 0     | 0     | 0.00   |
| Crucial   | CT120M500SSD3      | 120 GB | 1       | 12    | 16    | 0.00   |
| WDC       | WDS250G2B0A-00SM50 | 250 GB | 1       | 0     | 0     | 0.00   |
| Indilinx  | InM2246S3-128G     | 128 GB | 1       | 0     | 0     | 0.00   |
| KingSpec  | MT-64              | 64 GB  | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD8TN8U512G1001    | 512 GB | 1       | 0     | 0     | 0.00   |
| KingSpec  | ACSC2M064S25       | 63 GB  | 1       | 0     | 0     | 0.00   |
| QUMO      | SSD                | 480 GB | 1       | 625   | 1015  | 0.00   |
| Toshiba   | THNSNK256GVN8 M... | 256 GB | 1       | 60    | 100   | 0.00   |
| SPCC      | SSD170             | 55 GB  | 1       | 593   | 1017  | 0.00   |
| KingSpec  | ACSC2M128mSA       | 126 GB | 1       | 0     | 0     | 0.00   |
| QUMO      | SSD                | 120 GB | 1       | 579   | 1017  | 0.00   |
| Intenso   | SSD Sata III       | 247 GB | 1       | 18    | 32    | 0.00   |
| SK hynix  | HFS128G38MNB-2200A | 128 GB | 2       | 41    | 120   | 0.00   |
| Gost      | SSD120             | 120 GB | 1       | 0     | 0     | 0.00   |
| KingSpec  | MSH-256            | 253 GB | 1       | 0     | 0     | 0.00   |
| China     | T60                | 60 GB  | 2       | 0     | 0     | 0.00   |
| KingFast  | SSD                | 256 GB | 1       | 0     | 0     | 0.00   |
| Plextor   | PX-128S3C          | 128 GB | 1       | 0     | 0     | 0.00   |
| Kingston  | SH103S3240G-NV     | 240 GB | 1       | 377   | 1018  | 0.00   |
| PNY       | SSD2SC120GE2DA0... | 120 GB | 1       | 373   | 1018  | 0.00   |
| SPCC      | SSD170             | 64 GB  | 1       | 358   | 1016  | 0.00   |
| Mushkin   | MKNSSDCL120GB-DX   | 120 GB | 1       | 348   | 1006  | 0.00   |
| Lite-On   | CS1-SP32-11 M.2... | 32 GB  | 1       | 1     | 4     | 0.00   |
| Mushkin   | MKNSSDCL480GB-DX   | 480 GB | 1       | 347   | 1020  | 0.00   |
| SanDisk   | SDSSDXPS960G       | 960 GB | 1       | 13    | 39    | 0.00   |
| Lite-On   | LCH-128V2S-11 2... | 128 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD8SNAT-256G-1006  | 256 GB | 1       | 0     | 0     | 0.00   |
| KingFast  | SSD                | 60 GB  | 1       | 0     | 1     | 0.00   |
| Kingston  | SVP200S37A256G     | 256 GB | 1       | 311   | 1017  | 0.00   |
| FASTDISK  | SSD 32G            | 32 GB  | 1       | 0     | 0     | 0.00   |
| GLOWAY    | STK120GS3-S7       | 120 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | CV1-8B512          | 512 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | CV3-8D256-11 SATA  | 256 GB | 1       | 0     | 0     | 0.00   |
| Patriot   | Torch LE           | 120 GB | 1       | 0     | 0     | 0.00   |
| Apacer    | AS330              | 120 GB | 1       | 0     | 0     | 0.00   |
| China     | SATA SSD           | 60 GB  | 1       | 0     | 0     | 0.00   |
| Kingmax   | SSD                | 240 GB | 1       | 0     | 0     | 0.00   |
| Samsung   | MZNTY256HDHP-00000 | 256 GB | 1       | 0     | 0     | 0.00   |
| GeIL      | ZENITH S3-120GB    | 120 GB | 1       | 245   | 1021  | 0.00   |
| Samsung   | MZ7PA256HMDR-010H1 | 256 GB | 1       | 236   | 1040  | 0.00   |
| Goldenfir | T650-120G          | 126 GB | 1       | 0     | 0     | 0.00   |
| KingDian  | S200               | 120 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | S960 256           | 256 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD8SBAT-032G-1006  | 32 GB  | 2       | 0     | 0     | 0.00   |
| WDC       | WDS100T1B0A-00H9H0 | 1 TB   | 1       | 0     | 0     | 0.00   |
| Zheino    | CHN25SATAS1 064    | 64 GB  | 1       | 0     | 0     | 0.00   |
| Patriot   | Pyro SE            | 240 GB | 1       | 180   | 1016  | 0.00   |
| China     | T120               | 120 GB | 1       | 0     | 0     | 0.00   |
| Faspeed   | H5-30G             | 30 GB  | 1       | 0     | 0     | 0.00   |
| KingDian  | S200               | 60 GB  | 1       | 0     | 0     | 0.00   |
| China     | 80GB SSD           | 80 GB  | 2       | 0     | 0     | 0.00   |
| Intel     | SSDMCEAW080A4 m... | 80 GB  | 1       | 124   | 1009  | 0.00   |
| Lite-On   | LSS-16L6G-HP       | 16 GB  | 1       | 125   | 1275  | 0.00   |
| Kingston  | SMS151S324G        | 24 GB  | 1       | 95    | 1022  | 0.00   |
| Plextor   | PX-32G5L           | 32 GB  | 1       | 0     | 0     | 0.00   |
| Micron    | MTFDDAT064MAM-1J2  | 64 GB  | 1       | 85    | 1039  | 0.00   |
| PNY       | SSD2SC240G1SA75... | 240 GB | 1       | 7     | 88    | 0.00   |
| Transcend | TS64GSSD340K       | 64 GB  | 1       | 74    | 1008  | 0.00   |
| Mushkin   | MKNSSDCR120GB-DX7  | 120 GB | 1       | 73    | 1016  | 0.00   |
| SanDisk   | SDSSDX480GG25      | 480 GB | 1       | 76    | 1090  | 0.00   |
| MicroData | MD300 128G         | 126 GB | 1       | 41    | 666   | 0.00   |
| Samsung   | MZMPA128HMFU-000H1 | 128 GB | 2       | 69    | 1727  | 0.00   |
| ADATA     | SU650              | 120 GB | 1       | 0     | 0     | 0.00   |
| Intel     | SSDSC2BB150G7      | 150 GB | 1       | 0     | 0     | 0.00   |
| KingDian  | S180               | 120 GB | 1       | 0     | 0     | 0.00   |
| SPCC      | M.2 SSD            | 120 GB | 1       | 0     | 0     | 0.00   |
| Corsair   | Force LS SSD       | 240 GB | 1       | 16    | 412   | 0.00   |
| ADATA     | SX300              | 64 GB  | 1       | 32    | 1020  | 0.00   |
| SanDisk   | TE22D10400GE8001   | 400 GB | 1       | 34    | 2047  | 0.00   |
| SanDisk   | SSD U100           | 32 GB  | 1       | 16    | 1006  | 0.00   |
| AMD       | R5S120GBSF         | 120 GB | 1       | 15    | 1016  | 0.00   |
| Samsung   | MZNLN128HAHQ-000H1 | 128 GB | 1       | 0     | 100   | 0.00   |
| Lite-On   | L8T-128L6G-HP      | 128 GB | 1       | 1     | 1279  | 0.00   |
| ADATA     | SX900              | 256 GB | 1       | 0     | 1023  | 0.00   |
| SMI       | SSD DISK           | 506 GB | 1       | 0     | 1957  | 0.00   |
| Mushkin   | MKNSSDCR120GB-7    | 120 GB | 1       | 0     | 1023  | 0.00   |

SSD by Family
--------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

| MFG       | Family                 | Models | Samples | Days  | Err   | Rating |
|-----------|------------------------|--------|---------|-------|-------|--------|
| Toshiba   | HG2 Series             | 2      | 3       | 832   | 0     | 2.28   |
| Crucial   | RealSSD m4/C400/P400   | 2      | 8       | 548   | 0     | 1.50   |
| Apple     | SD/SM/TS E/F/G SSDs    | 1      | 1       | 545   | 0     | 1.49   |
| Crucial   | RealSSD m4/C400        | 4      | 20      | 526   | 51    | 1.40   |
| Toshiba   | HG5 Series             | 1      | 2       | 471   | 0     | 1.29   |
| Verbatim  | Unknown                | 1      | 1       | 470   | 0     | 1.29   |
| Foxline   | Unknown                | 1      | 1       | 443   | 0     | 1.22   |
| OCZ       | SandForce Driven SSDs  | 30     | 168     | 549   | 43    | 1.17   |
| Toshiba   | HG3 Series             | 3      | 3       | 403   | 0     | 1.11   |
| OCZ       | Indilinx Barefoot_2... | 11     | 77      | 386   | 4     | 0.99   |
| KingShare | Unknown                | 1      | 1       | 358   | 0     | 0.98   |
| Kingston  | JMicron based SSDs     | 9      | 21      | 416   | 2     | 0.97   |
| Corsair   | SandForce Driven SSDs  | 18     | 76      | 413   | 95    | 0.96   |
| Intel     | 520 Series SSDs        | 2      | 2       | 315   | 0     | 0.86   |
| Intel     | 510 Series SSDs        | 1      | 1       | 311   | 0     | 0.85   |
| Ramaxel   | Unknown                | 1      | 2       | 295   | 0     | 0.81   |
| Intel     | 320 Series SSDs        | 5      | 13      | 272   | 0     | 0.75   |
| Mushkin   | SandForce Driven SSDs  | 6      | 6       | 372   | 678   | 0.67   |
| Toshiba   | HG5d Series            | 7      | 10      | 244   | 0     | 0.67   |
| HP        | Unknown                | 1      | 1       | 238   | 0     | 0.65   |
| Apple     | JMicron based SSDs     | 2      | 2       | 233   | 0     | 0.64   |
| ADATA     | SandForce Driven SSDs  | 7      | 43      | 276   | 9     | 0.62   |
| Intel     | 330/335 Series SSDs    | 2      | 9       | 224   | 0     | 0.62   |
| Intel     | Unknown                | 6      | 8       | 234   | 127   | 0.55   |
| Kingston  | SandForce Driven SSDs  | 27     | 435     | 210   | 32    | 0.51   |
| Intel     | X18-M/X25-M/X25-V G... | 9      | 15      | 533   | 8     | 0.51   |
| Toshiba   | HG6 Series SSD         | 3      | 7       | 186   | 0     | 0.51   |
| Samsung   | Unknown                | 9      | 13      | 217   | 3     | 0.50   |
| OCZ       | Indilinx Barefoot b... | 2      | 2       | 183   | 0     | 0.50   |
| Transcend | SandForce Driven SSDs  | 4      | 6       | 177   | 0     | 0.49   |
| Samsung   | based SSDs             | 64     | 378     | 178   | 9     | 0.48   |
| OCZ       | Indilinx Barefoot 3... | 9      | 25      | 163   | 1     | 0.45   |
| Samsung   | Samsung based SSDs     | 25     | 40      | 170   | 93    | 0.45   |
| SanDisk   | Marvell based SanDi... | 22     | 76      | 167   | 21    | 0.44   |
| Crucial   | RealSSD C300/M500      | 7      | 24      | 270   | 96    | 0.41   |
| OCZ       | Trion SSDs             | 4      | 10      | 147   | 1     | 0.40   |
| Micron    | Unknown                | 6      | 6       | 257   | 176   | 0.40   |
| Crucial   | MX100/M500/M510/M55... | 2      | 13      | 142   | 0     | 0.39   |
| Apacer    | Unknown                | 4      | 4       | 140   | 0     | 0.38   |
| Intel     | X18-M/X25-M G1 SSDs    | 2      | 2       | 139   | 0     | 0.38   |
| Corsair   | Unknown                | 5      | 9       | 174   | 34    | 0.38   |
| Smartbuy  | Unknown                | 8      | 68      | 138   | 1     | 0.37   |
| Toshiba   | Unknown                | 11     | 13      | 139   | 9     | 0.36   |
| OCZ       | Unknown                | 8      | 15      | 131   | 0     | 0.36   |
| Chiprex   | Unknown                | 1      | 1       | 126   | 0     | 0.35   |
| Crucial   | MX100/MX200/M5x0/M6... | 6      | 15      | 229   | 145   | 0.34   |
| TEAM      | Unknown                | 3      | 3       | 112   | 0     | 0.31   |
| ADATA     | JMicron based SSDs     | 5      | 14      | 117   | 1     | 0.31   |
| Intel     | 730 and DC S3500/S3... | 3      | 3       | 110   | 0     | 0.30   |
| Plextor   | Unknown                | 16     | 29      | 108   | 0     | 0.30   |
| SPCC      | Unknown                | 17     | 168     | 162   | 187   | 0.29   |
| Intel     | 525 Series SSDs        | 1      | 2       | 105   | 0     | 0.29   |
| Goodram   | Unknown                | 5      | 16      | 106   | 1     | 0.29   |
| Transcend | Indilinx Barefoot b... | 1      | 1       | 309   | 2     | 0.28   |
| China     | Unknown                | 21     | 56      | 104   | 1     | 0.27   |
| Toshiba   | HG6 Series             | 1      | 1       | 98    | 0     | 0.27   |
| SanDisk   | SanDisk based SSDs     | 17     | 79      | 111   | 32    | 0.27   |
| Intel     | 530 Series SSDs        | 4      | 33      | 101   | 1     | 0.27   |
| Plextor   | M3/M5 (Pro) Series ... | 8      | 61      | 108   | 18    | 0.27   |
| Plextor   | M3/M5/M6 Series SSDs   | 7      | 71      | 92    | 30    | 0.25   |
| Toshiba   | OCZ                    | 5      | 12      | 85    | 0     | 0.23   |
| Transcend | JMicron based SSDs     | 4      | 7       | 82    | 0     | 0.23   |
| Seagate   | 600 Series             | 1      | 1       | 79    | 0     | 0.22   |
| ADATA     | Unknown                | 24     | 49      | 159   | 170   | 0.21   |
| SanDisk   | Unknown                | 27     | 40      | 99    | 86    | 0.20   |
| Kingston  | Phison Driven SSDs     | 8      | 41      | 70    | 0     | 0.19   |
| PNY       | Phison Driven SSDs     | 2      | 3       | 64    | 0     | 0.18   |
| PHISON    | Unknown                | 1      | 1       | 121   | 1     | 0.17   |
| Radeon    | Indilinx Barefoot 3... | 1      | 1       | 56    | 0     | 0.15   |
| Intel     | 730 and DC S35x0/36... | 4      | 4       | 55    | 0     | 0.15   |
| KingFast  | Unknown                | 7      | 13      | 52    | 1     | 0.14   |
| Patriot   | Unknown                | 11     | 20      | 61    | 51    | 0.14   |
| Kingston  | Unknown                | 19     | 118     | 72    | 236   | 0.14   |
| PNY       | Unknown                | 5      | 5       | 125   | 222   | 0.14   |
| KingSpec  | Unknown                | 17     | 22      | 49    | 0     | 0.14   |
| SanDisk   | SandForce Driven SSDs  | 5      | 45      | 50    | 25    | 0.13   |
| Apple     | SD/SM/TS E/F SSDs      | 4      | 4       | 48    | 0     | 0.13   |
| QUMO      | Unknown                | 3      | 3       | 449   | 678   | 0.13   |
| PRETEC    | Unknown                | 1      | 1       | 44    | 0     | 0.12   |
| Intel     | 53x and Pro 2500 Se... | 4      | 10      | 42    | 0     | 0.12   |
| Crucial   | MX1/2/300, M5/600, ... | 6      | 14      | 52    | 3     | 0.12   |
| Micron    | RealSSD m4/C400/P400   | 3      | 4       | 47    | 253   | 0.11   |
| ZOTAC     | Unknown                | 1      | 2       | 34    | 0     | 0.09   |
| Fordisk   | Unknown                | 2      | 2       | 32    | 0     | 0.09   |
| Toshiba   | SG2 Series             | 1      | 1       | 32    | 0     | 0.09   |
| KingPower | Unknown                | 1      | 1       | 29    | 0     | 0.08   |
| Transcend | SiliconMotion based... | 14     | 36      | 26    | 0     | 0.07   |
| Crucial   | SiliconMotion based... | 3      | 6       | 25    | 0     | 0.07   |
| SK hynix  | Unknown                | 5      | 8       | 138   | 157   | 0.07   |
| WDC       | Blue PC SSD            | 4      | 7       | 25    | 0     | 0.07   |
| Corsair   | Indilinx Barefoot b... | 1      | 1       | 99    | 3     | 0.07   |
| Kingmax   | Unknown                | 3      | 29      | 166   | 500   | 0.07   |
| Transcend | Unknown                | 3      | 5       | 38    | 202   | 0.07   |
| Crucial   | Unknown                | 3      | 3       | 22    | 0     | 0.06   |
| Lite-On   | Unknown                | 15     | 16      | 29    | 160   | 0.06   |
| Netac     | Unknown                | 1      | 1       | 19    | 0     | 0.05   |
| AMD       | Unknown                | 7      | 27      | 23    | 38    | 0.05   |
| GLOWAY    | Unknown                | 3      | 3       | 18    | 0     | 0.05   |
| Hyperdisk | Unknown                | 1      | 1       | 18    | 0     | 0.05   |
| KingDian  | Unknown                | 10     | 24      | 17    | 0     | 0.05   |
| Intenso   | Unknown                | 2      | 3       | 38    | 11    | 0.05   |
| LDLC      | Unknown                | 2      | 4       | 16    | 0     | 0.05   |
| WDC       | Green PC SSD           | 3      | 15      | 16    | 0     | 0.05   |
| Seagate   | 600 Pro Series         | 1      | 1       | 14    | 0     | 0.04   |
| Micron    | MX100/MX200/M5x0/M6... | 1      | 1       | 13    | 0     | 0.04   |
| Intel     | 540 Series SSDs        | 2      | 2       | 24    | 1     | 0.03   |
| WDC       | Unknown                | 2      | 3       | 12    | 0     | 0.03   |
| FORESEE   | Unknown                | 3      | 3       | 10    | 0     | 0.03   |
| Kingrich  | Unknown                | 2      | 2       | 9     | 0     | 0.03   |
| ADATA     | SiliconMotion based... | 2      | 18      | 7     | 0     | 0.02   |
| FASTDISK  | Unknown                | 6      | 6       | 7     | 0     | 0.02   |
| SK hynix  | SATA SSDs              | 3      | 3       | 8     | 1     | 0.02   |
| Mushkin   | Unknown                | 1      | 2       | 116   | 508   | 0.01   |
| Faspeed   | Unknown                | 2      | 2       | 4     | 0     | 0.01   |
| BIWIN     | Unknown                | 1      | 2       | 4     | 0     | 0.01   |
| CHN       | Unknown                | 1      | 1       | 3     | 0     | 0.01   |
| GeIL      | Unknown                | 5      | 5       | 52    | 205   | 0.01   |
| MicroData | Unknown                | 2      | 2       | 23    | 333   | 0.01   |
| Golden... | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| Indilinx  | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| Gost      | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| Goldenfir | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| Zheino    | Unknown                | 1      | 1       | 0     | 0     | 0.00   |
| SMI       | Unknown                | 1      | 1       | 0     | 1957  | 0.00   |

SSD by Vendor
-------------

Please take all columns into account when reading the table. Pay attention on the
number of tested samples and power-on days. Simultaneous high values of both rating
and errors are possible if only rare drives in the subset encounter errors.

Days   — avg. days per sample,
Err    — avg. errors per sample,
Rating — avg. rating per sample.

| MFG         | Models | Samples | Days  | Err   | Rating |
|-------------|--------|---------|-------|-------|--------|
| Verbatim    | 1      | 1       | 470   | 0     | 1.29   |
| Foxline     | 1      | 1       | 443   | 0     | 1.22   |
| OCZ         | 64     | 297     | 437   | 26    | 0.99   |
| KingShare   | 1      | 1       | 358   | 0     | 0.98   |
| Corsair     | 24     | 86      | 384   | 88    | 0.89   |
| Ramaxel     | 1      | 2       | 295   | 0     | 0.81   |
| HP          | 1      | 1       | 238   | 0     | 0.65   |
| Crucial     | 33     | 103     | 268   | 54    | 0.60   |
| Toshiba     | 34     | 52      | 218   | 3     | 0.59   |
| Mushkin     | 7      | 8       | 308   | 635   | 0.51   |
| Samsung     | 98     | 431     | 178   | 17    | 0.48   |
| Apple       | 7      | 7       | 172   | 0     | 0.47   |
| Kingston    | 63     | 615     | 181   | 68    | 0.44   |
| Intel       | 45     | 104     | 204   | 11    | 0.41   |
| Apacer      | 4      | 4       | 140   | 0     | 0.38   |
| Smartbuy    | 8      | 68      | 138   | 1     | 0.37   |
| Chiprex     | 1      | 1       | 126   | 0     | 0.35   |
| ADATA       | 38     | 124     | 173   | 70    | 0.34   |
| TEAM        | 3      | 3       | 112   | 0     | 0.31   |
| SPCC        | 17     | 168     | 162   | 187   | 0.29   |
| SanDisk     | 71     | 240     | 115   | 36    | 0.29   |
| Goodram     | 5      | 16      | 106   | 1     | 0.29   |
| China       | 21     | 56      | 104   | 1     | 0.27   |
| Plextor     | 31     | 161     | 101   | 20    | 0.26   |
| Micron      | 10     | 11      | 159   | 188   | 0.26   |
| PHISON      | 1      | 1       | 121   | 1     | 0.17   |
| Radeon      | 1      | 1       | 56    | 0     | 0.15   |
| PNY         | 7      | 8       | 102   | 139   | 0.15   |
| KingFast    | 7      | 13      | 52    | 1     | 0.14   |
| Patriot     | 11     | 20      | 61    | 51    | 0.14   |
| Transcend   | 26     | 55      | 56    | 19    | 0.14   |
| KingSpec    | 17     | 22      | 49    | 0     | 0.14   |
| QUMO        | 3      | 3       | 449   | 678   | 0.13   |
| Seagate     | 2      | 2       | 46    | 0     | 0.13   |
| PRETEC      | 1      | 1       | 44    | 0     | 0.12   |
| ZOTAC       | 1      | 2       | 34    | 0     | 0.09   |
| Fordisk     | 2      | 2       | 32    | 0     | 0.09   |
| KingPower   | 1      | 1       | 29    | 0     | 0.08   |
| Kingmax     | 3      | 29      | 166   | 500   | 0.07   |
| Lite-On     | 15     | 16      | 29    | 160   | 0.06   |
| SK hynix    | 8      | 11      | 102   | 115   | 0.06   |
| Netac       | 1      | 1       | 19    | 0     | 0.05   |
| AMD         | 7      | 27      | 23    | 38    | 0.05   |
| WDC         | 9      | 25      | 18    | 0     | 0.05   |
| GLOWAY      | 3      | 3       | 18    | 0     | 0.05   |
| Hyperdisk   | 1      | 1       | 18    | 0     | 0.05   |
| KingDian    | 10     | 24      | 17    | 0     | 0.05   |
| Intenso     | 2      | 3       | 38    | 11    | 0.05   |
| LDLC        | 2      | 4       | 16    | 0     | 0.05   |
| FORESEE     | 3      | 3       | 10    | 0     | 0.03   |
| Kingrich    | 2      | 2       | 9     | 0     | 0.03   |
| FASTDISK    | 6      | 6       | 7     | 0     | 0.02   |
| Faspeed     | 2      | 2       | 4     | 0     | 0.01   |
| BIWIN       | 1      | 2       | 4     | 0     | 0.01   |
| CHN         | 1      | 1       | 3     | 0     | 0.01   |
| GeIL        | 5      | 5       | 52    | 205   | 0.01   |
| MicroData   | 2      | 2       | 23    | 333   | 0.01   |
| Goldendisk  | 1      | 1       | 0     | 0     | 0.00   |
| Indilinx    | 1      | 1       | 0     | 0     | 0.00   |
| Gost        | 1      | 1       | 0     | 0     | 0.00   |
| Goldenfir   | 1      | 1       | 0     | 0     | 0.00   |
| Zheino      | 1      | 1       | 0     | 0     | 0.00   |
| SMI         | 1      | 1       | 0     | 1957  | 0.00   |

