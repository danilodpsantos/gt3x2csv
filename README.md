# gt3x2csv

`gt3x2csv` is an R package designed to convert Actigraph gt3x files to csv files with the same data structure exported by the Actilife software.

## Installation

``` r
# Installs the development version from GitHub:

install.packages("devtools")

devtools::install_github("danilodpsantos/gt3x2csv")
```

## Usage

Soon

## Objective

This project was designed with the intent of converting files from the gt3x Actigraph generated files to csv files with the same structure used when exporting/converting raw accelerometer data in the csv format directly from the Actilife software.

## What is the problem? 

Recently, many large scientific studies are using raw accelerometer data to perform physical activity and sleep analysis, and one of the most used accelerometer brands is Actigraph. 
Actigraph uses the full license Actilife software to set the analysis and to export data from the devices. 
The raw accelerometer data can be exported from the Actilife software in 2 different formats, gt3x and csv. For a 24 hour/ 7 days protocol, with the data sampling frequency of 30 Hz, the size of the gt3x file gets around 50MB, while the csv file size is of around 500MB, which can generate an storage problem for large studies. Also, the Actilife software takes around 1 minute to convert each file to the csv format, and can process only one file at a time. For a study with 10.000 participants, the estimated time would be of 7 days only to convert all the files. 
Another point is the fact that many studies only have one full license of the Actilife software, making the data extracting / conversion a cumbersome task.
Most of the raw accelerometer data analysis is performed using the GGIR R package (https://cran.r-project.org/web/packages/GGIR/index.html) which provides extensive information about physical activity, sleep and 24 hour activity cycles. The GGIR package only accepts the Actigraph data structure if it was extracted to csv files, making it impossible to use the Actigraph proprietary gt3x file to perform the analysis.
For chronobiology and time series analysis there are other packages and softwares such as ElTmps (http://www.el-temps.com/principal.html).

## How can this package help?

The `gt3x2csv` package makes the data processing and storage of raw accelerometer data feasible, since it allows the conversion of Actigraph raw accelerometer data exported in the .gt3x format to .csv files, enabling the use of packages like GGIR to process Actigraph data. 
The main advantages are that the conversion of 1 file takes around 30 seconds (half the time of Actilife software) and the csv file size for a 24 hour/ 7 days collection protocol is around 250MB (half the size of the csv exported from Actilife software).
Another advantage is that the package allows for parallel data processing, enabling the processing of more than one file at a time.
Last, but not least, the package lets researchers which have .gt3x files and don't have the Actilife software to perform their analysis without the need of the software.

## How does the package work?

The .gt3x file is a zip file containing a .txt file, with metadata about the data collection and a .bin file containing the accelerometer data.
The package uses the .txt file to generate the header of the csv file with the information about the protocol and the .bin file to read the data (through `read.gt3x` R package) and record it in the the csv file (using `data.table` R package). The `read.gt3x` package implements a c++ code to read .gt3x files, which makes it fast and smooth (for more information look at: https://github.com/THLfi/read.gt3x). 

## Author

Danilo de Paula Santos (https://github.com/danilodpsantos)

## Contributors

Rodrigo Citton Padilha dos Reis (https://github.com/rdosreis)
Angelo Bastos (https://github.com/angelorbastos)
Fernando Souza (https://github.com/fcsest)
