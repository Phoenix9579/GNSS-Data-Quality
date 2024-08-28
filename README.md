# GNSS reading protocol

This Gitlab repository documents a continued project to develope and maintain a 
set of Matlab source codes to be used for reading and processing GNSS 
observation and navigation files of various formats. Most notable among these 
are the RINEX3 file format. The source code included was initially developed by 
Bjørn-Eirik Roald (NMBU) as part of his master thesis, and is now maintained 
for further use and developement.

This repository contains the following different protocols, each comprised of 
multiple scripts:

- readRinexObs304
- readSP3


### readRinexObs304

readRinexObs304 is a protocol that may be used to read data from a RINEX3 
observation file. Currently this protocol is compatible with RINEX 3.02-3.04.
However, it will be further updated to encompass later updates in the RINEX 
file format. The source code for this protocol can be found in the directory
"readRinexObs304/readRinexObs304_sourcecode". The main function of this protocol is the Matlab script 
"readRinexObs304.m", but this script is dependent on the following scripts, all
of which are in the same directory:

- rinexFindNEpochs304.m
- rinexReadObsBlock304.m
- rinexReadObsBlockHead304.m
- rinexReadObsFileHeader304.m
- date2gpstime.m 

For a more fully encompassing guide to the use of this protocol, the user should 
read the user manual "ReadRinex3Obs_Manual.pdf", found in the directory 
"readRinexObs304\readRinexObs304_Manual". This presents detailed information on 
both the input arguments and the outputs of the protocol. If the user seeks 
inspiration for different ways to use the output data effectivly in Matlab, 
they should look at the example codes found in the directory 
"Example_codes\readRinexObs304".   


### readSP3

readSP3 is a protocol that may be used to read satellite navigation data from 
the SP3 file format. The protocol has currently been tested for formats SP3c 
and d, but will be developed to be compatible with future versions. The source 
code for this protocol can be found in the directory "readSP3". The 
main function of this protocol is the Matlab script "read_multiple_SP3Nav.m", 
which will read up to 3 SP3 files that are consecute in time, and that have the 
same GNSS systems and epoch interval. However, this script is dependent on the 
following scripts, all of which are in the same directory:

- readSP3Nav.m
- combineSP3Nav.m

Note that while "readSP3Nav.m" will read a single SP3 navigation file, it is 
still advised to use the parent function "read_multiple_SP3Nav.m", as it has 
more functionality, and will call upon "readSP3Nav.m".

If the user sets the inputs arguments boolean plot_overview to 1, an overview 
will be plotted showing which epochs the various satellites' navigation 
data is stored.

In addition to the function dedicated to reading data from the SP3 files, there 
is also a function "interpolatePreciseOrbits2ECEF.m" which will interpolate a 
satellite position from the SP3 data. This function is found in the same 
directory and is dependent on the following scripts:

- barylag.m

For a guide to how this protocol may be used, the user should look at the 
example code "readSP3_examples.m" in the directory "Example_codes\readSP3"   
