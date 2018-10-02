# Version 1.1 of the Mode Estimator Application

This application's purpose is to acquire Auto-Regressive/Moving Average (ARMA) coefficients of a signal coming from a PDC.

Version 1.1 is a functional, updated version from version 1.0, yet lacks the user friendly interface and versatility of version 2.0.
It resembles the algorithm loop of version 2.0.

The stages of this VI are as follows:

-    Initialize
-    Read Real Data / Read Simulated Data
-    Preprocessing
-    Compute AR Coefficients
-    Get Spectrum


## Initialize

The program analyzes whether the current run is a simulation or not. This value is taken from the boolean control "Simulate Data?"
In addition, all indicators (graphs, arrays) are reset.

## Read Real Data

1. Obtains PMU data from either a PDC source or a CSV file (current supported formats: Format A, Format B)

**Acquisition Settings**

PDC options (example: PDC Simulator): Select Data/channels. If the user wants to do a phase comparison, select another data set or 
channel. *Note: The program does not directly access a PDC source. Must be opened from another source (i.e. TestPDC.vi)*

CSV options (CSV Reader Inputs): File Input - input a CSV file (WAN/Format B), Measurement Type (Voltage/Current/Power), Frequency input
(Frequency or d(Frequency)/dt), Format selection (must match format)

Outputs: Timestamps - date/time of samples taken, Phasor Data - voltage/current/power data - user selection, Analog Data -
frequency or d(Frequency)/dt - user selection


2. Formats the data to match the user's signal selection.

**Signal Selection Options**

Real Component: Use the real component of the Phasor Data
Imaginary Component: Use the imaginary component of the Phasor Data
Analog: Use the Analog Data
Phase Comparison: Use a comparison of phase angles from two separate terminals
Magnitude: Use the magnitude of the Phasor Data


3. Creates a waveform with the data, using the user input sampling frequency and passes it on to Preprocessing.

## Read Simulated Data

The user can create a transfer function that is compunded with Gaussian White Noise to obtain a simulated signal.
Transfer Function options: Create by inputting a set of poles and zeros, or a damping ratio and input frequency.

The resulting waveform is passed to Preprocessing.

Note: Real time data is first shown before preprocessing occurs.
## Preprocessing

Detrends the input waveform, passes it through a low-pass filter, then downsamples it in Downsample.vi. Passes resulting waveform
to Compute AR Coeffs AND Get Spectrum.

## Compute AR/MA Coeffs

1. Passes the preprocessed waveform into a series of subVIs, extracting the AR and MA coefficients (displayed as a transfer function) in accordance with the AR and MA orders that were input by the user.

2. Converts back to the s-domain and finds complex poles, damping ratios and frequencies for each mode.

3. Records and displays damping ratio evolution throughout entire procedure (for each mode). Also determines the mean and standard deviation of each set of damping ratio history (per mode) and indicates whether it is above or below the "Std Threshold," using smiley.vi.

*Note: For the CSV acquisition option, due to the way the acquisition is structured, the damping ratio standard deviation will be close
to zero, which is inaccurate.*

## Get Spectrum

Obtains a spectrum (amplitude vs. frequency) and 3D spectrogram (amplitude vs. frequency vs. time).

Tip: User can see the spectrum graph on the spectrogram by hitting the bottom-right-most button on the spectrogram.


