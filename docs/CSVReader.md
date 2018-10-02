## CSV Reader.vi
This VI is designed to obtain and separate data for several terminals taken over one period of time. The input is a CSV file with data for
a certain number of terminals, all taken over the same time period. The output is an array of clusters of terminal data, which includes 
the terminal name, terminal ID, analog data, phasor data and digital data, all taken over the given time period. There is one cluster of
terminal data per terminal that is identified in the document.


First, the program determines the number of terminals in the file. 

![ScreenShot](https://github.com/ALSETLab/Ambient-Mode-Estimator/blob/master/pics/CSVReader_pic.png)


Next, it executes a for loop that passes through every row of data, besides the headers (already deleted using the Delete from Array subVI).
The terminal is determined by the iteration number divided by the number of terminals. The data put in the terminals is dependent on the 4
inputs: Format Type, Measurement Type, Frequency Type, and Digital Channel Selector. The options for each are as follows:

Format Type – Format A or Format B (the current supported original CSV formats)
Measurement Type - Power or Voltage or Current
Frequency Type - Frequency or d(Frequency)/dt
Digital Channel Selector - 1 or 2 or 3 (the Format B files may have values for some, all, or none of these channels)

**This set of inputs [besides the "FORMAT type" input] was designed to mimic the PRL Channel Selector from the S3DK toolkit, where the user 
selects a phasor data channel (either a voltage or current channel), an analog channel (Frequency, df/dt, none) and a digital channel.**

The program will obtain phasor values, analog values and digital values in accordance with the user's settings. This data is processed row 
by row - automatically placed in time order in the cluster pertaining to the terminal it applies to. In addition, the Terminal Names and 
ID's are extracted from the data and placed in their respective Terminal Data clusters.



*This program will not run if an error is input into the program or if an error occurs from Read Delimited Spreadsheet.vi.*

*Also note that this differs from the operation in Version 2.0, where its version of the CSV Reader (there entitled Format CSV) operates on one row per occurrence. In Main.vi Version 1.1, if the CSV option is selected, CSV Reader.vi will run one time and the data will be retained for the rest of the run of Main.vi (v1.1).*

