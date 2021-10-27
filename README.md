# Maya 2022.1 package for Arch Linux
Use it at your own risk.   
## About
Based on thanks to [AUR maya package & forum](https://aur.archlinux.org/packages/maya/)

Pay Maya if you like it or learn Blender :)
## Install
### -1 Firs of all you need to recompile `libtiff`.
See: [libtiff-for-maya-arch](https://github.com/aaronrancsik/libtiff-for-maya-arch)
### 0. Download Maya BIG archive.
[Official Link](https://trial2.autodesk.com/NetSWDLD/2022/MAYA/8A2BC89C-9B8B-33FC-949F-C7CAE28366A4/ESD/Autodesk_Maya_2022_1_ML_Linux_64bit.tgz)

`cd /tmp && wget -O Maya20221_BIG.tgz shorturl.at/aduIW`
### 1. Extract to BIG folder with GUI or in Terminal

`mkdir /tmp/Maya20221_BIG`

`cd /tmp/Maya20221_BIG`

`tar zxvf ../Maya20221_BIG.tgz`
### 2. Get this package source.
#### Select a dir
`cd /tmp/`

Or somewhere else if you want keep it.
#### Choose one:

#### A. Git HTTPS

`git clone https://github.com/aaronrancsik/maya-arch.git`

#### B. Git SSH
`git clone git@github.com:aaronrancsik/maya-arch.git`
### 3. Get maya's installer .rpm from the BIG folder. 
`cp /tmp/maya20221_BIG/Packages/Maya2022_64-2022.1-579.x86_64.rpm /tmp/maya-arch/`
### 4. Install aur dependencies
For example with `paru`.

`paru -S libpng15 ncurses5-compat-libs --asdeps`

You can use another aur helper like `yay`.
### 5. Create package & Install
`cd /tmp/maya-arch`

`makepkd -s`

`pacman -U maya-2022.1-1-x86_64.pkg.tar.zst`
### 6. Start maya from GUI or Terminal, click 'Go to Maya' than close it.
`/usr/autodesk/maya2022/bin/maya2022`
### 7. Finishing touch to disable telemetry.
`chmod -rwx ~/.autodesk/UI/Autodesk/ADPSDK/JSON/`
### 8. It's done.
