# Conversion from Main v1.1 to Main v2.0 
## **(Currently Incomplete - see bold text for proposed changes)**

Version 2.0 is based on the general PMU Application template created by Maxime Baudette (https://github.com/MaximeBaudette).

The main differences lie in the acquisition of data and the user interface. In addiiton, the S3DK GUI can be opened within the application instead of being opened from another VI.

This guide will explain the changes specific to the Mode Estimator application.

## User Interface

The User Interface now fits in one window, with all displays in one tab control. The user can still switch between tabs to view different data displays. Also, user selections now occur via pop-up menus that conveniently close upon user selection confirmation.

## Acquisition Loop

The PRL Buffer works similar to how it does in v1.1. Obtaining CSV data now works in a similar fashion to it, whereas in v1.1 all of the
data was used at once for the entire process. In v2.0, the CSV data is buffered one row at a time to create a stream of data.

This was accomplished by first formatting the CSV files to fit Maxime's CSV Reader. FormatCSV.vi takes a Format A or Format B file and creates a newly formatted CSV file containing separate data (within a user-selected time frame) for each terminal. Afterwards, the user can select which terminal to use for Mode Estimation from ConfigureCSV.vi, which I coded specifically to fit this application. Instead of occurring after InitializeCSV.vi, as it does in Maxime's base template, ConfigureCSV.vi occurs *before* InitializeCSV.vi.

**Currently, the Parcel Length is determined by the user, yet for the CSV option the parcel length is supposed to be determined by the time frame. I have already implemented a parcel length output in FormatCSV.vi, but it needs to be able to override the user input parcel length value.**

## Algorithm Loop

The algorithm loop now contains the final 3 stages of v1.1 as its main process. 

**The signal selection currently does not work correctly. It should be replaced with "CreateWaveform.vi" (may need editing, but may not). In addition, the "Phase Comparison" selection should be updated to work with this template. To begin, I have made an output of ConfigureCSV.vi entitled "Remaining Terminal Data," which gives an array of clusters containing the CSV files, respective Terminal IDs and respective Terminal Names of the unused terminals. This must somehow make it through the buffer as well, or otherwise be compared alongside the selected terminal data (going through the buffer) while matching up the timestamps for each dataset. This produces an accurate Phase Comparison at the correct times. There should be a similar implementation for the PRL option, where the user can choose a second channel (possibly through a pop-up window as well).**



To me, one of the most important updates is the user friendly pop-up windows, which can smooth the dynamic execution of the program 
instead of relying on user inputs before the program begins. It creates less room for user error and less undesired outcomes/inputs.

