# Raman_Sugars
Dataset of Raman spectra collected from a set of sugar mixtures

## Motivation
The goal of this dataset is to serve as a benchmark dataset for the development of new spectral analysis techniques. 

## Dataset
Two datasets are contained in this repository, corresponding to the measured Raman response of a series of sugar and water mixtures (see Experimental Methods). In particular, a total of 245 combinations of 4 sugars + water have been measured. The two datasets, *Sugar_Concentration_Test* and *Sugar_Concentration_Test_Fast*, are generated from measuring the same mixtures but with different integration times, resulting in different levels of signal-to-noise ratio. Each measurement was repeated several times. In particular, each mixture in the *Sugar_Concentration_Test* dataset was measured a total of 8 times, while the ones in the *Sugar_Concentration_Test_Fast* were measured a total of 32 times, resulting in 1960 and 7840 observations, respectively.

## Data Structure
Two .csv files containing all the spectral information are provided *Sugar_Concentration_Test_ALL_spectra.csv* and *Sugar_Concentration_Test_Fast_ALL_spectra.csv*. In these files, the wavenumber is provided in the first column ('Wavenumber [cm-1]'), and the spectra for each measurement are provided in the column with the name corresponding to the measurement name, which is structured as: *Sugar_Concentration_Test{_Fast}_1_{WellCode}_{Plate#}_RD{Round#}_M1_R{Repetition#}* (e.g., *Sugar_Concentration_Test_1_D3_2_RD2_M1_R3* corresponds to the third repetition measurement of the second round of the measurement of the D3 well of the second plate). Thus, the information about the well plate and repeat and round can be extracted from the name, but it is also found in the corresponding metadata .csv files named *Sugar_Concentration_Test_ALL_metadata.csv* and *Sugar_Concentration_Test_Fast_ALL_metadata.csv*, respectively.

Finally, the raw data is separated into two folders 'Sugar_Concentration_Test' and 'Sugar_Concentration_Test_Fast' for the high and low integration times, respectively (see Materials and Methods). Each measurement is in an individual .csv file with five columns:
* Pixel: Corresponding to the pixel in the
* wl: Wavelength, converted from the pixel with the calibration made in the spectrometer.
* cm-1: Wavenumber, converted from the wavelength and the excitation (785m).
* Intensity: Intensity of the Raman scattering signal
* Metadata: Contains metadata about the measurement, including time, excitation power, etc.

Note that no pre-processing has been performed such that the user can decide what is best for the analysis. 

An [example Python notebook](https://colab.research.google.com/drive/1u5U2aYW_5c2b5Tp3Jt_t7rXN9s5IiT9A?usp=sharing) is provided to extract the information from each file. The same information can be found in the file *Example_Readout_Raman_Sugars.py*

## Experimental Methods
For the experiment, four different sugar solutions (Sucrose, Fructose, Maltose, and Glucose) were mixed along with water in various concentrations, and the Raman spectral response of the mixture was measured using a custom Raman microspectometer platform known as [B-Raman](b-raman.com). 

### Preparation of sugar solutions
We prepared four sugar solutions, each one to have a 1M sugar concentration. To that end, the following mixtures were prepared:
* 13.83 g of Sucrose ([Thermo Scientific Chemicals -- Sucrose, 99%](https://www.thermofisher.com/order/catalog/product/A17718.30?SID=srch-srp-A15583.36)) were added to 40 mL of ultrapure water distilled water ([Invitrogen™ -- UltraPure™ DNase/RNase-Free Distilled Water](https://www.thermofisher.com/order/catalog/product/10977049?SID=srch-srp-10977049))
* 7.279 g of Fructose ([Thermo Scientific Chemicals -- D-Fructose, 99%](https://www.thermofisher.com/order/catalog/product/A17718.30?SID=srch-srp-A17718.30)) were added to 40 mL of ultrapure water distilled water ([Invitrogen™ -- UltraPure™ DNase/RNase-Free Distilled Water](https://www.thermofisher.com/order/catalog/product/10977049?SID=srch-srp-10977049))
* 15.171 g of Maltose ([Thermo Scientific Chemicals -- D-(+)-Maltose monohydrate, 95%](https://www.thermofisher.com/order/catalog/product/A17718.30?SID=srch-srp-A16266.36)) were added to 40 mL of ultrapure water distilled water ([Invitrogen™ -- UltraPure™ DNase/RNase-Free Distilled Water](https://www.thermofisher.com/order/catalog/product/10977049?SID=srch-srp-10977049))
* 7.279 g of Glucose ([D-(+)-Glucose, AnalaR NORMAPUR® analytical reagent](https://uk.vwr.com/store/product/2340278/d-glucose-analar-normapur-analytical-reagent)) were added to 40 mL of ultrapure water distilled water ([Invitrogen™ -- UltraPure™ DNase/RNase-Free Distilled Water](https://www.thermofisher.com/order/catalog/product/10977049?SID=srch-srp-10977049))

All the solutions were mixed and vortexed in standard 50 mL centrifuge tubes until no solute was visible.

### Preparation of sugar mixtures
The different sugar mixtures were prepared in standard 96-well plates. In particular, a full factorial experiment was prepared following the following volumes:
* 4 volume levels for each sugar: 0 ul, 30 ul, 75 ul, and 120 ul
* 4 total sugars: Sucrose, Fructose, Maltose, and Glucose
* 375 ul of total volume, filled with [Invitrogen™ -- UltraPure™ DNase/RNase-Free Distilled Water](https://www.thermofisher.com/order/catalog/product/10977049?SID=srch-srp-10977049)
* 5 extra wells of *pure* solutions (i.e., 375 ul of water, Sucrose, Fructose, Maltose, and Glucose, respectively)

In total, this resulted in a total of 245 wells, which were distributed in three standard 96-well plates. The exact distribution of each well can be found in the 'Sugar_Concentration' files, where each well is identified as {RowLetter}{ColumnNumber}_{PlateNumber} (e.g., D3_2 corresponds to the D3 well of the second well plate).

After the mixtures were prepared in the well plates, all wells were mixed using standard 200ul pipettes to ensure a proper mixture.

Mixtures were prepared by Dr. Alvaro Fernandez Galiana and George Papadopoulos.

### Measurement of Raman spectra
All the spectra were acquired in a custom Raman microspectroscopy platform particularly designed for high-throughput analysis known as [B-Raman](b-raman.com). The instrument was calibrated using an Argon wavelength calibration source ([AR-2 -- Ocean Insight](https://www.oceaninsight.com/products/light-sources/calibration-sources/ar-2/?qty=1)) before the data was collected, and the following experimental conditions applied:
* Excitation wavelength: 785 nm
* Excitation power: 36.3 mW
* Objective: [Leica N PLAN 10x/0.25](https://www.leica-microsystems.com/objectivefinder/objective/506405/)
* Numerical apperture (NA): 0.25
* Approximate excitation beam waist radius (w_0): 40 um

* Spectral resolution: 230 nm
* Acquisition range: 142 cm-1 - 3684.8 cm-1

For each well, the spectra were measured at the center (horizontal) of the well and at a depth that was established to provide the highest signal, and all measurements were made at the same depth. The spectra for each well were obtained several times, divided into repetitions and rounds. Repetitions are the number of times that a well was probed before moving into the next one, that is, the number of consecutive spectra that were acquired at each well. Conversely, the round represents the number of times that the whole plate was scanned. Therefore, 4 repetitions and 3 rounds would give a total of 12 measurements per well (i.e., each well was scanned 3 times and, each time, 4 consecutive measurements were made). Overall, the goal of this collection strategy is to provide consistency and to be able to detect (and correct) potential temporal effects (as the measurements between each round are more spaced in time than the different repetitions). Overall, two sets of measurements were made and are divided into two folders:
* Sugar_Concentration_Test: High integration time for higher SNR
    * Integration time: 5 s
    * Number of repeats: 4
    * Number of rounds: 2
* Sugar_Concentration_Test_Fast: Low integration time for lower SNR, measured 24h after preparation and after higher SNR measurement.
    * Integration time: 0.5 s
    * Number of repeats: 4
    * Number of rounds: 8
 
Spectral acquisition was performed by Dr. Alvaro Fernandez Galiana.

#### Notes on measurement times
For the high SNR dataset, Plate 2 was measured right after sample preparation, whereas Plates 1 and 3 were measured 4 and 2 hours after preparation, respectively. All measurements for the low SNR dataset were performed 24 hours after sample preparation.

## Contact
For any questions regarding the dataset or its use, please reach out to: 

* Alvaro Fernandez Galiana (afernandezgaliana@schmidtsciencefellows.org)

