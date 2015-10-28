# UBC-TGA200-Bag-Sampling
Code to analyze bag samples run on UBC's Campbell Scientific TGA 200 for stable isotope analysis of 13C and 18O in air samples.

The plist file needs to be edited by the user to have the following settings:

### DefaultSetupFile  

File where the TANK ID connected to the five sites TGA 200 are described as they change over time.

### DefaultTankCalibrationFile

This file contains the total CO2, d13C, and d18O values for each TANK ID.

### DefaultBagSampleDirectory

The default directory in which the bag sampling sequence description file and the output reports / graphs will be stored. The user can change this when running the program.

### DefaultLoggerDataDir

This is the default directory where logger data from the TGA200 is stored. The user can change this when running. the program.
