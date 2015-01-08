---
title: "extraTrappingNOBS"
author: "Bryan Milstead"
date: "Thursday, January 08, 2015"
output: html_document
---
<!---
use these command instead of the knit icon if you want the data and work loaded into the R workspace
  library(knitr)
  knit('extraTrappingNOBS.rmd')
-->
Introduction
-------------------------
* Purpose: Calculate the number of unique individual by Month for the extra trapping grids and the control grids.
* This document is available here: https://github.com/FrayJorge/FJ_NOBS/blob/master/extraTrappingNOBS.md
* The details of all data processing steps including notes and rcode are available here: https://github.com/FrayJorge/FJ_NOBS/blob/master/extraTrappingNOBS.Rmd
* The dataset is available here in .csv format https://github.com/FrayJorge/FJ_NOBS/blob/master/extraTrappingNOBS.csv?raw=true
    - right click on the link and choose “Save As” to save the file to your computer, otherwise, it will open in your browser
    - you browser may want to save this as "extraTrappingNOBS.txt".  If this happens change the name to "extraTrappingNOBS.csv" so that it is more easily recognized as a CSV file.

Data Steps
-------------------------
* Get the Raw Data from tblCapturesUpdated in FJ.mdb



**Data Definitions**

Field  | Description 
------------- | ------------- 
**CaptureID** | Record ID for the Capture
**NewNum** | Unique ID for the Individual-Blanks are missing values, usually unmarked animals that died in the trap or escaped or the tag number was unresolved. Remove these from the analysis.
**MO** | Month YYMM before 2000 and YYYYMM after
**GR** | Grid Number
**TRT** | Treatment
**SP** | Species
**SEX** | Sex
**ST** | Status: 0 = N = New, animal never capture before.; 1 = previously captured animal; already marked.; 2 = R = Remarked.  Animal was obviously marked before but the tag was lost.  Old Number is unknown.; 3 = C = Changed.  Animal in danger of loosing a tag (ear torn; leg swelling) so a new tag is added.  Be sure to add old and new numbers to the "Cambios / 2#'s" worksheet.
**F** | Fate: 0 = Released; 1 = Died in the Trap; 2 = Injured in Trap or during handling; 3 = Escaped; 4 = Repeat Capture: during the same trap revision session.; 5 = Animal removed from the grid.  Release site unknown or not one of the two below.; 6 = Animal removed from the grid and released between grids 2 and 3.; 7 = Animal removed from the grid and released between grids 11 and 12.
**C1** | Comment1: 1=SEXO?; 2=NUMERO?; 3=PARASITOS; 4=TAPON; 5=Ejaculation; 6=PARTO - RECIEN PARIDO; 7=MISMA TRAMPA; 8=OTRO; 9=TAG LOOSE; 10=ZORRO - ANIMAL NO SACADO; 11=DOS NUMEROS:  Make sure that this is noted in the "cambios / 2#'s" worksheet.; 13=ZORRO - ANIMAL SACADO; 14=DISTENDED PENIS; 15=SANGRE EN LA VAGINA; 16=ANILLO APRETADO; 17=ANILLO SOLTADO O CAMBIADO; 18=ESPECIES?; 19=ADN ; 20=rear foot amputated; 21=-PI; missing left rear foot; 22=-PD; missing right rear foot; 23=-PC; missing the tip of the tail; 24=HIPOTERMIA; 25=ANILLO FLOJO; 26=Oreja rajada por crotal anterior; 27=zorro- se desconoce si hubo animal y qué tipo; 28=Recolección de Fecas; 99=Unresolvable number
**C2** | Comment2: see Comment 1
**C3** | Comment3: see Comment 1

* Replace any Blanks in NewNum with NA 
* Delete observations for Newnum==NA 
* Keep the following Months Only: 


```
##  [1]   9608   9610   9612   9702   9704   9707   9710   9802   9808   9902
## [11]   9905   9907   9911 200002 200005 200008 200103 200108 200202 200208
## [21] 200302 200308
```

* Keep the following Treatments Only: 


```
##  [1] "A1"   "A2"   "E2"   "E3"   "F1"   "F2"   "F3"   "G10"  "G11"  "G15" 
## [11] "G3"   "PDPP" "Q0"   "Q3"   "Q4"   "Q5"
```

* Calculate NOBS by gr/trt/mo/SP/


    
* Save the data as extraTrappingNOBS.csv 


