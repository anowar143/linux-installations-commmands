
## Install Bijoy
### Step 1

```
sudo apt-get install ibus-m17n
sudo chmod 777 /usr/share/m17n/
sudo chmod 777 /usr/share/m17n/icons/
```
### Download & Unzip folder
##### https://drive.google.com/file/d/1mWaUlA1AH5LXsTxv553z8UK9hIS-UDTF/edit


### Step 2

#### Open Terminal in Unziped folder then type following command:

```
mv bn-bijoyClassic.mim /usr/share/m17n/
mv bn-bijoyUnicode.mim /usr/share/m17n/
mv bn-bijoyClassic.png /usr/share/m17n/icons/
mv bn-bijoyUnicode.png /usr/share/m17n/icons/
sudo chmod 777 /var/lib/dpkg/info/m17n-db.list
```


### Step 3

#### nano /var/lib/dpkg/info/m17n-db.list
##### and put the following code 

```
/usr/share/m17n/icons/bn-bijoyClassic.png
/usr/share/m17n/icons/bn-bijoyUniconde.png
/usr/share/m17n/bn-bijoyClassic.mim
/usr/share/m17n/bn-bijoyUniconde.mim
```


### Step 4

#### Linux : Find out and go to "Startup Applications" on your system and open it.
##### In the pop box Click on "Add" and fill the empty according to the below.

```
Name: IBus Daemon
Command:/usr/bin/ibus-daemon -d
Comment: Start IBus daemon when Gnome starts

```
##### Restart your System

### Step 5
#### Go to Unziped folder and find out "SutonnyMJ" Folder, Then install following files manualy by click on them one by one
```
install SutonnyMJ-Bold.ttf, SutonnyMJ-Bolditalic.ttf, SutonnyMJ-Italic.ttf, SutonnyMJ-Regular.ttf
```

### Step 6

```
Setting > Region & Language > Input Sources
+  -  here click to '+'  search Bangla/bijoyUnicode(m17n)  to add
+  -  here click to '+'  search Bangla/bijoyClassic(m17n)  to add
```

### Complete Installations
