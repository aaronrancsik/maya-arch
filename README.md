# Maya 2022.1 package for Arch Linux
Use it at your own risk.   
## About
Based on thanks to [AUR maya package & forum](https://aur.archlinux.org/packages/maya/)

Pay Maya if you like it or learn Blender :)
## Install
### -1 Firs of all you need to recompile `libtiff`.
See: [Libtiff with version script](https://example.com)
### 0. Download Maya 22.1 BIG archive.
[Official Link](https://trial2.autodesk.com/NetSWDLD/2022/MAYA/8A2BC89C-9B8B-33FC-949F-C7CAE28366A4/ESD/Autodesk_Maya_2022_1_ML_Linux_64bit.tgz)

`cd /tmp && wget -O Maya20221_BIG.tgz shorturl.at/aduIW`
### 1. Extract with GUI or in Terminal

`mkdir /tmp/maya221_BIG`

`cd /tmp/maya221_BIG`

`tar zxvf ../Maya20221_BIG.tgz`
### 2. Get this package source.
Clone it somewhere else if you want keep it.

`cd /tmp/ && git clone github.com/aaronrancsik/maya-arch`
### 3. Copy maya's installer .rpm from the BIG archive. 
`cp /tmp/maya221_BIG/Packages/Maya2022_64-2022.1-579.x86_64.rpm /tmp/maya-arch/`
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
