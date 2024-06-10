# Melissa - Global Address Object Linux Python3

## Purpose

This code showcases the Melissa Global Address Object using Python3.

Please feel free to copy or embed this code to your own project. Happy coding!

For the latest Melissa Global Address Object release notes, please visit: https://releasenotes.melissa.com/on-premise-api/global-address-object/

For further details, please visit: https://docs.melissa.com/on-premise-api/global-address-object/global-address-object-quickstart.html

The console will ask the user for:

- Address Line 1
- Address Line 2
- Address Line 3
- Locality
- Administrative Area
- Postal Code
- Country

And return 

- Melissa Address Key (MAK)
- Company
- Address Line 1
- Address Line 2
- Address Line 3
- Address Line 4
- Address Line 5
- Locality
- Administrative Area
- Postal Code
- Postbox
- Country
- Country ISO 2
- Country ISO 3
- Latitude
- Longitude
- Formatted Address
- Result Codes

## Tested Environments

- Linux 64-bit Python 3.8.7, Ubuntu 20.04.05 LTS
- Melissa data files for 2024-Q2

## Required File(s) and Programs

#### Binaries

This is the c++ code of the Melissa Object.

- libmdAddr.so
- libmdGeo.so
- libmdGlobalAddr.so
- libmdRightFielder.so

#### Data File(s)
- Addr.dbf
- Congress.csv
- dph256.dte
- dph256.hsa
- dph256.hsc
- dph256.hsd
- dph256.hsf
- dph256.hsn
- dph256.hsp
- dph256.hsr
- dph256.hst
- dph256.hsu
- dph256.hsv
- dph256.hsx
- dph256.hsy
- dph256.hsz
- ews.txt
- icudt52l.dat
- lcd256
- mdAddr.dat
- mdAddr.lic
- mdAddr.nat
- mdAddr.str
- mdAddrKey.db
- mdAddrKeyCA.db
- mdCanada3.db
- mdCanadaPOC.db
- mdGeoCode.db3
- mdGlobalAddr.ffbb
- mdGlobalAddr.ffhb
- mdGlobalAddr.ffpl
- mdGlobalAddr.ffps
- mdGlobalAddr.ffst
- mdGlobalAddr.sac
- mdLACS256.dat
- mdRBDI.dat
- mdRightFielder.cfg
- mdRightFielder.dat
- mdSteLink256.dat
- mdSuiteFinder.db
- month256.dat

## Getting Started
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

This project is compatible with Python3

#### Install Python3
Before starting, make sure that Python3 has been correctly installed on your machine and your environment paths are configured. 

You can download Python here: 
https://www.python.org/downloads/

You can check that your environment is set up correctly by opening a command prompt window and typing the following:
`python3 --version`

![alt text](/screenshots/python_version.PNG)

If you see the version number then you have installed Python3 and set up your environment paths correctly!

----------------------------------------

#### Download this project
```
$ git clone https://github.com/MelissaData/GlobalAddressObject-Python3-Linux
$ cd GlobalAddressObject-Python3-Linux
```

#### Set up Melissa Updater 


Melissa Updater is a CLI application allowing the user to update their Melissa applications/data. 

- In the root directory of the project, create a folder called `MelissaUpdater` by using the command: 

  `mkdir MelissaUpdater`

- Enter the newly created folder using the command:

  `cd MelissaUpdater`

- Proceed to install the Melissa Updater using the curl command: 

  `curl -L -O https://releases.melissadata.net/Download/Library/LINUX/NET/ANY/latest/MelissaUpdater`

- After the Melissa Updater is installed, you will need to change the Melissa Updater to an executable using the command:

  `chmod +x MelissaUpdater`

- Now that the Melissa Updater is set up, you can now proceed to move back into the project folder by using the command:
  
   `cd ..`

----------------------------------------

#### Different ways to get data file(s)
1.  Using Melissa Updater
    - It will handle all of the data download/path and .so file(s) for you. 
    - **Please be aware that this object will require about 100GB of disk space.**
2.  If you already have the latest release zip, you can find the data file(s) in there
    - To pass in your own data file path directory, you may either use the '--dataPath' parameter or enter the data file path directly in interactive mode.
    - Comment out this line "DownloadDataFiles $license" in the bash script.
    - This will prevent you from having to redownload all the files.
	
### Change Bash Script Permissions
To be able to run the bash script, you must first make it an executable using the command:

`chmod +x MelissaGlobalAddressObjectLinuxPython3.sh`

Then you need to add permissions to the build directory with the command:

`chmod +rwx MelissaGlobalAddressObjectLinuxPython3`

As an indicator, the filename will change colors once it becomes an executable.

You may also need to alter permissions for the python files. To do this navigate into the MelissaGlobalAddressObjectLinuxPython3 directory and run these commands: \
`chmod +rx MelissaGlobalAddressObjectLinuxPython3/MelissaGlobalAddressObjectLinuxPython3.py` \
`chmod +rx MelissaGlobalAddressObjectLinuxPython3/mdAddr_pythoncode.py`

## Run Bash Script
Parameters:
- --addressLine1: a test address line 1
- --addressLine2 (optional): a test address line 2
- --addressLine3 (optional): a test address line 3
- --locality: a test locality
- --administrativeArea: a test administrative area
- --postalCode: a test postal code
- --country: a test country
 	
  These are convenient when you want to get results for a specific address in one run instead of testing multiple addresses in interactive mode.

- --dataPath (optional): a data file path directory to test the Global Address Object
- --license (optional): a license string to test the Global Address Object
- --quiet (optional): add to the command if you do not want to get any console output from the Melissa Updater

When you have modified the script to match your data location, let's run the script. There are two modes:
- Interactive 

	The script will prompt the user for an address line 1, address line 2, address line 3, locality, administrative area, postal code, and country, then use the provided inputs to test Global Address Object. For example:
	```
	$ ./MelissaAddressObjectLinuxPython3.sh
	```
    For quiet mode:
    ```
    $ ./MelissaAddressObjectLinuxPython3.sh -quiet
    ```
- Command Line 

	You can pass an address line 1, address line 2, address line 3, locality, administrative area, postal code, country, and a license string into the ```--addressLine1```, ```--addressLine2```, ```--addressLine3```, ```--locality```, ```--administrativeArea```, ```--postalCode```, ```--country```, and ```--license``` parameters respectively to test Global Address Object. For example:

    ```
    $ ./MelissaGlobalAddressObjectLinuxPython3.sh --addressLine1 "Melissa Data GmbH" --addressLine2 "Cäcilienstr. 42-44" --addressLine3 "50667 Köln" --country "Germany"
    $ ./MelissaGlobalAddressObjectLinuxPython3.sh --addressLine1 "Melissa Data GmbH" --addressLine2 "Cäcilienstr. 42-44" --addressLine3 "50667 Köln" --country "Germany" --license "<your_license_string>"
    ```

    For quiet mode:
    ```
    $ ./MelissaGlobalAddressObjectLinuxPython3.sh --addressLine1 "Melissa Data GmbH" --addressLine2 "Cäcilienstr. 42-44" --addressLine3 "50667 Köln" --country "Germany" --quiet
    $ ./MelissaGlobalAddressObjectLinuxPython3.sh --addressLine1 "Melissa Data GmbH" --addressLine2 "Cäcilienstr. 42-44" --addressLine3 "50667 Köln" --country "Germany" --license "<your_license_string>" --quiet
    ```
This is the expected output of a successful setup for interactive mode:

![alt text](/screenshots/output.PNG)

    
## Troubleshooting

Troubleshooting for errors found while running your program.

### Errors:

| Error      | Description |
| ----------- | ----------- |
| ErrorRequiredFileNotFound      | Program is missing a required file. Please check your Data folder and refer to the list of required files above. If you are unable to obtain all required files through the Melissa Updater, please contact technical support below. |
| ErrorDatabaseExpired   | .db file(s) are expired. Please make sure you are downloading and using the latest release version. (If using the Melissa Updater, check bash script for 'RELEASE_VERSION = {version}'  and change the release version if you are using an out of date release).     |
| ErrorFoundOldFile   | File(s) are out of date. Please make sure you are downloading and using the latest release version. (If using the Melissa Updater, check bash script for 'RELEASE_VERSION = {version}'  and change the release version if you are using an out of date release).    |
| ErrorLicenseExpired   | Expired license string. Please contact technical support below. |


## Contact Us

For free technical support, please call us at 800-MELISSA ext. 4
(800-635-4772 ext. 4) or email us at tech@melissa.com.

To purchase this product, contact the Melissa sales department at
800-MELISSA ext. 3 (800-635-4772 ext. 3).
