# Script for sorting photographs by date

This script will take a list of EXIF files (`.jpg`, `.arw`, .`cr2`, etc.) retrieve file dates
and place them in the directories named as follows:
```
${ROOT}/{raw,jpg}/YYYY/YYYY_MM_DD/
```
By default `${ROOT}` is set to `/backup_disk/home/vbendeb/docs/pictures`, the script needs to
be edited to change this.

Again, by default the files come from a removable media, say from a flash card plugged in into
a USB card reader. The script will find the removable media, mount it and look for image files
on it

If necessary a list of files and or directories containing image files to be copied can be
passed as command line parameter(s), in this case the script does not look for removable media.

The following command line parameters are accepted:
```
usage: file_handler [-h] [-a] [-t TIME_OFFSET]

Utility for copying files into directories based on EXIF file date

optional arguments:
  -h, --help            show this help message and exit
  -a, --add             if specified - add files to existing directories
  -t TIME_OFFSET, --time_offset TIME_OFFSET
                        if specified - time offset, hours to add to the photo timestamps
```
The `-a` parameter is handy when processing a card which has old and new files. Without `-a`
the script will presume that the files with dates falling into existing directories were
copied before, but were removed by the user for whatever reason. The script will just skip 
such files, only handling new files creating directories for them. If `-a` is given - all 
files will be copied unless they already exist at destination.

The `-t` parameter allows to adjust the EXIF timestamp in case the camera time did not match 
the time zone of the location where pictures were taken.