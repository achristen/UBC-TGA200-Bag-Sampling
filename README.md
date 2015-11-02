# UBC-TGA200-Bag-Sampling
Code to analyze bag samples run on UBC's Campbell Scientific TGA 200 for stable isotope analysis of 13C and 18O in CO2 of ambient air samples.

## The file "tga200.plist"

This plist file needs to be edited by the user to fit the local or server paths of where data are stored. It contains file path settings to the following files or directories:

### DefaultSetupFile  

File in TOA5 ASCII format where the TANK ID connected to the five sites TGA 200 are described as they change over time. The attached file contains an example

### DefaultTankCalibrationFile

File in TOA5 ASCII format that contains the total CO2, d13C, and d18O values for each TANK ID in UBC's Greenhouse Gas Laboratory.

### DefaultBagSampleDirectory

The default directory in which the bag sampling sequence description file and the output reports / graphs will be stored. The user can change this when running the program.

### DefaultLoggerDataDir

This is the default directory where logger data from the TGA200 is stored. The user can change this when running. the program.

## Tank Calibration File

This is a file that fulfills the TOA5 format as specified by Campbell Scientific. It is a comma separated file. It has 4 header rows, where rows 2-4 are column headers that indicate column headers (row 2), column units (row 3) and a generic "Smp" for all entries in row 4.

Each row is a calibration tank, that is identified by a unique ID.

    "TOA5","CALIBRATION-TANKS-USED-WITH-TGA200,"UBC","LAST-UPDATED-2015-11-02","N/A","N/A","N/A","N/A"
    "TANK_ID","TOTAL_CO2","D13C","D18O","NOTES"
    "text","ppm","per mil","per mil","text"
    "Smp","Smp","Smp","Smp","Smp"
    "CO2-001",503.767,-15.024, -8.349,"TGA UBC (2014-01-14 / 2014-05-02)"
    "CO2-002",447.965,-11.724, -4.947,"TGA UBC (2013-04-24 / 2013-06-11 / 2013-07-10)"
    "CO2-003",397.762,-10.525, -4.546,"TGA UBC (2013-04-22 / 2013-06-11)"
    "CO2-004",499.283,-37.104,-15.601,"TGA UBC (2013-04-22 / 2013-04-24 / 2013-06-11)"
    "CO2-005",357.150,-46.564,-38.939,"TGA UBC (2013-04-24)"
