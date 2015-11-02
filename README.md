# UBC-TGA200-Bag-Sampling
Code to analyze bag samples run on UBC's Campbell Scientific TGA 200 for stable isotope analysis of 13C and 18O in CO2 of ambient air samples.

## The file "tga200.plist"

This plist file needs to be edited by the user to fit the local or server paths of where data are stored. It contains file path settings to the following files or directories:

### DefaultSetupFile  

Path to the [Setup File](#setupfile) in TOA5 ASCII format where the TANK ID connected to the five sites TGA 200 are described as they change over time. 

### DefaultTankCalibrationFile

Path to the [Tank Calibration File](#tankcalibfile) in TOA5 ASCII format that contains the total CO2, d13C, and d18O values for each TANK ID in UBC's Greenhouse Gas Laboratory. 

### DefaultBagSampleDirectory

The default directory in which the bag sampling sequence description file and the output reports / graphs will be stored. The user can change this when running the program.

### DefaultLoggerDataDir

This is the default directory where logger data from the TGA200 is stored. The user can change this when running. the program.

## <a name="setupfile"></a>Setup File

This is a file that fulfills the TOA5 format as specified by Campbell Scientific. It is a comma separated file. It has 4 header rows, where rows 2-4 are column headers that indicate column headers (row 2), column units (row 3) and a generic "Smp" for all entries in row 4. Following on lines 5 - ... are then data entries, where each entry corresponds to a time period during which the described setup of the TGA was operated. The first date contains year (column 1), month (column 2), day (column 3), hour (column 4) and minute (column 5) for the first date/time on which the current configuration of tanks was operated. The second date with year (column 6), month (column 7), day (column 8), hour (column 9) and minute (column 10) is the last date/time for which the current configuration of tanks was valid. "TANK_SITE1" (column 11), "TANK_SITE2" (column 12), "TANK_SITE3" (column 13), "TANK_SITE4" (column 14) and "TANK_SITE5" (column 15) descrive what was connected to to site 1 to site 5 of the TGA. In regular operation, site 1 is the EC inlet, site 2 is the storage inlet, and sites 3 to 5 are calibration tanks. This order, however can be different in different projects. Then "BRACKET_LOW" (column 16),"BRACKET_MED" (column 17),""BRACKET_HIGH" (column 18) are the calibration tank IDs as specified in the separate [Tank Calibration File](#tankcalibfile). The IDs must match those. For the purpose of the bag calibration, #only BRACKET_LOW and BRACKET_HIGH are used*. BRACKET_MED is usually the bag sample. However, as those files are also used for the regular operation of the TGA in EC mode, BRACKET_MED is included, but not used.

An example file is contained in this project under the name "TOA5_TGA200_Setup.txt". Here is the header and a few sample lines:

        "TOA5","CALIBRATION-TANKS-CONNECTED-TO-TGA200,"UBC","LAST-UPDATED-2013-04-25","N/A","N/A","N/A","N/A"
        "START_YEAR","START_MONTH","START_DAY","START_HOUR","START_MINUTE","END_YEAR","END_MONTH","END_DAY","END_HOUR","END_MINUTE","TANK_SITE1","TANK_SITE2","TANK_SITE3","TANK_SITE4","TANK_SITE5","BRACKET_LOW","BRACKET_MED",""BRACKET_HIGH"
        "year","month","day","hour","minute","year","month","day","hour","minute","text","text","text","text","text","site","site","site"
        "Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp","Smp"
        2014,09,12,14,40,2014,10,03,23,44,”Outdoor","Indoor","CO2-012","CO2-013","CO2-014",3,4,5
        2014,10,03,23,44,2014,10,06,20,00,"Outdoor","Outdoor2cm","CO2-012","CO2-014","CO2-013",3,5,4
        2014,10,06,20,00,2014,10,27,17,30,"Outdoor","Outdoor2cm","CO2-014","CO2-012","CO2-013",5,4,3
        ...


## <a name="tankcalibfile"></a> Tank Calibration File

This is a file that fulfills the TOA5 format as specified by Campbell Scientific. It is a comma separated file. It has 4 header rows, where rows 2-4 are column headers that indicate column headers (row 2), column units (row 3) and a generic "Smp" for all entries in row 4. Following on lines 5 - ... are then data entries. Each row is a calibration tank, that is identified by a unique ID (column 1), followed by total CO2 mixing ratio (column 2), d13C in CO2 (column 3), d18O in CO2 (column 4) and a note on the calibration of the tank / source (column 5). 

An example file is contained in this project under the name "TOA5_TGA200_Calibration_Gases.txt". Here is the header and to first entires for tanks with the IDs "CO2-001" and "CO2-002":

    "TOA5","CALIBRATION-TANKS-USED-WITH-TGA200,"UBC","LAST-UPDATED-2015-11-02","N/A","N/A","N/A","N/A"
    "TANK_ID","TOTAL_CO2","D13C","D18O","NOTES"
    "text","ppm","per mil","per mil","text"
    "Smp","Smp","Smp","Smp","Smp"
    "CO2-001",503.767,-15.024, -8.349,"TGA UBC (2014-01-14 / 2014-05-02)"
    "CO2-002",447.965,-11.724, -4.947,"TGA UBC (2013-04-24 / 2013-06-11 / 2013-07-10)"
    ...

Usually the latest sheet of tank analysis can be found under http://ibis.geog.ubc.ca/~achristn/tga200/calibration-tanks/



The high-frequency raw data are locally stored on the TGA PC under D:\met-data\tga200\ in the file CR3000_RawData.dat
