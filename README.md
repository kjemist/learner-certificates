# Automatic generation of Software Carpentry Certificates as used in University of Bergen, Norway

Modifications from 2024:

* Made compatible with windows

## How-to (from SWC Bergen 2024, on Windows 10)


1. Make sure cairosvg is installed. Even if pip is succesful in installing these files, you might be unable to retrieve the library. Follow the steps [from this Stack Overflow post](https://stackoverflow.com/a/60220855/11598009). If you have Inkscape installed on your computer (I did in May 2024), the dlls should be under "C:\Program Files\Inkscape\bin". If they are in a different folder, you will need to edit the Python script to reflect the location of this (line 56, see the Stack overflow question). The script 'certificates.py' in this repo has this line added to work with my computer. \
**UPDATE 2024-11-21:** Added "C:\Program Files\Inkscape\bin" to PATH. This did the trick, and no path changing in Python was necessary :)

2. clone this repo (git clone git@github.com:kjemist/learner-certificates.git) 
3. Create a csv-file called 'attendance_names.csv', and add rows in the following style:
   
> `swc-attendance,<Instructor Name>,<file_name>,<learner name>,<email/>,<YYYY-MM-YY>`

or, if you wish to autogenerate the file name from the email addresses:

> `swc-attendance,<Instructor Name>,<learner name>,<email/>,<YYYY-MM-YY>`


**or**

use the template attendance-template.csv and fill in the missing values.

The first column is necessary for the template and is kept same for all entries, the second is the instructor name (e.g "Name1 Namesen1"), then the output file name (usually styled as "name2_namesen2"), then the learner name ("Name2 Namesen"), email (of whoever, will not be used), then date in the format YYYY_MM_DD. Make sure the file "swc-attendance.svg" is in the folder "templates".

4. run
```
python .\bin\certificates.py -r .\templates\ -c .\attendance_names.csv
```

**or** 

```
python .\bin\certificates.py -r .\templates\ -c .\attendance_names.csv -f
```

if you wish to autogenerate file names from the email column

5. The pdfs should be in templates/swc_attendance/

TODO: Make a script which automates sending of email

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

