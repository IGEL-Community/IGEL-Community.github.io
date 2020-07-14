# Building Custom Partition Scripts

## Summary of steps to create custom partitions

•	Setup lab environment
•	Download Linux package
•	Unpack the package on a Linux system
•	Create the initialization script
•	Compress the custom partition contents
•	Write the \*.inf Metadata file
•	Upload the files to the UMS
•	Create a UMS profile for the custom partition
•	Assign the profile, check for missing libraries, and test the application


## Finding and adding missing shared libraries

Find the missing libraries on the IGEL OS.

On IGEL OS:
```{find missing shared libraries}
cd /custom/zoom
find . -executable -type f -exec ldd ‘{}’ \; | grep ‘not found’ >> /custom/ldd.txt
  ```

On Linux Ubuntu:
```{download missing libraries and add to CP}
apt download <filename>
dpkg -x <filename>.deb zoom
  ```

To seach for missing libraries to download:  https://packages.ubuntu.com/bionic/allpackages


## Microsoft Teams

|  CP Information |            |
|-----------------------|------------|
| Package | Microsoft Teams 1.3.00.16851|
| Script Name | [msteams-cp-init-script.sh](msteams-cp-init-script.sh) |
| CP Mount Path | /custom/msteams |
| CP Size | 400M |
| IGEL OS Version (min) | 11.3.110 |
| Metadata File <br /> msteams-1.3.00.16851.inf | [INFO] <br /> [PART] <br /> file="msteams_amd64_1.3.00.16851.tar.bz2" <br /> version="1.3.00.16851" <br /> size="400M" <br /> minfw="11.03.110" |
| Path to Executable | /custom/msteams/usr/bin/teams |
| Path to Icon | /custom/msteams/usr/share/pixmaps/teams.png |
| Missing Libraries | libboost_filesystem.so.1.58.0 <br /> libboost_system.so.1.58.0 <br /> libcapnp-0.5.3.so <br /> libgnome-keyring.so.0 <br /> libkj-0.5.3.so <br /> libmirclient.so.9 <br /> libmircommon.so.7 <br /> libmircore.so.1 <br /> libmirprotobuf.so.3 <br /> libprotobuf-lite.so.9 |


## Zoom

|  CP Information |            |
|-----------------------|------------|
| Package | Zoom 5.1.422789.0705|
| Script Name | [zoom-cp-init-script.sh](zoom-cp-init-script.sh) |
| CP Mount Path | /custom/zoom |
| CP Size | 200M |
| IGEL OS Version (min) | 11.3.110 |
| Metadata File <br /> zoom-5.1.422789.0705.inf | [INFO] <br /> [PART] <br /> file="zoom_amd64._5.1.422789.0705.tar.bz2" <br /> version="5.1.422789.0705" <br /> size="200M" <br /> minfw="11.03.110" |
| Path to Executable | /custom/zoom/usr/bin/zoom |
| Path to Icon | /custom/zoom/usr/share/pixmaps/Zoom.png |
| Missing Libraries | libqt53dcore5_5.9.5+dfsg-0ubuntu2_amd64.deb <br /> libqt53dinput5_5.9.5+dfsg-0ubuntu2_amd64.deb <br /> libqt53dlogic5_5.9.5+dfsg-0ubuntu2_amd64.deb <br /> libqt53dquick5_5.9.5+dfsg-0ubuntu2_amd64.deb <br /> libqt53dquickscene2d5_5.9.5+dfsg-0ubuntu2_amd64.deb <br /> libqt53drender5_5.9.5+dfsg-0ubuntu2_amd64.deb <br /> libqt5concurrent5_5.9.5+dfsg-0ubuntu2.5_amd64.deb <br /> libqt5gamepad5_5.14.2-2_amd64.deb <br /> libqt5gui5_5.9.5+dfsg-0ubuntu2.5_amd64.deb <br /> libqt5multimedia5_5.9.5-0ubuntu1_amd64.deb <br /> libqt5quickcontrols2-5_5.9.5-0ubuntu2_amd64.deb <br /> libqt5quickparticles5_5.9.5-0ubuntu1.1_amd64.deb <br /> libqt5quicktemplates2-5_5.9.5-0ubuntu2_amd64.deb <br /> libqt5xmlpatterns5_5.9.5-0ubuntu1_amd64.deb <br /> libsdl2-2.0-0_2.0.8+dfsg1-1ubuntu1.18.04.4_amd64.deb <br /> libsndio6.1_1.1.0-3_amd64.deb <br /> libxcb-xtest0_1.13-2~ubuntu18.04_amd64.deb |
