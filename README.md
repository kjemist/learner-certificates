Modifications from 2024:

* Made compatible with windows

# How-to (from SWC Bergen 2024, on Windows 10)

:::
1. Make sure cairosvg is installed. Even if pip is succesful in installing these files, you might be unable to retrieve the library. Follow the steps [from this Stack Overflow post](https://stackoverflow.com/a/60220855/11598009). If you have Inkscape installed on your computer (I did in May 2024), the dlls should be under "C:\Program Files\Inkscape\bin". If they are in a different folder, you will need to edit the Python script to reflect the location of this (line 56, see the Stack overflow question)
2. clone this repo (git clone git@github.com:kjemist/learner-certificates.git)
3. create a folder named 'templates'
4. Create a csv-file called 'attendance_names' in the folder from step 3.
> swc-attendance,Grace Hopper,turing_alan,Alan Turing,alan@turing.org,2016-01-27
with rows of attendee-names (no commas between rows). The email is not used in the certificate pdf, so the placeholder alan@turing.com can be used. The first parameter must match the template name (swc-attendance), and the script will have an easier time finding this if it is placed in an appropiate subfolder (see step 3)
5. run
'''
python .\bin\certificates.py -r .\templates\ -c .\attendance_names.csv
'''
6. The pdfs should be in templates/swc_attendance/

use the python script 'certificates.py' in bin/

# Certificates for The Carpentries


There are two ways to build certificates from this repo, one depends on the python package cairosvg which in turn depends on cairo development libraries being installed. To use this method, use `bin/certificates.py` to build certificates.

The second, pure python method uses the python packages jinja2, jinja2-cli and svglib to build the certificates.

To build certificates this way, you can run:
```
jinja2 swc-attendance.svg -D name="Firstname Lastname" -D date="Nov. 6, 2017" -D instructor="Some Instructor Name" > lastname_firstname.svg
svg2pdf lastname_firstname.svg 
```

