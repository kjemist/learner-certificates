Modifications from 2024:

* Made compatible with windows

# How-to (from SWC Bergen 2024, on Windows 10)


1. Make sure cairosvg is installed. Even if pip is succesful in installing these files, you might be unable to retrieve the library. Follow the steps [from this Stack Overflow post](https://stackoverflow.com/a/60220855/11598009). If you have Inkscape installed on your computer (I did in May 2024), the dlls should be under "C:\Program Files\Inkscape\bin". If they are in a different folder, you will need to edit the Python script to reflect the location of this (line 56, see the Stack overflow question). The script 'certificates.py' in this repo has this line added to work with my computer.
2. clone this repo (git clone git@github.com:kjemist/learner-certificates.git) 
3. Create a csv-file called 'attendance_names.csv', and add rows in the following style:
> swc-attendance,Instructor Name,learner_name,Learner Name,alan@turing.org,2016-01-27
>
The first column is necessary for the template, the second is the instructor name (e.g "Name1 Namesen1"), then the output file name ("name2_namesen2"), then the learner name ("Name2 Namesen"), email (of whoever, will not be used), then date in the format YYYY_MM_DD. Make sure the file "swc-attendance.svg" is in the folder "templates".

4. run
```
python .\bin\certificates.py -r .\templates\ -c .\attendance_names.csv
```

6. The pdfs should be in templates/swc_attendance/


------------------------
Below is text from original repo

# Certificates for The Carpentries


There are two ways to build certificates from this repo, one depends on the python package cairosvg which in turn depends on cairo development libraries being installed. To use this method, use `bin/certificates.py` to build certificates.

The second, pure python method uses the python packages jinja2, jinja2-cli and svglib to build the certificates.

To build certificates this way, you can run:
```
jinja2 swc-attendance.svg -D name="Firstname Lastname" -D date="Nov. 6, 2017" -D instructor="Some Instructor Name" > lastname_firstname.svg
svg2pdf lastname_firstname.svg 
```

