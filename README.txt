
*************************************
*
* README.txt file for SPHEREFIT v0.1
*
*************************************

This file specifies in a quick and easy way all the steps necessary to
successfully download and run SPHEREFIT. The directions that follow focus
on the "quickstart" mode of SPHEREFIT, where only light curves or spectra
can be calculated, for a user-specified combination of input physical
parameters. A thorough explanation of the source code, relevant variables,
user settings and steps to perform fits of model parameters to data is
provided in SPHEREFIT_guide.pdf, generated once SPHEREFIT.tgz is unarchived.

SPHEREFIT is written for Linux/OSx systems and requires a C++ compiler. The
only library necessary to run SPHEREFIT is the math library.

- DOWNLOADING AND EXTRACTING.

i) Once in the correct repository "KonstantinosLeventis/SPHEREFIT",
click on the SPHEREFIT.tgz target and then "View Raw". This should
initiate the download of SPHEREFIT.tgz in your downloads/ directory.

ii) Move the downloaded tgz file to a directory of your preference and
extract it, for example by typing
tar zxvf SPHEREFIT.tzg

iii) This will create the directory Spherefit_Public/ within the current
directory. Spherefit_Public/ contains SPHEREFIT_guide.pdf as well as the
following sub-directories:
bin/
data/
settings/
src/


- COMPILING AND RUNNING.

i) Go to the src/ directory and type
make clean all
This will result in the creation of the executable "spherefit" inside
the bin/ directory. Create a working directory (for example temp/) and
copy the executable "spherefit", the data file "default.txt" from the
data/ directory and the file "spherefitsettings.txt" from the settings/
directory into the newly created temp/.

ii) default.txt is a replacement of a real data file. The reason is
is that the executable spherefit expects a data file of a given format
(see SPHEREFIT_guide.pdf for details) to run. The simplest form of such
a file is default.txt. The dummy data included in this file are of course
not suitable for fitting but will serve the purpose of allowing spherefit
to run calculating a light curve or a spectrum for a set of user-defined
physical parameters.

iii) Open spherefitsettings.txt. Make sure that the "what_to_do" variable
is either set to 1 (calculation of a light curve) or 2 (calculation of
a spectrum). From that point on the user settings are subdivided into
categories. Make sure that data_filename = "default.txt" in the file I/O
settings" category. Right next, the "light curve and spectrum settings"
category allows you to specify the range and the frequency/observer time
of the calculated light curve/spectrum, as well as the number of data
points to be calculated during the run. The luminosity distance and
redshift of the source can be set in the "distance settings". Further
down the file, the category "initial values for the fit parameters" can
be found where the values of the model physical parameters can be set.
The rest of the user-defined settings are relevant only when fitting data
sets and are explained in SPHEREFIT_guide.pdf.

iv) Once all the desirable settings have been applied, save the
changes to spherefitsettings.txt and run the executable by typing
./spherefit
If what_to_do = 1, a file named lightcurve.txt will be created, while if
what_to_do = 2, the file will be named spectrum.txt. Both types of files
contain information on the user settings, as these have been defined
in spherefitsettings.txt, and the results of the calculations. After
several commented-out lines (those that start with the character "#"),
that also appear on screen, the file lightcurve.txt (or spectrum.txt)
contains 4 columns. The first column denotes the data- point number. The
second and third columns carry the observer time (in days) and frequency
(in Hz) of a datapoint, respectively. The fourth column contains the result
of the calculation, which is the observed flux, in units of mJy.

v) The results, as they appear in lightcurve.txt or spectrum.txt can
then be readily visualized with a plotting software, like gnuplot.
