HDD/SSD Real-Life Reliability Test
==================================

This is a project to estimate reliability of HDD/SSD drives in real-life conditions by
the analysis of SMART data collected by Linux users at https://linux-hardware.org. The
primary aim of the project is to find drives with longest "power on hours" and minimal
number of errors.

Everyone can contribute to this report by uploading probes of their computers by
the hw-probe tool: https://github.com/linuxhw/hw-probe

Total drives: 21074.

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
| Hitachi   | HDS728040PLA320... | 40 GB  | 1       | 3563  | 0     | 9.76   |
| Samsung   | HE160HJ            | 160 GB | 1       | 2967  | 0     | 8.13   |
| WDC       | WD2500YS-01SHB0    | 251 GB | 1       | 2484  | 0     | 6.81   |
| WDC       | WD740GD-00FLA1     | 74 GB  | 1       | 2362  | 0     | 6.47   |
| Fujitsu   | MHV2040BH          | 40 GB  | 1       | 2224  | 0     | 6.09   |
| Seagate   | ST3750641NS        | 750 GB | 1       | 2169  | 0     | 5.94   |
| WDC       | WD2500AAJS-61B4A0  | 250 GB | 1       | 2168  | 0     | 5.94   |
| HP        | GB0250EAFYK        | 250 GB | 1       | 2025  | 0     | 5.55   |
| Hitachi   | HUA722020ALA331    | 2 TB   | 1       | 2009  | 0     | 5.51   |
| WDC       | WD2003FYPS-27Y2B0  | 2 TB   | 4       | 2277  | 1     | 5.45   |
| WDC       | WD1600AABS-61PRA0  | 160 GB | 1       | 1982  | 0     | 5.43   |
| WDC       | WD1601ABYS-01C0A0  | 164 GB | 1       | 1982  | 0     | 5.43   |
| WDC       | WD1600AAJS-00RYA0  | 160 GB | 1       | 1970  | 0     | 5.40   |
| WDC       | WD7500AAKS-22RBA0  | 750 GB | 1       | 1816  | 0     | 4.98   |
| WDC       | WD360GD-00FNA0     | 37 GB  | 2       | 2599  | 1     | 4.95   |
| Hitachi   | HUA721050KLA330    | 500 GB | 2       | 1774  | 0     | 4.86   |
| WDC       | WD2500KS-22MJB0    | 250 GB | 1       | 1734  | 0     | 4.75   |
| Seagate   | ST960813AS         | 60 GB  | 1       | 1729  | 0     | 4.74   |
| WDC       | WD5000ABYS-01TNA0  | 500 GB | 1       | 1707  | 0     | 4.68   |
| WDC       | WD5000BMVV-11GNWS0 | 500 GB | 1       | 1671  | 0     | 4.58   |
| WDC       | WD1600JS-88MHB0    | 160 GB | 1       | 1667  | 0     | 4.57   |
| WDC       | WD3200AAJS-22RYA0  | 320 GB | 3       | 1653  | 0     | 4.53   |
| HP        | FB080C4080         | 80 GB  | 1       | 1630  | 0     | 4.47   |
| WDC       | WD3200AAVS-00ZTB0  | 320 GB | 1       | 1583  | 0     | 4.34   |
| WDC       | WD2502ABYS-01B7A0  | 251 GB | 2       | 1576  | 0     | 4.32   |
| WDC       | WD4000AAJS-65TKA0  | 400 GB | 1       | 1532  | 0     | 4.20   |
| WDC       | WD2502ABYS-23B7... | 250 GB | 2       | 1522  | 0     | 4.17   |
| WDC       | WD1200JS-55NCB1    | 120 GB | 1       | 1487  | 0     | 4.08   |
| WDC       | WD2000JD-00GBB0    | 200 GB | 1       | 1482  | 0     | 4.06   |
| WDC       | WD800JD-75MSA2     | 79 GB  | 1       | 1432  | 0     | 3.92   |
| Hitachi   | HDT722520DLAT80    | 200 GB | 2       | 1406  | 0     | 3.85   |
| Hitachi   | HUA723030ALA640    | 3 TB   | 1       | 1403  | 0     | 3.84   |
| WDC       | WD2500JB-22REA0    | 250 GB | 1       | 1398  | 0     | 3.83   |
| WDC       | WD2001FASS-00W2B0  | 2 TB   | 1       | 1392  | 0     | 3.82   |
| WDC       | WD2500AAJS-22RYA0  | 250 GB | 1       | 1365  | 0     | 3.74   |
| WDC       | WD10EACS-00D6B1    | 1 TB   | 2       | 1668  | 1     | 3.73   |
| WDC       | WD7500BPVT-80HXZT1 | 750 GB | 1       | 1360  | 0     | 3.73   |
| WDC       | WD3200AAJB-00WGA0  | 320 GB | 2       | 1356  | 0     | 3.72   |
| WDC       | WD20EADS-00S2B0    | 2 TB   | 1       | 1315  | 0     | 3.60   |
| WDC       | WD10EACS-00D6B0    | 1 TB   | 3       | 1638  | 3     | 3.59   |
| WDC       | WD2500AAKX-08ERMA0 | 250 GB | 1       | 1306  | 0     | 3.58   |
| WDC       | WD2500AAKS-22VSA0  | 250 GB | 1       | 1305  | 0     | 3.58   |
| WDC       | WD5000AAKS-07YGA0  | 500 GB | 2       | 1295  | 0     | 3.55   |
| Hitachi   | HCS5C3232SLA380    | 320 GB | 1       | 1281  | 0     | 3.51   |
| WDC       | WD4000AAKS-00A7B0  | 400 GB | 1       | 1280  | 0     | 3.51   |
| WDC       | WD15EVDS-68V9B0    | 1.5 TB | 1       | 1276  | 0     | 3.50   |
| WDC       | WD800JD-08LSA0     | 80 GB  | 8       | 1428  | 3     | 3.47   |
| WDC       | WD10EAVS-00D7B0    | 1 TB   | 2       | 1248  | 0     | 3.42   |
| WDC       | WD2500JS-00NCB1    | 250 GB | 5       | 1239  | 0     | 3.40   |
| Samsung   | SP0451N            | 40 GB  | 1       | 1237  | 0     | 3.39   |
| WDC       | WD6400AACS-00G8B0  | 640 GB | 2       | 1216  | 0     | 3.33   |
| WDC       | WD1200JD-00HBB0    | 120 GB | 5       | 1411  | 3     | 3.32   |
| Hitachi   | HDT721075SLA380    | 750 GB | 1       | 1205  | 0     | 3.30   |
| Seagate   | ST3160828AS        | 159 GB | 1       | 1198  | 0     | 3.28   |
| Seagate   | ST3300631A         | 300 GB | 1       | 1185  | 0     | 3.25   |
| WDC       | WD1001FALS-40U9B0  | 1 TB   | 1       | 1175  | 0     | 3.22   |
| WDC       | WD3200AAJB-56WGA0  | 320 GB | 3       | 1172  | 0     | 3.21   |
| WDC       | WD3200AAJS-07RYA0  | 320 GB | 1       | 1168  | 0     | 3.20   |
| WDC       | WD1500AHFD-00RAR5  | 150 GB | 1       | 1164  | 0     | 3.19   |
| WDC       | WD5000AVJB-63YUA0  | 500 GB | 1       | 1163  | 0     | 3.19   |
| WDC       | WD1600JB-00REA0    | 160 GB | 7       | 1289  | 4     | 3.18   |
| WDC       | WD2503ABYX-01WERA0 | 251 GB | 1       | 1155  | 0     | 3.16   |
| WDC       | WD1500HLFS-01G6U3  | 150 GB | 1       | 1145  | 0     | 3.14   |
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
| Hitachi   | HTS545032B9SA00    | 320 GB | 2       | 1104  | 0     | 3.03   |
| WDC       | WD1200JS-00SGB0    | 120 GB | 2       | 1091  | 0     | 2.99   |
| WDC       | WD7500AARX-00N0YB0 | 750 GB | 1       | 1081  | 0     | 2.96   |
| WDC       | WD7500AYYS-01RCA0  | 750 GB | 3       | 1197  | 1     | 2.94   |
| WDC       | WD3200AAKS-00G3A0  | 320 GB | 5       | 1061  | 0     | 2.91   |
| WDC       | WD6400AACS-00D6B1  | 640 GB | 1       | 1058  | 0     | 2.90   |
| Seagate   | ST3250823AS        | 250 GB | 9       | 1243  | 28    | 2.90   |
| Seagate   | ST3400620A         | 400 GB | 3       | 1802  | 61    | 2.88   |
| WDC       | WD2500JS-00MHB1    | 250 GB | 2       | 1052  | 0     | 2.88   |
| WDC       | WD3200AAJB-00TYA0  | 320 GB | 2       | 1046  | 0     | 2.87   |
| WDC       | WD3200JD-00KLB0    | 320 GB | 1       | 1045  | 0     | 2.87   |
| WDC       | WD800BB-75FRA0     | 80 GB  | 2       | 1034  | 0     | 2.83   |
| Seagate   | ST340823A          | 40 GB  | 1       | 1034  | 0     | 2.83   |
| WDC       | WD1001FALS-00J7B0  | 1 TB   | 7       | 1031  | 0     | 2.83   |
| Samsung   | HD040GJ            | 40 GB  | 3       | 1360  | 41    | 2.82   |
| Hitachi   | HDS721016CLA382    | 160 GB | 5       | 1062  | 1     | 2.82   |
| WDC       | WD800BB-22JHA0     | 80 GB  | 2       | 1029  | 0     | 2.82   |
| WDC       | WD800AAJS-75M0A0   | 80 GB  | 2       | 1114  | 4     | 2.81   |
| Hitachi   | HDT725040VLA360    | 400 GB | 2       | 1024  | 0     | 2.81   |
| WDC       | WD400LB-00DNA0     | 40 GB  | 2       | 1103  | 2     | 2.78   |
| WDC       | WD200BB-00DEA0     | 20 GB  | 1       | 1015  | 0     | 2.78   |
| Hitachi   | HUA723020ALA640    | 2 TB   | 10      | 1014  | 0     | 2.78   |
| WDC       | WD1600JB-00EVA0    | 160 GB | 1       | 1012  | 0     | 2.77   |
| Hitachi   | HDT725032VLA380    | 320 GB | 7       | 1356  | 139   | 2.73   |
| WDC       | WD1000FYPS-01ZKB0  | 1 TB   | 1       | 989   | 0     | 2.71   |
| WDC       | WD1600BEVS-75RST0  | 160 GB | 1       | 984   | 0     | 2.70   |
| WDC       | WD400JB-00JJC0     | 40 GB  | 1       | 980   | 0     | 2.69   |
| Samsung   | HD040GJ-P          | 40 GB  | 1       | 975   | 0     | 2.67   |
| Hitachi   | HDS728040PLAT20    | 41 GB  | 4       | 1171  | 1     | 2.67   |
| WDC       | WD10EALS-002BA0    | 1 TB   | 2       | 969   | 0     | 2.66   |
| Seagate   | ST3250820SCE       | 250 GB | 2       | 960   | 0     | 2.63   |
| WDC       | WD2000JS-00MVB1    | 200 GB | 1       | 957   | 0     | 2.62   |
| WDC       | WD1600JS-55MHB1    | 160 GB | 1       | 954   | 0     | 2.61   |
| WDC       | WD4000AAKS-00YGA0  | 400 GB | 5       | 1144  | 1     | 2.61   |
| Quantum   | FIREBALLP AS20.5   | 20 GB  | 1       | 946   | 0     | 2.59   |
| Hitachi   | HDS5C1010CLA382    | 1 TB   | 7       | 945   | 0     | 2.59   |
| WDC       | WD2500JS-22NCB1    | 250 GB | 6       | 1088  | 1     | 2.59   |
| Hitachi   | HDS721075KLA330    | 750 GB | 6       | 1270  | 17    | 2.57   |
| Seagate   | ST250LT020-1AE14C  | 250 GB | 1       | 936   | 0     | 2.57   |
| WDC       | WD5000AAKB-00YSA0  | 500 GB | 2       | 935   | 0     | 2.56   |
| Hitachi   | HDS722020ALA330    | 2 TB   | 11      | 1248  | 7     | 2.56   |
| WDC       | WD1600AAJS-22PSA0  | 160 GB | 12      | 960   | 1     | 2.55   |
| WDC       | WD800JB-00DUA3     | 80 GB  | 1       | 923   | 0     | 2.53   |
| WDC       | WD30EZRX-00DC0B0   | 3 TB   | 6       | 917   | 0     | 2.51   |
| Hitachi   | HDS5C3015ALA632    | 1.5 TB | 2       | 1186  | 160   | 2.51   |
| Seagate   | ST3300622A         | 300 GB | 1       | 912   | 0     | 2.50   |
| WDC       | WD15EARS-00J2GB0   | 1.5 TB | 1       | 908   | 0     | 2.49   |
| Seagate   | ST3400833AS        | 400 GB | 1       | 905   | 0     | 2.48   |
| Seagate   | ST3300831AS        | 300 GB | 2       | 1451  | 4     | 2.48   |
| WDC       | WD400BB-71DGA0     | 40 GB  | 1       | 900   | 0     | 2.47   |
| Seagate   | ST3802110AS        | 80 GB  | 2       | 899   | 0     | 2.46   |
| WDC       | WD2500JB-57REA0    | 250 GB | 1       | 898   | 0     | 2.46   |
| WDC       | WD10EARX-32N0YB0   | 1 TB   | 1       | 897   | 0     | 2.46   |
| WDC       | WD740ADFD-00NLR1   | 74 GB  | 1       | 895   | 0     | 2.45   |
| WDC       | WD800JD-60LSA5     | 80 GB  | 12      | 938   | 1     | 2.45   |
| Hitachi   | HDS5C3030ALA630    | 3 TB   | 1       | 891   | 0     | 2.44   |
| WDC       | WD800BB-22HEA1     | 80 GB  | 1       | 888   | 0     | 2.43   |
| WDC       | WD5000AAKS-00TMA0  | 500 GB | 3       | 888   | 0     | 2.43   |
| WDC       | WD2500AAJS-55RYA0  | 250 GB | 2       | 887   | 0     | 2.43   |
| Seagate   | ST360015A          | 60 GB  | 1       | 885   | 0     | 2.43   |
| WDC       | WD4000KS-00MNB0    | 400 GB | 3       | 883   | 0     | 2.42   |
| Seagate   | ST91000640NS 81... | 1 TB   | 1       | 883   | 0     | 2.42   |
| WDC       | WD6400AAKS-00A7B2  | 640 GB | 5       | 882   | 0     | 2.42   |
| WDC       | WD2500AAJS-75VWA0  | 250 GB | 1       | 880   | 0     | 2.41   |
| WDC       | WD1600AAJS-75WAA0  | 160 GB | 2       | 880   | 0     | 2.41   |
| WDC       | WD3200BEVE-00A0HT0 | 320 GB | 2       | 877   | 0     | 2.40   |
| WDC       | WD7500AAKS-00RBA0  | 750 GB | 6       | 1002  | 84    | 2.40   |
| WDC       | WD1600JS-55NCB1    | 160 GB | 4       | 874   | 0     | 2.39   |
| Seagate   | ST360021A          | 60 GB  | 3       | 868   | 0     | 2.38   |
| WDC       | WD1600BEVS-08VAT2  | 160 GB | 5       | 957   | 1     | 2.37   |
| WDC       | WD800BB-75JHA0     | 79 GB  | 1       | 865   | 0     | 2.37   |
| WDC       | WD2500AAJS-75M0A0  | 250 GB | 1       | 862   | 0     | 2.36   |
| WDC       | WD3202ABYS-02B7A0  | 320 GB | 6       | 929   | 1     | 2.36   |
| WDC       | WD5000AAKS-00YGA0  | 500 GB | 15      | 1008  | 2     | 2.34   |
| WDC       | WD800AAJS-22PSA0   | 80 GB  | 4       | 852   | 0     | 2.33   |
| Seagate   | ST3500630A         | 500 GB | 7       | 1381  | 33    | 2.33   |
| WDC       | WD10EACS-00ZJB0    | 1 TB   | 2       | 851   | 0     | 2.33   |
| WDC       | WD20NMVW-11AV3S2   | 2 TB   | 2       | 848   | 0     | 2.33   |
| Hitachi   | HCS5C1050CLA382    | 500 GB | 1       | 848   | 0     | 2.33   |
| WDC       | WD7502AAEX-00Z3A0  | 750 GB | 1       | 848   | 0     | 2.32   |
| WDC       | WD800JD-75MSA3     | 80 GB  | 16      | 980   | 1     | 2.32   |
| WDC       | WD10EADS-00L5B1    | 1 TB   | 23      | 1285  | 4     | 2.31   |
| WDC       | WD1600BB-55RDA0    | 160 GB | 2       | 841   | 0     | 2.31   |
| WDC       | WD2500JS-55NCB1    | 250 GB | 2       | 1144  | 16    | 2.30   |
| WDC       | WD2500YS-01SHB1    | 250 GB | 6       | 999   | 1     | 2.29   |
| WDC       | WD800BB-00DKA0     | 80 GB  | 3       | 977   | 1     | 2.29   |
| WDC       | WD10EALX-089BA0    | 1 TB   | 2       | 836   | 0     | 2.29   |
| WDC       | WD5000AAKS-65YGA0  | 500 GB | 6       | 830   | 0     | 2.28   |
| Seagate   | ST3750840AS        | 750 GB | 1       | 828   | 0     | 2.27   |
| WDC       | WD400BB-00DEA0     | 40 GB  | 1       | 825   | 0     | 2.26   |
| WDC       | WD800BD-88JMC0     | 80 GB  | 2       | 824   | 0     | 2.26   |
| WDC       | WD1600AAJS-00M0A0  | 160 GB | 4       | 930   | 99    | 2.25   |
| WDC       | WD1200JB-00EVA0    | 120 GB | 3       | 821   | 0     | 2.25   |
| WDC       | WD2500BEVE-00WZT0  | 250 GB | 2       | 817   | 0     | 2.24   |
| WDC       | WD400BB-00LNA0     | 40 GB  | 1       | 817   | 0     | 2.24   |
| Hitachi   | HDT725050VLA380    | 500 GB | 2       | 1307  | 19    | 2.24   |
| WDC       | WD5000AUDX-63WNHY0 | 500 GB | 1       | 816   | 0     | 2.24   |
| WDC       | WD1500HLFS-01G6U1  | 150 GB | 3       | 813   | 0     | 2.23   |
| WDC       | WD2500JB-00GVC0    | 250 GB | 2       | 811   | 0     | 2.22   |
| Samsung   | SP1644N            | 160 GB | 2       | 921   | 790   | 2.22   |
| Hitachi   | HDT725050VLA360    | 500 GB | 2       | 1052  | 2     | 2.21   |
| Seagate   | ST3320620NS        | 320 GB | 2       | 1021  | 1     | 2.21   |
| Seagate   | ST3120213AS        | 120 GB | 1       | 806   | 0     | 2.21   |
| WDC       | WD3200AAKS-22B3A0  | 320 GB | 1       | 806   | 0     | 2.21   |
| Hitachi   | HTS723232L9SA62    | 320 GB | 1       | 804   | 0     | 2.20   |
| WDC       | WD15EARS-00S0XB0   | 1.5 TB | 1       | 802   | 0     | 2.20   |
| WDC       | WD1600BB-56RDA0    | 160 GB | 2       | 800   | 0     | 2.19   |
| WDC       | WD6400AAKS-00A7B0  | 640 GB | 7       | 1065  | 5     | 2.19   |
| WDC       | WD1600JS-75NCB3    | 160 GB | 3       | 794   | 0     | 2.18   |
| HGST      | HDN726060ALE610    | 6 TB   | 1       | 787   | 0     | 2.16   |
| Seagate   | ST6000DM001-1XY17Z | 6 TB   | 1       | 783   | 0     | 2.15   |
| Seagate   | ST6000VN0021-1Z... | 6 TB   | 1       | 783   | 0     | 2.15   |
| WDC       | WD6001FFWX-68Z39N0 | 6 TB   | 1       | 782   | 0     | 2.14   |
| WDC       | WD5000HHTZ-04N21V0 | 500 GB | 4       | 782   | 0     | 2.14   |
| WDC       | WD6400AAKS-75A7B2  | 640 GB | 3       | 1059  | 3     | 2.14   |
| WDC       | WD5000AADS-56S9B0  | 500 GB | 1       | 782   | 0     | 2.14   |
| Seagate   | ST91603110CS       | 160 GB | 1       | 781   | 0     | 2.14   |
| WDC       | WD2500BB-00GUA0    | 250 GB | 1       | 773   | 0     | 2.12   |
| WDC       | WD2500JS-60NCB2    | 250 GB | 2       | 773   | 0     | 2.12   |
| WDC       | WD3200AAKS-00VYA0  | 320 GB | 5       | 822   | 1     | 2.11   |
| Hitachi   | HTS723225L9A362    | 250 GB | 1       | 770   | 0     | 2.11   |
| WDC       | WD1600AAJS-07PSA0  | 160 GB | 3       | 1618  | 9     | 2.10   |
| Hitachi   | HTS722012K9SA00    | 120 GB | 3       | 851   | 340   | 2.10   |
| WDC       | WD3200AAKX-083CA1  | 320 GB | 1       | 763   | 0     | 2.09   |
| WDC       | WD1600JS-60MHB1    | 160 GB | 4       | 759   | 0     | 2.08   |
| WDC       | WD2500AAKS-00VSA0  | 250 GB | 16      | 863   | 1     | 2.08   |
| WDC       | WD2500JD-55HBB0    | 250 GB | 2       | 1468  | 16    | 2.07   |
| WDC       | WD7501AALS-00J7B1  | 750 GB | 7       | 1005  | 1     | 2.07   |
| WDC       | WD3000JS-19PDB0    | 300 GB | 1       | 751   | 0     | 2.06   |
| WDC       | WD5001AALS-00L3B2  | 500 GB | 24      | 919   | 3     | 2.05   |
| Seagate   | ST9750422AS        | 750 GB | 1       | 746   | 0     | 2.05   |
| WDC       | WD400BB-60JKA0     | 40 GB  | 2       | 746   | 0     | 2.04   |
| Quantum   | FIREBALLP AS40.0   | 40 GB  | 1       | 744   | 0     | 2.04   |
| WDC       | WD5000AACS-00ZUB0  | 500 GB | 8       | 790   | 1     | 2.04   |
| WDC       | WD2500AAJS-00VTA0  | 250 GB | 18      | 864   | 5     | 2.04   |
| Hitachi   | HDS723015BLA642    | 1.5 TB | 5       | 869   | 4     | 2.04   |
| Fujitsu   | MHV2060AH PL       | 52 GB  | 1       | 741   | 0     | 2.03   |
| WDC       | WD1600YS-01SHB1    | 164 GB | 5       | 739   | 0     | 2.03   |
| WDC       | WD5000AAKS-00A7B0  | 500 GB | 19      | 972   | 9     | 2.01   |
| WDC       | WD1600AAJS-60PSA0  | 160 GB | 4       | 904   | 257   | 2.01   |
| WDC       | WD800JD-00LSA0     | 80 GB  | 15      | 1041  | 15    | 1.99   |
| WDC       | WD3200BEVT-75ZCT2  | 320 GB | 2       | 720   | 0     | 1.98   |
| Fujitsu   | MHV2100AH          | 100 GB | 2       | 719   | 0     | 1.97   |
| WDC       | WD6402AAEX-00Z3A0  | 640 GB | 3       | 719   | 0     | 1.97   |
| Seagate   | ST310211A          | 10 GB  | 1       | 716   | 0     | 1.96   |
| WDC       | WD1502FAEX-007BA0  | 1.5 TB | 5       | 816   | 35    | 1.96   |
| WDC       | WD1600JS-58NCB1    | 160 GB | 1       | 712   | 0     | 1.95   |
| Samsung   | HD300LJ            | 300 GB | 7       | 1073  | 487   | 1.95   |
| WDC       | WD2000JS-22MHB0    | 200 GB | 2       | 2525  | 19    | 1.95   |
| Seagate   | ST1000VM002-9ZL162 | 1 TB   | 1       | 709   | 0     | 1.95   |
| WDC       | WD7500AALX-009BA0  | 750 GB | 5       | 709   | 0     | 1.94   |
| WDC       | WD200BB-32CFC0     | 20 GB  | 1       | 709   | 0     | 1.94   |
| WDC       | WD800AAJS-22WAA0   | 80 GB  | 1       | 708   | 0     | 1.94   |
| WDC       | WD1600AAJS-07WAA0  | 160 GB | 3       | 1303  | 283   | 1.93   |
| WDC       | WD3200AAJS-65B4A0  | 320 GB | 1       | 699   | 0     | 1.92   |
| Seagate   | ST3300620AS        | 300 GB | 1       | 692   | 0     | 1.90   |
| WDC       | WD6400AAKS-65A7B0  | 640 GB | 5       | 787   | 3     | 1.89   |
| WDC       | WD2500BEKT-75PVMT1 | 250 GB | 1       | 689   | 0     | 1.89   |
| Seagate   | ST3400620AS        | 400 GB | 18      | 935   | 9     | 1.89   |
| WDC       | WD1001FALS-00Y6A0  | 1 TB   | 4       | 936   | 28    | 1.88   |
| Seagate   | ST340215AS         | 40 GB  | 1       | 686   | 0     | 1.88   |
| Hitachi   | HDS722580VLSA80    | 82 GB  | 2       | 1317  | 1007  | 1.88   |
| Fujitsu   | MHZ2080BH G2       | 80 GB  | 1       | 684   | 0     | 1.88   |
| WDC       | WD30EZRX-00MMMB0   | 3 TB   | 5       | 883   | 2     | 1.87   |
| WDC       | WD15EARS-22Z5B1    | 1.5 TB | 3       | 675   | 0     | 1.85   |
| WDC       | WD800BB-75DKA0     | 80 GB  | 1       | 672   | 0     | 1.84   |
| WDC       | WD6401AALS-00L3B2  | 640 GB | 14      | 901   | 7     | 1.84   |
| WDC       | WD1200JS-55MHB0    | 120 GB | 2       | 671   | 0     | 1.84   |
| Seagate   | ST4000NM0033-9Z... | 4 TB   | 1       | 667   | 0     | 1.83   |
| WDC       | WD1502FYPS-01U1B1  | 1.5 TB | 1       | 667   | 0     | 1.83   |
| WDC       | WD2500KS-00MJB0    | 250 GB | 14      | 898   | 24    | 1.83   |
| WDC       | WD30EURS-63R8UY0   | 3 TB   | 2       | 664   | 0     | 1.82   |
| WDC       | WD800AAJS-00PSA0   | 80 GB  | 10      | 844   | 73    | 1.82   |
| WDC       | WD3000HLFS-01G6U4  | 300 GB | 1       | 662   | 0     | 1.81   |
| WDC       | WD1200JD-00FYB0    | 120 GB | 1       | 661   | 0     | 1.81   |
| WDC       | WD740ADFD-00NLR5   | 74 GB  | 1       | 659   | 0     | 1.81   |
| WDC       | WD2003FYYS-02W0B0  | 2 TB   | 3       | 757   | 1     | 1.80   |
| Seagate   | ST2000VM003-1CT164 | 2 TB   | 4       | 814   | 1     | 1.80   |
| WDC       | WD5000BPVT-75HXZT1 | 500 GB | 1       | 657   | 0     | 1.80   |
| WDC       | WD5000AAJS-00TKA0  | 500 GB | 1       | 656   | 0     | 1.80   |
| WDC       | WD2500AAKX-22ERMA0 | 250 GB | 1       | 656   | 0     | 1.80   |
| WDC       | WD1600JS-98NCB1    | 160 GB | 1       | 655   | 0     | 1.80   |
| Hitachi   | HUA721010KLA330... | 1 TB   | 1       | 2622  | 3     | 1.80   |
| Hitachi   | HTS723216L9SA60    | 160 GB | 2       | 654   | 0     | 1.79   |
| WDC       | WD3200AAJS-65RYA0  | 320 GB | 2       | 652   | 0     | 1.79   |
| Seagate   | ST3000DM003-1F216N | 3 TB   | 1       | 652   | 0     | 1.79   |
| WDC       | WD5000AAKS-00Z7B0  | 500 GB | 1       | 652   | 0     | 1.79   |
| Samsung   | HD204UI            | 2 TB   | 10      | 821   | 10    | 1.79   |
| WDC       | WD400BD-60JPA0     | 40 GB  | 1       | 651   | 0     | 1.78   |
| WDC       | WD10EADS-65L5B1    | 1 TB   | 8       | 1190  | 4     | 1.78   |
| WDC       | WD1600AAJS-60M0A0  | 160 GB | 2       | 648   | 0     | 1.78   |
| Seagate   | ST980812AS         | 80 GB  | 1       | 647   | 0     | 1.77   |
| WDC       | WD5000AAKS-07TMA0  | 500 GB | 1       | 646   | 0     | 1.77   |
| Toshiba   | DT01ABA050V        | 500 GB | 1       | 644   | 0     | 1.77   |
| Fujitsu   | MHW2080BH PL       | 80 GB  | 2       | 644   | 0     | 1.77   |
| WDC       | WD5000AAKS-00C8A0  | 500 GB | 2       | 1045  | 93    | 1.76   |
| WDC       | WD1001FALS-19J7B0  | 1 TB   | 1       | 641   | 0     | 1.76   |
| Seagate   | ST31500541AS       | 1.5 TB | 7       | 909   | 53    | 1.76   |
| WDC       | WD1001FALS-403AA0  | 1 TB   | 1       | 639   | 0     | 1.75   |
| WDC       | WD1600JS-98MHB0    | 160 GB | 1       | 638   | 0     | 1.75   |
| WDC       | WD1200JS-00MHB0    | 120 GB | 11      | 684   | 1     | 1.75   |
| WDC       | WD1002FAEX-00Y9A0  | 1 TB   | 24      | 722   | 31    | 1.74   |
| WDC       | WD6400AAKS-65Z7B0  | 640 GB | 4       | 708   | 5     | 1.74   |
| WDC       | WD3200AAKS-22SBA0  | 320 GB | 1       | 633   | 0     | 1.73   |
| WDC       | WD7501AALS-00J7B0  | 750 GB | 12      | 943   | 73    | 1.73   |
| WDC       | WD1600AABS-00PRA0  | 160 GB | 1       | 630   | 0     | 1.73   |
| WDC       | WD1001FALS-00E3A0  | 1 TB   | 3       | 839   | 1     | 1.73   |
| Seagate   | ST3320413CS        | 320 GB | 6       | 663   | 20    | 1.72   |
| Toshiba   | MK1032GSX          | 100 GB | 3       | 628   | 0     | 1.72   |
| WDC       | WD7500BPKX-60HPJT0 | 750 GB | 1       | 627   | 0     | 1.72   |
| WDC       | WD2500AAJS-00Z0A0  | 250 GB | 1       | 626   | 0     | 1.72   |
| WDC       | WD4000BEVT-11ZAT0  | 400 GB | 1       | 626   | 0     | 1.72   |
| WDC       | WD3200AAJS-00VWA0  | 320 GB | 7       | 626   | 0     | 1.72   |
| WDC       | WD1600AAJB-00WRA0  | 160 GB | 2       | 950   | 543   | 1.72   |
| WDC       | WD2002FYPS-02W3B0  | 2 TB   | 1       | 626   | 0     | 1.72   |
| WDC       | WD800JD-22MSA1     | 80 GB  | 8       | 625   | 0     | 1.71   |
| Seagate   | ST3160812AS        | 160 GB | 27      | 950   | 391   | 1.71   |
| WDC       | WD2500AAJS-08L7A0  | 250 GB | 2       | 624   | 0     | 1.71   |
| WDC       | WD360GD-00FLC0     | 37 GB  | 1       | 622   | 0     | 1.70   |
| Hitachi   | HDS728080PLAT20    | 82 GB  | 14      | 794   | 10    | 1.70   |
| WDC       | WD1600AAJS-55PSA0  | 160 GB | 1       | 620   | 0     | 1.70   |
| WDC       | WD6400BEVT-00A0RT0 | 640 GB | 1       | 619   | 0     | 1.70   |
| WDC       | WD800BB-55JKA0     | 80 GB  | 3       | 852   | 2     | 1.70   |
| Hitachi   | HDS5C1032CLA382    | 320 GB | 4       | 714   | 3     | 1.69   |
| Hitachi   | HDS723020BLA642    | 2 TB   | 15      | 797   | 70    | 1.69   |
| WDC       | WD3200AAJS-65VWA0  | 320 GB | 2       | 617   | 0     | 1.69   |
| WDC       | WD800BB-00JHA0     | 80 GB  | 6       | 1044  | 5     | 1.68   |
| Samsung   | HD083GJ            | 80 GB  | 2       | 613   | 0     | 1.68   |
| Hitachi   | HDS723020BLE640    | 2 TB   | 7       | 612   | 0     | 1.68   |
| WDC       | WD5000AACS-00G8B1  | 500 GB | 9       | 854   | 3     | 1.68   |
| WDC       | WD20EADS-00R6B0    | 2 TB   | 4       | 802   | 2     | 1.68   |
| WDC       | WD2500JS-22MHB0    | 250 GB | 3       | 610   | 0     | 1.67   |
| WDC       | WD800JD-00LUA0     | 80 GB  | 1       | 610   | 0     | 1.67   |
| Hitachi   | HDS721075CLA332    | 750 GB | 2       | 610   | 0     | 1.67   |
| Seagate   | ST3160023A         | 160 GB | 13      | 852   | 157   | 1.67   |
| WDC       | WD2500BEKT-75PVMT0 | 250 GB | 3       | 609   | 0     | 1.67   |
| Seagate   | ST31000526SV       | 1 TB   | 3       | 769   | 343   | 1.67   |
| Seagate   | ST3250620NS        | 250 GB | 11      | 988   | 195   | 1.66   |
| WDC       | WD800JD-75MSA1     | 80 GB  | 1       | 607   | 0     | 1.66   |
| WDC       | WD3200AAJS-61B4A0  | 320 GB | 1       | 607   | 0     | 1.66   |
| WDC       | WD3200AAKS-00L9A0  | 320 GB | 31      | 827   | 9     | 1.66   |
| WDC       | WD1002FAEX-007BA0  | 1 TB   | 2       | 709   | 1     | 1.66   |
| Seagate   | ST32000644NS       | 2 TB   | 2       | 608   | 1     | 1.66   |
| WDC       | WD3000JS-60PDB0    | 300 GB | 2       | 603   | 0     | 1.65   |
| Hitachi   | HTS545016B9SA02    | 160 GB | 1       | 602   | 0     | 1.65   |
| Seagate   | ST9200420AS        | 200 GB | 2       | 601   | 0     | 1.65   |
| WDC       | WD800JD-23LSA0     | 80 GB  | 1       | 1202  | 1     | 1.65   |
| WDC       | WD1600JS-23MHB0    | 160 GB | 1       | 600   | 0     | 1.64   |
| Seagate   | ST3320620AS        | 320 GB | 83      | 1011  | 248   | 1.64   |
| Seagate   | ST3250820AS        | 250 GB | 31      | 876   | 274   | 1.64   |
| WDC       | WD30EFRX-68AX9N0   | 3 TB   | 6       | 785   | 2     | 1.64   |
| Hitachi   | HTS723220L9A360    | 200 GB | 1       | 598   | 0     | 1.64   |
| WDC       | WD10EZEX-00ER1A0   | 1 TB   | 2       | 597   | 0     | 1.64   |
| Seagate   | ST3500320NS        | 500 GB | 6       | 1002  | 190   | 1.64   |
| WDC       | WD10EALS-00Z8A0    | 1 TB   | 20      | 865   | 73    | 1.63   |
| WDC       | WD5000AAKS-00D2B0  | 500 GB | 7       | 836   | 4     | 1.63   |
| WDC       | WD10EURX-63FH1Y0   | 1 TB   | 4       | 592   | 0     | 1.62   |
| WDC       | WD20EARX-008FB0    | 2 TB   | 2       | 591   | 0     | 1.62   |
| WDC       | WD2500BEVS-26UST0  | 250 GB | 3       | 588   | 0     | 1.61   |
| Seagate   | ST2000DL003-9VT166 | 2 TB   | 45      | 694   | 80    | 1.61   |
| Hitachi   | HDT721016SLA380    | 160 GB | 11      | 730   | 6     | 1.60   |
| WDC       | WD20EARS-55MVWB0   | 2 TB   | 1       | 584   | 0     | 1.60   |
| Hitachi   | HDT725025VLA380    | 250 GB | 6       | 929   | 2     | 1.60   |
| WDC       | WD5000BEVT-75A0RT0 | 500 GB | 2       | 584   | 0     | 1.60   |
| WDC       | WD800BB-63JKC0     | 80 GB  | 1       | 584   | 0     | 1.60   |
| WDC       | WD2500AVJS-63WDA0  | 250 GB | 2       | 582   | 0     | 1.60   |
| Maxtor    | STM3320620A        | 320 GB | 2       | 579   | 0     | 1.59   |
| Hitachi   | HDP725040GLA360    | 400 GB | 2       | 979   | 2     | 1.59   |
| WDC       | WD6400AAKS-65A7B2  | 640 GB | 10      | 1078  | 49    | 1.59   |
| WDC       | WD2500BEKT-60V5T1  | 250 GB | 1       | 578   | 0     | 1.59   |
| WDC       | WD1600BEVS-22RST0  | 160 GB | 23      | 608   | 25    | 1.59   |
| WDC       | WD6400AAKS-22A7B0  | 640 GB | 5       | 1047  | 6     | 1.58   |
| Hitachi   | HDS721612PLA380    | 120 GB | 4       | 1082  | 3     | 1.58   |
| WDC       | WD10EADS-00M2B0    | 1 TB   | 21      | 834   | 96    | 1.58   |
| WDC       | WD1500ADFD-00NLR1  | 150 GB | 1       | 574   | 0     | 1.57   |
| Seagate   | ST3160212AS        | 160 GB | 2       | 572   | 0     | 1.57   |
| WDC       | WD15EVDS-63V9B1    | 1.5 TB | 1       | 571   | 0     | 1.57   |
| Seagate   | ST3500630AS        | 500 GB | 21      | 953   | 355   | 1.56   |
| WDC       | WD800JD-55MUA1     | 80 GB  | 6       | 648   | 2     | 1.55   |
| Hitachi   | HDT722525DLA380    | 250 GB | 8       | 1197  | 3     | 1.55   |
| Seagate   | ST380215AS         | 80 GB  | 13      | 1017  | 860   | 1.54   |
| WDC       | WD1600AAJS-60M0A1  | 160 GB | 1       | 1125  | 1     | 1.54   |
| Samsung   | HD253GJ            | 250 GB | 7       | 768   | 17    | 1.53   |
| Seagate   | ST3320413AS        | 320 GB | 6       | 836   | 4     | 1.53   |
| WDC       | WD2500JB-98GVA0    | 250 GB | 1       | 3354  | 5     | 1.53   |
| Fujitsu   | MHY2250BH          | 250 GB | 5       | 862   | 65    | 1.53   |
| WDC       | WD2000JS-00MHB0    | 200 GB | 7       | 769   | 20    | 1.53   |
| Samsung   | HD103SI            | 1 TB   | 20      | 910   | 164   | 1.52   |
| Hitachi   | HDS728080PLA380    | 80 GB  | 26      | 797   | 8     | 1.52   |
| WDC       | WD3000JS-00PDB0    | 300 GB | 1       | 554   | 0     | 1.52   |
| Hitachi   | HDS721010CLA332    | 1 TB   | 72      | 814   | 73    | 1.52   |
| Seagate   | ST32000645NS       | 2 TB   | 4       | 553   | 0     | 1.52   |
| WDC       | WD1001FALS-00J7B1  | 1 TB   | 9       | 824   | 4     | 1.52   |
| Seagate   | ST3200826AS        | 200 GB | 8       | 910   | 5     | 1.52   |
| WDC       | WD5000AVCS-732DY1  | 500 GB | 1       | 551   | 0     | 1.51   |
| WDC       | WD3200BPVT-00HXZT0 | 320 GB | 1       | 549   | 0     | 1.51   |
| WDC       | WD3200AAKS-75L9A0  | 320 GB | 12      | 687   | 2     | 1.51   |
| WDC       | WD1600JS-00SGB0    | 160 GB | 1       | 549   | 0     | 1.50   |
| WDC       | WD400BB-00JHC0     | 40 GB  | 4       | 872   | 24    | 1.50   |
| WDC       | WD360ADFD-00NLR1   | 37 GB  | 1       | 547   | 0     | 1.50   |
| WDC       | WD1002FAEX-00Z3A0  | 1 TB   | 42      | 733   | 121   | 1.50   |
| WDC       | WD2500AAKS-00B3A0  | 250 GB | 2       | 1093  | 5     | 1.49   |
| Samsung   | HD103UJ            | 1 TB   | 27      | 817   | 155   | 1.49   |
| Seagate   | ST3200827A         | 200 GB | 1       | 544   | 0     | 1.49   |
| MediaMax  | WL1000GSA6472C     | 1 TB   | 1       | 543   | 0     | 1.49   |
| Hitachi   | HDT725025VLAT80    | 250 GB | 2       | 1843  | 2     | 1.49   |
| WDC       | WD1600AAJS-00B4A0  | 160 GB | 13      | 766   | 102   | 1.48   |
| WDC       | WD5001AALS-00E3A0  | 500 GB | 8       | 541   | 0     | 1.48   |
| WDC       | WD3200AAJS-08L7A0  | 320 GB | 6       | 761   | 290   | 1.48   |
| WDC       | WD3000HLFS-01G6U0  | 300 GB | 1       | 540   | 0     | 1.48   |
| WDC       | WD2000JB-00REA0    | 200 GB | 3       | 837   | 1     | 1.48   |
| Fujitsu   | MHV2100BH          | 100 GB | 3       | 700   | 2     | 1.48   |
| WDC       | WD1200JS-00NCB1    | 120 GB | 1       | 539   | 0     | 1.48   |
| Seagate   | ST3320620A         | 320 GB | 20      | 693   | 6     | 1.48   |
| Samsung   | HD103SJ            | 1 TB   | 57      | 736   | 17    | 1.47   |
| WDC       | WD800AAJS-22L7A0   | 80 GB  | 1       | 534   | 0     | 1.46   |
| Seagate   | ST3320418AS        | 320 GB | 60      | 755   | 83    | 1.46   |
| WDC       | WD7502AAEX-00Y9A0  | 750 GB | 4       | 532   | 0     | 1.46   |
| HGST      | HDN724040ALE640    | 4 TB   | 2       | 532   | 0     | 1.46   |
| WDC       | WD1600JS-22MHB0    | 160 GB | 3       | 700   | 9     | 1.46   |
| Seagate   | ST3750640NS        | 750 GB | 6       | 1275  | 524   | 1.45   |
| WDC       | WD20EFRX-68AX9N0   | 2 TB   | 7       | 619   | 1     | 1.45   |
| Samsung   | HD321HJ            | 320 GB | 4       | 903   | 39    | 1.44   |
| WDC       | WD2002FAEX-007BA0  | 2 TB   | 10      | 605   | 2     | 1.44   |
| WDC       | WD7500BPVT-00HXZT1 | 750 GB | 1       | 525   | 0     | 1.44   |
| WDC       | WD1600AAJS-60B4A0  | 160 GB | 1       | 522   | 0     | 1.43   |
| Maxtor    | 4K020H1            | 20 GB  | 1       | 522   | 0     | 1.43   |
| Seagate   | ST640LM000 HM641JI | 640 GB | 1       | 521   | 0     | 1.43   |
| Seagate   | ST3250620AS        | 250 GB | 41      | 876   | 406   | 1.42   |
| WDC       | WD800JD-00MSA1     | 80 GB  | 5       | 701   | 15    | 1.42   |
| WDC       | WD5000AAJS-00A8B0  | 500 GB | 2       | 516   | 0     | 1.41   |
| Seagate   | ST3160215ACE       | 160 GB | 3       | 809   | 72    | 1.41   |
| Fujitsu   | MHW2120BH          | 120 GB | 13      | 592   | 1     | 1.41   |
| ExcelStor | J9250S             | 250 GB | 2       | 513   | 0     | 1.41   |
| WDC       | WD10EADS-00P8B0    | 1 TB   | 4       | 846   | 4     | 1.40   |
| WDC       | WD1500HLFS-01MZUV0 | 150 GB | 2       | 511   | 0     | 1.40   |
| WDC       | WD5000BEVT-35A0RT0 | 500 GB | 7       | 593   | 2     | 1.40   |
| WDC       | WD10JPVT-24A1YT0   | 1 TB   | 1       | 511   | 0     | 1.40   |
| Seagate   | ST3000VX000-1CU166 | 3 TB   | 3       | 509   | 0     | 1.40   |
| WDC       | WD3200AAJS-55B4A0  | 320 GB | 2       | 749   | 4     | 1.40   |
| Seagate   | ST340014A          | 40 GB  | 59      | 743   | 49    | 1.39   |
| WDC       | WD6400AAKS-55A7B0  | 640 GB | 1       | 507   | 0     | 1.39   |
| Hitachi   | HDS5C3020ALA632    | 2 TB   | 8       | 507   | 0     | 1.39   |
| WDC       | WD1600AAJS-00PSA0  | 160 GB | 19      | 834   | 73    | 1.39   |
| Toshiba   | MK2559GSXP         | 250 GB | 3       | 506   | 0     | 1.39   |
| WDC       | WD5000LPVT-16G33T0 | 500 GB | 2       | 505   | 0     | 1.39   |
| WDC       | WD5000AVDS-63U7B1  | 500 GB | 3       | 505   | 0     | 1.38   |
| Toshiba   | MK2556GSYF         | 250 GB | 1       | 503   | 0     | 1.38   |
| WDC       | WD2500HHTZ-04N21V0 | 250 GB | 3       | 503   | 0     | 1.38   |
| Seagate   | ST340015A          | 40 GB  | 3       | 763   | 45    | 1.38   |
| WDC       | WD1600AAJS-08PSA0  | 160 GB | 6       | 703   | 15    | 1.37   |
| WDC       | WD10EARS-22Y5B1    | 1 TB   | 7       | 927   | 36    | 1.37   |
| WDC       | WD800JD-55MSA1     | 80 GB  | 2       | 497   | 0     | 1.36   |
| WDC       | WD5000BPKT-60PK4T0 | 500 GB | 2       | 679   | 128   | 1.36   |
| WDC       | WD200EB-00BHF0     | 20 GB  | 1       | 992   | 1     | 1.36   |
| WDC       | WD1200JD-00GBB0    | 120 GB | 3       | 754   | 4     | 1.36   |
| Seagate   | ST3500630NS        | 500 GB | 5       | 684   | 529   | 1.36   |
| Seagate   | ST380012ACE        | 80 GB  | 3       | 494   | 0     | 1.36   |
| WDC       | WD1600AAJS-75M0A0  | 160 GB | 1       | 494   | 0     | 1.35   |
| Fujitsu   | MPE3136AH          | 13 GB  | 1       | 494   | 0     | 1.35   |
| Seagate   | ST1000VX000-9YW162 | 1 TB   | 3       | 492   | 0     | 1.35   |
| Seagate   | ST3500413AS        | 500 GB | 81      | 585   | 36    | 1.35   |
| WDC       | WD10EADX-22TDHB0   | 1 TB   | 3       | 634   | 3     | 1.35   |
| WDC       | WD10JPVT-16A1YT0   | 1 TB   | 1       | 490   | 0     | 1.34   |
| WDC       | WD20EARS-00MVWB0   | 2 TB   | 29      | 754   | 80    | 1.33   |
| Seagate   | ST3160815AS        | 160 GB | 110     | 749   | 450   | 1.33   |
| Seagate   | ST98823A           | 80 GB  | 4       | 633   | 323   | 1.33   |
| Fujitsu   | MHT2040AH          | 40 GB  | 1       | 484   | 0     | 1.33   |
| WDC       | WD7500AADS-00M2B0  | 750 GB | 13      | 900   | 27    | 1.33   |
| WDC       | WD5000LPVT-60G33T0 | 500 GB | 1       | 482   | 0     | 1.32   |
| Seagate   | ST31000524NS       | 1 TB   | 2       | 731   | 9     | 1.32   |
| WDC       | WD4000AAKS-00TMA0  | 400 GB | 4       | 551   | 1     | 1.32   |
| WDC       | WD7500BPKT-22PK4T0 | 750 GB | 5       | 481   | 0     | 1.32   |
| Seagate   | ST9640423AS        | 640 GB | 3       | 704   | 387   | 1.32   |
| Hitachi   | HDS728040PLA320    | 40 GB  | 2       | 1225  | 8     | 1.32   |
| WDC       | WD2500AAJB-00J3A0  | 250 GB | 8       | 857   | 7     | 1.31   |
| WDC       | WD1600JS-60MHB5    | 160 GB | 1       | 478   | 0     | 1.31   |
| Seagate   | ST380819AS         | 80 GB  | 1       | 478   | 0     | 1.31   |
| WDC       | WD10EARS-003BB1    | 1 TB   | 8       | 651   | 11    | 1.31   |
| WDC       | WD20EARS-00S8B1    | 2 TB   | 7       | 650   | 2     | 1.31   |
| Seagate   | ST380011A          | 80 GB  | 105     | 772   | 116   | 1.31   |
| WDC       | WD3200AAKS-61L9A0  | 320 GB | 3       | 483   | 10    | 1.31   |
| Hitachi   | HUA722050CLA330    | 500 GB | 2       | 476   | 0     | 1.31   |
| Seagate   | ST3120026AS        | 120 GB | 21      | 1129  | 9     | 1.31   |
| WDC       | WD2500AAJB-00WGA0  | 250 GB | 3       | 1216  | 8     | 1.31   |
| WDC       | WD7500AZEX-00ZF5A0 | 750 GB | 5       | 475   | 0     | 1.30   |
| Seagate   | ST3160212A         | 160 GB | 8       | 750   | 101   | 1.30   |
| Seagate   | ST3750525AS        | 750 GB | 9       | 595   | 1     | 1.30   |
| Seagate   | ST380013AS         | 80 GB  | 20      | 1102  | 89    | 1.30   |
| WDC       | WD1200JB-00GVA0    | 120 GB | 3       | 836   | 1     | 1.30   |
| WDC       | WD3200AAJB-56R1A0  | 320 GB | 1       | 473   | 0     | 1.30   |
| WDC       | WD5000AAKS-00V0A0  | 500 GB | 3       | 556   | 2     | 1.30   |
| WDC       | WD20NPVX-00EA4T0   | 2 TB   | 1       | 473   | 0     | 1.30   |
| WDC       | WD5000AAKS-75A7B2  | 500 GB | 3       | 1036  | 6     | 1.29   |
| WDC       | WD2500AAKS-00L9A0  | 250 GB | 8       | 971   | 5     | 1.29   |
| WDC       | WD10EARS-00Z5B1    | 1 TB   | 6       | 648   | 106   | 1.29   |
| Seagate   | ST3160215A         | 160 GB | 15      | 705   | 203   | 1.29   |
| WDC       | WD2000JB-00GVA0    | 200 GB | 2       | 468   | 0     | 1.28   |
| WDC       | WD7500BPKT-80PK4T0 | 750 GB | 2       | 467   | 0     | 1.28   |
| Seagate   | ST32000646NS       | 2 TB   | 1       | 467   | 0     | 1.28   |
| Seagate   | ST380815AS         | 80 GB  | 84      | 698   | 256   | 1.28   |
| Hitachi   | HDP725025GLA380    | 250 GB | 27      | 798   | 96    | 1.28   |
| Samsung   | SV0221N            | 20 GB  | 1       | 2328  | 4     | 1.28   |
| WDC       | WD5000AAKS-75V0A0  | 500 GB | 2       | 521   | 4     | 1.27   |
| Hitachi   | HDT721064SLA380    | 640 GB | 1       | 464   | 0     | 1.27   |
| WDC       | WD2500AAJS-00V4A0  | 250 GB | 3       | 589   | 1     | 1.27   |
| Seagate   | ST3802110A         | 80 GB  | 27      | 687   | 417   | 1.26   |
| Hitachi   | HDS721050CLA362    | 500 GB | 93      | 630   | 11    | 1.26   |
| Samsung   | HD105SI            | 1 TB   | 7       | 686   | 552   | 1.26   |
| Hitachi   | HDP725050GLA360    | 500 GB | 55      | 896   | 45    | 1.26   |
| Samsung   | HD502HJ            | 500 GB | 63      | 603   | 52    | 1.26   |
| Seagate   | ST3250312AS        | 250 GB | 11      | 607   | 11    | 1.26   |
| Seagate   | ST3250624AS        | 250 GB | 11      | 762   | 119   | 1.25   |
| Seagate   | ST320LM000 HM321HI | 320 GB | 8       | 482   | 2     | 1.25   |
| WDC       | WD1600BEVS-07RST0  | 160 GB | 5       | 523   | 1     | 1.25   |
| Seagate   | ST380012A          | 80 GB  | 1       | 456   | 0     | 1.25   |
| Seagate   | ST3120026A         | 120 GB | 15      | 927   | 204   | 1.25   |
| WDC       | WD2500AABS-00SDA0  | 250 GB | 1       | 455   | 0     | 1.25   |
| Seagate   | ST3808110AS        | 80 GB  | 25      | 829   | 322   | 1.25   |
| WDC       | WD7500BPVT-24HXZT1 | 750 GB | 6       | 549   | 1     | 1.25   |
| WDC       | WD20EARX-00PASB0   | 2 TB   | 45      | 650   | 160   | 1.25   |
| WDC       | WD5000AAKS-007AA0  | 500 GB | 6       | 846   | 17    | 1.25   |
| Seagate   | ST1000DL002-9TT153 | 1 TB   | 17      | 898   | 492   | 1.24   |
| WDC       | WD5000AZRX-00A8LB0 | 500 GB | 54      | 463   | 1     | 1.24   |
| WDC       | WD10EARX-00N0YB0   | 1 TB   | 39      | 589   | 4     | 1.24   |
| Samsung   | HD153WI            | 1.5 TB | 1       | 451   | 0     | 1.24   |
| WDC       | WD1600JS-00NCB1    | 160 GB | 13      | 551   | 12    | 1.23   |
| Hitachi   | HDS728080PLA380... | 80 GB  | 1       | 449   | 0     | 1.23   |
| WDC       | WD5000BEKT-00KA9T0 | 500 GB | 2       | 1084  | 7     | 1.23   |
| ExcelStor | J360               | 61 GB  | 1       | 897   | 1     | 1.23   |
| Toshiba   | MK1234GAX          | 120 GB | 2       | 448   | 0     | 1.23   |
| WDC       | WD800JB-00JJA0     | 80 GB  | 2       | 873   | 8     | 1.23   |
| Hitachi   | HTS541064A9E680    | 640 GB | 3       | 447   | 0     | 1.23   |
| WDC       | WD15EARX-00ZUDB0   | 1.5 TB | 2       | 776   | 3     | 1.22   |
| WDC       | WD3200YS-01PGB0    | 320 GB | 1       | 446   | 0     | 1.22   |
| WDC       | WD1600AAJS-00Z4A0  | 160 GB | 1       | 445   | 0     | 1.22   |
| Seagate   | ST380817AS         | 80 GB  | 34      | 681   | 8     | 1.22   |
| WDC       | WD740GD-00FLA2     | 74 GB  | 1       | 1330  | 2     | 1.22   |
| WDC       | WD1600BEKT-75A25T0 | 160 GB | 1       | 442   | 0     | 1.21   |
| WDC       | WD5000AAKX-221CA0  | 500 GB | 1       | 882   | 1     | 1.21   |
| WDC       | WD3200LPVX-80V0TT0 | 320 GB | 1       | 440   | 0     | 1.21   |
| Hitachi   | HTS721080G9SA00    | 80 GB  | 2       | 439   | 0     | 1.21   |
| WDC       | WD3200AAKS-00B3A0  | 320 GB | 28      | 673   | 39    | 1.20   |
| WDC       | WD15EZRX-00DC0B0   | 1.5 TB | 1       | 438   | 0     | 1.20   |
| Seagate   | ST3160812A         | 160 GB | 22      | 665   | 420   | 1.20   |
| WDC       | WD5000AADS-00M2B0  | 500 GB | 15      | 643   | 5     | 1.20   |
| Maxtor    | STM3160211AS       | 160 GB | 2       | 437   | 0     | 1.20   |
| WDC       | WD10EALX-759BA1    | 1 TB   | 3       | 554   | 1     | 1.19   |
| WDC       | WD1600BEVT-00ZCT0  | 160 GB | 3       | 435   | 0     | 1.19   |
| WDC       | WD5000AAVS-00ZTB0  | 500 GB | 3       | 434   | 0     | 1.19   |
| WDC       | WD5000AAKS-00WWPA0 | 500 GB | 4       | 570   | 15    | 1.19   |
| Seagate   | ST3120022A         | 120 GB | 30      | 679   | 24    | 1.19   |
| WDC       | WD800JD-22LSA0     | 80 GB  | 6       | 644   | 110   | 1.19   |
| WDC       | WD7500BPKX-80HPJT0 | 750 GB | 2       | 432   | 0     | 1.19   |
| WDC       | WD2500AAKX-001CA0  | 250 GB | 22      | 545   | 65    | 1.19   |
| WDC       | WD6400AAKS-00H2B0  | 640 GB | 1       | 432   | 0     | 1.19   |
| Seagate   | ST3120814A         | 120 GB | 12      | 841   | 252   | 1.18   |
| WDC       | WD2500JS-60NCB1    | 250 GB | 5       | 553   | 1     | 1.18   |
| Toshiba   | MK4058GSX          | 400 GB | 1       | 431   | 0     | 1.18   |
| WDC       | WD10EZEX-00ZF5A0   | 1 TB   | 9       | 526   | 226   | 1.18   |
| Hitachi   | HTS543216A7A384    | 160 GB | 2       | 430   | 0     | 1.18   |
| Samsung   | HD160JJ-P          | 160 GB | 5       | 1099  | 610   | 1.18   |
| Hitachi   | HTE545025B9A300    | 250 GB | 1       | 430   | 0     | 1.18   |
| WDC       | WD6400BPVT-35HXZT1 | 640 GB | 2       | 430   | 0     | 1.18   |
| WDC       | WD1200JS-00MHB1    | 120 GB | 2       | 647   | 12    | 1.18   |
| Samsung   | HD501LJ            | 500 GB | 25      | 801   | 409   | 1.18   |
| WDC       | WD2500AAKS-00VYA0  | 250 GB | 2       | 428   | 0     | 1.17   |
| Seagate   | ST500LM011 HM501II | 500 GB | 1       | 428   | 0     | 1.17   |
| WDC       | WD1200LB-55EDA0    | 120 GB | 1       | 425   | 0     | 1.17   |
| Fujitsu   | MHV2100AT PL       | 100 GB | 1       | 424   | 0     | 1.16   |
| WDC       | WD7500BPVT-80HXZT3 | 750 GB | 7       | 475   | 1     | 1.15   |
| Toshiba   | MK6461GSY          | 640 GB | 2       | 420   | 0     | 1.15   |
| WDC       | WD5000AAKS-22A7B2  | 500 GB | 3       | 939   | 6     | 1.15   |
| WDC       | WD2500JS-00SGB0    | 250 GB | 5       | 566   | 1     | 1.15   |
| WDC       | WD3200AAKS-00SBA0  | 320 GB | 9       | 686   | 21    | 1.15   |
| WDC       | WD1200BEVS-22RST0  | 120 GB | 3       | 444   | 1     | 1.15   |
| WDC       | WD5000AAKS-75A7B0  | 500 GB | 1       | 417   | 0     | 1.14   |
| WDC       | WD1600AAJS-00L7A0  | 160 GB | 20      | 712   | 4     | 1.14   |
| Hitachi   | HTS545050KTA300    | 500 GB | 1       | 834   | 1     | 1.14   |
| Maxtor    | STM3500630AS       | 500 GB | 1       | 416   | 0     | 1.14   |
| WDC       | WD10EARS-00MVWB0   | 1 TB   | 22      | 869   | 44    | 1.14   |
| WDC       | WD2500AAJS-22VTA0  | 250 GB | 4       | 751   | 7     | 1.14   |
| WDC       | WD1600JS-08MHB0    | 160 GB | 1       | 414   | 0     | 1.14   |
| Seagate   | ST3500411SV        | 500 GB | 2       | 694   | 37    | 1.13   |
| Seagate   | ST9160411ASG       | 160 GB | 1       | 413   | 0     | 1.13   |
| Seagate   | ST3250318AS        | 250 GB | 68      | 684   | 123   | 1.13   |
| WDC       | WD15EADS-00P8B0    | 1.5 TB | 5       | 601   | 4     | 1.13   |
| WDC       | WD15EARX-00PASB0   | 1.5 TB | 4       | 412   | 0     | 1.13   |
| Seagate   | ST94813AS          | 40 GB  | 2       | 412   | 0     | 1.13   |
| Seagate   | ST31000525SV       | 1 TB   | 2       | 782   | 2     | 1.13   |
| Seagate   | ST3320820AS        | 320 GB | 5       | 586   | 615   | 1.13   |
| Hitachi   | HDP725032GLA360    | 320 GB | 10      | 860   | 158   | 1.13   |
| Maxtor    | 6V320F0            | 320 GB | 1       | 410   | 0     | 1.13   |
| Maxtor    | STM3160215AS       | 160 GB | 10      | 866   | 491   | 1.13   |
| Seagate   | ST1000DM005 HD1... | 1 TB   | 8       | 542   | 2     | 1.12   |
| WDC       | WD10JPVT-08A1YT1   | 1 TB   | 2       | 408   | 0     | 1.12   |
| Fujitsu   | MHV2080AT PL       | 80 GB  | 2       | 408   | 0     | 1.12   |
| WDC       | WD7500AARS-00Y5B1  | 750 GB | 10      | 482   | 3     | 1.12   |
| WDC       | WD800EB-11DJF0     | 80 GB  | 1       | 407   | 0     | 1.12   |
| WDC       | WD1600AAJS-07M0A0  | 160 GB | 2       | 866   | 1     | 1.12   |
| WDC       | WD5000AAKS-00V2B0  | 500 GB | 2       | 665   | 1     | 1.12   |
| Seagate   | ST3200827AS        | 200 GB | 20      | 821   | 191   | 1.12   |
| WDC       | WD2500JD-00HBB0    | 250 GB | 1       | 406   | 0     | 1.11   |
| Seagate   | ST3160827AS        | 160 GB | 18      | 908   | 19    | 1.11   |
| Samsung   | HM251HI            | 250 GB | 4       | 532   | 3     | 1.11   |
| WDC       | WD10EURX-63C57Y0   | 1 TB   | 1       | 405   | 0     | 1.11   |
| Hitachi   | HTS721080G9AT00    | 80 GB  | 1       | 405   | 0     | 1.11   |
| WDC       | WD2500JS-60MHB5    | 250 GB | 2       | 1170  | 18    | 1.11   |
| Seagate   | ST3000VX000-9YW166 | 3 TB   | 1       | 405   | 0     | 1.11   |
| WDC       | WD2500AAKS-00V6A0  | 250 GB | 1       | 404   | 0     | 1.11   |
| WDC       | WD1600AAJS-00V4A0  | 160 GB | 5       | 408   | 15    | 1.11   |
| Fujitsu   | MHZ2320BH G1       | 320 GB | 5       | 572   | 5     | 1.11   |
| Fujitsu   | MHW2160BH PL       | 160 GB | 5       | 800   | 11    | 1.11   |
| WDC       | WD10EZEX-00RKKA0   | 1 TB   | 49      | 498   | 46    | 1.11   |
| Fujitsu   | MHV2080AH          | 80 GB  | 2       | 402   | 0     | 1.10   |
| WDC       | WD1200BB-00GUC0    | 120 GB | 1       | 1606  | 3     | 1.10   |
| Samsung   | HD642JJ            | 640 GB | 15      | 1015  | 362   | 1.10   |
| Hitachi   | HDS723030ALA640    | 3 TB   | 2       | 400   | 0     | 1.10   |
| Toshiba   | MK1031GAS          | 100 GB | 2       | 647   | 4     | 1.10   |
| WDC       | WD1600AAJS-00WAA0  | 160 GB | 6       | 431   | 3     | 1.10   |
| WDC       | WD10EADS-11P8B2    | 1 TB   | 1       | 799   | 1     | 1.10   |
| WDC       | WD10EZEX-19ZF5A0   | 1 TB   | 1       | 399   | 0     | 1.09   |
| Seagate   | ST3160815A         | 160 GB | 27      | 689   | 187   | 1.09   |
| WDC       | WD2500BEVS-08VAT2  | 250 GB | 2       | 398   | 0     | 1.09   |
| Seagate   | ST3200820A         | 200 GB | 3       | 474   | 101   | 1.09   |
| WDC       | WD6400AARS-00Y5B1  | 640 GB | 11      | 729   | 6     | 1.09   |
| WDC       | WD2500AAKS-00YGA0  | 250 GB | 1       | 397   | 0     | 1.09   |
| WDC       | WD1600BB-22RDA0    | 160 GB | 1       | 396   | 0     | 1.09   |
| WDC       | WD3200AAKS-00L6A0  | 320 GB | 3       | 579   | 4     | 1.09   |
| Seagate   | ST3160318AS        | 160 GB | 34      | 663   | 103   | 1.09   |
| WDC       | WD1000CHTZ-04JCPV0 | 1 TB   | 1       | 395   | 0     | 1.08   |
| WDC       | WD6400BPVT-80HXZT3 | 640 GB | 7       | 668   | 10    | 1.08   |
| WDC       | WD2001FASS-00U0B0  | 2 TB   | 1       | 1578  | 3     | 1.08   |
| WDC       | WD10EALX-008EA0    | 1 TB   | 3       | 394   | 0     | 1.08   |
| Hitachi   | HDS721616PLA380    | 160 GB | 56      | 843   | 112   | 1.08   |
| WDC       | WD15EARS-00S8B1    | 1.5 TB | 2       | 1078  | 4     | 1.08   |
| Seagate   | ST2000NM0033-9Z... | 2 TB   | 3       | 392   | 0     | 1.07   |
| WDC       | WD3200BPVT-00JJ5T0 | 320 GB | 5       | 391   | 0     | 1.07   |
| Seagate   | ST3500418AS        | 500 GB | 229     | 700   | 175   | 1.07   |
| Samsung   | HD502IJ            | 500 GB | 20      | 781   | 372   | 1.07   |
| Seagate   | ST2000NC001-1DY164 | 2 TB   | 4       | 390   | 0     | 1.07   |
| WDC       | WD3200AAJS-00B4A0  | 320 GB | 14      | 850   | 152   | 1.07   |
| WDC       | WD5002ABYS-01B1B0  | 500 GB | 7       | 880   | 4     | 1.07   |
| Fujitsu   | MHV2040AH          | 40 GB  | 4       | 749   | 5     | 1.07   |
| WDC       | WD1600AAJB-00PVA0  | 160 GB | 8       | 714   | 226   | 1.07   |
| WDC       | WD5000LPVT-00FMCT0 | 500 GB | 3       | 389   | 0     | 1.07   |
| WDC       | WD5000BEKT-75KA9T0 | 500 GB | 1       | 387   | 0     | 1.06   |
| Seagate   | ST2000DM001-9YN164 | 2 TB   | 29      | 617   | 236   | 1.06   |
| WDC       | WD10EZEX-00KUWA0   | 1 TB   | 10      | 469   | 2     | 1.06   |
| Hitachi   | HDS721680PLAT80    | 80 GB  | 5       | 866   | 4     | 1.06   |
| Seagate   | ST3250820ACE       | 250 GB | 3       | 520   | 698   | 1.05   |
| WDC       | WD5000BEVT-00A03T0 | 500 GB | 3       | 384   | 0     | 1.05   |
| WDC       | WD10EFRX-68JCSN0   | 1 TB   | 7       | 494   | 147   | 1.05   |
| WDC       | WD2500BEVT-22ZCT0  | 250 GB | 19      | 459   | 1     | 1.05   |
| Seagate   | ST3200820AS        | 200 GB | 18      | 719   | 590   | 1.05   |
| WDC       | WD800JD-22JNA0     | 80 GB  | 1       | 383   | 0     | 1.05   |
| WDC       | WD3000HLHX-01JJPV0 | 300 GB | 2       | 455   | 2     | 1.05   |
| Seagate   | ST1500DM003-1CH16G | 1.5 TB | 7       | 416   | 2     | 1.05   |
| WDC       | WD5000AAKS-00A7B2  | 500 GB | 24      | 799   | 16    | 1.05   |
| WDC       | WD7500AZEX-00RKKA0 | 750 GB | 5       | 381   | 0     | 1.04   |
| WDC       | WD2000JD-22HBB0    | 200 GB | 3       | 993   | 7     | 1.04   |
| Seagate   | ST3500514NS        | 500 GB | 7       | 1229  | 128   | 1.04   |
| WDC       | WD1600AAJS-60WAA0  | 160 GB | 2       | 517   | 506   | 1.04   |
| WDC       | WD20EARX-55PASB0   | 2 TB   | 3       | 380   | 0     | 1.04   |
| Samsung   | HD161HJ 41R0186LEN | 160 GB | 1       | 380   | 0     | 1.04   |
| Seagate   | ST340212AS         | 40 GB  | 2       | 1049  | 105   | 1.04   |
| Maxtor    | STM380215AS        | 80 GB  | 6       | 678   | 809   | 1.04   |
| WDC       | WD5000AAKX-083CA1  | 500 GB | 4       | 448   | 183   | 1.04   |
| WDC       | WD3200AAKS-00V1A0  | 320 GB | 5       | 882   | 319   | 1.04   |
| WDC       | WD1600JS-00MHB0    | 160 GB | 5       | 575   | 36    | 1.04   |
| Maxtor    | 6V080E0            | 81 GB  | 7       | 794   | 7     | 1.04   |
| WDC       | WD5000BEVT-24A0RT0 | 500 GB | 17      | 513   | 3     | 1.03   |
| WDC       | WD1001FALS-00E8B0  | 1 TB   | 9       | 765   | 248   | 1.03   |
| Fujitsu   | MHZ2160BH G2       | 160 GB | 18      | 512   | 347   | 1.03   |
| WDC       | WD2000JS-00SGB0    | 200 GB | 1       | 377   | 0     | 1.03   |
| WDC       | WD5000AAJS-22TKA0  | 500 GB | 1       | 376   | 0     | 1.03   |
| WDC       | WD800BEVS-08RST2   | 80 GB  | 2       | 376   | 0     | 1.03   |
| WDC       | WD5000AAKX-603CA0  | 500 GB | 8       | 461   | 127   | 1.03   |
| WDC       | WD2500BEVS-22UST0  | 250 GB | 35      | 516   | 18    | 1.03   |
| Seagate   | ST9320328CS        | 320 GB | 4       | 730   | 424   | 1.03   |
| WDC       | WD1200BEVS-22UST0  | 120 GB | 12      | 551   | 134   | 1.03   |
| WDC       | WD800BB-00JKA0     | 80 GB  | 1       | 374   | 0     | 1.03   |
| WDC       | WD10EZRX-00A8LB0   | 1 TB   | 30      | 393   | 1     | 1.03   |
| Seagate   | ST3160811AS        | 160 GB | 64      | 804   | 442   | 1.03   |
| Maxtor    | STM3320820AS       | 320 GB | 9       | 744   | 118   | 1.02   |
| WDC       | WD5000BPVT-24HXZT3 | 500 GB | 12      | 433   | 1     | 1.02   |
| Seagate   | ST9402112A         | 40 GB  | 1       | 1117  | 2     | 1.02   |
| WDC       | WD6400BPVT-22HXZT3 | 640 GB | 4       | 372   | 0     | 1.02   |
| WDC       | WD3200AAKS-00UU3A0 | 320 GB | 7       | 609   | 17    | 1.02   |
| WDC       | WD5000BPVT-80HXZT3 | 500 GB | 19      | 428   | 58    | 1.01   |
| Maxtor    | 7V300F0            | 300 GB | 1       | 738   | 1     | 1.01   |
| WDC       | WD3200AAJS-22L7A0  | 320 GB | 4       | 828   | 57    | 1.01   |
| WDC       | WD5000AADS-00S9B0  | 500 GB | 71      | 650   | 37    | 1.01   |
| Hitachi   | HDS5C1050CLA382    | 500 GB | 10      | 603   | 136   | 1.01   |
| WDC       | WD6400AAKS-22A7B2  | 640 GB | 9       | 557   | 2     | 1.01   |
| WDC       | WD10EZEX-08RKKA0   | 1 TB   | 3       | 368   | 0     | 1.01   |
| Samsung   | HD252HJ            | 250 GB | 16      | 705   | 160   | 1.01   |
| WDC       | WD6400AAVS-00G9B1  | 640 GB | 1       | 367   | 0     | 1.01   |
| Hitachi   | HDT721010SLA360    | 1 TB   | 16      | 745   | 10    | 1.00   |
| WDC       | WD3200BPVT-55JJ5T0 | 320 GB | 2       | 366   | 0     | 1.00   |
| Seagate   | ST4000VM000-1F3168 | 4 TB   | 2       | 365   | 0     | 1.00   |
| Hitachi   | HDS721050CLA662    | 500 GB | 6       | 491   | 172   | 1.00   |
| WDC       | WD800JB-00JJC0     | 80 GB  | 18      | 630   | 30    | 1.00   |
| WDC       | WD5000BPKX-00HPJT0 | 500 GB | 2       | 363   | 0     | 1.00   |
| Samsung   | SP0812N            | 80 GB  | 5       | 699   | 5     | 0.99   |
| WDC       | WD20EARS-00J99B0   | 2 TB   | 1       | 362   | 0     | 0.99   |
| WDC       | WD5000BPVT-22HXZT3 | 500 GB | 29      | 456   | 2     | 0.99   |
| WDC       | WD5000AAKS-22A7B0  | 500 GB | 10      | 923   | 6     | 0.99   |
| Hitachi   | HDS721010CLA330    | 1 TB   | 26      | 558   | 46    | 0.99   |
| WDC       | WD3200AAKB-00WHA0  | 320 GB | 1       | 360   | 0     | 0.99   |
| WDC       | WD5000BPKX-60HPJT0 | 500 GB | 2       | 360   | 0     | 0.99   |
| Maxtor    | STM3160212A        | 160 GB | 2       | 817   | 1     | 0.99   |
| WDC       | WD1600JS-56MHB1    | 160 GB | 5       | 477   | 5     | 0.99   |
| Samsung   | SP1613N            | 160 GB | 1       | 1079  | 2     | 0.99   |
| Seagate   | ST3250310AS        | 250 GB | 111     | 808   | 210   | 0.98   |
| Samsung   | HD401LJ            | 400 GB | 1       | 357   | 0     | 0.98   |
| WDC       | WD4000FYYZ-01UL1B1 | 4 TB   | 1       | 357   | 0     | 0.98   |
| WDC       | WD7500BPVT-75A1YT0 | 750 GB | 1       | 357   | 0     | 0.98   |
| WDC       | WD10EALX-009BA0    | 1 TB   | 38      | 587   | 15    | 0.98   |
| Seagate   | ST3500830AS        | 500 GB | 5       | 580   | 1     | 0.98   |
| Seagate   | ST3250310NS        | 250 GB | 3       | 737   | 755   | 0.98   |
| Fujitsu   | MHW2120BJ G2       | 120 GB | 1       | 356   | 0     | 0.98   |
| Seagate   | ST3160211AS        | 160 GB | 5       | 765   | 1271  | 0.97   |
| WDC       | WD5000LPVT-75G33T0 | 500 GB | 4       | 411   | 2     | 0.97   |
| WDC       | WD800BB-00JHC0     | 80 GB  | 14      | 678   | 125   | 0.97   |
| WDC       | WD3200AAJS-00M0A0  | 320 GB | 2       | 574   | 1     | 0.97   |
| Toshiba   | MK3261GSYG         | 320 GB | 1       | 354   | 0     | 0.97   |
| WDC       | WD7500BPKT-75PK4T0 | 750 GB | 4       | 354   | 0     | 0.97   |
| Seagate   | ST500VT000-1DK142  | 500 GB | 2       | 354   | 0     | 0.97   |
| WDC       | WD10EADX-00TDHB0   | 1 TB   | 4       | 762   | 17    | 0.97   |
| WDC       | WD2500BEKT-60PVMT0 | 250 GB | 6       | 353   | 0     | 0.97   |
| WDC       | WD3200BEVT-22ZCT0  | 320 GB | 56      | 454   | 114   | 0.97   |
| Hitachi   | HCP725032GLA380    | 320 GB | 2       | 1010  | 2     | 0.97   |
| Seagate   | ST380811AS         | 80 GB  | 39      | 514   | 383   | 0.97   |
| WDC       | WD6400AACS-00M3B0  | 640 GB | 1       | 352   | 0     | 0.97   |
| Seagate   | ST3120827AS        | 120 GB | 32      | 707   | 12    | 0.96   |
| Seagate   | ST380215A          | 80 GB  | 21      | 485   | 21    | 0.96   |
| WDC       | WD10JPVT-60A1YT0   | 1 TB   | 2       | 455   | 505   | 0.96   |
| Fujitsu   | MHV2120AH          | 120 GB | 2       | 482   | 3     | 0.96   |
| WDC       | WD25EZRX-00MMMB0   | 2.5 TB | 1       | 1049  | 2     | 0.96   |
| WDC       | WD3000BLFS-08YBU0  | 300 GB | 1       | 349   | 0     | 0.96   |
| WDC       | WD6000BLHX-01V7BV0 | 600 GB | 1       | 349   | 0     | 0.96   |
| Samsung   | HD161GJ            | 160 GB | 13      | 630   | 165   | 0.96   |
| Toshiba   | MK6465GSXN         | 640 GB | 6       | 529   | 197   | 0.95   |
| IBM/Hi... | IC35L040AVVA07-0   | 41 GB  | 3       | 711   | 2     | 0.95   |
| WDC       | WD5000BPVT-22HXZT1 | 500 GB | 13      | 450   | 1     | 0.95   |
| WDC       | WD1600BEVS-08RST2  | 160 GB | 1       | 345   | 0     | 0.95   |
| WDC       | WD6400BPVT-16HXZT1 | 640 GB | 1       | 1037  | 2     | 0.95   |
| Seagate   | ST500DM002-1BC142  | 500 GB | 36      | 517   | 161   | 0.95   |
| Hitachi   | HTS541610J9SA00    | 100 GB | 1       | 344   | 0     | 0.94   |
| Samsung   | HD251HJ            | 250 GB | 7       | 753   | 62    | 0.94   |
| WDC       | WD740GD-00FLA0     | 74 GB  | 1       | 2395  | 6     | 0.94   |
| WDC       | WD800BB-00FRA0     | 80 GB  | 2       | 441   | 16    | 0.94   |
| WDC       | WD7500BPVT-60HXZT3 | 750 GB | 4       | 609   | 265   | 0.94   |
| Samsung   | HD322HJ            | 320 GB | 15      | 640   | 106   | 0.94   |
| WDC       | WD6400BPVT-55HXZT2 | 640 GB | 1       | 340   | 0     | 0.93   |
| WDC       | WD15EARX-22PASB0   | 1.5 TB | 1       | 340   | 0     | 0.93   |
| WDC       | WD10EALX-559BA0    | 1 TB   | 4       | 600   | 8     | 0.93   |
| WDC       | WD1600BEVT-22ZCT0  | 160 GB | 58      | 466   | 64    | 0.93   |
| Hitachi   | HDT721032SLA360    | 320 GB | 17      | 835   | 13    | 0.93   |
| WDC       | WD1200BEVS-75UST0  | 120 GB | 9       | 429   | 2     | 0.93   |
| ExcelStor | J680               | 82 GB  | 1       | 1687  | 4     | 0.92   |
| IBM/Hi... | IC35L090AVV207-0   | 80 GB  | 2       | 735   | 2     | 0.92   |
| WDC       | WD10EARS-00Y5B1    | 1 TB   | 61      | 799   | 73    | 0.92   |
| WDC       | WD2500BEVS-75UST0  | 250 GB | 7       | 336   | 0     | 0.92   |
| WDC       | WD1002FBYS-02A6B0  | 1 TB   | 3       | 564   | 3     | 0.92   |
| HGST      | HUS724020ALA640    | 2 TB   | 6       | 335   | 0     | 0.92   |
| Toshiba   | MK6034GAX          | 60 GB  | 1       | 335   | 0     | 0.92   |
| Seagate   | ST3250820A         | 250 GB | 9       | 929   | 595   | 0.92   |
| WDC       | WD10EZEX-60ZF5A0   | 1 TB   | 32      | 405   | 81    | 0.92   |
| WDC       | WD20EZRX-00DC0B0   | 2 TB   | 13      | 387   | 2     | 0.92   |
| Samsung   | HD080HJ            | 80 GB  | 70      | 795   | 371   | 0.92   |
| Maxtor    | STM3160815AS       | 160 GB | 16      | 595   | 220   | 0.92   |
| WDC       | WD5000BHTZ-04JCPV0 | 500 GB | 1       | 334   | 0     | 0.92   |
| WDC       | WD3200BEVT-80A0RT0 | 320 GB | 27      | 454   | 6     | 0.91   |
| WDC       | WD5000BEVT-60A0RT0 | 500 GB | 1       | 667   | 1     | 0.91   |
| Hitachi   | HDS721025CLA382    | 250 GB | 10      | 402   | 3     | 0.91   |
| WDC       | WD2500BEVT-35A23T0 | 250 GB | 17      | 441   | 2     | 0.91   |
| Seagate   | ST3250410AS        | 250 GB | 123     | 775   | 264   | 0.91   |
| Seagate   | ST320DM000-1BC14C  | 320 GB | 12      | 370   | 3     | 0.91   |
| Hitachi   | HDS721032CLA362    | 320 GB | 27      | 668   | 36    | 0.91   |
| WDC       | WD5000AAKS-00E4A0  | 500 GB | 5       | 635   | 3     | 0.91   |
| Fujitsu   | MJA2250BH FFS G1   | 250 GB | 2       | 332   | 0     | 0.91   |
| WDC       | WD1001FALS-00U9B0  | 1 TB   | 1       | 995   | 2     | 0.91   |
| Samsung   | HD154UI            | 1.5 TB | 23      | 743   | 321   | 0.90   |
| Fujitsu   | MHW2080BH          | 80 GB  | 3       | 565   | 6     | 0.90   |
| Hitachi   | HDS721680PLA380    | 80 GB  | 34      | 669   | 161   | 0.90   |
| Toshiba   | MK6459GSXP         | 640 GB | 8       | 421   | 373   | 0.90   |
| Hitachi   | HTS725016A9A364    | 160 GB | 5       | 366   | 204   | 0.90   |
| WDC       | WD15EARS-00MVWB0   | 1.5 TB | 28      | 801   | 365   | 0.90   |
| WDC       | WD2500AAKX-083CA1  | 250 GB | 5       | 720   | 5     | 0.90   |
| WDC       | WD20EARS-07MVWB0   | 2 TB   | 1       | 329   | 0     | 0.90   |
| Hitachi   | HDT721075SLA360    | 750 GB | 1       | 328   | 0     | 0.90   |
| WDC       | WD5000AAKS-00UU3A0 | 500 GB | 38      | 612   | 34    | 0.90   |
| Samsung   | HD753LJ            | 750 GB | 19      | 813   | 260   | 0.90   |
| WDC       | WD6401AALS-00E3A0  | 640 GB | 3       | 579   | 4     | 0.90   |
| WDC       | WD6400AAKS-40H2B0  | 640 GB | 2       | 1447  | 406   | 0.90   |
| WDC       | WD1600BEVS-26VAT0  | 160 GB | 1       | 326   | 0     | 0.89   |
| WDC       | WD5000LPLX-66ZNTT0 | 500 GB | 1       | 326   | 0     | 0.89   |
| WDC       | WD2003FZEX-00Z4SA0 | 2 TB   | 3       | 325   | 0     | 0.89   |
| WDC       | WD3200AAKS-75VYA0  | 320 GB | 2       | 324   | 0     | 0.89   |
| Samsung   | HD503HI            | 500 GB | 12      | 572   | 20    | 0.89   |
| Hitachi   | HDT725032VLA360    | 320 GB | 11      | 623   | 4     | 0.89   |
| Hitachi   | HDS725050KLA360    | 500 GB | 1       | 1941  | 5     | 0.89   |
| Hitachi   | HTS725050A7E630    | 500 GB | 5       | 419   | 1017  | 0.89   |
| WDC       | WD2500JS-58NCB1    | 250 GB | 2       | 773   | 308   | 0.89   |
| Hitachi   | HDE721010SLA330    | 1 TB   | 1       | 323   | 0     | 0.89   |
| Hitachi   | HDS721050CLA660    | 500 GB | 6       | 442   | 14    | 0.89   |
| Seagate   | ST1000NC001-1DY162 | 1 TB   | 2       | 323   | 0     | 0.89   |
| WDC       | WD2500AAKX-00U6AA0 | 250 GB | 2       | 327   | 4     | 0.88   |
| WDC       | WD800AAJS-00WAA0   | 80 GB  | 3       | 323   | 4     | 0.88   |
| Samsung   | HM641JI            | 640 GB | 11      | 408   | 93    | 0.88   |
| Seagate   | ST2000VN000-1H3164 | 2 TB   | 1       | 321   | 0     | 0.88   |
| WDC       | WD800BEVT-22ZCT0   | 80 GB  | 1       | 321   | 0     | 0.88   |
| Seagate   | ST32000542AS       | 2 TB   | 13      | 815   | 532   | 0.88   |
| WDC       | WD2500AAJS-08B4A0  | 250 GB | 2       | 931   | 1211  | 0.88   |
| WDC       | WD3200AAJS-00YZCA0 | 320 GB | 10      | 588   | 5     | 0.88   |
| WDC       | WD10JPVT-55A1YT0   | 1 TB   | 1       | 320   | 0     | 0.88   |
| Seagate   | ST1000VX000-1CU162 | 1 TB   | 19      | 338   | 53    | 0.88   |
| WDC       | WD5000AZDX-00SC2B0 | 500 GB | 2       | 319   | 0     | 0.88   |
| WDC       | WD3200AAKX-001CA0  | 320 GB | 24      | 555   | 17    | 0.88   |
| WDC       | WD5003AZEX-00K1GA0 | 500 GB | 16      | 382   | 68    | 0.87   |
| Seagate   | ST2000DM001-1CH164 | 2 TB   | 68      | 422   | 117   | 0.87   |
| Seagate   | ST3200822AS        | 200 GB | 11      | 750   | 194   | 0.87   |
| WDC       | WD2500BEVT-75ZCT2  | 250 GB | 2       | 317   | 0     | 0.87   |
| WDC       | WD5000AAKX-001CA0  | 500 GB | 117     | 575   | 61    | 0.87   |
| WDC       | WD5003ABYX-01WERA0 | 500 GB | 6       | 556   | 3     | 0.87   |
| Fujitsu   | MHV2100AT          | 100 GB | 1       | 316   | 0     | 0.87   |
| Maxtor    | STM380815AS        | 80 GB  | 14      | 612   | 868   | 0.87   |
| WDC       | WD20EURX-63T0FY0   | 2 TB   | 4       | 315   | 0     | 0.87   |
| WDC       | WD800BEVS-00UST0   | 80 GB  | 1       | 315   | 0     | 0.86   |
| Toshiba   | MK8007GAH          | 80 GB  | 1       | 315   | 0     | 0.86   |
| WDC       | WD6400BEVT-60A0RT0 | 640 GB | 2       | 382   | 18    | 0.86   |
| Seagate   | ST1000NM0033-9Z... | 1 TB   | 17      | 325   | 60    | 0.86   |
| WDC       | WD2500BEVT-00A23T0 | 250 GB | 6       | 657   | 6     | 0.86   |
| WDC       | WD2000JS-55MHB0    | 200 GB | 1       | 313   | 0     | 0.86   |
| WDC       | WD2000JD-00HBB0    | 200 GB | 3       | 636   | 3     | 0.86   |
| WDC       | WD5000BPKT-00PK4T0 | 500 GB | 3       | 340   | 1     | 0.86   |
| WDC       | WD800BB-00FJA0     | 80 GB  | 5       | 405   | 42    | 0.86   |
| WDC       | WD800AAJS-00L7A0   | 80 GB  | 1       | 313   | 0     | 0.86   |
| Fujitsu   | MHY2200BH          | 200 GB | 11      | 615   | 53    | 0.86   |
| Samsung   | HN-M500MBB         | 500 GB | 22      | 400   | 3     | 0.86   |
| Seagate   | ST2000VX002-1AH166 | 2 TB   | 1       | 312   | 0     | 0.85   |
| WDC       | WD3001FAEX-00MJRA0 | 3 TB   | 2       | 311   | 0     | 0.85   |
| WDC       | WD30EFRX-68EUZN0   | 3 TB   | 16      | 334   | 1     | 0.85   |
| Seagate   | ST3160021A         | 160 GB | 7       | 514   | 866   | 0.85   |
| IBM/Hi... | IC35L120AVV207-0   | 123 GB | 1       | 933   | 2     | 0.85   |
| ExcelStor | J8160S             | 160 GB | 3       | 462   | 3     | 0.85   |
| WDC       | WD3200BPVT-35ZEST0 | 320 GB | 17      | 369   | 2     | 0.85   |
| Seagate   | ST2000NM0011       | 2 TB   | 2       | 1218  | 7     | 0.85   |
| WDC       | WD1200JB-00DUA3    | 120 GB | 1       | 1235  | 3     | 0.85   |
| WDC       | WD1600JS-40TGB0    | 160 GB | 1       | 308   | 0     | 0.85   |
| WDC       | WD10EZEX-21M2NA0   | 1 TB   | 17      | 320   | 1     | 0.84   |
| WDC       | WD3200BEVT-00SCST0 | 320 GB | 1       | 306   | 0     | 0.84   |
| Seagate   | ST3250824AS        | 250 GB | 14      | 732   | 611   | 0.84   |
| WDC       | WD400BB-00JHA0     | 40 GB  | 1       | 1836  | 5     | 0.84   |
| Samsung   | HD400LJ            | 400 GB | 2       | 480   | 5     | 0.84   |
| Seagate   | STM3320418AS       | 320 GB | 9       | 586   | 43    | 0.84   |
| Maxtor    | 6V200E0            | 203 GB | 4       | 712   | 225   | 0.84   |
| WDC       | WD5000AAJS-19A8B0  | 500 GB | 1       | 305   | 0     | 0.84   |
| Seagate   | ST250DM001 HD253GJ | 250 GB | 5       | 304   | 0     | 0.83   |
| WDC       | WD5000BPVT-08HXZT3 | 500 GB | 7       | 333   | 1     | 0.83   |
| WDC       | WD7500BPVT-22HXZT3 | 750 GB | 21      | 365   | 1     | 0.83   |
| Seagate   | ST1500LM006 HN-... | 1.5 TB | 1       | 302   | 0     | 0.83   |
| Seagate   | ST9250410AS        | 250 GB | 21      | 429   | 98    | 0.83   |
| Seagate   | ST500DM005 HD502HJ | 500 GB | 25      | 405   | 3     | 0.83   |
| WDC       | WD3200BEKT-60PVMT0 | 320 GB | 3       | 301   | 0     | 0.83   |
| Seagate   | ST3000DM001-1ER166 | 3 TB   | 5       | 300   | 0     | 0.82   |
| WDC       | WD7500BPVX-22JC3T0 | 750 GB | 9       | 369   | 1     | 0.82   |
| WDC       | WD600BEAS-22KZT0   | 60 GB  | 1       | 300   | 0     | 0.82   |
| Seagate   | ST3250620A         | 250 GB | 11      | 536   | 58    | 0.82   |
| WDC       | WD5002AALX-00J37A0 | 500 GB | 7       | 522   | 3     | 0.82   |
| Toshiba   | DT01ACA300         | 3 TB   | 28      | 358   | 73    | 0.82   |
| WDC       | WD5000BPVT-00HXZT1 | 500 GB | 9       | 412   | 70    | 0.82   |
| Seagate   | ST340016A          | 40 GB  | 19      | 640   | 36    | 0.82   |
| WDC       | WD5000AAKX-08ERMA0 | 500 GB | 15      | 425   | 155   | 0.82   |
| Samsung   | HM321HI            | 320 GB | 50      | 435   | 45    | 0.82   |
| Seagate   | ST1000DM003-9YN162 | 1 TB   | 68      | 492   | 260   | 0.81   |
| Fujitsu   | MHX2300BT          | 300 GB | 3       | 759   | 47    | 0.81   |
| WDC       | WD800BB-56JKC0     | 80 GB  | 2       | 450   | 4     | 0.81   |
| Toshiba   | DT01ACA200         | 2 TB   | 51      | 306   | 41    | 0.81   |
| Seagate   | ST320011A          | 20 GB  | 6       | 549   | 5     | 0.80   |
| WDC       | WD3200BEKT-08PVMT1 | 320 GB | 2       | 293   | 0     | 0.80   |
| WDC       | WD2500AAJS-07M0A0  | 250 GB | 3       | 622   | 6     | 0.80   |
| Seagate   | ST31000524AS       | 1 TB   | 120     | 540   | 229   | 0.80   |
| Samsung   | SV1203N            | 120 GB | 2       | 441   | 3     | 0.80   |
| Seagate   | ST2000LM003 HN-... | 2 TB   | 11      | 292   | 0     | 0.80   |
| WDC       | WD2500BEKT-75A25T0 | 250 GB | 1       | 292   | 0     | 0.80   |
| WDC       | WD2500AAJS-60Z0A0  | 250 GB | 2       | 291   | 0     | 0.80   |
| Hitachi   | HDS721050CLA360    | 500 GB | 34      | 431   | 59    | 0.80   |
| WDC       | WD3200AAJS-22B4A0  | 320 GB | 4       | 1078  | 7     | 0.80   |
| Seagate   | ST31000520AS       | 1 TB   | 12      | 961   | 477   | 0.80   |
| Magnet... | MD02500-BJDW-RO    | 250 GB | 1       | 291   | 0     | 0.80   |
| WDC       | WD2500AAJS-00B4A0  | 250 GB | 13      | 670   | 59    | 0.80   |
| WDC       | WD10EZRX-00DC0B0   | 1 TB   | 3       | 290   | 0     | 0.80   |
| Hitachi   | HCS5C1025CLA382    | 250 GB | 1       | 290   | 0     | 0.80   |
| Fujitsu   | MJA2160BH G2       | 160 GB | 3       | 435   | 74    | 0.79   |
| IBM/Hi... | IC35L120AVV207-1   | 123 GB | 1       | 288   | 0     | 0.79   |
| WDC       | WD3200LPVT-08G33T1 | 320 GB | 2       | 287   | 0     | 0.79   |
| WDC       | WD3000GLFS-01F8U0  | 300 GB | 1       | 287   | 0     | 0.79   |
| WDC       | WD20EZRX-00D8PB0   | 2 TB   | 18      | 330   | 27    | 0.79   |
| Maxtor    | STM380811AS        | 80 GB  | 4       | 500   | 5     | 0.79   |
| Toshiba   | MK3029GAC          | 30 GB  | 1       | 287   | 0     | 0.79   |
| WDC       | WD5000LPVT-22G33T0 | 500 GB | 12      | 315   | 97    | 0.79   |
| Seagate   | ST2000VX000-1CU164 | 2 TB   | 8       | 286   | 0     | 0.79   |
| Samsung   | HD502HI            | 500 GB | 12      | 541   | 107   | 0.78   |
| Seagate   | ST1000DM003-1CH162 | 1 TB   | 193     | 368   | 18    | 0.78   |
| WDC       | WD10EADS-22M2B0    | 1 TB   | 4       | 825   | 5     | 0.78   |
| Toshiba   | MK4025GAS          | 40 GB  | 1       | 571   | 1     | 0.78   |
| WDC       | WD5003ABYX-01WERA1 | 500 GB | 4       | 469   | 1     | 0.78   |
| Toshiba   | HDWA130            | 3 TB   | 1       | 285   | 0     | 0.78   |
| WDC       | WD2500BEKT-00PVMT0 | 250 GB | 1       | 284   | 0     | 0.78   |
| Seagate   | ST3160316AS        | 160 GB | 8       | 470   | 11    | 0.78   |
| WDC       | WD6402AAEX-00Y9A0  | 640 GB | 2       | 555   | 15    | 0.78   |
| WDC       | WD1600BEVS-60RST0  | 160 GB | 7       | 518   | 323   | 0.78   |
| Hitachi   | HDS721032CLA662    | 320 GB | 1       | 283   | 0     | 0.78   |
| WDC       | WD5000AAKS-65A7B0  | 500 GB | 4       | 505   | 101   | 0.77   |
| WDC       | WD2500BEKT-60A25T1 | 250 GB | 5       | 462   | 2     | 0.77   |
| WDC       | WD1600BEVT-75ZCT2  | 160 GB | 10      | 335   | 6     | 0.77   |
| WDC       | WD6400AACS-00G8B1  | 640 GB | 5       | 667   | 6     | 0.77   |
| WDC       | WD40EZRX-00SPEB0   | 4 TB   | 3       | 366   | 7     | 0.77   |
| WDC       | WD1200BEVT-22ZCT0  | 120 GB | 1       | 281   | 0     | 0.77   |
| Samsung   | HD321KJ            | 320 GB | 40      | 695   | 287   | 0.77   |
| WDC       | WD1600BEVT-60ZCT1  | 160 GB | 3       | 391   | 336   | 0.77   |
| Seagate   | ST2000DX001-1NS164 | 2 TB   | 2       | 279   | 0     | 0.77   |
| WDC       | WD800BB-22JHC0     | 80 GB  | 8       | 452   | 47    | 0.76   |
| WDC       | WD1600JS-60NCB1    | 160 GB | 4       | 602   | 78    | 0.76   |
| Fujitsu   | MHW2100BH          | 100 GB | 1       | 279   | 0     | 0.76   |
| WDC       | WD100EB-00BHF0     | 10 GB  | 1       | 557   | 1     | 0.76   |
| Hitachi   | HDP725050GLAT80    | 500 GB | 1       | 278   | 0     | 0.76   |
| Seagate   | ST3160023AS        | 160 GB | 9       | 738   | 52    | 0.76   |
| Toshiba   | MK8032GSX          | 80 GB  | 6       | 426   | 214   | 0.76   |
| WDC       | WD5000BPVT-35HXZT1 | 500 GB | 3       | 275   | 0     | 0.75   |
| WDC       | WD800BEVS-22RST0   | 80 GB  | 20      | 415   | 63    | 0.75   |
| WDC       | WD3200BEKT-60V5T1  | 320 GB | 17      | 464   | 341   | 0.75   |
| WDC       | WD1600AAJS-00YZCA0 | 160 GB | 8       | 541   | 45    | 0.75   |
| WDC       | WD3200BPVT-22ZEST0 | 320 GB | 34      | 418   | 29    | 0.75   |
| Hitachi   | HUA721010KLA330    | 1 TB   | 2       | 272   | 0     | 0.75   |
| WDC       | WD5000AAKX-00ERMA0 | 500 GB | 63      | 392   | 4     | 0.75   |
| WDC       | WD3200BPVT-55ZEST0 | 320 GB | 2       | 316   | 2     | 0.75   |
| Hitachi   | HTS545050B9A300    | 500 GB | 70      | 539   | 174   | 0.74   |
| WDC       | WD10JPVX-16JC3T3   | 1 TB   | 2       | 269   | 0     | 0.74   |
| WDC       | WD2500BEVT-24A23T0 | 250 GB | 14      | 358   | 43    | 0.74   |
| WDC       | WD5000AAKS-22V1A0  | 500 GB | 8       | 576   | 169   | 0.74   |
| WDC       | WD5000BPVT-00HXZT3 | 500 GB | 7       | 387   | 70    | 0.74   |
| Toshiba   | MK2035GSS          | 200 GB | 6       | 524   | 21    | 0.74   |
| Samsung   | HD250HJ            | 250 GB | 26      | 804   | 670   | 0.74   |
| WDC       | WD5000AAJS-22YFA0  | 500 GB | 4       | 809   | 528   | 0.74   |
| Hitachi   | HTS545032B9A300    | 320 GB | 65      | 484   | 141   | 0.73   |
| WDC       | WD1200JD-22HBB0    | 120 GB | 2       | 1602  | 5     | 0.73   |
| WDC       | WD3200LPVT-00FMCT0 | 320 GB | 1       | 266   | 0     | 0.73   |
| WDC       | WD3200BEKX-75B7WT0 | 320 GB | 1       | 266   | 0     | 0.73   |
| WDC       | WD7500BPVT-24HXZT3 | 750 GB | 8       | 320   | 32    | 0.73   |
| WDC       | WD6000HLHX-01JJPV0 | 600 GB | 6       | 482   | 5     | 0.73   |
| WDC       | WD3200BPVT-24JJ5T0 | 320 GB | 37      | 318   | 50    | 0.73   |
| WDC       | WD5000AAKS-65A7B2  | 500 GB | 1       | 265   | 0     | 0.73   |
| WDC       | WD2500AAKS-61L9A0  | 250 GB | 1       | 265   | 0     | 0.73   |
| WDC       | WD2500BEKT-00A25T0 | 250 GB | 1       | 264   | 0     | 0.73   |
| WDC       | WD1200BEVS-07RST0  | 120 GB | 2       | 263   | 0     | 0.72   |
| WDC       | WD2500AAKX-00ERMA0 | 250 GB | 15      | 371   | 91    | 0.72   |
| Seagate   | ST250DM000-1BC141  | 250 GB | 8       | 339   | 12    | 0.72   |
| Seagate   | ST3750528AS        | 750 GB | 28      | 675   | 176   | 0.72   |
| Maxtor    | STM3250310AS       | 250 GB | 40      | 600   | 369   | 0.72   |
| WDC       | WD3200AAJS-00L7A0  | 320 GB | 49      | 691   | 71    | 0.72   |
| Seagate   | ST3160215AS        | 160 GB | 11      | 481   | 761   | 0.72   |
| Fujitsu   | MHY2120BH          | 120 GB | 11      | 457   | 423   | 0.72   |
| WDC       | WD6400BPVT-00HXZT1 | 640 GB | 2       | 260   | 0     | 0.71   |
| Samsung   | HD080HJ-P          | 80 GB  | 4       | 484   | 2     | 0.71   |
| Hitachi   | HTS542516K9A300    | 160 GB | 6       | 789   | 220   | 0.71   |
| Seagate   | STM3500418AS       | 500 GB | 17      | 753   | 445   | 0.71   |
| Hitachi   | HUA722010CLA330    | 1 TB   | 6       | 368   | 10    | 0.71   |
| Seagate   | ST91208220AS       | 120 GB | 2       | 461   | 507   | 0.71   |
| WDC       | WD800JD-00JNC0     | 80 GB  | 3       | 539   | 20    | 0.71   |
| Maxtor    | STM3250820AS       | 250 GB | 7       | 742   | 239   | 0.71   |
| Hitachi   | HDT721032SLA380    | 320 GB | 5       | 581   | 468   | 0.70   |
| Seagate   | ST31000528AS       | 1 TB   | 121     | 594   | 250   | 0.70   |
| WDC       | WD10EURX-56FH1Y0   | 1 TB   | 1       | 256   | 0     | 0.70   |
| WDC       | WD5000AAKX-08ANVA0 | 500 GB | 2       | 256   | 0     | 0.70   |
| WDC       | WD10EZEX-08M2NA0   | 1 TB   | 43      | 278   | 2     | 0.70   |
| WDC       | WD10EAVS-00D7B1    | 1 TB   | 3       | 552   | 3     | 0.70   |
| WDC       | WD10JPVX-08JC3T5   | 1 TB   | 4       | 254   | 0     | 0.70   |
| Seagate   | ST250DM000-1BD141  | 250 GB | 51      | 398   | 143   | 0.70   |
| Fujitsu   | MHX2250BT          | 250 GB | 2       | 409   | 5     | 0.70   |
| Maxtor    | STM3320620AS       | 320 GB | 2       | 254   | 0     | 0.70   |
| WDC       | WD3200BEKT-00F3T0  | 320 GB | 2       | 253   | 0     | 0.69   |
| WDC       | WD800BEVS-07RST0   | 80 GB  | 1       | 253   | 0     | 0.69   |
| Hitachi   | HTS547550A9E384    | 500 GB | 92      | 375   | 256   | 0.69   |
| Toshiba   | MD04ACA400         | 4 TB   | 1       | 253   | 0     | 0.69   |
| WDC       | WD40PURX-64GVNY0   | 4 TB   | 1       | 253   | 0     | 0.69   |
| Seagate   | ST1000DM003-1ER162 | 1 TB   | 102     | 253   | 2     | 0.69   |
| WDC       | WD7500AZEX-00BN5A0 | 750 GB | 1       | 252   | 0     | 0.69   |
| HP        | VB0250EAVER        | 250 GB | 2       | 252   | 0     | 0.69   |
| WDC       | WD5000AAKS-07A7B0  | 500 GB | 3       | 754   | 6     | 0.69   |
| WDC       | WD1600JS-08NCB1    | 160 GB | 3       | 556   | 44    | 0.69   |
| Seagate   | ST3120211AS        | 120 GB | 4       | 601   | 15    | 0.69   |
| WDC       | WD3200AAKS-00V6A0  | 320 GB | 2       | 383   | 1     | 0.69   |
| Samsung   | HD163GJ            | 160 GB | 1       | 251   | 0     | 0.69   |
| Maxtor    | 6V160E0            | 160 GB | 5       | 300   | 1     | 0.69   |
| Hitachi   | HDS721010CLA632    | 1 TB   | 1       | 251   | 0     | 0.69   |
| WDC       | WD10EALX-229BA0    | 1 TB   | 4       | 841   | 9     | 0.69   |
| Maxtor    | 6L020J1            | 20 GB  | 2       | 463   | 3     | 0.69   |
| WDC       | WD2500JB-00REA0    | 250 GB | 7       | 617   | 31    | 0.68   |
| WDC       | WD3200AAJS-60M0A0  | 320 GB | 1       | 749   | 2     | 0.68   |
| WDC       | WD20EURS-63S48Y0   | 2 TB   | 2       | 266   | 1011  | 0.68   |
| Samsung   | HD120IJ            | 120 GB | 16      | 841   | 305   | 0.68   |
| WDC       | WD3200BPVT-24ZEST0 | 320 GB | 15      | 312   | 4     | 0.68   |
| Hitachi   | HDT722516DLA380    | 164 GB | 7       | 776   | 81    | 0.68   |
| Apple     | HDD HTS545050A7... | 500 GB | 5       | 293   | 3     | 0.68   |
| WDC       | WD1003FBYZ-010FB0  | 1 TB   | 5       | 442   | 3     | 0.68   |
| Toshiba   | MQ01ABD075         | 750 GB | 63      | 326   | 9     | 0.68   |
| Toshiba   | MK5075GSX          | 500 GB | 8       | 324   | 160   | 0.68   |
| WDC       | WD2500AAKS-00UU3A0 | 250 GB | 1       | 247   | 0     | 0.68   |
| WDC       | WD2000JS-00MHB1    | 200 GB | 1       | 246   | 0     | 0.68   |
| Seagate   | ST500DM002-1BD142  | 500 GB | 305     | 357   | 74    | 0.68   |
| WDC       | WD10EZRX-00L4HB0   | 1 TB   | 25      | 278   | 6     | 0.68   |
| Hitachi   | HCT721016SLA380    | 160 GB | 3       | 246   | 0     | 0.67   |
| Fujitsu   | MJA2500BH FFS G1   | 500 GB | 1       | 246   | 0     | 0.67   |
| Samsung   | HM320HJ            | 320 GB | 3       | 415   | 422   | 0.67   |
| WDC       | WD1600AAJS-22L7A0  | 160 GB | 12      | 447   | 7     | 0.67   |
| Seagate   | ST980813AS         | 80 GB  | 1       | 246   | 0     | 0.67   |
| WDC       | WD5000LPVT-08G33T1 | 500 GB | 9       | 245   | 0     | 0.67   |
| Toshiba   | HDWA120            | 2 TB   | 1       | 245   | 0     | 0.67   |
| Seagate   | ST750LM022 HN-M... | 750 GB | 65      | 311   | 26    | 0.67   |
| WDC       | WD7501AALS-00E3A0  | 750 GB | 7       | 635   | 52    | 0.67   |
| WDC       | WD800JB-00ETA0     | 80 GB  | 4       | 1139  | 341   | 0.67   |
| WDC       | WD7500BPVT-22A1YT0 | 750 GB | 1       | 733   | 2     | 0.67   |
| WDC       | WD1600BB-00RDA0    | 160 GB | 2       | 691   | 39    | 0.67   |
| WDC       | WD5000BEVT-11A0RT0 | 500 GB | 1       | 243   | 0     | 0.67   |
| Samsung   | SP0411N            | 40 GB  | 1       | 4382  | 17    | 0.67   |
| WDC       | WD1600AAJB-22WRA0  | 160 GB | 2       | 722   | 3     | 0.67   |
| Hitachi   | HTS547575A9E384    | 750 GB | 71      | 390   | 411   | 0.66   |
| WDC       | WD2500AAJS-07B4A0  | 250 GB | 1       | 2180  | 8     | 0.66   |
| WDC       | WD10EAVS-22D7B0    | 1 TB   | 1       | 2174  | 8     | 0.66   |
| WDC       | WD3200BPVT-22JJ5T0 | 320 GB | 76      | 290   | 50    | 0.66   |
| Fujitsu   | MHW2080AT          | 80 GB  | 1       | 241   | 0     | 0.66   |
| WDC       | WD10JPVT-08A1YT2   | 1 TB   | 6       | 305   | 1     | 0.66   |
| Samsung   | HM250HI            | 250 GB | 48      | 335   | 9     | 0.66   |
| Samsung   | MP0402H            | 40 GB  | 3       | 284   | 2     | 0.66   |
| WDC       | WD2500BEVT-22A23T0 | 250 GB | 35      | 390   | 36    | 0.66   |
| Toshiba   | DT01ACA100         | 1 TB   | 137     | 277   | 12    | 0.66   |
| Seagate   | ST9320423AS        | 320 GB | 24      | 381   | 253   | 0.66   |
| WDC       | WD2502ABYS-18B7A0  | 250 GB | 1       | 239   | 0     | 0.66   |
| WDC       | WD5000AARS-003BB1  | 500 GB | 4       | 626   | 5     | 0.66   |
| WDC       | WD1000DHTZ-04N21V0 | 1 TB   | 2       | 643   | 4     | 0.66   |
| WDC       | WD3200BEVT-00A0RT0 | 320 GB | 14      | 302   | 16    | 0.65   |
| Toshiba   | MQ01ABD032         | 320 GB | 50      | 282   | 61    | 0.65   |
| Hitachi   | HTS545025B9A300    | 250 GB | 69      | 439   | 158   | 0.65   |
| WDC       | WD800AAJS-00B4A0   | 80 GB  | 3       | 370   | 4     | 0.65   |
| Hitachi   | HTS541010G9AT00    | 100 GB | 1       | 474   | 1     | 0.65   |
| Seagate   | ST320410A          | 20 GB  | 3       | 1020  | 17    | 0.65   |
| WDC       | WD10EFRX-68PJCN0   | 1 TB   | 16      | 256   | 1     | 0.65   |
| WDC       | WD5000BPVT-75HXZT3 | 500 GB | 14      | 411   | 3     | 0.65   |
| Apple     | HDD HTS541010A9... | 1 TB   | 8       | 280   | 253   | 0.65   |
| Maxtor    | STM3250820A        | 250 GB | 3       | 603   | 435   | 0.64   |
| WDC       | WD3200BEVS-26VAT0  | 320 GB | 1       | 235   | 0     | 0.64   |
| Seagate   | ST2000VX000-1ES164 | 2 TB   | 4       | 234   | 0     | 0.64   |
| WDC       | WD1200BEVS-60UST0  | 120 GB | 4       | 605   | 605   | 0.64   |
| Samsung   | HM500JI            | 500 GB | 16      | 362   | 4     | 0.64   |
| WDC       | WD1003FZEX-00MK2A0 | 1 TB   | 32      | 234   | 0     | 0.64   |
| WDC       | WD3200BEKT-75KA9T0 | 320 GB | 1       | 234   | 0     | 0.64   |
| Samsung   | SP0802N            | 80 GB  | 19      | 698   | 51    | 0.64   |
| Samsung   | HD320KJ            | 320 GB | 1       | 234   | 0     | 0.64   |
| WDC       | WD5000AADS-67S9B0  | 500 GB | 1       | 2104  | 8     | 0.64   |
| WDC       | WD10EZEX-60M2NA0   | 1 TB   | 6       | 286   | 168   | 0.64   |
| WDC       | WD5000BEVT-00A0RT0 | 500 GB | 6       | 387   | 78    | 0.64   |
| Seagate   | ST1500DL003-9VT16L | 1.5 TB | 19      | 734   | 258   | 0.64   |
| WDC       | WD5000BPVT-55HXZT3 | 500 GB | 1       | 233   | 0     | 0.64   |
| WDC       | WD1600JD-22HBB0    | 160 GB | 1       | 1396  | 5     | 0.64   |
| WDC       | WD6400BPVT-26HXZT1 | 640 GB | 1       | 232   | 0     | 0.64   |
| WDC       | WD10SPCX-24HWST1   | 1 TB   | 1       | 232   | 0     | 0.64   |
| Seagate   | ST500NM0011        | 500 GB | 7       | 750   | 85    | 0.64   |
| WDC       | WD7500BPVT-75HXZT3 | 750 GB | 2       | 231   | 0     | 0.63   |
| Seagate   | ST3160813AS        | 160 GB | 23      | 848   | 185   | 0.63   |
| Toshiba   | MK5065GSXF         | 500 GB | 5       | 385   | 6     | 0.63   |
| Seagate   | ST320DM000-1BD14C  | 320 GB | 25      | 281   | 46    | 0.63   |
| WDC       | WD5000BPVT-22A1YT0 | 500 GB | 7       | 229   | 0     | 0.63   |
| Toshiba   | L200 Hard drive    | 2 TB   | 2       | 229   | 0     | 0.63   |
| WDC       | WD5002ABYS-02B1B0  | 500 GB | 4       | 557   | 3     | 0.63   |
| WDC       | WD800BB-98JHC0     | 80 GB  | 1       | 1829  | 7     | 0.63   |
| Seagate   | ST9160411AS        | 160 GB | 2       | 474   | 14    | 0.63   |
| Seagate   | ST1000VM002-1CT162 | 1 TB   | 2       | 227   | 0     | 0.62   |
| Seagate   | ST4000DM000-1F2168 | 4 TB   | 7       | 255   | 1     | 0.62   |
| WDC       | WD3200AAJS-60Z0A0  | 320 GB | 4       | 574   | 61    | 0.62   |
| Seagate   | ST9120822AS        | 120 GB | 26      | 430   | 136   | 0.62   |
| WDC       | WD2500YD-01NVB1    | 251 GB | 1       | 1357  | 5     | 0.62   |
| Seagate   | ST3250823A         | 250 GB | 4       | 854   | 659   | 0.62   |
| WDC       | WD5000BEKT-80KA9T1 | 500 GB | 4       | 280   | 1     | 0.62   |
| WDC       | WD5000AAKS-00V1A0  | 500 GB | 34      | 750   | 193   | 0.62   |
| Samsung   | SP1624N            | 160 GB | 1       | 225   | 0     | 0.62   |
| Toshiba   | MK5076GSXN         | 500 GB | 1       | 224   | 0     | 0.62   |
| Hitachi   | HDS721010CLA630    | 1 TB   | 5       | 321   | 1     | 0.62   |
| WDC       | WD3200BPVT-75JJ5T0 | 320 GB | 2       | 336   | 4     | 0.61   |
| WDC       | WD10EZEX-22RKKA0   | 1 TB   | 2       | 224   | 0     | 0.61   |
| Hitachi   | HDS721010DLE630    | 1 TB   | 22      | 575   | 346   | 0.61   |
| WDC       | WD3200BEVT-60ZCT1  | 320 GB | 2       | 386   | 10    | 0.61   |
| Fujitsu   | MHW2120BJ FFS G2   | 120 GB | 1       | 221   | 0     | 0.61   |
| WDC       | WD6400BPVT-22HXZT1 | 640 GB | 3       | 308   | 4     | 0.61   |
| WDC       | WD10EZEX-00BN5A0   | 1 TB   | 65      | 248   | 2     | 0.61   |
| Hitachi   | HTS545032A7E380    | 320 GB | 17      | 299   | 124   | 0.60   |
| Seagate   | ST1000LM014-1EJ164 | 1 TB   | 25      | 310   | 185   | 0.60   |
| Fujitsu   | MHZ2160BH G1       | 160 GB | 6       | 281   | 1     | 0.60   |
| WDC       | WD3200AAKX-221CA1  | 320 GB | 1       | 218   | 0     | 0.60   |
| WDC       | WD3000HLFS-75G6U1  | 300 GB | 1       | 218   | 0     | 0.60   |
| Maxtor    | 6G160P0            | 160 GB | 2       | 217   | 0     | 0.60   |
| Hitachi   | HTS541010A9E680    | 1 TB   | 6       | 371   | 526   | 0.60   |
| WDC       | WD10EZEX-22BN5A0   | 1 TB   | 10      | 307   | 2     | 0.59   |
| HGST      | HDN724030ALE640    | 3 TB   | 2       | 216   | 0     | 0.59   |
| Seagate   | ST3000DM001-1CH166 | 3 TB   | 12      | 310   | 338   | 0.59   |
| WDC       | WD20EZRX-22D8PB0   | 2 TB   | 1       | 215   | 0     | 0.59   |
| Seagate   | ST320LM001 HN-M... | 320 GB | 25      | 238   | 2     | 0.59   |
| WDC       | WD3200AZDX-00SC2B0 | 320 GB | 2       | 379   | 440   | 0.59   |
| Seagate   | ST9160823ASG       | 160 GB | 2       | 400   | 506   | 0.59   |
| Samsung   | HM320II            | 320 GB | 13      | 400   | 313   | 0.59   |
| Hitachi   | HTS542516K9SA00    | 160 GB | 28      | 563   | 215   | 0.59   |
| WDC       | WD10EZEX-75ZF5A0   | 1 TB   | 4       | 215   | 0     | 0.59   |
| Hitachi   | HDS721010KLA330    | 1 TB   | 5       | 575   | 10    | 0.59   |
| Hitachi   | HTS541080G9SA00    | 80 GB  | 4       | 467   | 5     | 0.59   |
| Samsung   | HD160JJ            | 160 GB | 48      | 807   | 444   | 0.59   |
| WDC       | WD10JPVX-60JC3T0   | 1 TB   | 8       | 249   | 101   | 0.59   |
| WDC       | WD10JPVX-80JC3T0   | 1 TB   | 7       | 214   | 0     | 0.59   |
| WDC       | WD3200BEVT-22A23T0 | 320 GB | 25      | 513   | 80    | 0.58   |
| Seagate   | ST33000651AS       | 3 TB   | 1       | 211   | 0     | 0.58   |
| Hitachi   | HTS545016B9A300    | 160 GB | 26      | 306   | 47    | 0.58   |
| Seagate   | ST9750420AS        | 750 GB | 32      | 384   | 75    | 0.58   |
| WDC       | WD1600BEVT-24A23T0 | 160 GB | 8       | 249   | 2     | 0.58   |
| Seagate   | ST320014A          | 20 GB  | 5       | 628   | 16    | 0.58   |
| WDC       | WD1600JB-00GVC0    | 160 GB | 1       | 210   | 0     | 0.58   |
| Seagate   | ST3160212ACE       | 160 GB | 4       | 492   | 27    | 0.57   |
| WDC       | WD1600JD-00HBB0    | 160 GB | 3       | 696   | 6     | 0.57   |
| Samsung   | HD322GJ            | 320 GB | 14      | 336   | 22    | 0.57   |
| WDC       | WD5000LPVX-80V0TT0 | 500 GB | 27      | 217   | 1     | 0.57   |
| Seagate   | ST32000641AS       | 2 TB   | 6       | 473   | 268   | 0.57   |
| WDC       | WD10JPVT-22A1YT0   | 1 TB   | 5       | 321   | 1     | 0.57   |
| Seagate   | STM3250318AS       | 250 GB | 16      | 443   | 125   | 0.57   |
| WDC       | WD5000BEKT-80KA9T0 | 500 GB | 3       | 317   | 1     | 0.57   |
| Hitachi   | HTS543225L9A300    | 250 GB | 16      | 590   | 352   | 0.57   |
| IBM/Hi... | IC35L040AVVN07-0   | 41 GB  | 2       | 576   | 3     | 0.57   |
| WDC       | WD3200BPVT-80JJ5T0 | 320 GB | 45      | 286   | 53    | 0.57   |
| Seagate   | ST2000VN000-1HJ164 | 2 TB   | 1       | 208   | 0     | 0.57   |
| WDC       | WD400BB-00FJA0     | 40 GB  | 2       | 699   | 222   | 0.57   |
| Hitachi   | HDT721025SLA380    | 250 GB | 7       | 550   | 5     | 0.57   |
| WDC       | WD1600BJKT-75F4T0  | 160 GB | 3       | 243   | 1     | 0.57   |
| WDC       | WD2500AAJS-65M0A0  | 250 GB | 3       | 500   | 13    | 0.57   |
| Samsung   | HN-M320MBB         | 320 GB | 3       | 401   | 3     | 0.57   |
| WDC       | WD5000AAKX-00U6AA0 | 500 GB | 9       | 308   | 3     | 0.57   |
| WDC       | WD20PURX-64P6ZY0   | 2 TB   | 4       | 206   | 0     | 0.56   |
| WDC       | WD800JD-00LSA5     | 80 GB  | 1       | 205   | 0     | 0.56   |
| WDC       | WD10EZEX-00UD2A0   | 1 TB   | 7       | 335   | 125   | 0.56   |
| WDC       | WD10EURS-630AB1    | 1 TB   | 1       | 1846  | 8     | 0.56   |
| WDC       | WD1200JB-00GVC0    | 120 GB | 3       | 539   | 4     | 0.56   |
| Hitachi   | HTS723232L9SA60    | 320 GB | 2       | 292   | 4     | 0.56   |
| WDC       | WD5003AZEX-00MK2A0 | 500 GB | 7       | 256   | 1     | 0.56   |
| WDC       | WD20EFRX-68EUZN0   | 2 TB   | 14      | 212   | 1     | 0.55   |
| Samsung   | HM501II            | 500 GB | 2       | 265   | 2     | 0.55   |
| Seagate   | ST360014A          | 60 GB  | 2       | 757   | 21    | 0.55   |
| WDC       | WD5000AAKS-08V0A0  | 500 GB | 5       | 411   | 7     | 0.55   |
| WDC       | WD1600AAJS-60Z0A0  | 160 GB | 2       | 199   | 0     | 0.55   |
| Seagate   | ST980813ASG        | 80 GB  | 2       | 436   | 6     | 0.55   |
| Samsung   | HD161HJ            | 160 GB | 26      | 942   | 550   | 0.55   |
| WDC       | WD5000BEVT-22A0RT0 | 500 GB | 25      | 528   | 25    | 0.54   |
| Seagate   | ST1000VX001-1HH162 | 1 TB   | 2       | 198   | 0     | 0.54   |
| Seagate   | ST1000LM024 HN-... | 1 TB   | 290     | 263   | 55    | 0.54   |
| Toshiba   | HDWN180            | 8 TB   | 1       | 198   | 0     | 0.54   |
| WDC       | WD30PURX-64P6ZY0   | 3 TB   | 2       | 197   | 0     | 0.54   |
| WDC       | WD15EARS-00Z5B1    | 1.5 TB | 19      | 920   | 630   | 0.54   |
| WDC       | WD10EADS-11M2B2    | 1 TB   | 1       | 1778  | 8     | 0.54   |
| WDC       | WD2500AAJS-00L7A0  | 250 GB | 16      | 506   | 15    | 0.54   |
| Seagate   | ST500LM012 HN-M... | 500 GB | 116     | 283   | 47    | 0.54   |
| WDC       | WD6400BPVT-60HXZT1 | 640 GB | 2       | 408   | 42    | 0.54   |
| Maxtor    | 6V250F0            | 250 GB | 2       | 196   | 0     | 0.54   |
| WDC       | WD400BD-75MRA1     | 40 GB  | 1       | 196   | 0     | 0.54   |
| WDC       | WD30EZRX-00D8PB0   | 3 TB   | 7       | 298   | 2     | 0.54   |
| HGST      | HTS541075A9E680    | 750 GB | 18      | 248   | 398   | 0.54   |
| Quantum   | FIREBALLlct15 30   | 30 GB  | 1       | 391   | 1     | 0.54   |
| Hitachi   | HDS721612PLAT80    | 123 GB | 1       | 1366  | 6     | 0.53   |
| Toshiba   | MK2555GSXF         | 250 GB | 3       | 194   | 0     | 0.53   |
| Hitachi   | HTS547564A9E384    | 640 GB | 23      | 486   | 511   | 0.53   |
| Seagate   | ST94011A           | 40 GB  | 1       | 194   | 0     | 0.53   |
| Seagate   | ST320414A          | 20 GB  | 1       | 194   | 0     | 0.53   |
| Hitachi   | HTS727575A9E364    | 750 GB | 9       | 219   | 121   | 0.53   |
| HGST      | HTS545032A7E680    | 320 GB | 8       | 224   | 2     | 0.53   |
| WDC       | WD400BB-00DKA0     | 40 GB  | 1       | 193   | 0     | 0.53   |
| Seagate   | ST3750640AS        | 750 GB | 7       | 910   | 399   | 0.53   |
| Samsung   | SP0822N            | 80 GB  | 4       | 194   | 1     | 0.53   |
| WDC       | WD10PURX-64D85Y0   | 1 TB   | 4       | 388   | 2     | 0.53   |
| WDC       | WD1600AABS-62PRA0  | 160 GB | 1       | 190   | 0     | 0.52   |
| WDC       | WD4001FAEX-00MJRA0 | 4 TB   | 1       | 190   | 0     | 0.52   |
| Toshiba   | MQ02ABD100H        | 1 TB   | 3       | 190   | 0     | 0.52   |
| Seagate   | ST380211AS         | 80 GB  | 5       | 721   | 462   | 0.52   |
| WDC       | WD800JD-75JNA0     | 80 GB  | 2       | 1563  | 59    | 0.52   |
| WDC       | WD5000LPVT-00G33T0 | 500 GB | 4       | 386   | 3     | 0.52   |
| WDC       | WD800BEVS-00RST0   | 80 GB  | 3       | 257   | 1     | 0.52   |
| WDC       | WD5000AZRX-00L4HB0 | 500 GB | 10      | 188   | 0     | 0.52   |
| WDC       | WD5000AZRZ-00HTKB0 | 500 GB | 5       | 188   | 0     | 0.52   |
| Seagate   | ST96812A           | 60 GB  | 3       | 375   | 758   | 0.52   |
| WDC       | WD2500BEVT-80A23T0 | 250 GB | 15      | 341   | 46    | 0.51   |
| WDC       | WD2500BJKT-00F4T0  | 250 GB | 2       | 187   | 0     | 0.51   |
| WDC       | WD10JPVX-22JC3T0   | 1 TB   | 67      | 197   | 15    | 0.51   |
| WDC       | WD7500BPKT-00PK4T0 | 750 GB | 1       | 187   | 0     | 0.51   |
| WDC       | WD1003FBYX-01Y7B1  | 1 TB   | 16      | 318   | 3     | 0.51   |
| Hitachi   | HDS721050DLE630    | 500 GB | 27      | 460   | 361   | 0.51   |
| Seagate   | ST9500420AS        | 500 GB | 45      | 526   | 415   | 0.51   |
| WDC       | WD800BEVS-75RST0   | 80 GB  | 3       | 436   | 336   | 0.51   |
| Hitachi   | HDT721064SLA360    | 640 GB | 2       | 1020  | 5     | 0.51   |
| Seagate   | ST3160812AS 41N... | 160 GB | 1       | 927   | 4     | 0.51   |
| WDC       | WD6400AADS-00M2B0  | 640 GB | 8       | 795   | 8     | 0.51   |
| Hitachi   | HTS543232L9A300    | 320 GB | 12      | 543   | 553   | 0.51   |
| WDC       | WD5000BEVT-80A0RT0 | 500 GB | 1       | 1662  | 8     | 0.51   |
| WDC       | WD7500BPVX-60JC3T0 | 750 GB | 3       | 247   | 2     | 0.50   |
| Quantum   | FIREBALLlct15 15   | 15 GB  | 1       | 183   | 0     | 0.50   |
| WDC       | WD3200AZRX-00A8LB0 | 320 GB | 2       | 183   | 0     | 0.50   |
| HGST      | HUS726040ALE611    | 4 TB   | 1       | 182   | 0     | 0.50   |
| Seagate   | ST31000523AS       | 1 TB   | 2       | 2094  | 11    | 0.50   |
| Seagate   | ST750LX003-1AC154  | 750 GB | 8       | 257   | 132   | 0.50   |
| Hitachi   | HDT722525DLAT80    | 250 GB | 2       | 733   | 3     | 0.50   |
| WDC       | WD1600AAJS-22WAA0  | 160 GB | 1       | 910   | 4     | 0.50   |
| Seagate   | ST9160827AS        | 160 GB | 25      | 477   | 375   | 0.50   |
| WDC       | WD10EARX-00PASB0   | 1 TB   | 1       | 1636  | 8     | 0.50   |
| Samsung   | HM321HX            | 320 GB | 2       | 263   | 4     | 0.50   |
| Toshiba   | MG03ACA300         | 3 TB   | 2       | 322   | 5     | 0.50   |
| WDC       | WD5000AAKS-22YGA0  | 500 GB | 2       | 527   | 228   | 0.50   |
| Hitachi   | IC25N030ATMR04-0   | 30 GB  | 1       | 544   | 2     | 0.50   |
| Hitachi   | HTS541060G9AT00    | 60 GB  | 5       | 479   | 5     | 0.50   |
| HGST      | HTS721010A9E630    | 1 TB   | 84      | 197   | 15    | 0.50   |
| Samsung   | HM250JI            | 250 GB | 3       | 515   | 11    | 0.50   |
| WDC       | WD7500BPKT-60PK4T0 | 750 GB | 2       | 343   | 4     | 0.49   |
| HGST      | HUS724040ALA640    | 4 TB   | 1       | 180   | 0     | 0.49   |
| Seagate   | ST3000VN000-1H4167 | 3 TB   | 1       | 179   | 0     | 0.49   |
| WDC       | WD1600BEVT-22A23T0 | 160 GB | 16      | 251   | 5     | 0.49   |
| Toshiba   | MK8009GAH          | 80 GB  | 2       | 360   | 43    | 0.49   |
| Samsung   | HE753LJ            | 750 GB | 2       | 374   | 51    | 0.49   |
| Samsung   | SP0812C            | 80 GB  | 12      | 510   | 175   | 0.49   |
| Seagate   | ST9120821A         | 120 GB | 3       | 490   | 26    | 0.49   |
| WDC       | WD5000BPKT-75PK4T0 | 500 GB | 5       | 302   | 4     | 0.49   |
| WDC       | WD5000BPKX-75HPJT0 | 500 GB | 1       | 178   | 0     | 0.49   |
| WDC       | WD10JPVX-08JC3T2   | 1 TB   | 4       | 197   | 1     | 0.49   |
| Seagate   | ST9500423AS        | 500 GB | 16      | 233   | 8     | 0.49   |
| WDC       | WD10JUCT-63J6SY0   | 1 TB   | 3       | 176   | 0     | 0.48   |
| Seagate   | ST3120811AS        | 120 GB | 10      | 520   | 194   | 0.48   |
| Seagate   | ST3300822AS        | 300 GB | 1       | 176   | 0     | 0.48   |
| Seagate   | ST9500420ASG       | 500 GB | 1       | 351   | 1     | 0.48   |
| WDC       | WD60EFRX-68MYMN1   | 6 TB   | 5       | 294   | 3     | 0.48   |
| Samsung   | HM080HC            | 72 GB  | 1       | 526   | 2     | 0.48   |
| Samsung   | HD082GJ            | 80 GB  | 10      | 467   | 341   | 0.48   |
| WDC       | WD2005FBYZ-01YCBB2 | 2 TB   | 2       | 175   | 0     | 0.48   |
| WDC       | WD1003FBYX-01Y7B0  | 1 TB   | 3       | 973   | 5     | 0.48   |
| WDC       | WD3200BPVT-75ZEST0 | 320 GB | 3       | 275   | 3     | 0.48   |
| WDC       | WD1600BEVT-35ZCT0  | 160 GB | 2       | 173   | 0     | 0.48   |
| WDC       | WD3200BEVT-26ZCT0  | 320 GB | 2       | 243   | 1     | 0.48   |
| WDC       | WD3200BEVT-24A23T0 | 320 GB | 8       | 515   | 127   | 0.47   |
| WDC       | WD3200AAJB-00J3A0  | 320 GB | 13      | 339   | 5     | 0.47   |
| WDC       | WD3200AAKS-22L6A0  | 320 GB | 3       | 378   | 5     | 0.47   |
| WDC       | WD5000LPVX-22V0TT0 | 500 GB | 105     | 203   | 3     | 0.47   |
| Seagate   | ST250LT003-9YG14C  | 250 GB | 2       | 170   | 0     | 0.47   |
| Toshiba   | MK1234GSX          | 120 GB | 6       | 517   | 5     | 0.47   |
| Hitachi   | HCS5C1010DLE630    | 1 TB   | 1       | 169   | 0     | 0.47   |
| Toshiba   | MK8046GSX          | 80 GB  | 2       | 299   | 2     | 0.47   |
| WDC       | WD3200BJKT-00F4T0  | 320 GB | 1       | 169   | 0     | 0.46   |
| Samsung   | HM250HJ            | 250 GB | 2       | 337   | 17    | 0.46   |
| Hitachi   | HTS545050A7E380    | 500 GB | 64      | 280   | 119   | 0.46   |
| Seagate   | ST1000DM000-9TS15E | 1 TB   | 1       | 168   | 0     | 0.46   |
| WDC       | WD10S21X-24R1BT... | 1 TB   | 5       | 168   | 0     | 0.46   |
| Seagate   | ST9500325ASG       | 500 GB | 2       | 432   | 58    | 0.46   |
| WDC       | WD1200BEVS-75RST0  | 120 GB | 2       | 167   | 0     | 0.46   |
| Toshiba   | DT01ACA050         | 500 GB | 171     | 187   | 28    | 0.46   |
| WDC       | WD7501AALS-00E8B0  | 750 GB | 1       | 1502  | 8     | 0.46   |
| Hitachi   | HDS722512VLAT20    | 123 GB | 1       | 834   | 4     | 0.46   |
| WDC       | WD5000MPCK-60AWHT0 | 500 GB | 1       | 166   | 0     | 0.46   |
| Seagate   | ST3250820NS        | 250 GB | 2       | 695   | 1050  | 0.46   |
| WDC       | WD7500BPVT-08HXZT3 | 750 GB | 2       | 165   | 0     | 0.45   |
| Hitachi   | HTS541616J9SA00    | 160 GB | 23      | 469   | 91    | 0.45   |
| WDC       | WD10SPCX-22HWST0   | 1 TB   | 1       | 165   | 0     | 0.45   |
| Maxtor    | 6G160E0            | 160 GB | 7       | 342   | 129   | 0.45   |
| Hitachi   | HDS721616PLAT80    | 164 GB | 2       | 1722  | 62    | 0.45   |
| WDC       | WD3200AVVS-56L2B0  | 320 GB | 5       | 457   | 78    | 0.45   |
| WDC       | WD10EZRX-00D8PB0   | 1 TB   | 6       | 164   | 0     | 0.45   |
| Hitachi   | HTS543232A7A384    | 320 GB | 117     | 277   | 291   | 0.45   |
| WDC       | WD5000LPVT-24G33T1 | 500 GB | 13      | 224   | 1     | 0.45   |
| WDC       | WD2500BPVT-22ZEST0 | 250 GB | 12      | 212   | 5     | 0.45   |
| WDC       | WD5000LPCX-22VHAT0 | 500 GB | 8       | 162   | 0     | 0.45   |
| WDC       | WD5000AAVS-00G9B0  | 500 GB | 1       | 1464  | 8     | 0.45   |
| Seagate   | ST320DM001 HD322GJ | 320 GB | 3       | 163   | 2     | 0.45   |
| WDC       | WD3200AAKX-00ERMA0 | 320 GB | 7       | 203   | 3     | 0.44   |
| WDC       | WD1600BEVS-22VAT0  | 160 GB | 1       | 324   | 1     | 0.44   |
| Seagate   | ST920217AS         | 20 GB  | 1       | 162   | 0     | 0.44   |
| WDC       | WD2000FYYZ-01UL1B1 | 2 TB   | 5       | 256   | 382   | 0.44   |
| WDC       | WD10SPCX-80HWST0   | 1 TB   | 1       | 160   | 0     | 0.44   |
| Toshiba   | MK3265GSXN         | 320 GB | 12      | 427   | 298   | 0.44   |
| Toshiba   | MQ01ABC150         | 1.5 TB | 1       | 160   | 0     | 0.44   |
| WDC       | WD6400BEVT-22A0RT0 | 640 GB | 6       | 467   | 6     | 0.44   |
| WDC       | WD5000AADS-56S9B1  | 500 GB | 2       | 411   | 4     | 0.44   |
| Seagate   | ST500DM002-9YN14C  | 500 GB | 2       | 391   | 503   | 0.44   |
| WDC       | WD5000LPVX-28V0TT0 | 500 GB | 1       | 159   | 0     | 0.44   |
| WDC       | WD400BB-23FJA0     | 40 GB  | 1       | 796   | 4     | 0.44   |
| WDC       | WD3200AVJS-63B6A0  | 320 GB | 3       | 1557  | 34    | 0.43   |
| Seagate   | ST910021AS         | 100 GB | 3       | 682   | 53    | 0.43   |
| Toshiba   | MK5059GSXP         | 500 GB | 20      | 339   | 314   | 0.43   |
| Hitachi   | HTS541075A9E680    | 750 GB | 4       | 325   | 764   | 0.43   |
| WDC       | WD7500BPKX-75HPJT0 | 750 GB | 1       | 157   | 0     | 0.43   |
| Seagate   | ST2000DM001-1ER164 | 2 TB   | 22      | 156   | 0     | 0.43   |
| Toshiba   | MK3276GSXN         | 320 GB | 1       | 156   | 0     | 0.43   |
| WDC       | WD3200BPVT-80ZEST0 | 320 GB | 19      | 344   | 12    | 0.43   |
| WDC       | WD5000BPVT-60HXZT3 | 500 GB | 6       | 480   | 31    | 0.43   |
| Seagate   | ST98823AS          | 80 GB  | 5       | 365   | 830   | 0.43   |
| HGST      | HTS541010A9E680    | 1 TB   | 93      | 242   | 231   | 0.43   |
| WDC       | WD5000AAKX-75U6AA0 | 500 GB | 4       | 169   | 3     | 0.43   |
| Seagate   | STM9120817AS       | 120 GB | 1       | 155   | 0     | 0.43   |
| Hitachi   | HDP725032GLA380    | 320 GB | 5       | 880   | 41    | 0.43   |
| WDC       | WD1600BEVT-80A23T0 | 160 GB | 16      | 204   | 3     | 0.43   |
| Seagate   | ST1000DX001-1CM162 | 1 TB   | 16      | 281   | 86    | 0.43   |
| WDC       | WD10JPVX-75JC3T0   | 1 TB   | 20      | 195   | 3     | 0.43   |
| Fujitsu   | MHZ2250BH G2       | 250 GB | 9       | 507   | 577   | 0.42   |
| WDC       | WD10JPVT-75A1YT0   | 1 TB   | 4       | 446   | 4     | 0.42   |
| Seagate   | ST2000DX001-1CM164 | 2 TB   | 12      | 259   | 301   | 0.42   |
| HGST      | HTS721075A9E630    | 750 GB | 5       | 153   | 0     | 0.42   |
| WDC       | WD10EZEX-07M2NA0   | 1 TB   | 1       | 152   | 0     | 0.42   |
| Toshiba   | MK1237GSX          | 120 GB | 7       | 391   | 32    | 0.42   |
| HGST      | HTS545032A7E380    | 320 GB | 13      | 162   | 1     | 0.42   |
| WDC       | WD400JB-00FMA0     | 40 GB  | 1       | 152   | 0     | 0.42   |
| Toshiba   | HDWE140            | 4 TB   | 6       | 152   | 0     | 0.42   |
| WDC       | WD800JD-22LSA1     | 80 GB  | 3       | 627   | 232   | 0.42   |
| WDC       | WD1600AVVS-63L2B0  | 160 GB | 2       | 151   | 0     | 0.41   |
| Seagate   | ST500LM000-1EJ1... | 500 GB | 2       | 150   | 0     | 0.41   |
| WDC       | WD7500BPVT-55HXZT4 | 750 GB | 1       | 150   | 0     | 0.41   |
| Hitachi   | HUA723020ALA641    | 2 TB   | 2       | 150   | 0     | 0.41   |
| WDC       | WD5000BPVT-80HXZT1 | 500 GB | 5       | 640   | 67    | 0.41   |
| Seagate   | ST9320325AS        | 320 GB | 145     | 432   | 381   | 0.41   |
| Samsung   | SP1634N            | 160 GB | 1       | 298   | 1     | 0.41   |
| WDC       | WD5001AALS-00LWTA0 | 500 GB | 3       | 495   | 80    | 0.41   |
| Toshiba   | MK7575GSX          | 750 GB | 14      | 505   | 670   | 0.41   |
| Seagate   | ST1500DM003-9YN16G | 1.5 TB | 14      | 450   | 446   | 0.41   |
| Seagate   | ST3160815SV        | 160 GB | 5       | 681   | 1240  | 0.41   |
| Fujitsu   | MHW2020BH          | 20 GB  | 1       | 148   | 0     | 0.41   |
| WDC       | WD800BB-75JHC0     | 80 GB  | 1       | 148   | 0     | 0.41   |
| WDC       | WD1600BEVT-75A23T0 | 160 GB | 3       | 244   | 1     | 0.41   |
| WDC       | WD1200JS-22NCB1    | 120 GB | 1       | 1184  | 7     | 0.41   |
| WDC       | WD2500BEVT-08A23T1 | 250 GB | 10      | 214   | 144   | 0.41   |
| WDC       | WD5000BEVT-60ZAT1  | 500 GB | 4       | 344   | 15    | 0.40   |
| WDC       | WD5000AAKX-08U6AA0 | 500 GB | 25      | 160   | 1     | 0.40   |
| Hitachi   | HDS722525VLSA80    | 250 GB | 2       | 370   | 17    | 0.40   |
| WDC       | WD2500BEVT-00A0RT1 | 245 GB | 1       | 146   | 0     | 0.40   |
| Hitachi   | HTS541680J9SA00    | 80 GB  | 35      | 472   | 42    | 0.40   |
| WDC       | WD3000FYYZ-01UL1B0 | 3 TB   | 1       | 145   | 0     | 0.40   |
| Samsung   | SP0842N            | 80 GB  | 8       | 625   | 592   | 0.40   |
| Hitachi   | HTS542512K9SA00    | 120 GB | 40      | 459   | 112   | 0.40   |
| WDC       | WD3200BPVT-60JJ5T0 | 320 GB | 7       | 400   | 25    | 0.40   |
| Fujitsu   | MHV2060BHPL        | 60 GB  | 1       | 144   | 0     | 0.40   |
| Seagate   | ST1000VM002-1SD102 | 1 TB   | 1       | 144   | 0     | 0.40   |
| Seagate   | ST3750330NS        | 750 GB | 3       | 560   | 337   | 0.39   |
| Seagate   | ST9250827AS        | 250 GB | 14      | 379   | 308   | 0.39   |
| WDC       | WD3200AAJS-55VWA0  | 320 GB | 1       | 1006  | 6     | 0.39   |
| Hitachi   | HTS545025B9SA02    | 250 GB | 4       | 184   | 507   | 0.39   |
| Seagate   | ST3000NM0033-9Z... | 3 TB   | 2       | 577   | 9     | 0.39   |
| Hitachi   | HTS543216L9A300    | 160 GB | 28      | 469   | 128   | 0.39   |
| Toshiba   | MQ01ABD100         | 1 TB   | 100     | 188   | 55    | 0.39   |
| WDC       | WD2500BEVT-60ZCT1  | 250 GB | 2       | 142   | 0     | 0.39   |
| Toshiba   | MK2555GSX          | 250 GB | 18      | 391   | 119   | 0.39   |
| WDC       | WD5000LPCX-24C6HT0 | 500 GB | 30      | 167   | 1     | 0.39   |
| Toshiba   | MQ01ABF032         | 320 GB | 15      | 140   | 0     | 0.39   |
| WDC       | WD2500AAJB-57WGA0  | 250 GB | 1       | 140   | 0     | 0.38   |
| IBM       | DTLA-305020        | 20 GB  | 2       | 1484  | 37    | 0.38   |
| WDC       | WD5000AAKB-00H8A0  | 500 GB | 12      | 510   | 9     | 0.38   |
| Hitachi   | HTS541212H9AT00    | 120 GB | 3       | 378   | 5     | 0.38   |
| WDC       | WD400EB-11CPF0     | 40 GB  | 2       | 1019  | 31    | 0.38   |
| WDC       | WD800BB-00HEA0     | 80 GB  | 1       | 836   | 5     | 0.38   |
| Toshiba   | MK6475GSX          | 640 GB | 16      | 314   | 420   | 0.38   |
| Seagate   | ST9250315AS        | 250 GB | 123     | 433   | 420   | 0.38   |
| Seagate   | ST320LT022-1AE142  | 320 GB | 1       | 138   | 0     | 0.38   |
| Seagate   | ST3250312CS        | 250 GB | 8       | 291   | 189   | 0.38   |
| HGST      | HTS545050A7E380    | 500 GB | 90      | 270   | 241   | 0.38   |
| Samsung   | SP2004C            | 200 GB | 23      | 697   | 505   | 0.38   |
| WDC       | WD2500BEVS-60UST0  | 250 GB | 6       | 425   | 338   | 0.38   |
| Toshiba   | MQ01ABD050         | 500 GB | 65      | 293   | 328   | 0.38   |
| Hitachi   | HTS723232A7A364    | 320 GB | 18      | 255   | 455   | 0.38   |
| Seagate   | ST9640320AS        | 640 GB | 6       | 400   | 340   | 0.38   |
| Seagate   | ST3500312CS        | 500 GB | 7       | 816   | 484   | 0.38   |
| WDC       | WD2500BPVT-24JJ5T0 | 250 GB | 1       | 136   | 0     | 0.37   |
| Samsung   | SP1654N            | 160 GB | 3       | 615   | 414   | 0.37   |
| WDC       | WD60EFRX-68L0BN1   | 6 TB   | 3       | 174   | 6     | 0.37   |
| WDC       | WD2500AAKX-603CA0  | 250 GB | 3       | 138   | 401   | 0.37   |
| Hitachi   | HCT721050SLA380    | 500 GB | 1       | 136   | 0     | 0.37   |
| WDC       | WD7500BPKX-22HPJT0 | 750 GB | 6       | 170   | 2     | 0.37   |
| Hitachi   | HTS725032A9A364    | 320 GB | 10      | 410   | 848   | 0.37   |
| WDC       | WD800JD-00JNA0     | 80 GB  | 2       | 809   | 5     | 0.37   |
| WDC       | WD3201ABYS-01B9A0  | 320 GB | 2       | 926   | 278   | 0.37   |
| WDC       | WD3200AAKX-073CA1  | 320 GB | 2       | 342   | 4     | 0.37   |
| WDC       | WD6400BPVT-75HXZT1 | 640 GB | 2       | 385   | 3     | 0.37   |
| Seagate   | ST9750423AS        | 750 GB | 8       | 317   | 253   | 0.37   |
| Fujitsu   | MHW2160BH          | 160 GB | 1       | 134   | 0     | 0.37   |
| WDC       | WD5000LPVX-55V0TT0 | 500 GB | 9       | 133   | 0     | 0.37   |
| HGST      | HTS725050A7E630    | 500 GB | 76      | 173   | 83    | 0.37   |
| Seagate   | ST3200822A         | 200 GB | 3       | 1660  | 14    | 0.36   |
| Toshiba   | MK1655GSX          | 160 GB | 10      | 266   | 36    | 0.36   |
| WDC       | WD5000AAKX-22ERMA0 | 500 GB | 21      | 258   | 3     | 0.36   |
| IBM/Hi... | IC35L040AVER07-0   | 41 GB  | 2       | 1050  | 7     | 0.36   |
| Samsung   | HD403LJ            | 400 GB | 10      | 1202  | 722   | 0.36   |
| WDC       | WD10EARX-00NYB0    | 1 TB   | 1       | 130   | 0     | 0.36   |
| Toshiba   | MG03ACA100         | 1 TB   | 7       | 157   | 1     | 0.36   |
| Maxtor    | STM3160215A        | 160 GB | 6       | 209   | 512   | 0.36   |
| WDC       | WD7500KMVV-11TK7S1 | 750 GB | 1       | 129   | 0     | 0.36   |
| Seagate   | ST9120822A         | 120 GB | 2       | 273   | 53    | 0.36   |
| Toshiba   | MQ01ACF050         | 500 GB | 6       | 157   | 173   | 0.36   |
| Toshiba   | MK2546GSX          | 250 GB | 10      | 528   | 38    | 0.35   |
| Samsung   | HD752LJ            | 750 GB | 1       | 516   | 3     | 0.35   |
| Seagate   | ST3120813AS        | 120 GB | 14      | 827   | 819   | 0.35   |
| Hitachi   | HTS542525K9SA00    | 250 GB | 24      | 535   | 52    | 0.35   |
| WDC       | WD10EADS-98M2B0    | 1 TB   | 1       | 899   | 6     | 0.35   |
| WDC       | WD5000AZLX-00CL5A0 | 500 GB | 2       | 128   | 0     | 0.35   |
| WDC       | WD3200BPVT-16JJ5T0 | 320 GB | 2       | 231   | 1     | 0.35   |
| WDC       | WD3200AAJS-65M0A0  | 320 GB | 1       | 1152  | 8     | 0.35   |
| Samsung   | HM500JJ            | 500 GB | 2       | 331   | 5     | 0.35   |
| WDC       | WD5000BPKT-22PK4T0 | 500 GB | 1       | 127   | 0     | 0.35   |
| Toshiba   | MK1034GSX          | 100 GB | 4       | 418   | 464   | 0.35   |
| Toshiba   | MK3252GSX          | 320 GB | 15      | 564   | 262   | 0.35   |
| Seagate   | ST3500830SCE       | 500 GB | 1       | 126   | 0     | 0.35   |
| Seagate   | ST9120821AS        | 120 GB | 5       | 274   | 1101  | 0.35   |
| WDC       | WD400BB-60DGA0     | 40 GB  | 1       | 504   | 3     | 0.35   |
| Seagate   | ST3500410AS        | 500 GB | 19      | 1016  | 324   | 0.35   |
| WDC       | WD10JPVX-00JC3T0   | 1 TB   | 23      | 128   | 1     | 0.34   |
| Toshiba   | MK1216GSG          | 120 GB | 3       | 272   | 4     | 0.34   |
| WDC       | WD3200AAJS-56M0A0  | 320 GB | 5       | 408   | 3     | 0.34   |
| Samsung   | HD252KJ            | 250 GB | 5       | 551   | 406   | 0.34   |
| Toshiba   | DT01ABA200         | 2 TB   | 1       | 124   | 0     | 0.34   |
| WDC       | WD20EARS-00J2GB0   | 2 TB   | 1       | 1120  | 8     | 0.34   |
| WDC       | WD3200AAKS-00C9A0  | 320 GB | 3       | 1080  | 8     | 0.34   |
| Toshiba   | MK5076GSX -63      | 500 GB | 2       | 123   | 0     | 0.34   |
| WDC       | WD5000AAKS-60Z1A0  | 500 GB | 2       | 371   | 2     | 0.34   |
| HGST      | HTE725050A7E630    | 500 GB | 1       | 122   | 0     | 0.34   |
| Toshiba   | MK7559GSXP         | 750 GB | 11      | 418   | 441   | 0.34   |
| Seagate   | ST1000NM0011       | 1 TB   | 4       | 506   | 68    | 0.34   |
| WDC       | WD5000AAKS-55V0A0  | 500 GB | 5       | 427   | 6     | 0.33   |
| Seagate   | ST9100827AS        | 100 GB | 1       | 838   | 6     | 0.33   |
| Seagate   | ST960821A          | 60 GB  | 1       | 358   | 2     | 0.33   |
| WDC       | WD5000AAKX-221CA1  | 500 GB | 8       | 430   | 35    | 0.33   |
| Toshiba   | MK6025GAS          | 60 GB  | 2       | 166   | 9     | 0.33   |
| WDC       | WD2500BPVT-75JJ5T0 | 250 GB | 2       | 117   | 0     | 0.32   |
| WDC       | WD5000AZLX-00K2TA0 | 500 GB | 4       | 117   | 0     | 0.32   |
| WDC       | WD10EZEX-21WN4A0   | 1 TB   | 5       | 117   | 0     | 0.32   |
| Toshiba   | MK1633GSG          | 160 GB | 2       | 116   | 0     | 0.32   |
| Hitachi   | HTS727550A9E364    | 500 GB | 7       | 324   | 440   | 0.32   |
| WDC       | ZALMAN             | 500 GB | 1       | 1047  | 8     | 0.32   |
| Hitachi   | HTS543216L9SA00    | 160 GB | 8       | 291   | 12    | 0.32   |
| Seagate   | ST640LM001 HN-M... | 640 GB | 1       | 116   | 0     | 0.32   |
| WDC       | WD5000LPCX-00VHAT0 | 500 GB | 9       | 115   | 0     | 0.32   |
| Seagate   | ST9160823AS        | 160 GB | 4       | 924   | 638   | 0.32   |
| Seagate   | ST320LT012-1DG14C  | 320 GB | 11      | 238   | 96    | 0.32   |
| WDC       | WD3200LPCX-24C6HT0 | 320 GB | 16      | 115   | 0     | 0.32   |
| WDC       | WD3200BEKX-00B7WT0 | 320 GB | 5       | 119   | 3     | 0.31   |
| Samsung   | SP2504C            | 250 GB | 21      | 993   | 828   | 0.31   |
| WDC       | WD5000AAKS-00M9A0  | 500 GB | 4       | 580   | 569   | 0.31   |
| Hitachi   | HTS725050A9A364    | 500 GB | 12      | 347   | 694   | 0.31   |
| WDC       | WD5000AVCS-632DY1  | 500 GB | 1       | 114   | 0     | 0.31   |
| Toshiba   | MK2565GSX          | 250 GB | 15      | 250   | 223   | 0.31   |
| WDC       | WD3200AVJS-63N9A0  | 320 GB | 1       | 114   | 0     | 0.31   |
| Toshiba   | MK1059GSMP         | 1 TB   | 11      | 468   | 334   | 0.31   |
| WDC       | WD3200LPVX-22V0TT0 | 320 GB | 10      | 148   | 2     | 0.31   |
| Seagate   | ST9500325AS        | 500 GB | 228     | 438   | 599   | 0.31   |
| WDC       | WD1002F9YZ-09H1JL1 | 1 TB   | 1       | 112   | 0     | 0.31   |
| WDC       | WD2500BEVT-75A23T0 | 250 GB | 4       | 498   | 14    | 0.31   |
| Samsung   | HD200HJ            | 200 GB | 11      | 872   | 757   | 0.31   |
| WDC       | WD3200BEVT-08A23T1 | 320 GB | 2       | 234   | 4     | 0.31   |
| WDC       | WD3200AAKS-00YGA0  | 320 GB | 1       | 562   | 4     | 0.31   |
| WDC       | WD4003FZEX-00Z4SA0 | 4 TB   | 1       | 112   | 0     | 0.31   |
| WDC       | WD5000AAKX-003CA0  | 500 GB | 10      | 463   | 54    | 0.31   |
| Seagate   | ST9100823A         | 95 GB  | 1       | 1007  | 8     | 0.31   |
| WDC       | WD1001FAES-55W7A0  | 1 TB   | 1       | 111   | 0     | 0.31   |
| Toshiba   | MK6465GSX          | 640 GB | 15      | 638   | 425   | 0.31   |
| Fujitsu   | MHV2060BH          | 60 GB  | 3       | 498   | 20    | 0.30   |
| Fujitsu   | MPE3064AT          | 6 GB   | 1       | 111   | 0     | 0.30   |
| WDC       | WD400EB-00CPF0     | 40 GB  | 2       | 534   | 11    | 0.30   |
| Seagate   | ST320LT020-9YG142  | 320 GB | 87      | 297   | 497   | 0.30   |
| WDC       | WD10EZEX-75M2NA0   | 1 TB   | 6       | 109   | 0     | 0.30   |
| Apple     | HDD ST1000DM003    | 1 TB   | 1       | 109   | 0     | 0.30   |
| Seagate   | ST9320310AS        | 320 GB | 3       | 281   | 338   | 0.30   |
| WDC       | WD20EADS-32S2B0    | 2 TB   | 1       | 1198  | 10    | 0.30   |
| Seagate   | ST980811AS         | 80 GB  | 14      | 428   | 342   | 0.30   |
| Hitachi   | HTS541612J9SA00    | 120 GB | 42      | 521   | 32    | 0.29   |
| WDC       | WD2500BEVT-00ZCT0  | 250 GB | 6       | 107   | 0     | 0.29   |
| WDC       | WD2503ABYX-01WERA1 | 251 GB | 2       | 107   | 0     | 0.29   |
| Seagate   | ST1000DM003-1SB10C | 1 TB   | 31      | 107   | 0     | 0.29   |
| WDC       | WD3200AAJS-60M0A1  | 320 GB | 3       | 596   | 1255  | 0.29   |
| Fujitsu   | MHW2040BH          | 40 GB  | 1       | 214   | 1     | 0.29   |
| Fujitsu   | MHV2100BH PL       | 100 GB | 3       | 291   | 4     | 0.29   |
| Hitachi   | HTS542520K9SA00    | 200 GB | 4       | 658   | 11    | 0.29   |
| China     | TP00250GB          | 250 GB | 1       | 106   | 0     | 0.29   |
| WDC       | WD5000LPLX-75ZNTT0 | 500 GB | 1       | 106   | 0     | 0.29   |
| Seagate   | ST320LM010-1KJ15C  | 320 GB | 2       | 105   | 0     | 0.29   |
| WDC       | WD1500HLFS-01G6U0  | 150 GB | 1       | 211   | 1     | 0.29   |
| Seagate   | ST500LM000-SSHD... | 500 GB | 14      | 158   | 91    | 0.29   |
| WDC       | WD6400BPVT-80HXZT1 | 640 GB | 4       | 422   | 6     | 0.29   |
| WDC       | WD5000AAKS-60WWPA0 | 500 GB | 4       | 550   | 582   | 0.29   |
| WDC       | WD5000AAKX-19U6AA0 | 500 GB | 1       | 103   | 0     | 0.28   |
| WDC       | WD2500AAKX-221CA1  | 250 GB | 1       | 931   | 8     | 0.28   |
| Hitachi   | HTS542580K9SA00    | 80 GB  | 6       | 336   | 6     | 0.28   |
| WDC       | WD10JPVX-35JC3T0   | 1 TB   | 1       | 103   | 0     | 0.28   |
| WDC       | WD5000LPVX-00V0TT0 | 500 GB | 14      | 154   | 54    | 0.28   |
| Toshiba   | MQ01ABF050         | 500 GB | 149     | 120   | 82    | 0.28   |
| Fujitsu   | MHT2040AH PL       | 40 GB  | 1       | 306   | 2     | 0.28   |
| Samsung   | SP1604N            | 160 GB | 3       | 394   | 62    | 0.28   |
| Hitachi   | HTS541040G9AT00    | 40 GB  | 2       | 206   | 3     | 0.28   |
| WDC       | WD5000BPKX-22HPJT0 | 500 GB | 7       | 119   | 1     | 0.28   |
| WDC       | WD5000BEVT-22ZAT0  | 500 GB | 4       | 311   | 2     | 0.28   |
| WDC       | WD5000BPVT-08HXZT1 | 500 GB | 1       | 100   | 0     | 0.28   |
| Toshiba   | MK3276GSX -63      | 320 GB | 5       | 146   | 1     | 0.28   |
| WDC       | WD5000HHTZ-04N21V1 | 500 GB | 1       | 100   | 0     | 0.27   |
| Seagate   | ST5000DM000-1FK178 | 5 TB   | 2       | 112   | 4     | 0.27   |
| WDC       | WD10SPCX-75HWST0   | 1 TB   | 1       | 100   | 0     | 0.27   |
| Seagate   | ST250LM004 HN-M... | 250 GB | 3       | 192   | 5     | 0.27   |
| Toshiba   | MK1637GSX          | 160 GB | 21      | 537   | 45    | 0.27   |
| Seagate   | ST3000DM001-9YN166 | 3 TB   | 11      | 475   | 1321  | 0.27   |
| Seagate   | ST340014AS         | 40 GB  | 2       | 1239  | 1016  | 0.27   |
| Toshiba   | MK3259GSXP         | 320 GB | 32      | 238   | 153   | 0.27   |
| Toshiba   | HDWD130            | 3 TB   | 3       | 97    | 0     | 0.27   |
| WDC       | WD7500BPVT-00HXZT3 | 750 GB | 7       | 496   | 16    | 0.27   |
| WDC       | WD3202ABYS-01B7A0  | 320 GB | 2       | 546   | 5     | 0.27   |
| WDC       | WD40EFRX-68WT0N0   | 4 TB   | 6       | 116   | 1     | 0.27   |
| Seagate   | ST380023A          | 80 GB  | 1       | 2900  | 29    | 0.26   |
| WDC       | WD5000LPVX-60V0TT0 | 500 GB | 7       | 195   | 25    | 0.26   |
| WDC       | WD5000BEKT-60KA9T0 | 500 GB | 1       | 383   | 3     | 0.26   |
| Samsung   | SP0401N            | 40 GB  | 1       | 95    | 0     | 0.26   |
| WDC       | WD3200AAKX-32ERMA0 | 320 GB | 1       | 95    | 0     | 0.26   |
| Seagate   | ST9120817AS        | 120 GB | 3       | 370   | 456   | 0.26   |
| Seagate   | ST4000DM005-2DP166 | 4 TB   | 2       | 94    | 0     | 0.26   |
| WDC       | WD1600AAJB-00J3A0  | 160 GB | 10      | 647   | 212   | 0.26   |
| Seagate   | ST1000UM000-1EK164 | 1 TB   | 1       | 94    | 0     | 0.26   |
| WDC       | WD1003FZEX-00K3CA0 | 1 TB   | 5       | 94    | 0     | 0.26   |
| WDC       | WD1600JS-22NCB1    | 160 GB | 2       | 478   | 5     | 0.26   |
| Toshiba   | MK1665GSX H        | 160 GB | 1       | 93    | 0     | 0.26   |
| Seagate   | ST4000VN000-1H4168 | 4 TB   | 3       | 93    | 0     | 0.26   |
| WDC       | WD10EZRZ-00Z5HB0   | 1 TB   | 4       | 93    | 0     | 0.26   |
| Toshiba   | MK8037GSX          | 80 GB  | 11      | 414   | 206   | 0.25   |
| WDC       | WD2500JS-19NCB1    | 250 GB | 1       | 92    | 0     | 0.25   |
| Seagate   | ST500LT012-1DG142  | 500 GB | 209     | 131   | 57    | 0.25   |
| Toshiba   | MK5065GSX          | 500 GB | 12      | 345   | 248   | 0.25   |
| WDC       | WD1600BPVT-22JJ5T0 | 160 GB | 1       | 91    | 0     | 0.25   |
| Seagate   | ST340810A          | 40 GB  | 7       | 490   | 43    | 0.25   |
| HP        | GB0250EAFJF        | 250 GB | 1       | 634   | 6     | 0.25   |
| Hitachi   | HTS541616J9AT00    | 160 GB | 2       | 356   | 7     | 0.25   |
| Samsung   | HS082HB            | 80 GB  | 1       | 89    | 0     | 0.25   |
| WDC       | WD5000AADS-00L4B1  | 500 GB | 4       | 283   | 7     | 0.24   |
| WDC       | WD10EZEX-35WN4A0   | 1 TB   | 3       | 88    | 0     | 0.24   |
| Toshiba   | MK1246GSX          | 120 GB | 9       | 433   | 72    | 0.24   |
| WDC       | WD3200AAKX-753CA1  | 320 GB | 2       | 221   | 4     | 0.24   |
| Seagate   | ST380021A          | 80 GB  | 6       | 663   | 20    | 0.24   |
| Samsung   | HN-M750MBB         | 750 GB | 4       | 229   | 7     | 0.24   |
| Toshiba   | MK3265GSX          | 320 GB | 42      | 586   | 238   | 0.24   |
| WDC       | WD10EZEX-08Y20A0   | 1 TB   | 2       | 87    | 0     | 0.24   |
| Seagate   | ST9160314AS        | 160 GB | 18      | 229   | 251   | 0.24   |
| WDC       | WD5000AAKS-65V0A0  | 500 GB | 2       | 786   | 8     | 0.24   |
| WDC       | WD2000JB-22GVA0    | 200 GB | 1       | 694   | 7     | 0.24   |
| Hitachi   | IC25N080ATMR04-0   | 80 GB  | 2       | 268   | 26    | 0.24   |
| WDC       | WD7500BPVT-22HXZT1 | 750 GB | 4       | 824   | 260   | 0.24   |
| WDC       | WD10JPLX-00MBPT0   | 1 TB   | 9       | 92    | 7     | 0.24   |
| Samsung   | HN-M101MBB         | 1 TB   | 7       | 517   | 477   | 0.24   |
| Seagate   | ST2000LM007-1R8174 | 2 TB   | 3       | 99    | 23    | 0.24   |
| WDC       | WD2500BPVT-22JJ5T0 | 250 GB | 3       | 217   | 248   | 0.24   |
| WDC       | WD1600BEVT-00A1TT0 | 160 GB | 2       | 273   | 3     | 0.24   |
| Hitachi   | HTS541010G9SA00    | 100 GB | 8       | 392   | 15    | 0.24   |
| WDC       | WD1600AAJS-56M0A0  | 160 GB | 1       | 770   | 8     | 0.23   |
| Seagate   | ST750LM030-1KKG62  | 750 GB | 1       | 85    | 0     | 0.23   |
| Toshiba   | MK1629GSG          | 160 GB | 1       | 594   | 6     | 0.23   |
| Seagate   | ST9160821AS        | 160 GB | 40      | 458   | 608   | 0.23   |
| WDC       | WD5000LPVX-08V0TT5 | 500 GB | 8       | 106   | 1     | 0.23   |
| Seagate   | ST1000VX000-1ES162 | 1 TB   | 11      | 84    | 0     | 0.23   |
| Seagate   | ST3500412AS        | 500 GB | 14      | 728   | 571   | 0.23   |
| Seagate   | ST1000DM003-1SB102 | 1 TB   | 16      | 83    | 0     | 0.23   |
| Samsung   | HD300LD            | 300 GB | 4       | 554   | 15    | 0.23   |
| Seagate   | ST1000LM014-SSH... | 1 TB   | 6       | 177   | 16    | 0.23   |
| Toshiba   | MK3263GSXN         | 320 GB | 5       | 582   | 15    | 0.23   |
| Toshiba   | MK3021GAS          | 30 GB  | 1       | 495   | 5     | 0.23   |
| WDC       | WD2500AAKX-753CA1  | 250 GB | 2       | 104   | 4     | 0.23   |
| Samsung   | SP2014N            | 200 GB | 4       | 313   | 18    | 0.23   |
| HGST      | HTS541010A7E630    | 1 TB   | 9       | 97    | 1     | 0.23   |
| WDC       | WD2500AAKX-193CA0  | 250 GB | 1       | 82    | 0     | 0.23   |
| WDC       | WD20EARS-22MVWB0   | 2 TB   | 1       | 739   | 8     | 0.23   |
| Seagate   | ST9250410ASG       | 250 GB | 1       | 409   | 4     | 0.22   |
| WDC       | WD5000AAKX-60U6AA0 | 500 GB | 18      | 163   | 77    | 0.22   |
| WDC       | WD800BB-55JKC0     | 80 GB  | 5       | 751   | 31    | 0.22   |
| WDC       | WD50EFRX-68MYMN1   | 5 TB   | 2       | 81    | 0     | 0.22   |
| Hitachi   | HTS541060G9SA00    | 60 GB  | 2       | 420   | 5     | 0.22   |
| WDC       | WD5000AAKS-00H2B0  | 499 GB | 1       | 731   | 8     | 0.22   |
| WDC       | WD2500LPCX-24C6HT0 | 250 GB | 19      | 84    | 1     | 0.22   |
| WDC       | WD10EURX-73C57Y0   | 1 TB   | 1       | 81    | 0     | 0.22   |
| HGST      | HTS545050A7E660    | 500 GB | 8       | 156   | 4     | 0.22   |
| WDC       | WD10J31X-00U3VT0   | 1 TB   | 1       | 80    | 0     | 0.22   |
| Fujitsu   | MHY2160BH          | 160 GB | 6       | 168   | 323   | 0.22   |
| Toshiba   | MK3263GSX          | 320 GB | 4       | 544   | 25    | 0.22   |
| Magnet... | MD03200-AJDW-RO    | 320 GB | 1       | 79    | 0     | 0.22   |
| WDC       | WD5000AAKS-00V6A0  | 500 GB | 2       | 894   | 19    | 0.22   |
| Toshiba   | MK4055GSX          | 400 GB | 1       | 557   | 6     | 0.22   |
| Seagate   | ST95005620AS       | 500 GB | 5       | 406   | 417   | 0.22   |
| WDC       | WD600BEVS-07LAT0   | 60 GB  | 1       | 635   | 7     | 0.22   |
| Maxtor    | STM3160811AS       | 160 GB | 5       | 687   | 257   | 0.22   |
| Seagate   | ST500LM000-1EJ162  | 500 GB | 31      | 170   | 56    | 0.22   |
| WDC       | WD1003FZEX-00RLFA0 | 1 TB   | 1       | 79    | 0     | 0.22   |
| WDC       | WD3200BUCT-63TWBY0 | 320 GB | 2       | 79    | 0     | 0.22   |
| Hitachi   | HTS543225A7A384    | 250 GB | 14      | 264   | 365   | 0.22   |
| Seagate   | ST320LT007-9ZV142  | 320 GB | 11      | 373   | 907   | 0.22   |
| Samsung   | SP2514N            | 250 GB | 5       | 476   | 610   | 0.21   |
| Seagate   | ST2000DM006-2DM164 | 2 TB   | 3       | 78    | 0     | 0.21   |
| WDC       | WD1600BEVT-26ZCT0  | 160 GB | 1       | 78    | 0     | 0.21   |
| WDC       | WD5000AZRX-00A3KB0 | 500 GB | 3       | 114   | 3     | 0.21   |
| Hitachi   | HDP725016GLA380    | 160 GB | 5       | 765   | 312   | 0.21   |
| WDC       | WD3200BEVT-60A23T0 | 320 GB | 13      | 298   | 386   | 0.21   |
| WDC       | WD10EZEX-00WN4A0   | 1 TB   | 22      | 77    | 0     | 0.21   |
| Toshiba   | MK1665GSX          | 160 GB | 11      | 215   | 158   | 0.21   |
| WDC       | WD7500LPCX-60KHST0 | 750 GB | 3       | 77    | 0     | 0.21   |
| WDC       | WD400JB-00ENA0     | 40 GB  | 1       | 1000  | 12    | 0.21   |
| Fujitsu   | MHV2060BH PL       | 60 GB  | 3       | 76    | 3     | 0.21   |
| Seagate   | ST9160310AS        | 160 GB | 24      | 273   | 226   | 0.21   |
| Toshiba   | MK1646GSX          | 160 GB | 4       | 527   | 58    | 0.21   |
| Seagate   | ST3320613AS        | 320 GB | 70      | 766   | 257   | 0.21   |
| WDC       | WD2502ABYS-50B7A1  | 250 GB | 1       | 1290  | 16    | 0.21   |
| Hitachi   | HTS543280L9A300    | 80 GB  | 2       | 99    | 1     | 0.21   |
| WDC       | WD7500BPKX-00HPJT0 | 750 GB | 3       | 75    | 0     | 0.21   |
| WDC       | WD1004FBYZ-01YCBB1 | 1 TB   | 1       | 75    | 0     | 0.21   |
| Toshiba   | MK6476GSXN         | 640 GB | 3       | 122   | 601   | 0.21   |
| WDC       | WD3200BPVT-00ZEST0 | 320 GB | 2       | 74    | 0     | 0.21   |
| WDC       | WD400VE-07HDT0     | 40 GB  | 1       | 74    | 0     | 0.20   |
| Seagate   | ST2000VX000-9YW164 | 2 TB   | 4       | 407   | 228   | 0.20   |
| Hitachi   | HTS541080G9AT00    | 80 GB  | 10      | 487   | 83    | 0.20   |
| WDC       | WD3200BEVT-00ZCT0  | 320 GB | 3       | 399   | 5     | 0.20   |
| WDC       | WD800VE-75HDT1     | 80 GB  | 1       | 369   | 4     | 0.20   |
| Hitachi   | HDE721050SLA330    | 500 GB | 1       | 2416  | 32    | 0.20   |
| WDC       | WD1500BLHX-01V7BV0 | 150 GB | 1       | 72    | 0     | 0.20   |
| WDC       | WD1600SD-01KCC0    | 160 GB | 1       | 2914  | 39    | 0.20   |
| Toshiba   | MK8034GSX          | 80 GB  | 6       | 356   | 51    | 0.20   |
| Fujitsu   | MJA2500BH G2       | 500 GB | 8       | 309   | 146   | 0.20   |
| Seagate   | ST500LM030-1RK17D  | 500 GB | 2       | 71    | 0     | 0.20   |
| Seagate   | ST9160412AS        | 160 GB | 4       | 449   | 256   | 0.20   |
| WDC       | WD1600AAJS-75PSA0  | 159 GB | 4       | 254   | 3     | 0.20   |
| WDC       | WD20EZRZ-00Z5HB0   | 2 TB   | 7       | 71    | 0     | 0.20   |
| HP        | MB1000EAMZE        | 1 TB   | 1       | 1919  | 26    | 0.19   |
| WDC       | WD3200BPVT-00HXZT1 | 320 GB | 4       | 332   | 257   | 0.19   |
| WDC       | WD1200BEVS-00UST0  | 120 GB | 1       | 69    | 0     | 0.19   |
| WDC       | WD7500BPVX-75JC3T0 | 750 GB | 1       | 349   | 4     | 0.19   |
| Seagate   | ST9160301AS        | 160 GB | 5       | 153   | 403   | 0.19   |
| WDC       | WD5000LPVX-75V0TT0 | 500 GB | 14      | 69    | 0     | 0.19   |
| Hitachi   | HTS722020K9SA00    | 200 GB | 3       | 636   | 9     | 0.19   |
| Hitachi   | HTS542525K9A300    | 250 GB | 2       | 367   | 511   | 0.19   |
| WDC       | WD2500AAJS-22L7A0  | 250 GB | 3       | 625   | 9     | 0.19   |
| Seagate   | ST91608220AS       | 160 GB | 1       | 135   | 1     | 0.19   |
| Seagate   | ST4000DX001-1CE168 | 4 TB   | 3       | 96    | 8     | 0.19   |
| WDC       | WD200BB-60CJA0     | 20 GB  | 1       | 1417  | 20    | 0.18   |
| WDC       | WD10JPCX-24UE4T0   | 1 TB   | 16      | 79    | 1     | 0.18   |
| HGST      | HTS545050A7E680    | 500 GB | 132     | 126   | 300   | 0.18   |
| WDC       | WD3200JS-22PDB0    | 320 GB | 1       | 1538  | 22    | 0.18   |
| WDC       | WD3200BEVT-75A23T0 | 320 GB | 1       | 133   | 1     | 0.18   |
| Seagate   | ST3402111A         | 40 GB  | 2       | 117   | 36    | 0.18   |
| WDC       | WD10JUCT-63CYNY0   | 1 TB   | 1       | 66    | 0     | 0.18   |
| WDC       | WD10PURX-64E5EY0   | 1 TB   | 3       | 69    | 1     | 0.18   |
| WDC       | WD30EZRX-22D8PB0   | 3 TB   | 1       | 65    | 0     | 0.18   |
| WDC       | WD1600AAJS         | 160 GB | 1       | 65    | 0     | 0.18   |
| HGST      | HTE721010A9E630    | 1 TB   | 2       | 65    | 0     | 0.18   |
| Hitachi   | HTS545032B9A302    | 320 GB | 2       | 228   | 13    | 0.18   |
| WDC       | WD5000LPCX-21VHAT0 | 500 GB | 21      | 65    | 0     | 0.18   |
| Toshiba   | MK1011GAH          | 100 GB | 4       | 378   | 9     | 0.18   |
| WDC       | WD30EZRZ-00Z5HB0   | 3 TB   | 7       | 64    | 0     | 0.18   |
| Seagate   | ST9100824AS        | 100 GB | 2       | 129   | 3     | 0.18   |
| Samsung   | HD400LD            | 400 GB | 1       | 63    | 0     | 0.17   |
| WDC       | WD10EZEX-08WN4A0   | 1 TB   | 33      | 63    | 0     | 0.17   |
| WDC       | WD10EURX-73FH1Y0   | 1 TB   | 2       | 63    | 0     | 0.17   |
| WDC       | WD3200BEVT-22A0RT0 | 320 GB | 2       | 120   | 2     | 0.17   |
| WDC       | WD5000BPKT-80PK4T0 | 500 GB | 1       | 563   | 8     | 0.17   |
| Hitachi   | HTS424040M9AT00    | 40 GB  | 5       | 483   | 20    | 0.17   |
| HGST      | HTS725032A7E630    | 320 GB | 5       | 112   | 410   | 0.17   |
| WDC       | WD10EZRX-22L4HB0   | 1 TB   | 1       | 62    | 0     | 0.17   |
| Toshiba   | HDWJ105            | 500 GB | 3       | 61    | 0     | 0.17   |
| WDC       | WD7500BPVT-35HXZT3 | 750 GB | 1       | 309   | 4     | 0.17   |
| Maxtor    | 4K060H3            | 60 GB  | 1       | 927   | 14    | 0.17   |
| Toshiba   | HDWD110            | 1 TB   | 38      | 68    | 11    | 0.17   |
| WDC       | WD10EZEX-07WN4A0   | 1 TB   | 1       | 61    | 0     | 0.17   |
| Hitachi   | HTS725016A9A362    | 160 GB | 1       | 61    | 0     | 0.17   |
| Seagate   | ST3120213A         | 120 GB | 8       | 494   | 773   | 0.17   |
| Toshiba   | MK2552GSX          | 250 GB | 5       | 533   | 41    | 0.17   |
| Toshiba   | HDWD120            | 2 TB   | 7       | 60    | 0     | 0.17   |
| HGST      | HTS545025A7E330    | 250 GB | 1       | 60    | 0     | 0.17   |
| Seagate   | ST9402115AS        | 40 GB  | 1       | 60    | 0     | 0.17   |
| Fujitsu   | MHV2100AH PL       | 100 GB | 1       | 423   | 6     | 0.17   |
| Seagate   | ST9320320AS        | 320 GB | 16      | 683   | 156   | 0.16   |
| Hitachi   | DK23FB-60          | 60 GB  | 1       | 960   | 15    | 0.16   |
| WDC       | WD2500AAJS-98B4A0  | 250 GB | 1       | 540   | 8     | 0.16   |
| Samsung   | HM120JI            | 120 GB | 4       | 327   | 5     | 0.16   |
| WDC       | WD2500AAKS-00F0A0  | 250 GB | 3       | 574   | 9     | 0.16   |
| WDC       | WD1600BEVT-60ZCT0  | 160 GB | 3       | 101   | 336   | 0.16   |
| Toshiba   | MQ01ABF050M        | 500 GB | 3       | 58    | 0     | 0.16   |
| WDC       | WD3200LPVT-22G33T0 | 320 GB | 1       | 58    | 0     | 0.16   |
| MediaMax  | WL250GPA872B       | 250 GB | 1       | 58    | 0     | 0.16   |
| WDC       | WD1600AAJS-08L7A0  | 160 GB | 4       | 415   | 317   | 0.16   |
| Hitachi   | HTS543225L9SA00    | 250 GB | 3       | 685   | 51    | 0.16   |
| Seagate   | ST9250311CS        | 250 GB | 1       | 2074  | 35    | 0.16   |
| WDC       | WD5000AACS-00G8B0  | 500 GB | 2       | 512   | 8     | 0.16   |
| Seagate   | ST1000LM014-1EJ... | 1 TB   | 4       | 145   | 1     | 0.16   |
| Seagate   | ST96812AS          | 60 GB  | 3       | 224   | 283   | 0.16   |
| Seagate   | ST2000LX001-1RG174 | 2 TB   | 1       | 56    | 0     | 0.15   |
| WDC       | WD3200BEKT-60F3T1  | 320 GB | 4       | 303   | 259   | 0.15   |
| WDC       | WD1500HLHX-01JJPV0 | 150 GB | 1       | 498   | 8     | 0.15   |
| WDC       | WD10EALX-229BA1    | 1 TB   | 1       | 493   | 8     | 0.15   |
| Samsung   | SP1213N            | 120 GB | 3       | 1017  | 346   | 0.15   |
| Toshiba   | MK1059GSM          | 1 TB   | 16      | 325   | 988   | 0.15   |
| Seagate   | ST500LM021-1KJ152  | 500 GB | 28      | 81    | 96    | 0.15   |
| WDC       | WD10EZEX-35M2NA0   | 1 TB   | 1       | 54    | 0     | 0.15   |
| WDC       | WD360GD-00FLA2     | 37 GB  | 3       | 914   | 19    | 0.15   |
| WDC       | WD3200BEVT-00A23T0 | 320 GB | 2       | 133   | 13    | 0.15   |
| WDC       | WD5000AZLX-22JKKA0 | 500 GB | 3       | 53    | 0     | 0.15   |
| Hitachi   | HDT725032VLAT80    | 320 GB | 3       | 1450  | 89    | 0.15   |
| WDC       | WD1600BEVS-00RST0  | 160 GB | 1       | 52    | 0     | 0.15   |
| IBM/Hi... | IC25N030ATCS04-0   | 30 GB  | 1       | 52    | 0     | 0.14   |
| WDC       | WD2500BEVT-22ZAT0  | 250 GB | 1       | 316   | 5     | 0.14   |
| WDC       | WD3200BEVT-11ZCT0  | 320 GB | 2       | 60    | 1     | 0.14   |
| Hitachi   | HTS722010K9SA00    | 100 GB | 1       | 468   | 8     | 0.14   |
| Fujitsu   | MJA2250BH G2       | 250 GB | 5       | 243   | 209   | 0.14   |
| WDC       | WD5000LPVX-16V0TT3 | 500 GB | 1       | 51    | 0     | 0.14   |
| WDC       | WD3200BEVT-60ZCT0  | 320 GB | 5       | 269   | 24    | 0.14   |
| WDC       | WD1600AAJB-56R1A0  | 160 GB | 2       | 152   | 4     | 0.14   |
| Seagate   | ST96023AS          | 60 GB  | 1       | 554   | 10    | 0.14   |
| Fujitsu   | MHV2080BH          | 78 GB  | 1       | 400   | 7     | 0.14   |
| Hitachi   | HTS545050B9SA00    | 500 GB | 5       | 944   | 808   | 0.14   |
| Toshiba   | MK3265GSXF         | 320 GB | 3       | 155   | 5     | 0.14   |
| WDC       | WD1600BEKT-60V5T1  | 160 GB | 2       | 145   | 1     | 0.13   |
| WDC       | WD5000AAKX-753CA1  | 500 GB | 3       | 590   | 22    | 0.13   |
| WDC       | WD10JUCT-61CYNY0   | 1 TB   | 1       | 48    | 0     | 0.13   |
| WDC       | WD600UE-22KVT0     | 60 GB  | 1       | 243   | 4     | 0.13   |
| WDC       | WD2500BPVT-26JJ5T0 | 250 GB | 1       | 48    | 0     | 0.13   |
| WDC       | WD6001FSYZ-01SS7B1 | 6 TB   | 1       | 47    | 0     | 0.13   |
| Seagate   | ST4000VM000-2AF166 | 4 TB   | 1       | 47    | 0     | 0.13   |
| WDC       | WD10EZRZ-00HTKB0   | 1 TB   | 13      | 47    | 0     | 0.13   |
| Samsung   | SP1203N            | 120 GB | 6       | 486   | 31    | 0.13   |
| Hitachi   | HTS421210H9AT00    | 100 GB | 1       | 568   | 11    | 0.13   |
| Toshiba   | HDWK105            | 500 GB | 1       | 47    | 0     | 0.13   |
| WDC       | WD7500AACS-00D6B1  | 750 GB | 1       | 423   | 8     | 0.13   |
| Fujitsu   | MHV2080BH PL       | 80 GB  | 6       | 215   | 7     | 0.13   |
| WDC       | WD5000LPCX-24VHAT0 | 500 GB | 19      | 47    | 59    | 0.13   |
| WDC       | WD1200BEVS-07LAT0  | 120 GB | 3       | 391   | 164   | 0.13   |
| Samsung   | SP1213C            | 120 GB | 4       | 750   | 54    | 0.13   |
| WDC       | WD1600BB-00GUC0    | 160 GB | 3       | 769   | 81    | 0.13   |
| Hitachi   | HTS542512K9A300    | 120 GB | 3       | 366   | 6     | 0.13   |
| Toshiba   | MK2046GSX          | 200 GB | 7       | 418   | 25    | 0.12   |
| Seagate   | ST2000DX002-2DV164 | 2 TB   | 3       | 45    | 0     | 0.12   |
| Samsung   | SV4012H            | 40 GB  | 2       | 1504  | 236   | 0.12   |
| WDC       | WD3200AAJS-00V4A0  | 320 GB | 3       | 396   | 9     | 0.12   |
| Toshiba   | MK3265GSX H        | 320 GB | 1       | 45    | 0     | 0.12   |
| WDC       | WD10EZEX-60WN4A0   | 1 TB   | 10      | 50    | 71    | 0.12   |
| Toshiba   | MK1652GSX          | 160 GB | 8       | 301   | 39    | 0.12   |
| WDC       | WD5000LPLX-08ZNTT0 | 500 GB | 2       | 44    | 0     | 0.12   |
| WDC       | WD10EFRX-68FYTN0   | 1 TB   | 9       | 65    | 1     | 0.12   |
| ExcelStor | J880S              | 82 GB  | 1       | 44    | 0     | 0.12   |
| Toshiba   | MK6008GAH          | 60 GB  | 2       | 399   | 8     | 0.12   |
| WDC       | WD10EZEX-22MFCA0   | 1 TB   | 11      | 50    | 1     | 0.12   |
| WDC       | WD10SPZX-22Z10T0   | 1 TB   | 3       | 43    | 0     | 0.12   |
| Hitachi   | HDP725025GLAT80    | 250 GB | 1       | 216   | 4     | 0.12   |
| Toshiba   | MK3276GSX H        | 320 GB | 1       | 43    | 0     | 0.12   |
| WDC       | WD1503FYYS-02W0B0  | 1.5 TB | 1       | 382   | 8     | 0.12   |
| WDC       | WD5000LPLX-00ZNTT0 | 500 GB | 16      | 42    | 0     | 0.12   |
| Hitachi   | IC25N060ATMR04-0   | 60 GB  | 5       | 215   | 10    | 0.11   |
| Seagate   | ST31500341AS       | 1.5 TB | 44      | 731   | 298   | 0.11   |
| Toshiba   | MK3275GSX          | 320 GB | 7       | 198   | 10    | 0.11   |
| Seagate   | ST3750330AS        | 750 GB | 8       | 713   | 295   | 0.11   |
| Hitachi   | HTS543232L9SA00    | 320 GB | 5       | 389   | 182   | 0.11   |
| Maxtor    | 7L250R0            | 251 GB | 1       | 40    | 0     | 0.11   |
| Fujitsu   | MHV2200BT PL       | 200 GB | 1       | 325   | 7     | 0.11   |
| WDC       | WD1600BEVE-00UYT0  | 160 GB | 1       | 40    | 0     | 0.11   |
| WDC       | WD3200LPVT-00G33T0 | 320 GB | 2       | 40    | 0     | 0.11   |
| Maxtor    | 6Y120M0            | 122 GB | 1       | 40    | 0     | 0.11   |
| WDC       | WD30EZRX-00AZ6B0   | 3 TB   | 1       | 40    | 0     | 0.11   |
| WDC       | WD6400AAKS-55A7B2  | 640 GB | 1       | 361   | 8     | 0.11   |
| WDC       | WD1600BEKT-60A25T1 | 160 GB | 1       | 79    | 1     | 0.11   |
| Hitachi   | HTS545012B9SA00    | 120 GB | 1       | 197   | 4     | 0.11   |
| Toshiba   | HDWJ110            | 1 TB   | 3       | 39    | 0     | 0.11   |
| WDC       | WD2000JS-22NCB1    | 200 GB | 1       | 1921  | 48    | 0.11   |
| WDC       | WD5000AVCS-612DY1  | 500 GB | 1       | 582   | 14    | 0.11   |
| Toshiba   | MK1252GSX          | 120 GB | 6       | 332   | 128   | 0.11   |
| Hitachi   | HTS421280H9AT00    | 80 GB  | 2       | 776   | 30    | 0.11   |
| Samsung   | HM100JC            | 100 GB | 1       | 383   | 9     | 0.10   |
| WDC       | WD1500ADFD-00NLR5  | 150 GB | 1       | 344   | 8     | 0.10   |
| Hitachi   | HTS541020G9SA00    | 20 GB  | 1       | 38    | 0     | 0.10   |
| WDC       | WD15EADS-22P8B0    | 1.5 TB | 1       | 339   | 8     | 0.10   |
| WDC       | WD3200BEVS-16VAT0  | 320 GB | 1       | 37    | 0     | 0.10   |
| HGST      | HTS541515A9E630    | 1.5 TB | 2       | 541   | 14    | 0.10   |
| WDC       | WD1002FBYS-18W8B0  | 1 TB   | 1       | 36    | 0     | 0.10   |
| WDC       | WD5000BEVT-80A0RT1 | 500 GB | 2       | 284   | 7     | 0.10   |
| Hitachi   | HTS543212L9A300    | 120 GB | 2       | 232   | 72    | 0.10   |
| Toshiba   | HDWD105            | 500 GB | 31      | 35    | 5     | 0.10   |
| WDC       | WD800AAJS-60B4A0   | 80 GB  | 2       | 1529  | 24    | 0.10   |
| WDC       | WD2500AAJS-75B4A0  | 250 GB | 2       | 348   | 9     | 0.10   |
| Maxtor    | 6L120P0            | 122 GB | 2       | 35    | 0     | 0.10   |
| WDC       | WD30EZRS-00J99B0   | 3 TB   | 4       | 769   | 875   | 0.10   |
| Seagate   | ST3000DM008-2DM166 | 3 TB   | 3       | 35    | 0     | 0.10   |
| Seagate   | ST980411ASG        | 80 GB  | 1       | 490   | 13    | 0.10   |
| Seagate   | ST1000DM010-2EP102 | 1 TB   | 38      | 34    | 0     | 0.10   |
| Hitachi   | HTS725025A9A361... | 250 GB | 1       | 34    | 0     | 0.09   |
| WDC       | WD5000LPVX-08V0TT2 | 500 GB | 1       | 274   | 7     | 0.09   |
| Toshiba   | MK5055GSX          | 500 GB | 7       | 550   | 200   | 0.09   |
| Seagate   | ST2000LM015-2E8174 | 2 TB   | 2       | 34    | 0     | 0.09   |
| Hitachi   | HDS722580VLAT20    | 82 GB  | 2       | 610   | 269   | 0.09   |
| Maxtor    | STM380211AS        | 80 GB  | 3       | 291   | 1165  | 0.09   |
| WDC       | WD10EZEX-75WN4A0   | 1 TB   | 5       | 83    | 2     | 0.09   |
| WDC       | WD5000BEKT-22KA9T0 | 500 GB | 1       | 302   | 8     | 0.09   |
| HGST      | HTS541050A9E680    | 500 GB | 3       | 33    | 0     | 0.09   |
| Seagate   | ST1000LM010-9YH146 | 1 TB   | 4       | 140   | 646   | 0.09   |
| WDC       | WD1600BB-55GUA0    | 160 GB | 1       | 668   | 19    | 0.09   |
| WDC       | WD2500AAJS-00YZCA0 | 250 GB | 1       | 33    | 0     | 0.09   |
| Toshiba   | HDWM105            | 500 GB | 1       | 32    | 0     | 0.09   |
| Maxtor    | STM3320613AS       | 320 GB | 8       | 1132  | 157   | 0.09   |
| HGST      | HUS726020ALE614    | 2 TB   | 1       | 31    | 0     | 0.09   |
| WDC       | WD1600BEVS-00VAT0  | 160 GB | 1       | 31    | 0     | 0.09   |
| Seagate   | ST3320311CS        | 320 GB | 2       | 31    | 0     | 0.09   |
| WDC       | WD800JB-00FSA0     | 80 GB  | 1       | 1366  | 43    | 0.09   |
| WDC       | WD2500JD-00HBC0    | 250 GB | 1       | 620   | 19    | 0.09   |
| Maxtor    | 2F030J1            | 30 GB  | 1       | 185   | 5     | 0.08   |
| Fujitsu   | MHV2060AT PL       | 60 GB  | 2       | 690   | 21    | 0.08   |
| WDC       | WD5000AAJS-00YFA0  | 500 GB | 2       | 469   | 81    | 0.08   |
| WDC       | WD2000JS-60NCB1    | 200 GB | 1       | 275   | 8     | 0.08   |
| WDC       | WD1600BEVT-00A23T0 | 160 GB | 2       | 111   | 5     | 0.08   |
| Seagate   | ST38410A           | 8 GB   | 1       | 754   | 24    | 0.08   |
| WDC       | WD5000LPLX-22ZNTT0 | 500 GB | 1       | 30    | 0     | 0.08   |
| WDC       | WD2500AAJS-55M0A0  | 250 GB | 1       | 269   | 8     | 0.08   |
| Samsung   | SV0401N            | 40 GB  | 1       | 952   | 31    | 0.08   |
| Seagate   | ST750LM028-1KK162  | 750 GB | 1       | 29    | 0     | 0.08   |
| HGST      | HTS541075A7E630    | 750 GB | 6       | 48    | 169   | 0.08   |
| WDC       | WD1600JS-00MHB1    | 160 GB | 1       | 1060  | 35    | 0.08   |
| Seagate   | ST1000DX002-2DV162 | 1 TB   | 3       | 29    | 0     | 0.08   |
| WDC       | WD5000AAKX-00KJ3A0 | 500 GB | 1       | 262   | 8     | 0.08   |
| Samsung   | MP0804H            | 80 GB  | 2       | 198   | 7     | 0.08   |
| WDC       | WD3200JB-00KFA0    | 320 GB | 1       | 29    | 0     | 0.08   |
| Samsung   | HM160HC            | 160 GB | 5       | 215   | 21    | 0.08   |
| Maxtor    | 6L080M0            | 80 GB  | 3       | 28    | 0     | 0.08   |
| Seagate   | ST1000VM002-1ET162 | 1 TB   | 1       | 28    | 0     | 0.08   |
| WDC       | WD2500BEVT-60A23T0 | 250 GB | 2       | 131   | 24    | 0.08   |
| WDC       | WD5000LPCX-60VHAT0 | 500 GB | 7       | 67    | 1     | 0.08   |
| Hitachi   | HTS543212L9SA02    | 120 GB | 1       | 27    | 0     | 0.08   |
| Toshiba   | MQ01ABD100M        | 1 TB   | 1       | 27    | 0     | 0.08   |
| MARSHAL   | MAL2500SA-T54      | 500 GB | 1       | 279   | 9     | 0.08   |
| WDC       | WD5000AZLX-21K2TA0 | 500 GB | 3       | 27    | 0     | 0.08   |
| Hitachi   | HTS541040G9SA00    | 40 GB  | 1       | 415   | 14    | 0.08   |
| Seagate   | ST3500320AS        | 500 GB | 49      | 804   | 558   | 0.07   |
| HGST      | HTS541010B7E610    | 1 TB   | 2       | 26    | 0     | 0.07   |
| WDC       | WD2000JD-55HBC0    | 200 GB | 1       | 26    | 0     | 0.07   |
| WDC       | WD3200AVVS-63L2B0  | 320 GB | 3       | 56    | 4     | 0.07   |
| WDC       | WD2502ABYS-02B7A0  | 251 GB | 1       | 316   | 11    | 0.07   |
| WDC       | WD3200AAJS-00VWA1  | 320 GB | 1       | 708   | 26    | 0.07   |
| Hitachi   | HTS548040M9AT00    | 40 GB  | 1       | 470   | 17    | 0.07   |
| Seagate   | ST1000LM048-2E7172 | 1 TB   | 9       | 26    | 0     | 0.07   |
| Seagate   | ST9250320AS        | 250 GB | 10      | 279   | 315   | 0.07   |
| WDC       | WD15EADS-00S2B0    | 1.5 TB | 1       | 483   | 18    | 0.07   |
| Samsung   | HM251JI            | 250 GB | 5       | 354   | 624   | 0.07   |
| Fujitsu   | MHT2080BH          | 80 GB  | 1       | 403   | 15    | 0.07   |
| Samsung   | HM320JI            | 320 GB | 3       | 324   | 10    | 0.07   |
| Toshiba   | MK5059GSX          | 500 GB | 1       | 932   | 36    | 0.07   |
| WDC       | WD5000LPCX-75VHAT0 | 500 GB | 6       | 24    | 0     | 0.07   |
| Seagate   | ST3320820SCE       | 320 GB | 1       | 24    | 0     | 0.07   |
| WDC       | WD6400BEVT-80A0RT1 | 640 GB | 1       | 664   | 26    | 0.07   |
| Hitachi   | HTS725032A9A360    | 320 GB | 1       | 24    | 0     | 0.07   |
| WDC       | WD2500AAJS-52B4A0  | 250 GB | 2       | 942   | 45    | 0.07   |
| Seagate   | ST3640323AS        | 640 GB | 5       | 1121  | 735   | 0.07   |
| HGST      | HTS545050B7E660    | 500 GB | 8       | 24    | 0     | 0.07   |
| WDC       | WD10SPCX-75KHST0   | 1 TB   | 1       | 24    | 0     | 0.07   |
| WDC       | WD5000AZLX-00JKKA0 | 500 GB | 2       | 23    | 0     | 0.07   |
| WDC       | WD400VE-75HDT1     | 40 GB  | 1       | 23    | 0     | 0.06   |
| WDC       | WD800JD-32LSA0     | 80 GB  | 1       | 2499  | 105   | 0.06   |
| WDC       | WD30EZRX-00SPEB0   | 3 TB   | 1       | 23    | 0     | 0.06   |
| Samsung   | HD160HJ            | 160 GB | 13      | 552   | 732   | 0.06   |
| Apple     | HDD HTS547550A9... | 500 GB | 1       | 23    | 0     | 0.06   |
| Toshiba   | MK6032GAX          | 60 GB  | 1       | 23    | 0     | 0.06   |
| Seagate   | ST4000VX000-2AG166 | 4 TB   | 1       | 23    | 0     | 0.06   |
| Fujitsu   | MJA2320BH G2       | 320 GB | 3       | 737   | 694   | 0.06   |
| Toshiba   | MK6465GSXW         | 640 GB | 1       | 552   | 23    | 0.06   |
| Toshiba   | MK2529GSG          | 250 GB | 2       | 313   | 1127  | 0.06   |
| WDC       | WD3200BEKX-22B7WT0 | 320 GB | 1       | 21    | 0     | 0.06   |
| WDC       | WD10JPVX-60JC3T1   | 1 TB   | 5       | 21    | 0     | 0.06   |
| Maxtor    | 6L200P0            | 203 GB | 1       | 21    | 0     | 0.06   |
| Seagate   | ST3300831A         | 300 GB | 1       | 347   | 15    | 0.06   |
| Seagate   | ST3250824SCE       | 250 GB | 1       | 21    | 0     | 0.06   |
| Hitachi   | HTS722016K9A300    | 160 GB | 1       | 236   | 10    | 0.06   |
| WDC       | WD5000AVDS-73U7B1  | 500 GB | 2       | 189   | 7     | 0.06   |
| Samsung   | HD103UI            | 1 TB   | 1       | 385   | 17    | 0.06   |
| Samsung   | HM160HI            | 160 GB | 39      | 310   | 244   | 0.06   |
| Toshiba   | MK1656GSY          | 160 GB | 1       | 379   | 17    | 0.06   |
| Hitachi   | HTS721060G9SA00    | 60 GB  | 2       | 335   | 17    | 0.06   |
| Maxtor    | STM3160613AS       | 160 GB | 1       | 41    | 1     | 0.06   |
| WDC       | WD400BB-22DEA0     | 40 GB  | 1       | 831   | 39    | 0.06   |
| WDC       | WD2000BB-00GUC0    | 200 GB | 1       | 637   | 30    | 0.06   |
| Maxtor    | 6B200M0            | 200 GB | 3       | 26    | 13    | 0.06   |
| WDC       | WD5000BPVT-75A1YT0 | 500 GB | 1       | 20    | 0     | 0.06   |
| WDC       | WD2500BPVT-00ZEST0 | 250 GB | 3       | 136   | 74    | 0.06   |
| Fujitsu   | MHZ2080BH G1       | 80 GB  | 1       | 20    | 0     | 0.06   |
| Maxtor    | STM3160813AS       | 160 GB | 3       | 745   | 370   | 0.06   |
| Toshiba   | MK5076GSX          | 500 GB | 21      | 56    | 228   | 0.05   |
| Maxtor    | STM3500320AS       | 500 GB | 9       | 772   | 404   | 0.05   |
| Seagate   | ST3160215SCE       | 160 GB | 1       | 98    | 4     | 0.05   |
| Seagate   | ST9250610NS        | 250 GB | 2       | 19    | 0     | 0.05   |
| Hitachi   | IC25N040ATMR04-0   | 40 GB  | 2       | 628   | 181   | 0.05   |
| Seagate   | ST1000DX001-1NS162 | 1 TB   | 1       | 195   | 9     | 0.05   |
| WDC       | WD200EB-75CPF0     | 20 GB  | 2       | 402   | 20    | 0.05   |
| Toshiba   | MK1032GAX          | 100 GB | 1       | 19    | 0     | 0.05   |
| WDC       | WD1600JD-00GBB0    | 160 GB | 1       | 727   | 37    | 0.05   |
| WDC       | WD3200BPVT-00HXZT3 | 320 GB | 2       | 229   | 12    | 0.05   |
| Seagate   | ST31000340NS       | 1 TB   | 7       | 1003  | 468   | 0.05   |
| Samsung   | HM080HI            | 80 GB  | 2       | 473   | 405   | 0.05   |
| Seagate   | ST31000340AS       | 1 TB   | 3       | 1146  | 386   | 0.05   |
| WDC       | WD5000LPVX-16V0TT0 | 500 GB | 1       | 71    | 3     | 0.05   |
| Quantum   | FIREBALLlct15 10   | 10 GB  | 1       | 105   | 5     | 0.05   |
| Samsung   | HM121HC            | 120 GB | 2       | 179   | 26    | 0.05   |
| WDC       | WD2500JS-75NCB1    | 250 GB | 1       | 2681  | 153   | 0.05   |
| WDC       | WD1600JS-55MHB0    | 160 GB | 1       | 761   | 43    | 0.05   |
| WDC       | WD5000AZLX-08K2TA0 | 500 GB | 6       | 16    | 0     | 0.05   |
| Seagate   | ST3320310CS        | 320 GB | 3       | 576   | 32    | 0.05   |
| Samsung   | HN-M250MBB         | 250 GB | 1       | 292   | 17    | 0.04   |
| Maxtor    | 2F040L0            | 41 GB  | 3       | 25    | 2     | 0.04   |
| WDC       | WD800BB-88JHC0     | 80 GB  | 1       | 1625  | 101   | 0.04   |
| Hitachi   | HDT721050SLA360    | 500 GB | 2       | 1337  | 95    | 0.04   |
| Hitachi   | HTS545025A7E380    | 250 GB | 1       | 15    | 0     | 0.04   |
| Hitachi   | HTS543232L9SA02    | 320 GB | 1       | 1319  | 84    | 0.04   |
| WDC       | WD5000LPLX-66ZNTT1 | 500 GB | 1       | 31    | 1     | 0.04   |
| Samsung   | SP1253N            | 120 GB | 1       | 286   | 18    | 0.04   |
| Maxtor    | 6L160M0            | 160 GB | 4       | 26    | 1     | 0.04   |
| Samsung   | SP1614C            | 160 GB | 2       | 124   | 22    | 0.04   |
| Hitachi   | HTS723225L9A360    | 250 GB | 3       | 322   | 1301  | 0.04   |
| WDC       | WD3200KS-00PFB0    | 320 GB | 1       | 1354  | 92    | 0.04   |
| Toshiba   | MK6034GSX          | 60 GB  | 2       | 376   | 29    | 0.04   |
| WDC       | WD10SPCX-21KHST0   | 1 TB   | 1       | 14    | 0     | 0.04   |
| Seagate   | ST9120310AS        | 120 GB | 1       | 14    | 0     | 0.04   |
| Seagate   | ST500DM002-1SB10A  | 500 GB | 14      | 17    | 1     | 0.04   |
| WDC       | WD2500BEKX-00B7WT0 | 250 GB | 1       | 13    | 0     | 0.04   |
| Seagate   | ST91000640NS       | 1 TB   | 1       | 13    | 0     | 0.04   |
| Seagate   | ST310212A          | 10 GB  | 1       | 380   | 27    | 0.04   |
| WDC       | WD5000AADS-98S9B1  | 500 GB | 1       | 120   | 8     | 0.04   |
| Seagate   | ST31000333AS       | 1 TB   | 11      | 591   | 241   | 0.04   |
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
| Seagate   | ST500LM030-2E717D  | 500 GB | 6       | 10    | 0     | 0.03   |
| Hitachi   | HTS723232L9A360    | 320 GB | 2       | 714   | 537   | 0.03   |
| Hitachi   | HTS541660J9SA00    | 60 GB  | 2       | 112   | 12    | 0.03   |
| WDC       | WD7500BPVT-60HXZT1 | 750 GB | 2       | 815   | 84    | 0.03   |
| WDC       | WD1002FBYS-43P1B0  | 1 TB   | 1       | 783   | 77    | 0.03   |
| Seagate   | ST4000DM004-2CV104 | 4 TB   | 2       | 9     | 0     | 0.03   |
| Maxtor    | 6E040L0            | 40 GB  | 7       | 32    | 25    | 0.03   |
| Samsung   | HM160JI            | 160 GB | 1       | 739   | 76    | 0.03   |
| Seagate   | ST9808210A         | 80 GB  | 1       | 344   | 37    | 0.02   |
| WDC       | WD3200AAJS-40VWA1  | 320 GB | 1       | 375   | 41    | 0.02   |
| Maxtor    | 4K040H2            | 33 GB  | 1       | 298   | 33    | 0.02   |
| Maxtor    | 6E030L0            | 30 GB  | 4       | 17    | 1     | 0.02   |
| WDC       | WD10EZRX-00A3KB0   | 1 TB   | 1       | 8     | 0     | 0.02   |
| WDC       | WD2500AVJS-63B6A0  | 250 GB | 1       | 77    | 8     | 0.02   |
| Seagate   | ST1000LM035-1RK172 | 1 TB   | 17      | 8     | 0     | 0.02   |
| WDC       | WD2500JS-60MHB1    | 250 GB | 1       | 124   | 14    | 0.02   |
| Toshiba   | MK7559GSXF         | 750 GB | 1       | 8     | 0     | 0.02   |
| Maxtor    | 6Y120L0            | 122 GB | 6       | 29    | 16    | 0.02   |
| Hitachi   | HTS548080M9AT00    | 80 GB  | 1       | 136   | 16    | 0.02   |
| ExcelStor | J9250              | 250 GB | 1       | 1349  | 167   | 0.02   |
| MediaMax  | WL250GLSA6410000   | 250 GB | 2       | 36    | 4     | 0.02   |
| Seagate   | ST9320421AS        | 320 GB | 2       | 709   | 98    | 0.02   |
| Samsung   | HM121HI            | 120 GB | 6       | 447   | 1147  | 0.02   |
| WDC       | WD5000LPCX-08VHA   | 500 GB | 5       | 7     | 0     | 0.02   |
| Maxtor    | 6Y060L2            | 61 GB  | 1       | 542   | 71    | 0.02   |
| Maxtor    | 6K040L0            | 41 GB  | 1       | 29    | 3     | 0.02   |
| Maxtor    | 6L160P0            | 163 GB | 1       | 29    | 3     | 0.02   |
| Seagate   | ST500DM009-2F110A  | 500 GB | 3       | 20    | 10    | 0.02   |
| WDC       | WD2000JS-00NCB1    | 200 GB | 1       | 537   | 73    | 0.02   |
| WDC       | WD3200BEKT-75PVMT0 | 320 GB | 1       | 208   | 28    | 0.02   |
| WDC       | WD5000LPLX-60ZNTT1 | 500 GB | 3       | 7     | 1     | 0.02   |
| HP        | GB0250C8045        | 250 GB | 1       | 1405  | 198   | 0.02   |
| WDC       | WD2500AAJS-41RYA0  | 250 GB | 1       | 76    | 10    | 0.02   |
| Maxtor    | 6B250S0            | 250 GB | 1       | 6     | 0     | 0.02   |
| HGST      | HUS722T1TALA604    | 1 TB   | 2       | 6     | 0     | 0.02   |
| Toshiba   | MK5061GSYN         | 500 GB | 6       | 188   | 188   | 0.02   |
| WDC       | WD360ADFD-00NLR4   | 37 GB  | 1       | 499   | 77    | 0.02   |
| Seagate   | ST9160821A         | 160 GB | 1       | 182   | 28    | 0.02   |
| Toshiba   | MQ01ACF032         | 320 GB | 1       | 6     | 0     | 0.02   |
| Maxtor    | 6L120M0            | 122 GB | 1       | 43    | 6     | 0.02   |
| WDC       | WD20NPVT-00Z2TT0   | 2 TB   | 1       | 171   | 27    | 0.02   |
| Maxtor    | 6L080P0            | 81 GB  | 2       | 10    | 10    | 0.02   |
| WDC       | WD10TMVW-11ZSMS5   | 1 TB   | 1       | 59    | 9     | 0.02   |
| Samsung   | HM120JC            | 120 GB | 1       | 605   | 102   | 0.02   |
| Hitachi   | HTS541612J9AT00    | 120 GB | 1       | 116   | 19    | 0.02   |
| Seagate   | ST3500320SV        | 500 GB | 1       | 45    | 7     | 0.02   |
| Samsung   | SV0412H            | 40 GB  | 3       | 733   | 124   | 0.02   |
| Seagate   | ST3000VX010-2E3166 | 3 TB   | 1       | 5     | 0     | 0.01   |
| Toshiba   | MQ02ABF050H-SSH... | 500 GB | 1       | 5     | 0     | 0.01   |
| Seagate   | ST500LT012-9WS142  | 500 GB | 114     | 265   | 1022  | 0.01   |
| WDC       | WD15EARS-22MVWB0   | 1.5 TB | 3       | 818   | 514   | 0.01   |
| WDC       | WD1200AAJS-00VTA0  | 120 GB | 1       | 995   | 203   | 0.01   |
| Maxtor    | 6Y080M0            | 80 GB  | 6       | 32    | 39    | 0.01   |
| Hitachi   | HTE721060G9AT00    | 60 GB  | 1       | 4     | 0     | 0.01   |
| Seagate   | ST320LT012-9WS14C  | 320 GB | 39      | 210   | 967   | 0.01   |
| Toshiba   | MG04ACA400E        | 4 TB   | 2       | 4     | 0     | 0.01   |
| Maxtor    | 4R060J0            | 61 GB  | 1       | 25    | 5     | 0.01   |
| Fujitsu   | MHZ2160BJ G1       | 160 GB | 1       | 4     | 0     | 0.01   |
| Seagate   | ST3500820AS        | 500 GB | 2       | 268   | 56    | 0.01   |
| WDC       | WD3200BEVT-75ZCT0  | 320 GB | 1       | 676   | 167   | 0.01   |
| Maxtor    | 6Y120P0            | 122 GB | 2       | 23    | 8     | 0.01   |
| WDC       | WD800JD-55JRC0     | 80 GB  | 1       | 243   | 62    | 0.01   |
| Samsung   | HM500LI            | 500 GB | 1       | 7     | 1     | 0.01   |
| Maxtor    | 6Y200P0            | 203 GB | 1       | 30    | 7     | 0.01   |
| WDC       | WD2500BEKT-66F3T2  | 250 GB | 1       | 193   | 50    | 0.01   |
| Seagate   | ST1000LX015-1U7172 | 1 TB   | 3       | 3     | 0     | 0.01   |
| Seagate   | ST3250310SV        | 250 GB | 1       | 287   | 79    | 0.01   |
| Maxtor    | 6Y080P0            | 81 GB  | 6       | 17    | 7     | 0.01   |
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
| WDC       | WD800JD-60LSA0     | 80 GB  | 2       | 231   | 394   | 0.01   |
| WDC       | WD2004FBYZ-01YCBB1 | 2 TB   | 1       | 2     | 0     | 0.01   |
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
| Maxtor    | 6L250S0            | 250 GB | 1       | 40    | 23    | 0.00   |
| Maxtor    | 2B020H1            | 20 GB  | 6       | 22    | 76    | 0.00   |
| Seagate   | ST3750630AS        | 750 GB | 1       | 1122  | 686   | 0.00   |
| WDC       | WD3200BEVT-26A23T0 | 320 GB | 1       | 352   | 218   | 0.00   |
| WDC       | WD5003ABYZ-011FA0  | 500 GB | 2       | 13    | 4     | 0.00   |
| Samsung   | HD251KJ            | 250 GB | 1       | 1539  | 1019  | 0.00   |
| Maxtor    | 6Y080L0            | 80 GB  | 23      | 21    | 275   | 0.00   |
| Seagate   | ST500VT000-1BS142  | 500 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WD20EZRZ-60Z5HB0   | 2 TB   | 1       | 1     | 0     | 0.00   |
| WDC       | WD2500JD-98GBB0    | 250 GB | 1       | 875   | 628   | 0.00   |
| Fujitsu   | MHZ2320BH G2       | 320 GB | 5       | 489   | 543   | 0.00   |
| WDC       | WD3200LPCX-60VHAT0 | 320 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WD1200             | 120 GB | 1       | 11    | 8     | 0.00   |
| WDC       | WD30EZRS-11J99B1   | 3 TB   | 1       | 794   | 663   | 0.00   |
| WDC       | WD400BB-00CAA0     | 40 GB  | 1       | 194   | 163   | 0.00   |
| WDC       | WD800UE-22HCT0     | 80 GB  | 1       | 436   | 395   | 0.00   |
| Toshiba   | MK5061GSY          | 500 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WD3200JS-63PDB1    | 320 GB | 1       | 343   | 342   | 0.00   |
| Maxtor    | 6Y160M0            | 160 GB | 3       | 12    | 184   | 0.00   |
| WDC       | WD2500AVVS-62L2B0  | 250 GB | 1       | 9     | 9     | 0.00   |
| Fujitsu   | MHV2160BT          | 160 GB | 1       | 483   | 535   | 0.00   |
| HGST      | HTS725050B7E630    | 500 GB | 1       | 0     | 0     | 0.00   |
| HGST      | TPH00100500GB 0... | 500 GB | 1       | 8     | 10    | 0.00   |
| Toshiba   | MK3256GSY          | 320 GB | 4       | 5     | 282   | 0.00   |
| Maxtor    | STM3750330AS       | 750 GB | 1       | 995   | 1293  | 0.00   |
| MediaMax  | WL400GSA6454G      | 400 GB | 1       | 0     | 0     | 0.00   |
| Seagate   | ST1000VN002-2EY102 | 1 TB   | 1       | 0     | 0     | 0.00   |
| WDC       | WD3200LPCX-22VHAT0 | 320 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD5000BPVX-00JC3T0 | 500 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD5000LPCX-75VHAT1 | 500 GB | 1       | 0     | 0     | 0.00   |
| Maxtor    | 6Y060L0            | 61 GB  | 3       | 19    | 76    | 0.00   |
| Seagate   | ST3320620SV        | 320 GB | 1       | 564   | 835   | 0.00   |
| Fujitsu   | MHZ2120BH G2       | 120 GB | 1       | 693   | 1028  | 0.00   |
| WDC       | WD800AAJS-60PSA0   | 80 GB  | 1       | 624   | 1007  | 0.00   |
| Hitachi   | DK23EA-40          | 40 GB  | 1       | 287   | 470   | 0.00   |
| Maxtor    | 4D060H3            | 60 GB  | 1       | 18    | 31    | 0.00   |
| WDC       | WD6400BPVT-24HXZT1 | 640 GB | 1       | 560   | 1013  | 0.00   |
| Hitachi   | HUA722010CLA630    | 1 TB   | 1       | 0     | 0     | 0.00   |
| WDC       | WD15EARS-19MVWB0   | 1.5 TB | 1       | 696   | 1306  | 0.00   |
| Hitachi   | HTS723212L9A360    | 120 GB | 1       | 535   | 1012  | 0.00   |
| China     | OOS500G            | 500 GB | 1       | 453   | 1024  | 0.00   |
| WDC       | WD15EURS-63S48Y0   | 1.5 TB | 1       | 11    | 26    | 0.00   |
| Hitachi   | HTS725025A9A364    | 250 GB | 10      | 447   | 1148  | 0.00   |
| Toshiba   | MK8025GAS          | 80 GB  | 1       | 22    | 58    | 0.00   |
| Seagate   | ST3500321CS        | 500 GB | 1       | 48    | 137   | 0.00   |
| WDC       | WD3200L22X-00JVPT0 | 320 GB | 1       | 0     | 0     | 0.00   |
| Seagate   | ST980817AS         | 80 GB  | 1       | 310   | 1009  | 0.00   |
| WDC       | WD5000LPLX-60ZNTT0 | 500 GB | 1       | 0     | 0     | 0.00   |
| Samsung   | SV2011H            | 20 GB  | 1       | 0     | 3     | 0.00   |
| WDC       | WD2500AAJS-55B4A0  | 250 GB | 1       | 476   | 2020  | 0.00   |
| Seagate   | ST250LT012-9WS141  | 250 GB | 3       | 232   | 1094  | 0.00   |
| Toshiba   | MQ01ABB200         | 2 TB   | 1       | 152   | 704   | 0.00   |
| Seagate   | ST9500424AS        | 500 GB | 1       | 200   | 1009  | 0.00   |
| Maxtor    | 7L300S0            | 300 GB | 1       | 5     | 33    | 0.00   |
| Seagate   | ST3160316CS        | 159 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WD3200BEKX-60B7WT0 | 320 GB | 1       | 0     | 0     | 0.00   |
| Seagate   | ST980829A          | 80 GB  | 1       | 222   | 2022  | 0.00   |
| Toshiba   | MK1214GAH          | 120 GB | 1       | 44    | 417   | 0.00   |
| WDC       | WD10EZEX-00MFCA0   | 1 TB   | 1       | 0     | 0     | 0.00   |
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
| Seagate   | Barracuda ES+          | 1      | 1       | 2169  | 0     | 5.94   |
| WDC       | RE4-GP                 | 3      | 6       | 1733  | 1     | 4.22   |
| Hitachi   | CinemaStar 5K320       | 1      | 1       | 1281  | 0     | 3.51   |
| WDC       | Raptor X               | 1      | 1       | 1164  | 0     | 3.19   |
| Samsung   | SpinPoint              | 2      | 3       | 1164  | 3     | 3.04   |
| WDC       | RE2                    | 5      | 8       | 1282  | 70    | 2.84   |
| WDC       | RE2-GP                 | 1      | 1       | 989   | 0     | 2.71   |
| Hitachi   | Ultrastar A7K1000      | 3      | 5       | 1343  | 1     | 2.60   |
| Hitachi   | Deskstar 7K2000        | 1      | 11      | 1248  | 7     | 2.56   |
| Hitachi   | Ultrastar 7K3000       | 3      | 13      | 911   | 0     | 2.50   |
| Seagate   | Constellation.2        | 1      | 1       | 883   | 0     | 2.42   |
| Seagate   | U5                     | 2      | 2       | 875   | 0     | 2.40   |
| Quantum   | Fireball Plus AS       | 2      | 2       | 845   | 0     | 2.32   |
| WDC       | Red Pro                | 1      | 1       | 782   | 0     | 2.14   |
| HP        | Proliant HardDrive     | 5      | 5       | 1523  | 46    | 2.10   |
| WDC       | Caviar SE16            | 4      | 19      | 963   | 23    | 1.98   |
| Seagate   | Barracuda 7200.8       | 6      | 25      | 1053  | 118   | 1.96   |
| WDC       | Elements / My Passport | 4      | 5       | 711   | 2     | 1.92   |
| WDC       | Scorpio Blue EIDE      | 3      | 5       | 686   | 0     | 1.88   |
| WDC       | Raptor                 | 12     | 15      | 1211  | 11    | 1.88   |
| Hitachi   | Deskstar 7K80          | 6      | 48      | 896   | 8     | 1.83   |
| Samsung   | SpinPoint F4 EG (AF)   | 1      | 10      | 821   | 10    | 1.79   |
| Toshiba   | 3.5" HDD DT01ABA..V    | 1      | 1       | 644   | 0     | 1.77   |
| Toshiba   | 2.5" HDD MK..32GSX     | 1      | 3       | 628   | 0     | 1.72   |
| Hitachi   | Deskstar 7K3000        | 4      | 29      | 738   | 37    | 1.71   |
| Hitachi   | Deskstar 5K3000        | 3      | 11      | 665   | 30    | 1.69   |
| Hitachi   | Deskstar 7K1000        | 2      | 11      | 954   | 14    | 1.67   |
| Hitachi   | Deskstar 5K1000        | 3      | 21      | 738   | 66    | 1.67   |
| WDC       | Caviar SE              | 121    | 338     | 842   | 25    | 1.61   |
| Hitachi   | Deskstar T7K500        | 8      | 35      | 1049  | 38    | 1.61   |
| Hitachi   | Deskstar T7K250        | 5      | 22      | 1053  | 28    | 1.60   |
| Hitachi   | CinemaStar 5K1000      | 2      | 2       | 569   | 0     | 1.56   |
| WDC       | Caviar Black           | 33     | 239     | 742   | 47    | 1.55   |
| Seagate   | Constellation ES.2 ... | 1      | 4       | 553   | 0     | 1.52   |
| Seagate   | Barracuda ES           | 5      | 26      | 976   | 386   | 1.51   |
| MediaMax  | WL1000                 | 1      | 1       | 543   | 0     | 1.49   |
| WDC       | RE3                    | 12     | 31      | 826   | 6     | 1.47   |
| Seagate   | Momentus               | 4      | 6       | 646   | 194   | 1.46   |
| WDC       | RE                     | 12     | 25      | 747   | 79    | 1.45   |
| Toshiba   | 2.5" HDD MK..59GSXP... | 1      | 3       | 506   | 0     | 1.39   |
| Seagate   | Barracuda 5400.1       | 1      | 3       | 763   | 45    | 1.38   |
| Samsung   | SpinPoint F3           | 4      | 128     | 669   | 34    | 1.36   |
| Seagate   | Barracuda ATA V        | 2      | 2       | 1892  | 15    | 1.35   |
| Seagate   | U9                     | 2      | 4       | 485   | 0     | 1.33   |
| Seagate   | Barracuda Green (AF)   | 3      | 81      | 746   | 208   | 1.30   |
| Seagate   | Constellation ES.2     | 1      | 1       | 467   | 0     | 1.28   |
| Samsung   | SpinPoint VL40         | 1      | 1       | 2328  | 4     | 1.28   |
| Seagate   | SpinPoint M7E          | 2      | 9       | 486   | 2     | 1.27   |
| HGST      | Deskstar NAS           | 3      | 5       | 457   | 0     | 1.25   |
| Fujitsu   | MHW BH                 | 9      | 28      | 592   | 3     | 1.25   |
| Seagate   | Barracuda 7200.10      | 27     | 800     | 800   | 289   | 1.25   |
| Hitachi   | Ultrastar A7K2000      | 4      | 10      | 517   | 6     | 1.24   |
| WDC       | Caviar                 | 50     | 103     | 747   | 38    | 1.23   |
| Seagate   | Barracuda 7200.7 an... | 18     | 383     | 802   | 91    | 1.23   |
| WDC       | VelociRaptor           | 20     | 35      | 524   | 2     | 1.22   |
| Seagate   | Constellation ES (S... | 3      | 11      | 1025  | 83    | 1.21   |
| Hitachi   | Deskstar 7K1000.C      | 13     | 288     | 634   | 40    | 1.20   |
| Seagate   | DB35.3                 | 6      | 11      | 559   | 211   | 1.19   |
| Toshiba   | 2.5" HDD MK..58GSX     | 1      | 1       | 431   | 0     | 1.18   |
| Samsung   | SpinPoint T133         | 5      | 15      | 740   | 232   | 1.16   |
| Hitachi   | Deskstar P7K500        | 8      | 106     | 850   | 79    | 1.15   |
| Hitachi   | Travelstar 5K500       | 1      | 1       | 834   | 1     | 1.14   |
| WDC       | Caviar Green           | 106    | 780     | 673   | 69    | 1.14   |
| Seagate   | SV35.5                 | 1      | 2       | 782   | 2     | 1.13   |
| Samsung   | SpinPoint F1 DT        | 11     | 139     | 777   | 208   | 1.11   |
| Samsung   | SpinPoint F2 EG        | 3      | 55      | 760   | 217   | 1.10   |
| Seagate   | Video 3.5 HDD          | 7      | 12      | 448   | 1     | 1.08   |
| Seagate   | Barracuda 7200.9       | 27     | 331     | 732   | 388   | 1.07   |
| Seagate   | Pipeline HD Mini       | 3      | 6       | 962   | 289   | 1.07   |
| Seagate   | Barracuda 7200.7       | 1      | 2       | 1049  | 105   | 1.04   |
| Samsung   | SpinPoint F3 EG        | 3      | 20      | 606   | 205   | 1.04   |
| Hitachi   | Deskstar 7K160         | 6      | 102     | 818   | 117   | 1.02   |
| Seagate   | Barracuda 7200.12      | 14     | 796     | 656   | 162   | 1.01   |
| Maxtor    | MaXLine III (SATA/300) | 1      | 1       | 738   | 1     | 1.01   |
| Seagate   | Constellation CS       | 2      | 6       | 368   | 0     | 1.01   |
| WDC       | Caviar Blue            | 255    | 1712    | 571   | 49    | 1.01   |
| Hitachi   | Deskstar 7K1000.B      | 10     | 63      | 756   | 48    | 1.01   |
| WDC       | Caviar Blue EIDE       | 16     | 72      | 667   | 73    | 1.00   |
| Toshiba   | 2.5" HDD MK..61GSY     | 1      | 1       | 354   | 0     | 0.97   |
| Hitachi   | CinemaStar P7K500      | 1      | 2       | 1010  | 2     | 0.97   |
| WDC       | Green                  | 1      | 1       | 1049  | 2     | 0.96   |
| Seagate   | Barracuda SpinPoint F3 | 2      | 33      | 438   | 3     | 0.90   |
| Seagate   | Constellation ES.3     | 4      | 23      | 370   | 45    | 0.89   |
| Hitachi   | Deskstar 7K500         | 1      | 1       | 1941  | 5     | 0.89   |
| Hitachi   | Travelstar Z7K500      | 1      | 5       | 419   | 1017  | 0.89   |
| HGST      | Ultrastar 7K4000       | 2      | 7       | 313   | 0     | 0.86   |
| Maxtor    | DiamondMax 10 (SATA... | 5      | 19      | 564   | 50    | 0.86   |
| ExcelStor | Jupiter                | 6      | 9       | 710   | 21    | 0.85   |
| Seagate   | Barracuda ATA IV       | 4      | 34      | 648   | 25    | 0.85   |
| Samsung   | SpinPoint P80 SD       | 7      | 147     | 818   | 376   | 0.84   |
| Samsung   | SpinPoint M7E (AF)     | 4      | 67      | 431   | 49    | 0.84   |
| Seagate   | Barracuda              | 1      | 5       | 304   | 0     | 0.83   |
| WDC       | AV-GP                  | 23     | 42      | 415   | 68    | 0.83   |
| Maxtor    | DiamondMax 21          | 14     | 118     | 609   | 401   | 0.82   |
| WDC       | Scorpio                | 1      | 1       | 300   | 0     | 0.82   |
| Seagate   | SpinPoint M9T          | 2      | 12      | 293   | 0     | 0.80   |
| IBM/Hi... | Deskstar 120GXP        | 2      | 5       | 657   | 3     | 0.80   |
| Fujitsu   | MHY BH                 | 4      | 33      | 519   | 228   | 0.80   |
| Seagate   | Barracuda LP           | 4      | 46      | 841   | 456   | 0.79   |
| Fujitsu   | MHW BJ                 | 2      | 2       | 289   | 0     | 0.79   |
| Hitachi   | Travelstar 7K200       | 5      | 9       | 574   | 119   | 0.79   |
| Fujitsu   | MHZ BH                 | 9      | 47      | 495   | 324   | 0.78   |
| WDC       | Scorpio Black          | 38     | 98      | 385   | 74    | 0.77   |
| Fujitsu   | MHX BT                 | 2      | 5       | 619   | 30    | 0.77   |
| Seagate   | SV35                   | 13     | 62      | 327   | 50    | 0.77   |
| Seagate   | Barracuda ES.2         | 4      | 19      | 891   | 405   | 0.75   |
| WDC       | Scorpio Blue           | 177    | 1241    | 399   | 48    | 0.75   |
| Toshiba   | 3.5" HDD E300          | 2      | 2       | 265   | 0     | 0.73   |
| WDC       | Red                    | 11     | 91      | 311   | 12    | 0.72   |
| Fujitsu   | MHV                    | 21     | 47      | 427   | 17    | 0.71   |
| WDC       | RE4                    | 11     | 44      | 446   | 3     | 0.71   |
| Seagate   | Barracuda 7200.14 (AF) | 23     | 1033    | 357   | 96    | 0.71   |
| Seagate   | Desktop HDD.15         | 3      | 10      | 280   | 2     | 0.71   |
| Samsung   | SpinPoint T166         | 7      | 95      | 753   | 436   | 0.71   |
| IBM/Hi... | Deskstar GXP-180       | 4      | 5       | 603   | 7     | 0.70   |
| Hitachi   | Travelstar 5K500.B     | 11     | 246     | 475   | 161   | 0.70   |
| Seagate   | NAS HDD                | 5      | 7       | 253   | 0     | 0.69   |
| Toshiba   | 3.5" MD04ACA Enterp... | 1      | 1       | 253   | 0     | 0.69   |
| HP        | 250GB SATA disk VB0... | 1      | 2       | 252   | 0     | 0.69   |
| Hitachi   | Travelstar 5K1000      | 3      | 13      | 374   | 478   | 0.69   |
| Maxtor    | DiamondMax Plus D740X  | 1      | 2       | 463   | 3     | 0.69   |
| Seagate   | Momentus 7200.2        | 5      | 11      | 620   | 325   | 0.68   |
| Apple     | HGST Travelstar Z5K500 | 1      | 5       | 293   | 3     | 0.68   |
| Hitachi   | Travelstar 7K320       | 9      | 16      | 522   | 655   | 0.68   |
| WDC       | Black                  | 11     | 52      | 254   | 1     | 0.67   |
| Samsung   | SpinPoint PL40         | 1      | 1       | 4382  | 17    | 0.67   |
| Hitachi   | Travelstar 5K750       | 3      | 186     | 395   | 346   | 0.66   |
| Fujitsu   | MHW AT                 | 1      | 1       | 241   | 0     | 0.66   |
| WDC       | Green Mobile           | 2      | 2       | 322   | 14    | 0.66   |
| Seagate   | Maxtor DiamondMax 23   | 4      | 44      | 572   | 226   | 0.65   |
| Seagate   | Pipeline HD 5900.2     | 6      | 25      | 484   | 201   | 0.65   |
| Seagate   | Video 2.5              | 2      | 3       | 236   | 0     | 0.65   |
| Apple     | Hitachi-HGST Travel... | 1      | 8       | 280   | 253   | 0.65   |
| Samsung   | SpinPoint M7           | 3      | 77      | 351   | 59    | 0.64   |
| WDC       | AV                     | 10     | 16      | 625   | 43    | 0.64   |
| Samsung   | SpinPoint M8 (AF)      | 5      | 37      | 401   | 93    | 0.63   |
| Toshiba   | 2.5" HDD               | 13     | 32      | 431   | 50    | 0.62   |
| Samsung   | SpinPoint S250         | 2      | 37      | 824   | 696   | 0.61   |
| Hitachi   | Travelstar 7K100       | 4      | 6       | 325   | 12    | 0.61   |
| Toshiba   | 3.5" HDD DT01ACA       | 4      | 387     | 247   | 27    | 0.60   |
| Seagate   | Momentus 7200.4        | 6      | 96      | 462   | 290   | 0.60   |
| Hitachi   | CinemaStar 7K1000.B    | 2      | 4       | 218   | 0     | 0.60   |
| Hitachi   | Deskstar 7K250         | 6      | 9       | 853   | 410   | 0.58   |
| Seagate   | Constellation ES (S... | 3      | 13      | 747   | 68    | 0.58   |
| Seagate   | UX                     | 1      | 5       | 628   | 16    | 0.58   |
| Seagate   | Barracuda XT           | 2      | 7       | 436   | 229   | 0.57   |
| Samsung   | SpinPoint F4           | 1      | 14      | 336   | 22    | 0.57   |
| Seagate   | Momentus 7200.5        | 4      | 50      | 339   | 71    | 0.57   |
| Fujitsu   | MPA..MPG               | 3      | 3       | 247   | 4     | 0.56   |
| Seagate   | SpinPoint M8 (AF)      | 6      | 500     | 272   | 46    | 0.56   |
| Fujitsu   | MHT                    | 3      | 3       | 398   | 6     | 0.56   |
| Hitachi   | Deskstar 7K1000.D      | 2      | 49      | 512   | 354   | 0.56   |
| Maxtor    | DiamondMax 20          | 5      | 16      | 551   | 300   | 0.56   |
| Hitachi   | Deskstar E7K1000       | 2      | 2       | 1369  | 16    | 0.54   |
| Samsung   | SpinPoint P80          | 17     | 76      | 590   | 162   | 0.54   |
| Toshiba   | N300                   | 1      | 1       | 198   | 0     | 0.54   |
| Samsung   | SpinPoint S166         | 3      | 37      | 799   | 478   | 0.54   |
| Maxtor    | DiamondMax D540X-4K    | 3      | 3       | 582   | 16    | 0.54   |
| Seagate   | Momentus 5400 PSD      | 2      | 3       | 352   | 338   | 0.53   |
| Seagate   | Barracuda ATA III      | 1      | 1       | 194   | 0     | 0.53   |
| WDC       | Protege                | 6      | 9       | 652   | 14    | 0.52   |
| Seagate   | Momentus 5400.2        | 12     | 31      | 406   | 490   | 0.52   |
| Toshiba   | 2.5" HDD MQ02ABD..H    | 1      | 3       | 190   | 0     | 0.52   |
| Samsung   | SpinPoint MP5          | 3      | 7       | 369   | 187   | 0.52   |
| Magnet... | Unknown                | 2      | 2       | 185   | 0     | 0.51   |
| Toshiba   | 2.5" HDD MQ01ABD       | 4      | 278     | 261   | 110   | 0.50   |
| Seagate   | Momentus XT (AF)       | 1      | 8       | 257   | 132   | 0.50   |
| Samsung   | SpinPoint F1 RE        | 1      | 2       | 374   | 51    | 0.49   |
| Hitachi   | Travelstar Z5K500      | 3      | 82      | 281   | 119   | 0.49   |
| HGST      | Travelstar 7K1000      | 3      | 91      | 192   | 13    | 0.48   |
| Maxtor    | DiamondMax 17          | 2      | 9       | 314   | 101   | 0.48   |
| WDC       | Gold                   | 1      | 2       | 175   | 0     | 0.48   |
| Hitachi   | CinemaStar 5K1000.B    | 1      | 1       | 169   | 0     | 0.47   |
| WDC       | Black SSHD             | 1      | 5       | 168   | 0     | 0.46   |
| WDC       | Blue UltraSlim         | 1      | 1       | 166   | 0     | 0.46   |
| Seagate   | Momentus 5400.4        | 3      | 42      | 437   | 358   | 0.45   |
| Seagate   | SpinPoint F4           | 1      | 3       | 163   | 2     | 0.45   |
| Toshiba   | 2.5" HDD MQ01ABC       | 1      | 1       | 160   | 0     | 0.44   |
| Hitachi   | Travelstar 7K750       | 2      | 16      | 265   | 260   | 0.44   |
| Hitachi   | Travelstar Z5K320      | 3      | 133     | 278   | 294   | 0.43   |
| Seagate   | Momentus 5400.3        | 7      | 85      | 454   | 386   | 0.43   |
| HGST      | Travelstar 5K1000      | 4      | 115     | 236   | 249   | 0.43   |
| Hitachi   | Travelstar 5K250       | 8      | 113     | 515   | 126   | 0.43   |
| Samsung   | SpinPoint M            | 2      | 5       | 249   | 4     | 0.43   |
| Seagate   | MobileMax-2            | 1      | 1       | 155   | 0     | 0.43   |
| Samsung   | SpinPoint V80          | 3      | 4       | 597   | 63    | 0.42   |
| Seagate   | Momentus 7200.3        | 4      | 6       | 545   | 40    | 0.42   |
| Toshiba   | 1.8" HDD               | 3      | 5       | 366   | 21    | 0.42   |
| Toshiba   | X300                   | 1      | 6       | 152   | 0     | 0.42   |
| Seagate   | Desktop SSHD           | 5      | 34      | 254   | 148   | 0.41   |
| WDC       | Blue Mobile            | 63     | 581     | 170   | 10    | 0.41   |
| Toshiba   | 2.5" HDD MK..75GSX     | 4      | 45      | 357   | 388   | 0.40   |
| WDC       | Purple                 | 8      | 17      | 190   | 1     | 0.39   |
| Hitachi   | Travelstar 5K320       | 10     | 78      | 480   | 221   | 0.39   |
| Toshiba   | 3.5" MG03ACAxxx(Y) ... | 2      | 9       | 194   | 2     | 0.39   |
| IBM       | Deskstar 40GV & 75G... | 1      | 2       | 1484  | 37    | 0.38   |
| Hitachi   | Travelstar 5K120       | 1      | 3       | 378   | 5     | 0.38   |
| Hitachi   | Travelstar Z7K320      | 1      | 18      | 255   | 455   | 0.38   |
| Toshiba   | 2.5" HDD MK..59GSXP    | 7      | 77      | 330   | 292   | 0.37   |
| Quantum   | Fireball lct15         | 3      | 3       | 226   | 2     | 0.36   |
| Seagate   | Momentus 7200.1        | 2      | 4       | 650   | 43    | 0.36   |
| Hitachi   | Travelstar 5K160       | 8      | 107     | 475   | 47    | 0.36   |
| Seagate   | Momentus 5400.6        | 9      | 529     | 425   | 477   | 0.36   |
| HGST      | Travelstar Z7K500      | 3      | 82      | 169   | 102   | 0.35   |
| Seagate   | Momentus 4200.2        | 3      | 3       | 561   | 687   | 0.35   |
| Toshiba   | 2.5" HDD MQ01ABF       | 2      | 18      | 126   | 0     | 0.35   |
| WDC       | Blue                   | 15     | 68      | 125   | 0     | 0.34   |
| Toshiba   | 1.8" HDD MK..16GSG     | 1      | 3       | 272   | 4     | 0.34   |
| Toshiba   | 3.5" DT01ABA Deskto... | 1      | 1       | 124   | 0     | 0.34   |
| Seagate   | SV35.2                 | 2      | 6       | 662   | 1173  | 0.34   |
| Samsung   | SpinPoint P120         | 5      | 54      | 770   | 595   | 0.34   |
| Seagate   | Laptop SSHD            | 7      | 85      | 202   | 91    | 0.34   |
| Toshiba   | 2.5" HDD MK..55GSX     | 5      | 39      | 377   | 100   | 0.34   |
| Seagate   | U6                     | 3      | 11      | 590   | 52    | 0.34   |
| Fujitsu   | MJA BH                 | 6      | 22      | 369   | 206   | 0.33   |
| Seagate   | Momentus 5400.7 (AF)   | 2      | 9       | 289   | 358   | 0.33   |
| WDC       | ZALMAN                 | 1      | 1       | 1047  | 8     | 0.32   |
| Toshiba   | 2.5" HDD MK..65GSX     | 12     | 126     | 449   | 250   | 0.31   |
| Toshiba   | 2.5" HDD MK..59GSM     | 1      | 11      | 468   | 334   | 0.31   |
| Hitachi   | Travelstar 5K100       | 9      | 34      | 425   | 30    | 0.31   |
| WDC       | Black Mobile           | 23     | 70      | 119   | 2     | 0.31   |
| WDC       | Se                     | 1      | 1       | 112   | 0     | 0.31   |
| Hitachi   | Travelstar 7K500       | 7      | 40      | 367   | 733   | 0.31   |
| Toshiba   | 2.5" HDD MK..37GSX     | 2      | 28      | 501   | 42    | 0.31   |
| Toshiba   | 2.5" HDD MQ01ACF       | 2      | 7       | 135   | 149   | 0.31   |
| Seagate   | LD25 Series            | 2      | 2       | 111   | 0     | 0.30   |
| Apple     | Seagate Barracuda      | 1      | 1       | 109   | 0     | 0.30   |
| Seagate   | Momentus 5400.7        | 1      | 3       | 281   | 338   | 0.30   |
| Toshiba   | 2.5" HDD MK..46GSX     | 4      | 25      | 475   | 51    | 0.30   |
| Toshiba   | 2.5" HDD MK..76GSX     | 6      | 13      | 136   | 139   | 0.30   |
| Seagate   | Momentus Thin          | 3      | 100     | 302   | 532   | 0.30   |
| HGST      | Ultrastar 7K6000       | 2      | 2       | 107   | 0     | 0.29   |
| Toshiba   | 2.5" HDD MQ01ABF       | 1      | 149     | 120   | 82    | 0.28   |
| HGST      | Travelstar Z5K500      | 5      | 251     | 184   | 244   | 0.28   |
| Toshiba   | 2.5" HDD L200          | 3      | 8       | 95    | 0     | 0.26   |
| Toshiba   | 2.5" HDD MK..34GSX     | 2      | 10      | 381   | 216   | 0.26   |
| Seagate   | Laptop Thin SSHD       | 1      | 1       | 94    | 0     | 0.26   |
| Toshiba   | 2.5" HDD MK..37GSX     | 1      | 11      | 414   | 206   | 0.25   |
| Samsung   | SpinPoint N2           | 1      | 1       | 89    | 0     | 0.25   |
| IBM/Hi... | Deskstar 60GXP         | 2      | 3       | 1032  | 106   | 0.24   |
| Toshiba   | 2.5" HDD MK..63GSX     | 2      | 9       | 565   | 20    | 0.22   |
| WDC       | Blue SSHD              | 1      | 1       | 80    | 0     | 0.22   |
| Toshiba   | 2.5" HDD MK..52GSX     | 5      | 35      | 450   | 151   | 0.22   |
| Seagate   | Momentus XT            | 1      | 5       | 406   | 417   | 0.22   |
| Toshiba   | 1.8" HDD MK..33GSG     | 2      | 3       | 634   | 316   | 0.21   |
| Toshiba   | 2.5" HDD MK..61GSY[N]  | 4      | 13      | 153   | 143   | 0.19   |
| Seagate   | Barracuda 7200.11      | 11     | 218     | 773   | 345   | 0.18   |
| Hitachi   | Travelstar 4K40        | 1      | 5       | 483   | 20    | 0.17   |
| HGST      | Travelstar Z5K1000     | 2      | 15      | 77    | 68    | 0.17   |
| Hitachi   | Travelstar 80GN        | 4      | 10      | 341   | 47    | 0.17   |
| Seagate   | Momentus 5400.5        | 4      | 51      | 398   | 217   | 0.16   |
| Toshiba   | 2.5" HDD MK..56GSY     | 5      | 9       | 101   | 128   | 0.16   |
| Seagate   | Ultra Mobile HDD       | 2      | 2       | 57    | 0     | 0.16   |
| Seagate   | Laptop Thin HDD        | 7      | 406     | 176   | 427   | 0.16   |
| Toshiba   | 2.5" HDD MK..59GSM     | 1      | 16      | 325   | 988   | 0.15   |
| China     | Unknown                | 2      | 2       | 279   | 512   | 0.15   |
| IBM/Hi... | Travelstar 60GH and... | 1      | 1       | 52    | 0     | 0.14   |
| Toshiba   | P300                   | 4      | 79      | 56    | 7     | 0.14   |
| Toshiba   | 1.8" HDD               | 2      | 5       | 312   | 91    | 0.14   |
| Samsung   | SpinPoint M40/60/80    | 6      | 10      | 451   | 102   | 0.14   |
| Toshiba   | 2.5" HDD L200 Slim     | 1      | 1       | 47    | 0     | 0.13   |
| Toshiba   | 2.5" HDD MK..46GSX     | 1      | 7       | 418   | 25    | 0.12   |
| WDC       | Scorpio EIDE           | 5      | 5       | 229   | 81    | 0.12   |
| Toshiba   | 1.8" HDD MK..29GSG     | 2      | 3       | 407   | 753   | 0.12   |
| Hitachi   | Travelstar 4K120       | 2      | 3       | 707   | 24    | 0.11   |
| Seagate   | FireCuda 3.5           | 2      | 6       | 37    | 0     | 0.10   |
| Seagate   | Barracuda 3.5          | 6      | 51      | 37    | 1     | 0.10   |
| HGST      | Travelstar 5K1500      | 1      | 2       | 541   | 14    | 0.10   |
| Seagate   | FreePlay               | 1      | 4       | 140   | 646   | 0.09   |
| Hitachi   | Travelstar DK23XX/D... | 2      | 2       | 624   | 243   | 0.08   |
| Samsung   | SpinPoint V40+         | 2      | 3       | 1003  | 159   | 0.08   |
| Seagate   | U8                     | 1      | 1       | 754   | 24    | 0.08   |
| Samsung   | SpinPoint M5           | 5      | 55      | 323   | 302   | 0.08   |
| Toshiba   | 2.5" HDD MQ01ABD       | 1      | 1       | 27    | 0     | 0.08   |
| MARSHAL   | Unknown                | 1      | 1       | 279   | 9     | 0.08   |
| Seagate   | Barracuda 2.5 5400     | 4      | 19      | 26    | 0     | 0.07   |
| HGST      | Travelstar Z5K1        | 1      | 2       | 26    | 0     | 0.07   |
| MediaMax  | WL250                  | 2      | 3       | 43    | 3     | 0.07   |
| HGST      | Travelstar Z5K500.B    | 1      | 8       | 24    | 0     | 0.07   |
| Maxtor    | DiamondMax 22          | 4      | 21      | 916   | 347   | 0.07   |
| Toshiba   | 2.5" HDD               | 1      | 1       | 23    | 0     | 0.06   |
| Seagate   | Surveillance           | 1      | 1       | 23    | 0     | 0.06   |
| Samsung   | SpinPoint M6           | 3      | 9       | 306   | 350   | 0.06   |
| Seagate   | DB35.2                 | 1      | 1       | 21    | 0     | 0.06   |
| Samsung   | SpinPoint F1 EG        | 1      | 1       | 385   | 17    | 0.06   |
| Seagate   | Mobile HDD             | 2      | 20      | 22    | 4     | 0.05   |
| Toshiba   | 2.5" HDD H200          | 2      | 3       | 18    | 0     | 0.05   |
| Seagate   | Constellation.2 (SATA) | 2      | 3       | 17    | 0     | 0.05   |
| Seagate   | FireCuda 2.5           | 2      | 4       | 16    | 0     | 0.05   |
| Toshiba   | 2.5" HDD MK..65GSX     | 2      | 3       | 368   | 31    | 0.04   |
| Maxtor    | Fireball 3             | 4      | 7       | 53    | 4     | 0.04   |
| Maxtor    | DiamondMax 10 (ATA/... | 14     | 23      | 24    | 84    | 0.04   |
| Maxtor    | MaXLine III (ATA/13... | 3      | 3       | 17    | 12    | 0.04   |
| Seagate   | U10                    | 1      | 1       | 380   | 27    | 0.04   |
| Apple     | HGST Travelstar 5K750  | 2      | 2       | 265   | 77    | 0.04   |
| Seagate   | Pipeline HD 5900.1     | 2      | 4       | 444   | 58    | 0.03   |
| Hitachi   | Travelstar 5K80        | 3      | 3       | 214   | 230   | 0.03   |
| Toshiba   | 2.5" HDD MK..76GSX     | 4      | 43      | 30    | 205   | 0.03   |
| Maxtor    | DiamondMax Plus 8      | 4      | 13      | 26    | 15    | 0.02   |
| Toshiba   | 2.5" HDD MK..59GSX     | 1      | 1       | 8     | 0     | 0.02   |
| HGST      | Ultrastar 7K2          | 1      | 2       | 6     | 0     | 0.02   |
| Seagate   | SV35.3                 | 1      | 1       | 45    | 7     | 0.02   |
| Samsung   | SpinPoint V60          | 1      | 3       | 733   | 124   | 0.02   |
| Toshiba   | 2.5" HDD MQ02ABF..H    | 1      | 1       | 5     | 0     | 0.01   |
| Hitachi   | Travelstar E7K100      | 1      | 1       | 4     | 0     | 0.01   |
| Toshiba   | 3.5" MG04ACA Enterp... | 1      | 2       | 4     | 0     | 0.01   |
| Maxtor    | DiamondMax 16          | 1      | 1       | 25    | 5     | 0.01   |
| Fujitsu   | MHZ BJ                 | 1      | 1       | 4     | 0     | 0.01   |
| Seagate   | SkyHawk                | 2      | 2       | 3     | 0     | 0.01   |
| Maxtor    | DiamondMax Plus 9      | 11     | 54      | 32    | 141   | 0.01   |
| Toshiba   | 2.5" HDD MQ02ABF       | 1      | 1       | 1     | 0     | 0.01   |
| Hitachi   | Ultrastar 5K3000       | 1      | 1       | 1045  | 595   | 0.00   |
| Maxtor    | Fireball 541DX         | 1      | 6       | 22    | 76    | 0.00   |
| Maxtor    | DiamondMax D540X-4D    | 2      | 3       | 24    | 229   | 0.00   |
| HGST      | Travelstar Z7K500.B    | 1      | 1       | 0     | 0     | 0.00   |
| CLOVER    | Hightech Utania        | 2      | 2       | 0     | 0     | 0.00   |
| HGST      | Unknown                | 1      | 1       | 8     | 10    | 0.00   |
| MediaMax  | WL400                  | 1      | 1       | 0     | 0     | 0.00   |
| Seagate   | IronWolf               | 1      | 1       | 0     | 0     | 0.00   |
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
| HP          | 6      | 7       | 1160  | 33    | 1.70   |
| Quantum     | 5      | 5       | 474   | 2     | 1.14   |
| WDC         | 1070   | 5745    | 517   | 43    | 0.95   |
| ExcelStor   | 6      | 9       | 710   | 21    | 0.85   |
| Hitachi     | 200    | 1977    | 562   | 161   | 0.84   |
| Samsung     | 114    | 1114    | 659   | 245   | 0.82   |
| Fujitsu     | 61     | 192     | 474   | 147   | 0.77   |
| Seagate     | 370    | 6331    | 519   | 226   | 0.75   |
| IBM/Hitachi | 9      | 14      | 675   | 26    | 0.60   |
| Apple       | 5      | 16      | 272   | 137   | 0.56   |
| Magnetic... | 2      | 2       | 185   | 0     | 0.51   |
| Maxtor      | 75     | 299     | 402   | 242   | 0.45   |
| Toshiba     | 136    | 1542    | 268   | 118   | 0.41   |
| IBM         | 1      | 2       | 1484  | 37    | 0.38   |
| HGST        | 30     | 584     | 191   | 172   | 0.36   |
| MediaMax    | 4      | 5       | 134   | 2     | 0.34   |
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
| Toshiba   | THNS064GG2BNAA     | 64 GB  | 2       | 1215  | 0     | 3.33   |
| OCZ       | VERTEX PLUS R2     | 61 GB  | 1       | 1202  | 0     | 3.29   |
| Mushkin   | MKNSSDCR120GB      | 120 GB | 1       | 1164  | 0     | 3.19   |
| Samsung   | MZ7WD240HCFV-00003 | 240 GB | 1       | 1154  | 0     | 3.16   |
| OCZ       | VERTEX2 3.5        | 120 GB | 1       | 1040  | 0     | 2.85   |
| Kingston  | SVP100S296G        | 96 GB  | 1       | 918   | 0     | 2.52   |
| Samsung   | SSD PM800 2.5"     | 256 GB | 1       | 871   | 0     | 2.39   |
| Corsair   | Force GS           | 180 GB | 2       | 854   | 0     | 2.34   |
| OCZ       | VERTEX2            | 40 GB  | 1       | 851   | 0     | 2.33   |
| Corsair   | Force GT           | 180 GB | 1       | 838   | 0     | 2.30   |
| OCZ       | AGILITY4           | 128 GB | 3       | 830   | 0     | 2.27   |
| OCZ       | DENRSTE251M45-0... | 100 GB | 1       | 801   | 0     | 2.20   |
| OCZ       | VERTEX PLUS R2     | 247 GB | 1       | 797   | 0     | 2.18   |
| OCZ       | VERTEX2            | 60 GB  | 3       | 788   | 0     | 2.16   |
| Micron    | MTFDDAT128MAM-1J2  | 128 GB | 1       | 783   | 0     | 2.15   |
| Corsair   | Force GS           | 90 GB  | 1       | 776   | 0     | 2.13   |
| Kingston  | SVP200S37A480G     | 480 GB | 1       | 765   | 0     | 2.10   |
| Toshiba   | THNSNJ120PCSZ      | 120 GB | 2       | 758   | 0     | 2.08   |
| Corsair   | Force 3 SSD        | 240 GB | 2       | 737   | 0     | 2.02   |
| SanDisk   | SD5SE2128G1002E    | 128 GB | 2       | 729   | 0     | 2.00   |
| ADATA     | SSD S510           | 120 GB | 3       | 727   | 0     | 1.99   |
| Samsung   | SSD 840 EVO        | 750 GB | 1       | 714   | 0     | 1.96   |
| OCZ       | NOCTI              | 60 GB  | 1       | 704   | 0     | 1.93   |
| Corsair   | Force 3 SSD        | 60 GB  | 8       | 695   | 0     | 1.91   |
| Kingston  | SVP200S390G        | 90 GB  | 1       | 686   | 0     | 1.88   |
| Intel     | SSDSC2CT080A4      | 80 GB  | 2       | 675   | 0     | 1.85   |
| Kingston  | SNVP325S2128GB     | 128 GB | 1       | 674   | 0     | 1.85   |
| Toshiba   | THNSNH060GMCT      | 60 GB  | 1       | 666   | 0     | 1.82   |
| OCZ       | AGILITY3           | 120 GB | 19      | 756   | 88    | 1.82   |
| Samsung   | SSD 840 EVO 120... | 120 GB | 1       | 641   | 0     | 1.76   |
| Samsung   | SSD 850 PRO        | 1 TB   | 1       | 626   | 0     | 1.72   |
| Kingston  | SVP200S37A240G     | 240 GB | 1       | 623   | 0     | 1.71   |
| Intel     | SSDSA2M040G2GC     | 40 GB  | 2       | 1007  | 3     | 1.69   |
| Samsung   | MZMPA128HMFU-00000 | 128 GB | 1       | 616   | 0     | 1.69   |
| Kingston  | SKC300S37A480G     | 480 GB | 1       | 613   | 0     | 1.68   |
| Crucial   | M4-CT064M4SSD2     | 64 GB  | 7       | 600   | 0     | 1.65   |
| Samsung   | SSD 830 Series     | 512 GB | 1       | 599   | 0     | 1.64   |
| Corsair   | Force 3 SSD        | 120 GB | 8       | 715   | 89    | 1.61   |
| OCZ       | DENCSTE351M16-0... | 240 GB | 1       | 585   | 0     | 1.60   |
| Plextor   | PX-512M7VC         | 512 GB | 1       | 575   | 0     | 1.58   |
| OCZ       | VERTEX2            | 120 GB | 2       | 568   | 0     | 1.56   |
| OCZ       | AGILITY4           | 64 GB  | 1       | 567   | 0     | 1.56   |
| OCZ       | REVODRIVE3         | 60 GB  | 4       | 564   | 0     | 1.55   |
| Crucial   | M4-CT128M4SSD2     | 128 GB | 14      | 587   | 73    | 1.54   |
| Samsung   | MZMPC128HBFU-000L1 | 128 GB | 1       | 559   | 0     | 1.53   |
| Kingston  | SVP200S360G        | 60 GB  | 4       | 550   | 0     | 1.51   |
| Toshiba   | THNSNH128GCST      | 128 GB | 1       | 549   | 0     | 1.51   |
| SanDisk   | SD6SB1M256G1002    | 256 GB | 1       | 548   | 0     | 1.50   |
| Apple     | SSD SM1024F        | 1 TB   | 1       | 545   | 0     | 1.49   |
| Samsung   | MZ7PC128HAFU-000   | 128 GB | 1       | 545   | 0     | 1.49   |
| Intel     | SSDSA2CW120G3      | 120 GB | 4       | 544   | 0     | 1.49   |
| OCZ       | VERTEX2 3.5        | 115 GB | 1       | 541   | 0     | 1.48   |
| Toshiba   | THNSFC256GAMJ      | 256 GB | 1       | 539   | 0     | 1.48   |
| OCZ       | D2RSTK251E14-0400  | 400 GB | 1       | 502   | 0     | 1.38   |
| Samsung   | SSD 830 Series     | 64 GB  | 3       | 497   | 0     | 1.36   |
| Samsung   | SSD 840 EVO        | 1 TB   | 2       | 496   | 0     | 1.36   |
| Transcend | TS128GSSD320       | 128 GB | 1       | 493   | 0     | 1.35   |
| Crucial   | CT500MX200SSD1     | 500 GB | 1       | 489   | 0     | 1.34   |
| SPCC      | SSD110             | 60 GB  | 4       | 482   | 0     | 1.32   |
| OCZ       | VERTEX3            | 60 GB  | 24      | 554   | 2     | 1.32   |
| Intel     | SSDSC2BW240A3L     | 240 GB | 1       | 480   | 0     | 1.32   |
| Toshiba   | THNSNF128GMCS      | 128 GB | 2       | 471   | 0     | 1.29   |
| Verbatim  | SATA-III SSD       | 128 GB | 1       | 470   | 0     | 1.29   |
| Plextor   | PX-64M2S           | 64 GB  | 2       | 467   | 0     | 1.28   |
| SPCC      | SSD110             | 120 GB | 3       | 466   | 0     | 1.28   |
| OCZ       | AGILITY3           | 60 GB  | 16      | 499   | 1     | 1.25   |
| Intel     | SSDSC2MH120A2      | 120 GB | 1       | 453   | 0     | 1.24   |
| Corsair   | Performance Pro    | 128 GB | 1       | 450   | 0     | 1.23   |
| Plextor   | PX-128M2S          | 128 GB | 1       | 447   | 0     | 1.23   |
| Foxline   | FLDMMS128G         | 128 GB | 1       | 443   | 0     | 1.22   |
| Corsair   | Force GT           | 60 GB  | 5       | 690   | 7     | 1.21   |
| OCZ       | VECTOR             | 128 GB | 2       | 439   | 0     | 1.20   |
| Samsung   | MZNTE128HMGR-000SO | 128 GB | 1       | 436   | 0     | 1.20   |
| OCZ       | REVODRIVE X2       | 25 GB  | 4       | 435   | 0     | 1.19   |
| Crucial   | M4-CT128M4SSD1     | 128 GB | 3       | 434   | 0     | 1.19   |
| Corsair   | Force GT           | 120 GB | 6       | 506   | 1     | 1.19   |
| Kingston  | SV200S3128G        | 128 GB | 6       | 432   | 0     | 1.19   |
| ADATA     | SSD S511           | 120 GB | 1       | 430   | 0     | 1.18   |
| Smartbuy  | SSD                | 60 GB  | 4       | 421   | 0     | 1.16   |
| Corsair   | CSSD-F60GB2        | 60 GB  | 1       | 420   | 0     | 1.15   |
| Kingston  | SKC380S360G        | 60 GB  | 1       | 420   | 0     | 1.15   |
| OCZ       | SOLID3             | 120 GB | 1       | 418   | 0     | 1.15   |
| Apple     | SSD TS128C         | 121 GB | 1       | 416   | 0     | 1.14   |
| SanDisk   | SD6SB2M128G1022I   | 128 GB | 1       | 412   | 0     | 1.13   |
| Samsung   | MMCRE28G5MXP-0VBH1 | 128 GB | 1       | 410   | 0     | 1.12   |
| Samsung   | MZRPA128HMCD-000SO | 64 GB  | 4       | 405   | 0     | 1.11   |
| Toshiba   | THNSNH060GBST      | 60 GB  | 2       | 400   | 0     | 1.10   |
| Crucial   | M4-CT256M4SSD2     | 256 GB | 2       | 399   | 0     | 1.09   |
| SanDisk   | SDSSDXP240G        | 240 GB | 2       | 398   | 0     | 1.09   |
| OCZ       | AGILITY3           | 64 GB  | 2       | 397   | 0     | 1.09   |
| OCZ       | VERTEX3 MI         | 120 GB | 13      | 476   | 74    | 1.07   |
| Kingston  | SNV425S264GB       | 64 GB  | 1       | 386   | 0     | 1.06   |
| Samsung   | MZ7TD256HAFV-000L9 | 256 GB | 1       | 385   | 0     | 1.06   |
| China     | SSD                | 60 GB  | 2       | 439   | 1     | 1.05   |
| Samsung   | MMCRE28GFMXP-MVB   | 128 GB | 2       | 383   | 0     | 1.05   |
| Samsung   | MZ7TE128HMGR-00000 | 128 GB | 2       | 382   | 0     | 1.05   |
| OCZ       | VERTEX3            | 120 GB | 36      | 538   | 48    | 1.05   |
| OCZ       | VERTEX4            | 128 GB | 49      | 403   | 1     | 1.05   |
| KingSpec  | SPK-SF12-M120      | 120 GB | 1       | 373   | 0     | 1.02   |
| Samsung   | MZMPC032HBCD-00000 | 32 GB  | 5       | 372   | 0     | 1.02   |
| Samsung   | MZ7TD256HAFV-000L7 | 256 GB | 2       | 370   | 0     | 1.02   |
| Samsung   | SSD 850 EVO mSATA  | 120 GB | 2       | 369   | 0     | 1.01   |
| Toshiba   | THNSNC128GCSJ      | 128 GB | 1       | 367   | 0     | 1.01   |
| Samsung   | MZMPC032HBCD-000H1 | 32 GB  | 4       | 367   | 0     | 1.01   |
| Corsair   | Force GS           | 240 GB | 1       | 365   | 0     | 1.00   |
| Samsung   | SSD 840 Series     | 500 GB | 1       | 365   | 0     | 1.00   |
| OCZ       | VERTEX3            | 90 GB  | 11      | 680   | 7     | 0.99   |
| Kingston  | SVP200S37A60G      | 60 GB  | 5       | 360   | 0     | 0.99   |
| KingShare | 230120SSD          | 128 GB | 1       | 358   | 0     | 0.98   |
| SanDisk   | SDSSDH2128G        | 128 GB | 1       | 356   | 0     | 0.98   |
| KingSpec  | KSD-SA25.5-016MJ   | 16 GB  | 1       | 353   | 0     | 0.97   |
| Toshiba   | THNSNX024GMNT      | 24 GB  | 2       | 346   | 0     | 0.95   |
| Samsung   | SSD 840 EVO        | 250 GB | 21      | 348   | 49    | 0.94   |
| OCZ       | VERTEX3            | 240 GB | 7       | 399   | 6     | 0.94   |
| Toshiba   | THNS064GE4BBDC     | 64 GB  | 1       | 338   | 0     | 0.93   |
| KingFast  | SSD                | 32 GB  | 1       | 332   | 0     | 0.91   |
| Plextor   | PX-128M3           | 128 GB | 2       | 331   | 0     | 0.91   |
| Crucial   | C300-CTFDDAC128MAG | 128 GB | 3       | 330   | 0     | 0.91   |
| China     | SATA SSD           | 20 GB  | 6       | 382   | 1     | 0.90   |
| Kingston  | SV200S364G         | 64 GB  | 1       | 327   | 0     | 0.90   |
| Samsung   | SSD 840 PRO Series | 512 GB | 2       | 326   | 0     | 0.90   |
| Kingston  | SH100S3240G        | 240 GB | 1       | 1628  | 4     | 0.89   |
| Kingston  | SMS100S264G        | 64 GB  | 1       | 323   | 0     | 0.89   |
| OCZ       | VERTEX3 LP         | 60 GB  | 1       | 320   | 0     | 0.88   |
| Kingston  | SH103S3120G        | 120 GB | 31      | 318   | 0     | 0.87   |
| Intel     | SSDSC2CT240A4      | 240 GB | 4       | 317   | 0     | 0.87   |
| SanDisk   | SD5SG2256G1052E    | 256 GB | 1       | 313   | 0     | 0.86   |
| OCZ       | AGILITY3           | 128 GB | 2       | 313   | 0     | 0.86   |
| Samsung   | SSD 830 Series     | 128 GB | 6       | 309   | 0     | 0.85   |
| OCZ       | VERTEX4            | 256 GB | 9       | 334   | 1     | 0.85   |
| Crucial   | C300-CTFDDAC064MAG | 64 GB  | 1       | 307   | 0     | 0.84   |
| Kingston  | SVP200S3240G       | 240 GB | 2       | 307   | 0     | 0.84   |
| Toshiba   | THNSNC128GBSJ      | 128 GB | 1       | 303   | 0     | 0.83   |
| Samsung   | SSD PM830 2.5" 7mm | 128 GB | 1       | 302   | 0     | 0.83   |
| OCZ       | AGILITY2           | 60 GB  | 2       | 302   | 0     | 0.83   |
| SanDisk   | SDSSDX120GG25      | 120 GB | 4       | 301   | 0     | 0.83   |
| OCZ       | SOLID3             | 60 GB  | 2       | 558   | 7     | 0.82   |
| Mushkin   | MKNSSDAT240GB-DX   | 240 GB | 1       | 299   | 0     | 0.82   |
| Samsung   | SSD PM830 mSATA    | 32 GB  | 4       | 299   | 0     | 0.82   |
| China     | SATA SSD           | 128 GB | 2       | 298   | 0     | 0.82   |
| SanDisk   | X300 2.5 7MM       | 256 GB | 1       | 297   | 0     | 0.81   |
| SanDisk   | SDSSDHII480G       | 480 GB | 3       | 295   | 0     | 0.81   |
| Kingston  | SKC300S37A60G      | 60 GB  | 10      | 327   | 4     | 0.81   |
| Ramaxel   | RDM-II XM020C024G  | 24 GB  | 2       | 295   | 0     | 0.81   |
| Kingston  | SNVP325S2256GB     | 256 GB | 1       | 293   | 0     | 0.80   |
| Samsung   | MZMPA064HMDR-00000 | 64 GB  | 1       | 290   | 0     | 0.79   |
| OCZ       | AGILITY3           | 90 GB  | 3       | 476   | 1     | 0.79   |
| OCZ       | CACHE-SYNAPSE      | 32 GB  | 1       | 286   | 0     | 0.79   |
| Corsair   | Force 3 SSD        | 90 GB  | 4       | 284   | 0     | 0.78   |
| OCZ       | AGILITY3           | 240 GB | 2       | 284   | 0     | 0.78   |
| Samsung   | MZMPA024HMCD-000L1 | 24 GB  | 1       | 283   | 0     | 0.78   |
| OCZ       | VERTEX PLUS R2     | 123 GB | 2       | 281   | 0     | 0.77   |
| Apacer    | AST680S            | 128 GB | 1       | 280   | 0     | 0.77   |
| OCZ       | VERTEX             | 64 GB  | 1       | 280   | 0     | 0.77   |
| Kingston  | SMS100S232G        | 32 GB  | 1       | 279   | 0     | 0.76   |
| Intel     | SSDSC2BW180A4      | 180 GB | 5       | 275   | 0     | 0.76   |
| Samsung   | SSD 840 EVO        | 120 GB | 33      | 269   | 0     | 0.74   |
| Goodram   | C40                | 120 GB | 3       | 266   | 0     | 0.73   |
| SanDisk   | SDSSDHP064G        | 64 GB  | 6       | 266   | 0     | 0.73   |
| SanDisk   | iSSD P4            | 8 GB   | 3       | 350   | 1     | 0.73   |
| Samsung   | SSD 840 PRO Series | 128 GB | 10      | 265   | 0     | 0.73   |
| Plextor   | PX-256M5Pro        | 256 GB | 3       | 262   | 0     | 0.72   |
| Apacer    | A7202              | 64 GB  | 1       | 262   | 0     | 0.72   |
| Samsung   | SSD PM830 mSATA    | 128 GB | 1       | 261   | 0     | 0.72   |
| Intel     | SSDSA2M080G2GC     | 80 GB  | 4       | 587   | 4     | 0.71   |
| Goodram   | C50                | 60 GB  | 2       | 258   | 0     | 0.71   |
| Samsung   | MMCQE28GFMUP-MVA   | 128 GB | 2       | 298   | 13    | 0.71   |
| Samsung   | SSD PM810 TM       | 64 GB  | 1       | 257   | 0     | 0.70   |
| SanDisk   | SD6SB1M128G        | 128 GB | 1       | 256   | 0     | 0.70   |
| Samsung   | SSD 840 Series     | 120 GB | 9       | 270   | 1     | 0.69   |
| ADATA     | SX900              | 64 GB  | 3       | 500   | 339   | 0.68   |
| Intel     | SSDSA2M080G2HP     | 80 GB  | 1       | 245   | 0     | 0.67   |
| Intel     | SSDSA1MH080G1GN    | 80 GB  | 1       | 244   | 0     | 0.67   |
| Intel     | SSDSA2BW160G3L     | 160 GB | 1       | 239   | 0     | 0.66   |
| SanDisk   | SDSSDHP128G        | 128 GB | 16      | 239   | 0     | 0.66   |
| OCZ       | VECTOR150          | 120 GB | 7       | 239   | 0     | 0.66   |
| ADATA     | SP900              | 128 GB | 19      | 281   | 18    | 0.66   |
| HP        | VK0240GDJXU        | 240 GB | 1       | 238   | 0     | 0.65   |
| Kingston  | SV300S37A60G       | 60 GB  | 83      | 241   | 1     | 0.65   |
| Samsung   | SSD 830 Series     | 256 GB | 2       | 238   | 0     | 0.65   |
| Crucial   | M4-CT128M4SSD3     | 128 GB | 1       | 238   | 0     | 0.65   |
| Kingston  | SV200S3256G        | 256 GB | 2       | 237   | 0     | 0.65   |
| Samsung   | SSD 840 PRO Series | 256 GB | 15      | 234   | 0     | 0.64   |
| Samsung   | SSD 850 PRO        | 128 GB | 9       | 233   | 0     | 0.64   |
| SanDisk   | SSD i100           | 16 GB  | 5       | 233   | 0     | 0.64   |
| Corsair   | Force GS           | 128 GB | 13      | 232   | 0     | 0.64   |
| Plextor   | PX-64M3            | 64 GB  | 3       | 408   | 346   | 0.64   |
| Kingston  | SM2280S3120G       | 120 GB | 3       | 230   | 0     | 0.63   |
| Kingston  | SV100S264G         | 64 GB  | 6       | 391   | 4     | 0.63   |
| Corsair   | Force 3 SSD        | 480 GB | 1       | 226   | 0     | 0.62   |
| OCZ       | OCTANE S2          | 64 GB  | 1       | 224   | 0     | 0.61   |
| Plextor   | PX-128M7VC         | 128 GB | 5       | 222   | 0     | 0.61   |
| TEAM      | L3 SSD             | 120 GB | 2       | 221   | 0     | 0.61   |
| Samsung   | MMDPE56GFDXP-MVB   | 256 GB | 1       | 218   | 0     | 0.60   |
| Crucial   | CT256MX100SSD1     | 256 GB | 8       | 215   | 0     | 0.59   |
| Samsung   | SSD 840 EVO        | 500 GB | 9       | 214   | 0     | 0.59   |
| Samsung   | SSD 840 Series     | 250 GB | 6       | 214   | 0     | 0.59   |
| Kingston  | SVP200S37A120G     | 120 GB | 6       | 283   | 179   | 0.58   |
| Toshiba   | THNSNJ128GCST      | 128 GB | 3       | 208   | 0     | 0.57   |
| OCZ       | VERTEX2            | 50 GB  | 2       | 309   | 320   | 0.57   |
| Toshiba   | THNSNH128GBST      | 128 GB | 2       | 207   | 0     | 0.57   |
| Intel     | SSDSC2BP240G4      | 240 GB | 1       | 206   | 0     | 0.56   |
| ADATA     | SP900              | 256 GB | 6       | 333   | 2     | 0.56   |
| SPCC      | SSD B29            | 32 GB  | 1       | 204   | 0     | 0.56   |
| Kingston  | SKC300S37A120G     | 120 GB | 10      | 201   | 0     | 0.55   |
| ADATA     | SX900              | 128 GB | 6       | 448   | 512   | 0.55   |
| Intel     | SSDSC2BA200G4      | 200 GB | 5       | 200   | 0     | 0.55   |
| SanDisk   | SD5SF2128G1014E    | 128 GB | 2       | 200   | 0     | 0.55   |
| ADATA     | SP600              | 256 GB | 1       | 198   | 0     | 0.55   |
| OCZ       | VERTEX PLUS        | 60 GB  | 1       | 396   | 1     | 0.54   |
| OCZ       | TRION100           | 240 GB | 6       | 197   | 0     | 0.54   |
| Toshiba   | THNSNJ128GCSU      | 128 GB | 2       | 195   | 0     | 0.54   |
| Samsung   | MZMPC032HBCD-000L1 | 32 GB  | 1       | 195   | 0     | 0.53   |
| OCZ       | VERTEX4            | 512 GB | 1       | 573   | 2     | 0.52   |
| Kingston  | SV100S2128G        | 128 GB | 2       | 359   | 2     | 0.52   |
| Samsung   | SG9MSM6D024GPM00   | 22 GB  | 1       | 188   | 0     | 0.52   |
| Transcend | TS128GSSD720       | 128 GB | 2       | 187   | 0     | 0.51   |
| Toshiba   | THNSNH128GMCT      | 128 GB | 2       | 186   | 0     | 0.51   |
| Smartbuy  | mSata              | 64 GB  | 1       | 186   | 0     | 0.51   |
| Crucial   | M4-CT512M4SSD2     | 512 GB | 1       | 184   | 0     | 0.51   |
| Transcend | TS128GMSA740       | 128 GB | 1       | 180   | 0     | 0.50   |
| Crucial   | CT960M500SSD1      | 960 GB | 4       | 428   | 517   | 0.49   |
| Toshiba   | TR150              | 120 GB | 3       | 178   | 0     | 0.49   |
| Kingston  | SV100S232G         | 32 GB  | 2       | 178   | 0     | 0.49   |
| Toshiba   | Q300 Pro           | 256 GB | 1       | 178   | 0     | 0.49   |
| Toshiba   | VX500              | 256 GB | 1       | 178   | 0     | 0.49   |
| ADATA     | SSD S599           | 60 GB  | 1       | 178   | 0     | 0.49   |
| Samsung   | SSD PM800 Serie... | 256 GB | 1       | 178   | 0     | 0.49   |
| Kingston  | SVP200S37A90G      | 90 GB  | 2       | 176   | 0     | 0.48   |
| Samsung   | MZNLF128HCHP-00004 | 128 GB | 2       | 176   | 0     | 0.48   |
| PNY       | CS900 120GB SSD    | 120 GB | 1       | 175   | 0     | 0.48   |
| Toshiba   | THNSNH060GCST      | 60 GB  | 1       | 175   | 0     | 0.48   |
| Kingston  | SV300S37A120G      | 120 GB | 218     | 195   | 22    | 0.48   |
| Intel     | SSDSC2CT180A4      | 180 GB | 5       | 174   | 0     | 0.48   |
| ADATA     | SP900              | 64 GB  | 12      | 234   | 2     | 0.47   |
| Crucial   | CT240M500SSD1      | 240 GB | 9       | 256   | 243   | 0.47   |
| Plextor   | PX-128M7VG         | 128 GB | 1       | 171   | 0     | 0.47   |
| OCZ       | VERTEX460          | 120 GB | 1       | 169   | 0     | 0.46   |
| SanDisk   | SDSSDP256G         | 256 GB | 2       | 169   | 0     | 0.46   |
| ADATA     | SP600              | 32 GB  | 3       | 168   | 0     | 0.46   |
| Toshiba   | Q300               | 120 GB | 1       | 168   | 0     | 0.46   |
| Intel     | SSDSA2CT040G3      | 40 GB  | 3       | 167   | 0     | 0.46   |
| Kingston  | SM2280S3G2120G     | 120 GB | 2       | 162   | 0     | 0.44   |
| Intel     | SSDSCMMW180A3L     | 180 GB | 1       | 160   | 0     | 0.44   |
| Samsung   | SSD 850 EVO        | 120 GB | 29      | 159   | 0     | 0.44   |
| SPCC      | SSD                | 60 GB  | 49      | 167   | 42    | 0.42   |
| Plextor   | PX-256S2C          | 256 GB | 2       | 153   | 0     | 0.42   |
| SPCC      | SSD162             | 120 GB | 5       | 412   | 407   | 0.42   |
| Samsung   | MZNLN128HCGR-000L2 | 128 GB | 1       | 153   | 0     | 0.42   |
| Samsung   | MZNTY128HDHP-000L1 | 128 GB | 1       | 153   | 0     | 0.42   |
| Intel     | SSDSA2CW080G3      | 80 GB  | 4       | 152   | 0     | 0.42   |
| Samsung   | SSD 840 EVO 500... | 500 GB | 1       | 152   | 0     | 0.42   |
| SanDisk   | SDSSDHII120G       | 120 GB | 13      | 150   | 0     | 0.41   |
| Intel     | SSDSC2BW180A3L     | 180 GB | 1       | 149   | 0     | 0.41   |
| Smartbuy  | SSD                | 120 GB | 36      | 149   | 0     | 0.41   |
| Kingston  | SHSS37A120G        | 120 GB | 6       | 148   | 0     | 0.41   |
| Intel     | SSDMCEAC180B3      | 180 GB | 2       | 148   | 0     | 0.41   |
| Toshiba   | THNSNJ256GCSU      | 256 GB | 2       | 144   | 0     | 0.40   |
| Intel     | SSDSC2BB120G4      | 120 GB | 1       | 143   | 0     | 0.39   |
| QUMO      | SSD                | 60 GB  | 1       | 143   | 0     | 0.39   |
| SanDisk   | SDSSDP128G         | 126 GB | 18      | 143   | 1     | 0.39   |
| KingSpec  | KSD-SA25.5-064MJ   | 64 GB  | 1       | 141   | 0     | 0.39   |
| ADATA     | SX930              | 120 GB | 1       | 138   | 0     | 0.38   |
| China     | SATA SSD           | 64 GB  | 2       | 138   | 0     | 0.38   |
| Samsung   | SSD 850 PRO        | 256 GB | 24      | 136   | 0     | 0.37   |
| Intel     | SSDSC2BB080G4      | 80 GB  | 1       | 135   | 0     | 0.37   |
| SanDisk   | SDSSDHP256G        | 256 GB | 5       | 135   | 0     | 0.37   |
| Corsair   | Force GT           | 90 GB  | 2       | 361   | 1     | 0.37   |
| Kingston  | SMS200S330G        | 30 GB  | 1       | 132   | 0     | 0.36   |
| SanDisk   | SDSSDP064G         | 63 GB  | 4       | 172   | 256   | 0.36   |
| OCZ       | AGILITY4           | 256 GB | 4       | 142   | 61    | 0.36   |
| Samsung   | MZMTD128HAFV-000L1 | 128 GB | 6       | 137   | 24    | 0.35   |
| Transcend | TS64GMSA370        | 64 GB  | 1       | 127   | 0     | 0.35   |
| OCZ       | VECTOR150          | 240 GB | 2       | 127   | 0     | 0.35   |
| Crucial   | CT512MX100SSD1     | 512 GB | 5       | 127   | 0     | 0.35   |
| Kingston  | SH103S3240G        | 240 GB | 9       | 306   | 237   | 0.35   |
| Chiprex   | S10T3120GB         | 120 GB | 1       | 126   | 0     | 0.35   |
| Transcend | TS128GSSD340       | 128 GB | 3       | 126   | 0     | 0.35   |
| KingFast  | SSD                | 29 GB  | 1       | 125   | 0     | 0.34   |
| Smartbuy  | SSD                | 60 GB  | 17      | 123   | 0     | 0.34   |
| Corsair   | Neutron GTX SSD    | 240 GB | 3       | 165   | 98    | 0.33   |
| Samsung   | SSD PM830 2.5" 7mm | 256 GB | 1       | 121   | 0     | 0.33   |
| OCZ       | ARC100             | 120 GB | 7       | 120   | 0     | 0.33   |
| ADATA     | SP310              | 128 GB | 1       | 120   | 0     | 0.33   |
| Kingston  | RBU-SNS8152S312... | 128 GB | 1       | 120   | 0     | 0.33   |
| SanDisk   | SDSSDHII240G       | 240 GB | 6       | 120   | 0     | 0.33   |
| ADATA     | SSD SX900 512GB... | 512 GB | 1       | 120   | 0     | 0.33   |
| OCZ       | VERTEX4            | 64 GB  | 5       | 121   | 1     | 0.33   |
| Plextor   | PX-128M5S          | 128 GB | 34      | 118   | 0     | 0.32   |
| OCZ       | TRION100           | 120 GB | 2       | 121   | 1     | 0.32   |
| Samsung   | SSD 850 EVO M.2    | 500 GB | 5       | 117   | 0     | 0.32   |
| ADATA     | XM13               | 32 GB  | 1       | 116   | 0     | 0.32   |
| Crucial   | CT1024MX200SSD1    | 1 TB   | 1       | 116   | 0     | 0.32   |
| Corsair   | Force LE SSD       | 120 GB | 2       | 114   | 0     | 0.31   |
| OCZ       | D2CSTK181M11-0180  | 180 GB | 3       | 114   | 0     | 0.31   |
| OCZ       | VERTEX2            | 90 GB  | 1       | 113   | 0     | 0.31   |
| Samsung   | SSD 840 EVO 250... | 250 GB | 2       | 112   | 0     | 0.31   |
| ADATA     | SSD S511           | 60 GB  | 3       | 441   | 679   | 0.31   |
| Samsung   | SSD 850 EVO        | 500 GB | 36      | 111   | 0     | 0.31   |
| OCZ       | VERTEX3            | 128 GB | 1       | 111   | 0     | 0.31   |
| SanDisk   | SD6SB1M128G1002    | 128 GB | 1       | 110   | 0     | 0.30   |
| Samsung   | MZNTD128HAGM-00000 | 128 GB | 1       | 110   | 0     | 0.30   |
| ADATA     | SP920SS            | 128 GB | 4       | 306   | 4     | 0.30   |
| Samsung   | MZNLF128HCHP-000H1 | 128 GB | 1       | 109   | 0     | 0.30   |
| SanDisk   | Ultra II           | 480 GB | 2       | 109   | 0     | 0.30   |
| Kingston  | SV300S37A240G      | 240 GB | 35      | 109   | 1     | 0.30   |
| Corsair   | Force LS SSD       | 120 GB | 7       | 166   | 433   | 0.30   |
| OCZ       | ARC100             | 240 GB | 3       | 108   | 0     | 0.30   |
| Crucial   | CT250MX200SSD1     | 250 GB | 3       | 107   | 0     | 0.30   |
| Samsung   | SSD 850 EVO        | 250 GB | 62      | 107   | 0     | 0.30   |
| Goodram   | CX100              | 120 GB | 5       | 115   | 2     | 0.29   |
| SanDisk   | SSD U100           | 16 GB  | 1       | 105   | 0     | 0.29   |
| Samsung   | MZ7PD256HCGM-000H7 | 256 GB | 1       | 104   | 0     | 0.29   |
| SanDisk   | SSD i100           | 24 GB  | 10      | 110   | 4     | 0.28   |
| ADATA     | SP600              | 64 GB  | 7       | 113   | 2     | 0.28   |
| Plextor   | PX-128M5M          | 128 GB | 7       | 103   | 0     | 0.28   |
| Transcend | TS120GSSD25D-M     | 128 GB | 1       | 309   | 2     | 0.28   |
| Toshiba   | THNSNH256GBST      | 256 GB | 1       | 102   | 0     | 0.28   |
| Smartbuy  | mSata              | 256 GB | 1       | 102   | 0     | 0.28   |
| KingFast  | SSD                | 30 GB  | 1       | 102   | 0     | 0.28   |
| TEAM      | L3 EVO SSD         | 120 GB | 1       | 101   | 0     | 0.28   |
| Samsung   | SSD 850 EVO M.2    | 250 GB | 7       | 100   | 0     | 0.28   |
| Toshiba   | THNSNJ128G8NY      | 128 GB | 1       | 98    | 0     | 0.27   |
| SPCC      | SSD A20            | 60 GB  | 1       | 97    | 0     | 0.27   |
| Lite-On   | CV3-8D128          | 128 GB | 1       | 97    | 0     | 0.27   |
| SanDisk   | SD7SB3Q128G1002    | 128 GB | 1       | 387   | 3     | 0.27   |
| Crucial   | CT128M550SSD3      | 128 GB | 2       | 126   | 8     | 0.27   |
| Crucial   | CT120M500SSD1      | 120 GB | 8       | 327   | 9     | 0.26   |
| Plextor   | PX-256M5S          | 256 GB | 8       | 95    | 0     | 0.26   |
| SPCC      | SSD170             | 120 GB | 3       | 245   | 341   | 0.26   |
| SanDisk   | SSD U100           | 256 GB | 1       | 94    | 0     | 0.26   |
| Patriot   | Blast              | 120 GB | 3       | 94    | 0     | 0.26   |
| Kingston  | SUV300S37A120G     | 120 GB | 15      | 93    | 0     | 0.26   |
| Transcend | TS256GMTS800       | 256 GB | 1       | 93    | 0     | 0.26   |
| Crucial   | CT525MX300SSD1     | 525 GB | 2       | 93    | 0     | 0.26   |
| SPCC      | SSD                | 120 GB | 71      | 139   | 145   | 0.26   |
| Lite-On   | PH2-CJ120          | 120 GB | 1       | 92    | 0     | 0.25   |
| OCZ       | VERTEX460A         | 120 GB | 4       | 92    | 0     | 0.25   |
| Samsung   | SSD 850 PRO        | 512 GB | 6       | 224   | 173   | 0.25   |
| OCZ       | ONYX               | 32 GB  | 1       | 89    | 0     | 0.24   |
| WDC       | WDS250G1B0A-00H9H0 | 250 GB | 4       | 88    | 0     | 0.24   |
| SanDisk   | SDSSDXPS240G       | 240 GB | 3       | 99    | 345   | 0.24   |
| Kingston  | RBU-SNS8151S396GG  | 96 GB  | 1       | 88    | 0     | 0.24   |
| Patriot   | Blast              | 240 GB | 3       | 87    | 0     | 0.24   |
| Kingston  | SKC380S3120G       | 120 GB | 1       | 86    | 0     | 0.24   |
| Plextor   | PX-256M3           | 256 GB | 1       | 256   | 2     | 0.23   |
| ADATA     | SP900NS38          | 128 GB | 2       | 85    | 0     | 0.23   |
| Plextor   | PX-128M5Pro        | 128 GB | 39      | 85    | 0     | 0.23   |
| Patriot   | Blaze              | 240 GB | 1       | 85    | 0     | 0.23   |
| PNY       | CS1311 240GB SSD   | 240 GB | 1       | 84    | 0     | 0.23   |
| Transcend | TS256GSSD320       | 256 GB | 2       | 84    | 0     | 0.23   |
| Apple     | SSD SM0256G        | 251 GB | 1       | 83    | 0     | 0.23   |
| SPCC      | SSD                | 55 GB  | 6       | 174   | 339   | 0.23   |
| Samsung   | SSD 750 EVO        | 120 GB | 18      | 83    | 0     | 0.23   |
| Samsung   | SSD 750 EVO        | 250 GB | 13      | 82    | 0     | 0.23   |
| OCZ       | VECTOR180          | 120 GB | 2       | 81    | 0     | 0.22   |
| Intel     | SSDSA2M160G2LE     | 160 GB | 1       | 1872  | 22    | 0.22   |
| Samsung   | MZMPC128HBFU-000   | 128 GB | 1       | 81    | 0     | 0.22   |
| Corsair   | Force LS SSD       | 480 GB | 1       | 80    | 0     | 0.22   |
| Seagate   | ST120HM000-1G5142  | 120 GB | 1       | 79    | 0     | 0.22   |
| Toshiba   | Q300 Pro           | 128 GB | 1       | 79    | 0     | 0.22   |
| Intel     | SSDSC2BW120A4      | 120 GB | 20      | 84    | 1     | 0.21   |
| SanDisk   | SSD i100           | 8 GB   | 2       | 77    | 0     | 0.21   |
| China     | 120GB SSD          | 120 GB | 16      | 77    | 0     | 0.21   |
| SK hynix  | SC311 SATA         | 512 GB | 1       | 77    | 0     | 0.21   |
| Transcend | TS256GSSD340       | 256 GB | 2       | 76    | 0     | 0.21   |
| OCZ       | VECTOR180          | 240 GB | 1       | 76    | 0     | 0.21   |
| Samsung   | SSD 650            | 120 GB | 3       | 75    | 0     | 0.21   |
| Patriot   | Flare              | 60 GB  | 1       | 75    | 0     | 0.21   |
| Corsair   | Neutron SSD        | 64 GB  | 2       | 174   | 6     | 0.21   |
| Intel     | SSDSC2BW240A4      | 240 GB | 7       | 74    | 0     | 0.21   |
| Kingmax   | SSD                | 120 GB | 13      | 138   | 394   | 0.20   |
| China     | 64GB SSD           | 64 GB  | 6       | 72    | 0     | 0.20   |
| Lite-On   | L8H-256V2G-HP      | 256 GB | 1       | 71    | 0     | 0.20   |
| Kingston  | SS200S330G         | 30 GB  | 1       | 70    | 0     | 0.19   |
| Patriot   | Spark              | 128 GB | 3       | 70    | 0     | 0.19   |
| SanDisk   | SSD U110           | 16 GB  | 8       | 70    | 0     | 0.19   |
| Fordisk   | S860 256G 6Gbps    | 256 GB | 1       | 69    | 0     | 0.19   |
| SanDisk   | PLUS               | 480 GB | 2       | 68    | 0     | 0.19   |
| ADATA     | S596               | 128 GB | 1       | 68    | 0     | 0.19   |
| Plextor   | PX-128M6M          | 128 GB | 4       | 67    | 0     | 0.19   |
| Toshiba   | TR150              | 240 GB | 7       | 67    | 0     | 0.19   |
| PNY       | SSD2SC240G1LC70... | 240 GB | 1       | 67    | 0     | 0.18   |
| ADATA     | SP900              | 512 GB | 2       | 66    | 0     | 0.18   |
| OCZ       | VERTEX460A         | 240 GB | 2       | 66    | 0     | 0.18   |
| Crucial   | CT250BX100SSD1     | 250 GB | 2       | 65    | 0     | 0.18   |
| Kingston  | SVP200S3120G       | 120 GB | 3       | 405   | 665   | 0.18   |
| Intel     | SSDSC2BW480A4      | 480 GB | 1       | 65    | 0     | 0.18   |
| Kingston  | SHFS37A240G        | 240 GB | 11      | 94    | 462   | 0.18   |
| Intel     | SSDSA2M160G2GC     | 160 GB | 1       | 578   | 8     | 0.18   |
| Apple     | SSD SM0128G        | 121 GB | 1       | 64    | 0     | 0.18   |
| Kingston  | SKC400S37256G      | 256 GB | 1       | 64    | 0     | 0.18   |
| Intel     | SSDSC2BW080A4      | 80 GB  | 1       | 63    | 0     | 0.17   |
| Kingston  | SUV400S37120G      | 120 GB | 23      | 87    | 15    | 0.17   |
| Crucial   | CT128M550SSD1      | 128 GB | 3       | 88    | 30    | 0.17   |
| Transcend | TS128GSSD370       | 128 GB | 6       | 62    | 0     | 0.17   |
| Plextor   | PX-128M6S          | 128 GB | 21      | 67    | 53    | 0.17   |
| Kingston  | SUV300S37A240G     | 240 GB | 5       | 60    | 0     | 0.17   |
| PHISON    | 128GB PS3109-S9    | 128 GB | 1       | 121   | 1     | 0.17   |
| Samsung   | MZNLN256HCHP-00000 | 256 GB | 1       | 60    | 0     | 0.17   |
| Crucial   | CT256M550SSD1      | 256 GB | 3       | 237   | 6     | 0.17   |
| Samsung   | SSD 850 EVO        | 1 TB   | 7       | 60    | 0     | 0.16   |
| China     | SATA SSD           | 120 GB | 2       | 59    | 0     | 0.16   |
| TEKET     | SA18-032M-4F       | 32 GB  | 2       | 59    | 0     | 0.16   |
| OCZ       | VERTEX2            | 180 GB | 1       | 58    | 0     | 0.16   |
| Kingston  | SM2280S3G2240G     | 240 GB | 1       | 57    | 0     | 0.16   |
| SanDisk   | SSD U100           | 128 GB | 5       | 148   | 39    | 0.16   |
| Intel     | SSDSC2BW120H6      | 120 GB | 6       | 56    | 0     | 0.15   |
| OCZ       | VERTEX460          | 240 GB | 1       | 56    | 0     | 0.15   |
| Radeon    | R7                 | 120 GB | 1       | 56    | 0     | 0.15   |
| SanDisk   | SSD U100           | 24 GB  | 14      | 66    | 20    | 0.15   |
| Transcend | TS64GSSD340        | 64 GB  | 1       | 54    | 0     | 0.15   |
| PNY       | CS1311 120GB SSD   | 120 GB | 2       | 54    | 0     | 0.15   |
| Goodram   | SSD                | 240 GB | 2       | 54    | 0     | 0.15   |
| Samsung   | MZMTD128HAFV-000H1 | 128 GB | 1       | 53    | 0     | 0.15   |
| Samsung   | MZMPC128HBFU-000MV | 128 GB | 1       | 53    | 0     | 0.15   |
| WDC       | WDS250G1B0B-00AS40 | 250 GB | 1       | 52    | 0     | 0.14   |
| Kingston  | SUV400S37240G      | 240 GB | 22      | 58    | 48    | 0.14   |
| Intel     | SSDSC2BB240G4      | 240 GB | 1       | 52    | 0     | 0.14   |
| Plextor   | PX-256M6S          | 256 GB | 7       | 56    | 145   | 0.14   |
| Apple     | SSD TS256C         | 251 GB | 1       | 51    | 0     | 0.14   |
| Lite-On   | LMT-19nmBGA-128G   | 128 GB | 1       | 51    | 0     | 0.14   |
| Samsung   | MZMTD128HAFV-000   | 128 GB | 3       | 51    | 0     | 0.14   |
| Kingston  | SMS200S360G        | 60 GB  | 3       | 67    | 1     | 0.14   |
| Patriot   | Blaze              | 60 GB  | 3       | 50    | 0     | 0.14   |
| Samsung   | SSD PB22-CS3 FD... | 256 GB | 1       | 50    | 0     | 0.14   |
| Samsung   | MZ7LF128HCHP-00004 | 128 GB | 1       | 50    | 0     | 0.14   |
| Corsair   | Neutron GTX SSD    | 480 GB | 1       | 49    | 0     | 0.14   |
| Kingston  | SA400S37240G       | 240 GB | 2       | 52    | 1     | 0.14   |
| Samsung   | MZ7TE256HMHP-000L7 | 256 GB | 1       | 49    | 0     | 0.13   |
| Corsair   | Force LS SSD       | 60 GB  | 12      | 150   | 250   | 0.13   |
| SanDisk   | SD8SB8U256G1122    | 256 GB | 1       | 48    | 0     | 0.13   |
| SK hynix  | HFS128G32MND-3212A | 128 GB | 1       | 48    | 0     | 0.13   |
| Micron    | 1100_MTFDDAV256TBN | 256 GB | 1       | 47    | 0     | 0.13   |
| Kingston  | SKC400S37512G      | 512 GB | 1       | 46    | 0     | 0.13   |
| SanDisk   | SD5SF2032G1010E    | 32 GB  | 1       | 45    | 0     | 0.13   |
| Kingston  | SHSS37A240G        | 240 GB | 9       | 45    | 0     | 0.12   |
| Crucial   | CT240BX300SSD1     | 240 GB | 1       | 45    | 0     | 0.12   |
| Kingston  | RBU-SC152S37128GG2 | 128 GB | 1       | 45    | 0     | 0.12   |
| KingDian  | S180               | 60 GB  | 8       | 44    | 0     | 0.12   |
| PRETEC    | G2000 SSD          | 29 GB  | 1       | 44    | 0     | 0.12   |
| China     | SSD128G            | 128 GB | 1       | 42    | 0     | 0.12   |
| ADATA     | SP600              | 128 GB | 2       | 42    | 0     | 0.12   |
| China     | 240GB SSD          | 240 GB | 1       | 41    | 0     | 0.11   |
| SPCC      | SSD                | 240 GB | 19      | 94    | 465   | 0.11   |
| ADATA     | SP610              | 128 GB | 1       | 39    | 0     | 0.11   |
| Samsung   | SSD 850 EVO mSATA  | 250 GB | 2       | 37    | 0     | 0.10   |
| SanDisk   | SD6SB1M128G1022I   | 128 GB | 2       | 37    | 0     | 0.10   |
| SanDisk   | SD8SN8U512G1002    | 512 GB | 1       | 37    | 0     | 0.10   |
| Goodram   | SSD                | 120 GB | 7       | 36    | 0     | 0.10   |
| Micron    | MTFDDAK512MAY-1... | 512 GB | 1       | 624   | 16    | 0.10   |
| Intel     | SSDSA1M080G2HP     | 80 GB  | 1       | 476   | 12    | 0.10   |
| SanDisk   | SDSSDA240G         | 240 GB | 21      | 36    | 0     | 0.10   |
| China     | SSD                | 126 GB | 1       | 34    | 0     | 0.10   |
| Plextor   | PX-256M5M          | 256 GB | 1       | 34    | 0     | 0.09   |
| ZOTAC     | SATA SSD           | 120 GB | 2       | 34    | 0     | 0.09   |
| Kingmax   | SSD                | 60 GB  | 17      | 234   | 553   | 0.09   |
| SanDisk   | SSD U110           | 63 GB  | 1       | 34    | 0     | 0.09   |
| AMD       | R5S240GBSF         | 240 GB | 1       | 33    | 0     | 0.09   |
| Intel     | SSDSA1MH080G1HP    | 80 GB  | 1       | 33    | 0     | 0.09   |
| SanDisk   | SD6SB1M-032G-1006  | 32 GB  | 1       | 33    | 0     | 0.09   |
| KingDian  | S400               | 120 GB | 2       | 32    | 0     | 0.09   |
| OCZ       | VERTEX4            | 79 GB  | 1       | 129   | 3     | 0.09   |
| SanDisk   | SDSSDXP120G        | 120 GB | 1       | 32    | 0     | 0.09   |
| Micron    | C400-MTFDDAK256MAM | 256 GB | 1       | 32    | 0     | 0.09   |
| Toshiba   | THNSNB062GMCJ      | 62 GB  | 1       | 32    | 0     | 0.09   |
| Kingston  | SMS200S3120G       | 120 GB | 3       | 42    | 254   | 0.09   |
| SPCC      | SSD                | 64 GB  | 2       | 31    | 0     | 0.09   |
| Smartbuy  | SSD                | 240 GB | 9       | 51    | 1     | 0.09   |
| OCZ       | TRION150           | 480 GB | 1       | 31    | 0     | 0.09   |
| KingSpec  | KSD-SA25.7-016MJ   | 16 GB  | 2       | 30    | 0     | 0.08   |
| Toshiba   | VT180              | 480 GB | 1       | 30    | 0     | 0.08   |
| SanDisk   | SSD i100           | 32 GB  | 2       | 30    | 0     | 0.08   |
| ADATA     | SP900NS34          | 128 GB | 1       | 30    | 0     | 0.08   |
| Micron    | MTFDDAK256MAM-1K12 | 256 GB | 3       | 66    | 1010  | 0.08   |
| Micron    | MTFDDAK128MAM-1J1  | 128 GB | 1       | 29    | 0     | 0.08   |
| SanDisk   | SDSA5DK-016G-1006  | 16 GB  | 1       | 29    | 0     | 0.08   |
| KingPower | 1108 SSD           | 64 GB  | 1       | 29    | 0     | 0.08   |
| Apple     | SSD SD0128F        | 121 GB | 1       | 29    | 0     | 0.08   |
| Samsung   | MZ7TY256HDHP-00000 | 256 GB | 1       | 29    | 0     | 0.08   |
| Transcend | TS120GSSD220S      | 120 GB | 3       | 29    | 0     | 0.08   |
| ADATA     | SU800NS38          | 256 GB | 1       | 29    | 0     | 0.08   |
| Intel     | SSDSA1M160G2HP     | 160 GB | 3       | 90    | 5     | 0.08   |
| Samsung   | SSD Thin uSATA ... | 128 GB | 1       | 378   | 12    | 0.08   |
| SanDisk   | SDSSDA480G         | 480 GB | 1       | 28    | 0     | 0.08   |
| Kingston  | SH103S3480G        | 480 GB | 1       | 28    | 0     | 0.08   |
| Kingston  | SHFS37A120G        | 120 GB | 39      | 51    | 418   | 0.08   |
| LDLC      | SSD                | 120 GB | 2       | 27    | 0     | 0.08   |
| KingDian  | S280-240GB         | 240 GB | 5       | 27    | 0     | 0.08   |
| Samsung   | MZ7TY128HDHP-000L1 | 128 GB | 2       | 27    | 0     | 0.08   |
| AMD       | R3S60GBSM          | 60 GB  | 1       | 27    | 0     | 0.08   |
| KingSpec  | CHA-M2B7-M256      | 256 GB | 2       | 27    | 0     | 0.07   |
| Crucial   | CT275MX300SSD1     | 275 GB | 7       | 26    | 0     | 0.07   |
| Transcend | TS64GSSD720        | 64 GB  | 1       | 26    | 0     | 0.07   |
| Kingston  | SV300S37A480G      | 480 GB | 5       | 38    | 202   | 0.07   |
| Kingston  | SHSS37A480G        | 480 GB | 3       | 26    | 0     | 0.07   |
| Toshiba   | THNSNH128G8NT      | 128 GB | 1       | 25    | 0     | 0.07   |
| Plextor   | PX-512M5Pro        | 512 GB | 1       | 25    | 0     | 0.07   |
| Plextor   | PX-128M6Pro        | 128 GB | 7       | 25    | 0     | 0.07   |
| Intel     | SSDSC2BW180A3H     | 180 GB | 1       | 25    | 0     | 0.07   |
| Patriot   | Spark              | 256 GB | 1       | 25    | 0     | 0.07   |
| Smartbuy  | mSata              | 128 GB | 1       | 25    | 0     | 0.07   |
| Intenso   | SSD                | 128 GB | 2       | 48    | 1     | 0.07   |
| WDC       | WDS240G1G0A-00SS50 | 240 GB | 6       | 25    | 0     | 0.07   |
| Samsung   | SSD 750 EVO        | 500 GB | 2       | 24    | 0     | 0.07   |
| Corsair   | CSSD-V32GB2        | 32 GB  | 1       | 99    | 3     | 0.07   |
| SK hynix  | HFS128G39TND-N210A | 128 GB | 3       | 24    | 0     | 0.07   |
| Intel     | SSDSA2BW160G3H     | 160 GB | 2       | 98    | 4     | 0.06   |
| Intel     | SSDSCKKW240H6      | 240 GB | 1       | 46    | 1     | 0.06   |
| GLOWAY    | FER240GS3-S7       | 240 GB | 1       | 23    | 0     | 0.06   |
| Toshiba   | THNSNS060GBSP      | 60 GB  | 1       | 22    | 0     | 0.06   |
| Plextor   | PX-128M6V          | 128 GB | 1       | 22    | 0     | 0.06   |
| Kingston  | SKC300S37A180G     | 180 GB | 2       | 166   | 1025  | 0.06   |
| KingDian  | S280               | 240 GB | 3       | 22    | 0     | 0.06   |
| Samsung   | MZNLF128HCHP-00000 | 128 GB | 1       | 22    | 0     | 0.06   |
| Transcend | TS128GSSD370S      | 128 GB | 10      | 21    | 0     | 0.06   |
| Plextor   | PX-256M6M          | 256 GB | 3       | 29    | 1     | 0.06   |
| Plextor   | PX-AG128M6e        | 128 GB | 2       | 21    | 0     | 0.06   |
| AMD       | R3SL120G           | 120 GB | 17      | 21    | 0     | 0.06   |
| KingSpec  | MT-128             | 128 GB | 3       | 20    | 0     | 0.06   |
| Transcend | TS32GSSD370S       | 32 GB  | 3       | 20    | 0     | 0.06   |
| SanDisk   | SDSSDH240GG25      | 240 GB | 1       | 20    | 0     | 0.06   |
| AMD       | R3SL240G           | 240 GB | 4       | 44    | 1     | 0.06   |
| SanDisk   | SSD PLUS 240 GB    | 240 GB | 2       | 20    | 0     | 0.06   |
| Samsung   | MZYLF128HCHP-000L2 | 128 GB | 1       | 20    | 0     | 0.05   |
| Netac     | SSD 120G           | 120 GB | 1       | 19    | 0     | 0.05   |
| Intel     | SSDSCKGF256A5 SATA | 256 GB | 1       | 19    | 0     | 0.05   |
| Crucial   | CT480BX200SSD1     | 480 GB | 1       | 19    | 0     | 0.05   |
| SK hynix  | SC308 SATA         | 256 GB | 1       | 18    | 0     | 0.05   |
| SK hynix  | SC210 2.5 7MM      | 128 GB | 1       | 18    | 0     | 0.05   |
| ADATA     | SP610              | 256 GB | 1       | 18    | 0     | 0.05   |
| Hyperdisk | SDOM               | 16 GB  | 1       | 18    | 0     | 0.05   |
| OCZ       | TRION150           | 240 GB | 1       | 18    | 0     | 0.05   |
| Apacer    | AS350              | 240 GB | 1       | 18    | 0     | 0.05   |
| Apacer    | AS510S             | 64 GB  | 1       | 17    | 0     | 0.05   |
| WDC       | WDS240G1G0B-00RC30 | 240 GB | 2       | 17    | 0     | 0.05   |
| KingFast  | SSD                | 120 GB | 2       | 17    | 0     | 0.05   |
| China     | RTMMB256VBV4KFY    | 256 GB | 1       | 17    | 0     | 0.05   |
| Kingrich  | SSD 120G           | 120 GB | 1       | 17    | 0     | 0.05   |
| SanDisk   | SSD U100           | 64 GB  | 3       | 16    | 0     | 0.05   |
| ADATA     | SX950              | 240 GB | 1       | 16    | 0     | 0.05   |
| Toshiba   | A100               | 240 GB | 1       | 16    | 0     | 0.05   |
| SanDisk   | SDSSDA120G         | 120 GB | 18      | 16    | 0     | 0.05   |
| SanDisk   | SD6SB1M-128G-1006  | 128 GB | 1       | 16    | 0     | 0.05   |
| Intel     | SSDSA2M080G2GN     | 80 GB  | 1       | 245   | 14    | 0.04   |
| KingFast  | SSD                | 128 GB | 6       | 16    | 0     | 0.04   |
| Transcend | TS64GSSD25S-M      | 64 GB  | 1       | 16    | 0     | 0.04   |
| WDC       | WDS500G1B0A-00H9H0 | 500 GB | 2       | 16    | 0     | 0.04   |
| Apple     | SSD SM256E         | 251 GB | 1       | 15    | 0     | 0.04   |
| Plextor   | PX-256M6Pro        | 256 GB | 1       | 15    | 0     | 0.04   |
| SanDisk   | SD8SBAT128G1122    | 128 GB | 1       | 15    | 0     | 0.04   |
| FASTDISK  | FASTDISK120G       | 120 GB | 1       | 15    | 0     | 0.04   |
| GLOWAY    | FER120GS3-S7       | 120 GB | 2       | 15    | 0     | 0.04   |
| FORESEE   | 240GB SSD          | 240 GB | 1       | 15    | 0     | 0.04   |
| Kingston  | SA400S37120G       | 120 GB | 7       | 15    | 0     | 0.04   |
| SPCC      | SSD                | 480 GB | 1       | 15    | 0     | 0.04   |
| Samsung   | SSD 850 EVO mSATA  | 500 GB | 3       | 14    | 0     | 0.04   |
| FASTDISK  | SSD 60G            | 60 GB  | 1       | 14    | 0     | 0.04   |
| Crucial   | CT240BX200SSD1     | 240 GB | 3       | 14    | 0     | 0.04   |
| Seagate   | ST480FP0021        | 480 GB | 1       | 14    | 0     | 0.04   |
| Transcend | TS256GSSD370S      | 256 GB | 1       | 14    | 0     | 0.04   |
| Micron    | M600_MTFDDAK1T0MBF | 1 TB   | 1       | 13    | 0     | 0.04   |
| Samsung   | MZNTY128HDHP-00000 | 128 GB | 1       | 13    | 0     | 0.04   |
| OCZ       | VECTOR180          | 960 GB | 1       | 13    | 0     | 0.04   |
| Intel     | SSDSC2BB240G7      | 240 GB | 1       | 13    | 0     | 0.04   |
| Samsung   | MZYTY128HDHP-000L2 | 128 GB | 1       | 13    | 0     | 0.04   |
| China     | 128GB SSD          | 128 GB | 2       | 13    | 0     | 0.04   |
| Transcend | TS512GMSA370       | 512 GB | 1       | 12    | 0     | 0.03   |
| Toshiba   | TL100              | 240 GB | 1       | 12    | 0     | 0.03   |
| WDC       | WDS120G1G0A-00SS50 | 120 GB | 8       | 11    | 0     | 0.03   |
| China     | SSD                | 120 GB | 2       | 11    | 0     | 0.03   |
| ADATA     | IM2S3138E-128GM-B  | 128 GB | 1       | 11    | 0     | 0.03   |
| Crucial   | CT250MX500SSD1     | 250 GB | 1       | 11    | 0     | 0.03   |
| Crucial   | V4-CT128V4SSD2     | 128 GB | 1       | 11    | 0     | 0.03   |
| Crucial   | CT2050MX300SSD1    | 2 TB   | 1       | 33    | 2     | 0.03   |
| AMD       | R5SL240G           | 240 GB | 1       | 10    | 0     | 0.03   |
| ADATA     | SX300              | 128 GB | 1       | 10    | 0     | 0.03   |
| KingSpec  | T-60               | 60 GB  | 2       | 10    | 0     | 0.03   |
| Plextor   | PX-AG256M6e        | 256 GB | 1       | 10    | 0     | 0.03   |
| Intel     | SSDSA2CW160G3      | 160 GB | 1       | 10    | 0     | 0.03   |
| Samsung   | MZ7TE512HMHP-000L2 | 512 GB | 1       | 10    | 0     | 0.03   |
| TEAM      | L5 LITE SSD        | 120 GB | 1       | 10    | 0     | 0.03   |
| LDLC      | SSD                | 128 GB | 2       | 10    | 0     | 0.03   |
| ADATA     | SU800              | 128 GB | 10      | 13    | 9     | 0.03   |
| Crucial   | CT480M500SSD1      | 480 GB | 1       | 166   | 16    | 0.03   |
| Crucial   | CT240M500SSD3      | 240 GB | 2       | 166   | 16    | 0.03   |
| ADATA     | SP550              | 120 GB | 13      | 9     | 0     | 0.03   |
| SPCC      | SSD162             | 240 GB | 1       | 203   | 20    | 0.03   |
| Lite-On   | CV1-8B128          | 128 GB | 2       | 9     | 0     | 0.03   |
| SK hynix  | SC210 mSATA        | 128 GB | 1       | 38    | 3     | 0.03   |
| Faspeed   | H5-120G PLUS       | 120 GB | 1       | 9     | 0     | 0.03   |
| Intel     | SSDSC2BW240H6      | 240 GB | 2       | 9     | 0     | 0.03   |
| KingSpec  | ACSC2M064mSA       | 63 GB  | 1       | 9     | 0     | 0.03   |
| Transcend | TS128GMTS800       | 128 GB | 3       | 9     | 0     | 0.03   |
| KingDian  | S280-120GB         | 120 GB | 2       | 9     | 0     | 0.03   |
| Patriot   | Blaze              | 120 GB | 3       | 9     | 0     | 0.03   |
| Intel     | SSDMCEAW180A4      | 180 GB | 1       | 9     | 0     | 0.02   |
| KingDian  | S280               | 480 GB | 1       | 9     | 0     | 0.02   |
| Kingston  | SKC400S37128G      | 128 GB | 1       | 8     | 0     | 0.02   |
| KingDian  | N400 60G           | 60 GB  | 1       | 8     | 0     | 0.02   |
| SanDisk   | SD7SN6S-128G-1006  | 128 GB | 1       | 8     | 0     | 0.02   |
| FORESEE   | 64GB SSD           | 64 GB  | 1       | 8     | 0     | 0.02   |
| Kingston  | RBU-SNS8100S312... | 128 GB | 2       | 8     | 0     | 0.02   |
| SanDisk   | Ultra II           | 240 GB | 4       | 7     | 0     | 0.02   |
| PNY       | SSD2SC256GM1P3D... | 256 GB | 1       | 7     | 0     | 0.02   |
| ADATA     | SU900              | 256 GB | 1       | 7     | 0     | 0.02   |
| FASTDISK  | SSD 120G           | 120 GB | 1       | 7     | 0     | 0.02   |
| ADATA     | SP580              | 120 GB | 3       | 7     | 0     | 0.02   |
| ADATA     | SP920SS            | 256 GB | 3       | 83    | 11    | 0.02   |
| Toshiba   | THNSNS128GMCP      | 128 GB | 1       | 7     | 0     | 0.02   |
| ADATA     | SP550              | 240 GB | 5       | 7     | 0     | 0.02   |
| SK hynix  | SC311 SATA         | 128 GB | 1       | 7     | 0     | 0.02   |
| FORESEE   | 128GB SSD          | 128 GB | 1       | 6     | 0     | 0.02   |
| Patriot   | Ignite             | 240 GB | 1       | 6     | 0     | 0.02   |
| Transcend | TS240GMTS820S      | 240 GB | 1       | 6     | 0     | 0.02   |
| Samsung   | SSD PM871b 2.5 7mm | 128 GB | 1       | 6     | 0     | 0.02   |
| Lite-On   | LMT-32L3M-HP       | 32 GB  | 1       | 6     | 0     | 0.02   |
| Lite-On   | CV5-8Q512-HP       | 512 GB | 1       | 6     | 0     | 0.02   |
| Toshiba   | A100               | 120 GB | 2       | 6     | 0     | 0.02   |
| Lite-On   | L8H-256V2G-11 M... | 256 GB | 1       | 6     | 0     | 0.02   |
| Smartbuy  | SSD                | 240 GB | 1       | 6     | 0     | 0.02   |
| GeIL      | Zenith A3-PRO      | 240 GB | 1       | 6     | 0     | 0.02   |
| GeIL      | Zenith A3          | 120 GB | 1       | 6     | 0     | 0.02   |
| Plextor   | PX-G256M6e         | 256 GB | 1       | 5     | 0     | 0.02   |
| OCZ       | ARC100             | 480 GB | 1       | 11    | 1     | 0.02   |
| Transcend | TS128GSSD360S      | 128 GB | 3       | 5     | 0     | 0.01   |
| Samsung   | SSD 860 EVO        | 250 GB | 1       | 5     | 0     | 0.01   |
| MicroData | MD500 120G         | 120 GB | 1       | 5     | 0     | 0.01   |
| AMD       | R3SL60G            | 60 GB  | 1       | 4     | 0     | 0.01   |
| Mushkin   | MKNSSDCG480GB      | 480 GB | 2       | 116   | 508   | 0.01   |
| Smartbuy  | S11-2280           | 128 GB | 1       | 4     | 0     | 0.01   |
| BIWIN     | SSD                | 128 GB | 2       | 4     | 0     | 0.01   |
| Plextor   | PX-128S2C          | 128 GB | 1       | 4     | 0     | 0.01   |
| SanDisk   | SD8SN8U-128G-1006  | 128 GB | 6       | 14    | 2     | 0.01   |
| SanDisk   | SD8SB8U512G1122    | 512 GB | 1       | 4     | 0     | 0.01   |
| Transcend | TS64GSSD370        | 64 GB  | 2       | 4     | 0     | 0.01   |
| Samsung   | MZNLN256HCHP-000L7 | 256 GB | 1       | 4     | 0     | 0.01   |
| Crucial   | CT525MX300SSD4     | 525 GB | 1       | 4     | 0     | 0.01   |
| AMD       | R5SL120G           | 120 GB | 2       | 4     | 0     | 0.01   |
| SanDisk   | SD8SNAT256G1002    | 256 GB | 1       | 4     | 0     | 0.01   |
| GeIL      | ZENITH-A3 120G     | 120 GB | 1       | 3     | 0     | 0.01   |
| Intel     | SSDSA1M080G2LE     | 80 GB  | 1       | 121   | 31    | 0.01   |
| Crucial   | CT512M550SSD1      | 512 GB | 1       | 63    | 16    | 0.01   |
| KingSpec  | ACJC2M032mSH       | 32 GB  | 1       | 3     | 0     | 0.01   |
| Toshiba   | Q300               | 240 GB | 1       | 32    | 8     | 0.01   |
| CHN       | 25SATA01M 060      | 60 GB  | 1       | 3     | 0     | 0.01   |
| OCZ       | REVODRIVE X2       | 60 GB  | 4       | 1204  | 516   | 0.01   |
| SPCC      | SSDB27             | 32 GB  | 1       | 23    | 6     | 0.01   |
| SanDisk   | SD8SBAT256G1122    | 256 GB | 2       | 3     | 0     | 0.01   |
| SK hynix  | SC210 mSATA        | 256 GB | 1       | 82    | 25    | 0.01   |
| SanDisk   | SSD i110           | 16 GB  | 1       | 3     | 0     | 0.01   |
| Samsung   | MZ7LN256HMJP-000H1 | 256 GB | 2       | 2     | 0     | 0.01   |
| Goodram   | IR_SSDPR_S25A_120  | 120 GB | 1       | 2     | 0     | 0.01   |
| Transcend | TS128GSSD230S      | 128 GB | 3       | 2     | 0     | 0.01   |
| KingSpec  | ACSC2M128S25       | 126 GB | 1       | 2     | 0     | 0.01   |
| SanDisk   | SSD i110           | 126 GB | 1       | 2     | 0     | 0.01   |
| Fordisk   | SATA SSD           | 120 GB | 1       | 2     | 0     | 0.01   |
| Samsung   | MZNLN512HCJH-000H1 | 512 GB | 1       | 2     | 0     | 0.01   |
| SanDisk   | SDSA5GK-016G-1006  | 16 GB  | 1       | 276   | 106   | 0.01   |
| ADATA     | SU700              | 120 GB | 2       | 2     | 0     | 0.01   |
| Intel     | SSDSC2KW240H6      | 240 GB | 1       | 2     | 0     | 0.01   |
| SanDisk   | SSD i110           | 24 GB  | 1       | 2     | 0     | 0.01   |
| Transcend | TS64GMTS800        | 64 GB  | 1       | 2     | 0     | 0.01   |
| Transcend | TS256GMTS400       | 256 GB | 2       | 2     | 0     | 0.01   |
| Samsung   | SSD 850            | 120 GB | 3       | 2     | 0     | 0.01   |
| SanDisk   | SSD P4             | 32 GB  | 8       | 79    | 151   | 0.01   |
| SanDisk   | SDSSDH120GG25      | 120 GB | 1       | 112   | 55    | 0.01   |
| Kingrich  | 64GB K9 SATA3 SSD  | 63 GB  | 1       | 2     | 0     | 0.01   |
| China     | SSD60G             | 60 GB  | 2       | 1     | 0     | 0.01   |
| Intel     | SSDSC2BP480G4      | 480 GB | 1       | 1     | 0     | 0.01   |
| Samsung   | SSD 860 PRO        | 512 GB | 1       | 1     | 0     | 0.01   |
| Transcend | TS32GMSA370        | 32 GB  | 1       | 1     | 0     | 0.01   |
| Kingston  | SKC300S37A240G     | 240 GB | 2       | 1     | 0     | 0.01   |
| China     | SSD 120G           | 120 GB | 1       | 1     | 0     | 0.01   |
| Golden... | GDSA25-120MS       | 120 GB | 1       | 1     | 0     | 0.01   |
| KingSpec  | P3-128             | 126 GB | 1       | 1     | 0     | 0.01   |
| KingSpec  | P3D-240            | 240 GB | 1       | 1     | 0     | 0.01   |
| FASTDISK  | SSD                | 64 GB  | 1       | 1     | 0     | 0.00   |
| KingSpec  | NT-256             | 256 GB | 1       | 1     | 0     | 0.00   |
| FASTDISK  | SSD 30G            | 30 GB  | 1       | 1     | 0     | 0.00   |
| KingSpec  | ACJC2M064S25       | 63 GB  | 1       | 1     | 0     | 0.00   |
| Kingmax   | SSD                | 240 GB | 1       | 1     | 0     | 0.00   |
| Micron    | C400-MTFDDAT064MAM | 64 GB  | 1       | 1     | 0     | 0.00   |
| China     | SSD 256G           | 256 GB | 1       | 1     | 0     | 0.00   |
| Samsung   | SSD 850 EVO mSATA  | 1 TB   | 1       | 1     | 0     | 0.00   |
| Samsung   | MZ7LF120HCHP-000L1 | 120 GB | 1       | 1     | 0     | 0.00   |
| Plextor   | PX-512M6M          | 512 GB | 1       | 1     | 0     | 0.00   |
| SanDisk   | SD8SNAT256G1122    | 256 GB | 1       | 1     | 0     | 0.00   |
| Samsung   | MZNTY128HDHP-000H1 | 128 GB | 1       | 1     | 0     | 0.00   |
| GeIL      | ZENITH R3_120GB    | 120 GB | 1       | 1     | 0     | 0.00   |
| Micron    | 1100_MTFDDAK256TBN | 256 GB | 1       | 1     | 0     | 0.00   |
| KingSpec  | ACJC2M128S25       | 126 GB | 1       | 1     | 0     | 0.00   |
| WDC       | WDS120G1G0B-00RC30 | 120 GB | 1       | 1     | 0     | 0.00   |
| Samsung   | MZMTD512HAGL-000L1 | 512 GB | 1       | 107   | 97    | 0.00   |
| SanDisk   | SSD P4             | 64 GB  | 1       | 14    | 14    | 0.00   |
| SanDisk   | SD6SB1M256G1022I   | 256 GB | 1       | 400   | 474   | 0.00   |
| SK hynix  | HFS060G32MNM-1010U | 60 GB  | 1       | 822   | 1016  | 0.00   |
| Plextor   | PX-128M6MV         | 128 GB | 1       | 0     | 0     | 0.00   |
| China     | SATA SSD           | 240 GB | 2       | 0     | 0     | 0.00   |
| Crucial   | CT120M500SSD3      | 120 GB | 1       | 12    | 16    | 0.00   |
| WDC       | WDS250G2B0A-00SM50 | 250 GB | 1       | 0     | 0     | 0.00   |
| Indilinx  | InM2246S3-128G     | 128 GB | 1       | 0     | 0     | 0.00   |
| KingSpec  | MT-64              | 64 GB  | 1       | 0     | 0     | 0.00   |
| Samsung   | SSD 860 EVO mSATA  | 250 GB | 1       | 0     | 0     | 0.00   |
| SanDisk   | SD8TN8U512G1001    | 512 GB | 1       | 0     | 0     | 0.00   |
| KingSpec  | ACSC2M064S25       | 63 GB  | 1       | 0     | 0     | 0.00   |
| KingSpec  | ACSC2M128mSA       | 126 GB | 1       | 0     | 0     | 0.00   |
| QUMO      | SSD                | 480 GB | 1       | 625   | 1015  | 0.00   |
| Toshiba   | THNSNK256GVN8 M... | 256 GB | 1       | 60    | 100   | 0.00   |
| SPCC      | SSD170             | 55 GB  | 1       | 593   | 1017  | 0.00   |
| QUMO      | SSD                | 120 GB | 1       | 579   | 1017  | 0.00   |
| Intenso   | SSD Sata III       | 247 GB | 1       | 18    | 32    | 0.00   |
| SK hynix  | HFS128G38MNB-2200A | 128 GB | 2       | 41    | 120   | 0.00   |
| Goodram   | SSDPR_CX300_120    | 120 GB | 1       | 0     | 0     | 0.00   |
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
| KingDian  | S200               | 120 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | CV1-8B512          | 512 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | CV3-8D256-11 SATA  | 256 GB | 1       | 0     | 0     | 0.00   |
| Patriot   | Torch LE           | 120 GB | 1       | 0     | 0     | 0.00   |
| Apacer    | AS330              | 120 GB | 1       | 0     | 0     | 0.00   |
| China     | SATA SSD           | 60 GB  | 1       | 0     | 0     | 0.00   |
| Samsung   | MZNTY256HDHP-00000 | 256 GB | 1       | 0     | 0     | 0.00   |
| GeIL      | ZENITH S3-120GB    | 120 GB | 1       | 245   | 1021  | 0.00   |
| SanDisk   | SD8SBAT-032G-1006  | 32 GB  | 2       | 0     | 0     | 0.00   |
| Samsung   | MZ7PA256HMDR-010H1 | 256 GB | 1       | 236   | 1040  | 0.00   |
| Goldenfir | T650-120G          | 126 GB | 1       | 0     | 0     | 0.00   |
| Lite-On   | S960 256           | 256 GB | 1       | 0     | 0     | 0.00   |
| WDC       | WDS100T1B0A-00H9H0 | 1 TB   | 1       | 0     | 0     | 0.00   |
| Zheino    | CHN25SATAS1 064    | 64 GB  | 1       | 0     | 0     | 0.00   |
| Patriot   | Pyro SE            | 240 GB | 1       | 180   | 1016  | 0.00   |
| China     | T120               | 120 GB | 1       | 0     | 0     | 0.00   |
| Faspeed   | H5-30G             | 30 GB  | 1       | 0     | 0     | 0.00   |
| KingDian  | S200               | 60 GB  | 1       | 0     | 0     | 0.00   |
| Intel     | SSDMCEAW080A4 m... | 80 GB  | 1       | 162   | 1009  | 0.00   |
| China     | 80GB SSD           | 80 GB  | 2       | 0     | 0     | 0.00   |
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
| Toshiba   | HG2 Series             | 2      | 3       | 922   | 0     | 2.53   |
| Crucial   | RealSSD m4/C400/P400   | 2      | 8       | 548   | 0     | 1.50   |
| Apple     | SD/SM/TS E/F/G SSDs    | 1      | 1       | 545   | 0     | 1.49   |
| Crucial   | RealSSD m4/C400        | 4      | 20      | 528   | 51    | 1.40   |
| Toshiba   | HG5 Series             | 1      | 2       | 471   | 0     | 1.29   |
| Verbatim  | Unknown                | 1      | 1       | 470   | 0     | 1.29   |
| Intel     | 510 Series SSDs        | 1      | 1       | 453   | 0     | 1.24   |
| Foxline   | Unknown                | 1      | 1       | 443   | 0     | 1.22   |
| OCZ       | SandForce Driven SSDs  | 30     | 169     | 564   | 43    | 1.21   |
| Toshiba   | HG3 Series             | 3      | 3       | 403   | 0     | 1.11   |
| OCZ       | Indilinx Barefoot_2... | 12     | 78      | 393   | 4     | 1.01   |
| KingShare | Unknown                | 1      | 1       | 358   | 0     | 0.98   |
| Kingston  | JMicron based SSDs     | 9      | 21      | 416   | 2     | 0.97   |
| Corsair   | SandForce Driven SSDs  | 18     | 76      | 415   | 95    | 0.96   |
| Intel     | 520 Series SSDs        | 2      | 2       | 315   | 0     | 0.86   |
| Ramaxel   | Unknown                | 1      | 2       | 295   | 0     | 0.81   |
| Intel     | 320 Series SSDs        | 5      | 13      | 272   | 0     | 0.75   |
| Toshiba   | HG5d Series            | 7      | 10      | 244   | 0     | 0.67   |
| Mushkin   | SandForce Driven SSDs  | 6      | 6       | 372   | 678   | 0.67   |
| HP        | Unknown                | 1      | 1       | 238   | 0     | 0.65   |
| ADATA     | SandForce Driven SSDs  | 7      | 44      | 290   | 9     | 0.65   |
| Intel     | 330/335 Series SSDs    | 2      | 9       | 237   | 0     | 0.65   |
| Apple     | JMicron based SSDs     | 2      | 2       | 233   | 0     | 0.64   |
| Toshiba   | Unknown                | 12     | 15      | 230   | 8     | 0.61   |
| Intel     | Unknown                | 6      | 8       | 239   | 127   | 0.55   |
| Kingston  | SandForce Driven SSDs  | 27     | 442     | 222   | 32    | 0.55   |
| Intel     | X18-M/X25-M/X25-V G... | 9      | 15      | 545   | 9     | 0.51   |
| Toshiba   | HG6 Series SSD         | 3      | 7       | 186   | 0     | 0.51   |
| Samsung   | based SSDs             | 64     | 394     | 188   | 9     | 0.51   |
| OCZ       | Indilinx Barefoot b... | 2      | 2       | 185   | 0     | 0.51   |
| Crucial   | MX100/M500/M510/M55... | 2      | 13      | 181   | 0     | 0.50   |
| Transcend | SandForce Driven SSDs  | 4      | 6       | 177   | 0     | 0.49   |
| OCZ       | Indilinx Barefoot 3... | 9      | 25      | 166   | 1     | 0.46   |
| Samsung   | Samsung based SSDs     | 25     | 40      | 173   | 93    | 0.45   |
| Samsung   | Unknown                | 11     | 15      | 189   | 3     | 0.44   |
| SanDisk   | Marvell based SanDi... | 22     | 78      | 166   | 20    | 0.44   |
| Intel     | 525 Series SSDs        | 1      | 2       | 148   | 0     | 0.41   |
| OCZ       | Trion SSDs             | 4      | 10      | 147   | 1     | 0.40   |
| Crucial   | RealSSD C300/M500      | 7      | 25      | 269   | 93    | 0.40   |
| Micron    | Unknown                | 6      | 6       | 257   | 176   | 0.40   |
| Intel     | X18-M/X25-M G1 SSDs    | 2      | 2       | 139   | 0     | 0.38   |
| TEAM      | Unknown                | 3      | 4       | 138   | 0     | 0.38   |
| Corsair   | Unknown                | 5      | 9       | 174   | 34    | 0.38   |
| Smartbuy  | Unknown                | 9      | 71      | 140   | 1     | 0.38   |
| Intel     | 730 and DC S35x0/36... | 5      | 9       | 135   | 0     | 0.37   |
| Crucial   | MX100/MX200/M5x0/M6... | 6      | 15      | 241   | 145   | 0.37   |
| Plextor   | Unknown                | 16     | 29      | 132   | 0     | 0.36   |
| OCZ       | Unknown                | 8      | 15      | 131   | 0     | 0.36   |
| Chiprex   | Unknown                | 1      | 1       | 126   | 0     | 0.35   |
| SPCC      | Unknown                | 17     | 170     | 168   | 167   | 0.33   |
| ADATA     | JMicron based SSDs     | 5      | 14      | 121   | 1     | 0.32   |
| Apacer    | Unknown                | 5      | 5       | 115   | 0     | 0.32   |
| Intel     | 730 and DC S3500/S3... | 3      | 3       | 110   | 0     | 0.30   |
| SanDisk   | SanDisk based SSDs     | 17     | 81      | 124   | 32    | 0.29   |
| Intel     | 530 Series SSDs        | 4      | 33      | 110   | 1     | 0.29   |
| Goodram   | Unknown                | 7      | 21      | 107   | 1     | 0.29   |
| Transcend | Indilinx Barefoot b... | 1      | 1       | 309   | 2     | 0.28   |
| Plextor   | M3/M5 (Pro) Series ... | 8      | 63      | 113   | 17    | 0.28   |
| China     | Unknown                | 21     | 56      | 107   | 1     | 0.27   |
| Toshiba   | HG6 Series             | 1      | 1       | 98    | 0     | 0.27   |
| Toshiba   | OCZ                    | 5      | 13      | 94    | 0     | 0.26   |
| Plextor   | M3/M5/M6 Series SSDs   | 7      | 72      | 95    | 30    | 0.25   |
| Transcend | JMicron based SSDs     | 4      | 7       | 86    | 0     | 0.24   |
| Seagate   | 600 Series             | 1      | 1       | 79    | 0     | 0.22   |
| SanDisk   | Unknown                | 28     | 41      | 104   | 84    | 0.22   |
| Kingston  | Phison Driven SSDs     | 8      | 41      | 78    | 0     | 0.21   |
| ADATA     | Unknown                | 24     | 51      | 162   | 163   | 0.21   |
| PNY       | Phison Driven SSDs     | 2      | 3       | 64    | 0     | 0.18   |
| PHISON    | Unknown                | 1      | 1       | 121   | 1     | 0.17   |
| TEKET     | Unknown                | 1      | 2       | 59    | 0     | 0.16   |
| Kingston  | Unknown                | 20     | 123     | 78    | 210   | 0.16   |
| Radeon    | Indilinx Barefoot 3... | 1      | 1       | 56    | 0     | 0.15   |
| WDC       | Blue PC SSD            | 4      | 8       | 55    | 0     | 0.15   |
| Patriot   | Unknown                | 11     | 21      | 62    | 49    | 0.15   |
| KingFast  | Unknown                | 7      | 13      | 53    | 1     | 0.15   |
| SanDisk   | SandForce Driven SSDs  | 5      | 45      | 52    | 25    | 0.14   |
| Kingmax   | Unknown                | 3      | 31      | 186   | 469   | 0.14   |
| PNY       | Unknown                | 5      | 5       | 126   | 222   | 0.14   |
| Apple     | SD/SM/TS E/F SSDs      | 4      | 4       | 48    | 0     | 0.13   |
| QUMO      | Unknown                | 3      | 3       | 449   | 678   | 0.13   |
| KingSpec  | Unknown                | 19     | 24      | 45    | 0     | 0.12   |
| PRETEC    | Unknown                | 1      | 1       | 44    | 0     | 0.12   |
| Intel     | 53x and Pro 2500 Se... | 4      | 10      | 42    | 0     | 0.12   |
| Crucial   | MX1/2/300, M5/600, ... | 6      | 14      | 52    | 3     | 0.12   |
| Fordisk   | Unknown                | 2      | 2       | 35    | 0     | 0.10   |
| ZOTAC     | Unknown                | 1      | 2       | 34    | 0     | 0.09   |
| Transcend | Unknown                | 4      | 6       | 46    | 168   | 0.09   |
| Crucial   | SiliconMotion based... | 3      | 6       | 32    | 0     | 0.09   |
| Toshiba   | SG2 Series             | 1      | 1       | 32    | 0     | 0.09   |
| Micron    | RealSSD m4/C400/P400   | 3      | 5       | 52    | 606   | 0.08   |
| KingPower | Unknown                | 1      | 1       | 29    | 0     | 0.08   |
| Transcend | SiliconMotion based... | 14     | 38      | 27    | 0     | 0.08   |
| KingDian  | Unknown                | 10     | 25      | 26    | 0     | 0.07   |
| Corsair   | Indilinx Barefoot b... | 1      | 1       | 99    | 3     | 0.07   |
| SK hynix  | Unknown                | 6      | 9       | 123   | 140   | 0.06   |
| Crucial   | Unknown                | 3      | 3       | 22    | 0     | 0.06   |
| Lite-On   | Unknown                | 15     | 16      | 30    | 160   | 0.06   |
| Netac     | Unknown                | 1      | 1       | 19    | 0     | 0.05   |
| LDLC      | Unknown                | 2      | 4       | 19    | 0     | 0.05   |
| AMD       | Unknown                | 8      | 28      | 22    | 37    | 0.05   |
| Hyperdisk | Unknown                | 1      | 1       | 18    | 0     | 0.05   |
| Intenso   | Unknown                | 2      | 3       | 38    | 11    | 0.05   |
| WDC       | Green PC SSD           | 3      | 15      | 16    | 0     | 0.05   |
| Seagate   | 600 Pro Series         | 1      | 1       | 14    | 0     | 0.04   |
| Micron    | MX100/MX200/M5x0/M6... | 1      | 1       | 13    | 0     | 0.04   |
| GLOWAY    | Unknown                | 3      | 4       | 13    | 0     | 0.04   |
| Intel     | 540 Series SSDs        | 2      | 2       | 24    | 1     | 0.03   |
| SK hynix  | SATA SSDs              | 4      | 4       | 39    | 7     | 0.03   |
| WDC       | Unknown                | 2      | 3       | 12    | 0     | 0.03   |
| FORESEE   | Unknown                | 3      | 3       | 10    | 0     | 0.03   |
| Kingrich  | Unknown                | 2      | 2       | 9     | 0     | 0.03   |
| ADATA     | SiliconMotion based... | 2      | 18      | 9     | 0     | 0.02   |
| FASTDISK  | Unknown                | 6      | 6       | 7     | 0     | 0.02   |
| Mushkin   | Unknown                | 1      | 2       | 116   | 508   | 0.01   |
| Faspeed   | Unknown                | 2      | 2       | 4     | 0     | 0.01   |
| BIWIN     | Unknown                | 1      | 2       | 4     | 0     | 0.01   |
| CHN       | Unknown                | 1      | 1       | 3     | 0     | 0.01   |
| GeIL      | Unknown                | 5      | 5       | 52    | 205   | 0.01   |
| MicroData | Unknown                | 2      | 2       | 23    | 333   | 0.01   |
| Golden... | Unknown                | 1      | 1       | 1     | 0     | 0.01   |
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
| OCZ         | 65     | 299     | 448   | 25    | 1.02   |
| KingShare   | 1      | 1       | 358   | 0     | 0.98   |
| Corsair     | 24     | 86      | 386   | 88    | 0.89   |
| Ramaxel     | 1      | 2       | 295   | 0     | 0.81   |
| Toshiba     | 35     | 55      | 245   | 2     | 0.67   |
| HP          | 1      | 1       | 238   | 0     | 0.65   |
| Crucial     | 33     | 104     | 275   | 54    | 0.62   |
| Mushkin     | 7      | 8       | 308   | 635   | 0.51   |
| Samsung     | 100    | 449     | 187   | 16    | 0.50   |
| Apple       | 7      | 7       | 172   | 0     | 0.47   |
| Kingston    | 64     | 627     | 191   | 64    | 0.46   |
| Intel       | 46     | 109     | 212   | 11    | 0.43   |
| TEAM        | 3      | 4       | 138   | 0     | 0.38   |
| Smartbuy    | 9      | 71      | 140   | 1     | 0.38   |
| ADATA       | 38     | 127     | 180   | 69    | 0.35   |
| Chiprex     | 1      | 1       | 126   | 0     | 0.35   |
| SPCC        | 17     | 170     | 168   | 167   | 0.33   |
| Apacer      | 5      | 5       | 115   | 0     | 0.32   |
| SanDisk     | 72     | 245     | 121   | 36    | 0.30   |
| Goodram     | 7      | 21      | 107   | 1     | 0.29   |
| Plextor     | 31     | 164     | 108   | 20    | 0.28   |
| China       | 21     | 56      | 107   | 1     | 0.27   |
| Micron      | 10     | 12      | 151   | 341   | 0.24   |
| PHISON      | 1      | 1       | 121   | 1     | 0.17   |
| TEKET       | 1      | 2       | 59    | 0     | 0.16   |
| Radeon      | 1      | 1       | 56    | 0     | 0.15   |
| PNY         | 7      | 8       | 103   | 139   | 0.15   |
| Patriot     | 11     | 21      | 62    | 49    | 0.15   |
| KingFast    | 7      | 13      | 53    | 1     | 0.15   |
| Transcend   | 27     | 58      | 56    | 18    | 0.14   |
| Kingmax     | 3      | 31      | 186   | 469   | 0.14   |
| QUMO        | 3      | 3       | 449   | 678   | 0.13   |
| Seagate     | 2      | 2       | 46    | 0     | 0.13   |
| KingSpec    | 19     | 24      | 45    | 0     | 0.12   |
| PRETEC      | 1      | 1       | 44    | 0     | 0.12   |
| Fordisk     | 2      | 2       | 35    | 0     | 0.10   |
| ZOTAC       | 1      | 2       | 34    | 0     | 0.09   |
| KingPower   | 1      | 1       | 29    | 0     | 0.08   |
| WDC         | 9      | 26      | 27    | 0     | 0.08   |
| KingDian    | 10     | 25      | 26    | 0     | 0.07   |
| Lite-On     | 15     | 16      | 30    | 160   | 0.06   |
| Netac       | 1      | 1       | 19    | 0     | 0.05   |
| SK hynix    | 10     | 13      | 97    | 99    | 0.05   |
| LDLC        | 2      | 4       | 19    | 0     | 0.05   |
| AMD         | 8      | 28      | 22    | 37    | 0.05   |
| Hyperdisk   | 1      | 1       | 18    | 0     | 0.05   |
| Intenso     | 2      | 3       | 38    | 11    | 0.05   |
| GLOWAY      | 3      | 4       | 13    | 0     | 0.04   |
| FORESEE     | 3      | 3       | 10    | 0     | 0.03   |
| Kingrich    | 2      | 2       | 9     | 0     | 0.03   |
| FASTDISK    | 6      | 6       | 7     | 0     | 0.02   |
| Faspeed     | 2      | 2       | 4     | 0     | 0.01   |
| BIWIN       | 1      | 2       | 4     | 0     | 0.01   |
| CHN         | 1      | 1       | 3     | 0     | 0.01   |
| GeIL        | 5      | 5       | 52    | 205   | 0.01   |
| MicroData   | 2      | 2       | 23    | 333   | 0.01   |
| Goldendisk  | 1      | 1       | 1     | 0     | 0.01   |
| Indilinx    | 1      | 1       | 0     | 0     | 0.00   |
| Gost        | 1      | 1       | 0     | 0     | 0.00   |
| Goldenfir   | 1      | 1       | 0     | 0     | 0.00   |
| Zheino      | 1      | 1       | 0     | 0     | 0.00   |
| SMI         | 1      | 1       | 0     | 1957  | 0.00   |

