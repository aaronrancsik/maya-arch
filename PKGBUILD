# Maintainer ~ kyle[dot]devir[at]mykolab[dot]com
# Co-Maintainer: William Tang <ttan0037@student.monash.edu>
# Co-Maintainer: Ilya Chelyadin  <ilya77105@gmail.com>
# Contributor: Luca Weiss <luca (at) z3ntu (dot) xyz>

pkgname=maya
pkgver=2022.1
pkgrel=1
pkgdesc='Autodesk Maya 3D Animation, Modelling, Simulation and Rendering Software'
arch=('x86_64')
url='http://www.autodesk.com/products/maya/overview'
license=('custom')
depends=('glu' 'gst-plugins-base-libs' 'gtk2' 'gts' 'lib32-glibc' 'libjpeg6-turbo' 'libpng15' 'libpulse'
         'libtool' 'libxaw' 'libxkbcommon-x11' 'libxtst' 'ncurses5-compat-libs' 'xcb-util-image' 'xcb-util-keysyms'
         'xcb-util-renderutil' 'xcb-util-wm' 'audiofile' 'xorg-fonts-75dpi' 'xorg-fonts-100dpi')
optdepends=(
            'maya-arnold: Maya Arnold Renderer Plugin'
            'maya-bifrost: Maya Bifrost Effects Plugin'
            'maya-rokoko-motion-library: Maya Rokoko Motion Library Animation Plugin'
            'maya-substance: Maya Substance Material Plugin'
            'maya-usd: Maya Universal Scene Description Plugin')
makedepends=(
  'bsdiff'
  )

DLAGENTS+=('manual::/usr/bin/echo \ \ Note: Please download the package manually from the official website')
source=(
  'manual://Maya2022_64-2022.1-579.x86_64.rpm'
  'maya.patch'
)
sha256sums=(
  'a7932fdaf15b52b19908314c6b575f2ca4037871f26c3feaf907b091ba493817'
  '6a97ebc0b9234aac1c457ba5db9ea68c1f05d71aa1b9e2c846c0a030eff1d757'
)

options=(!strip)

prepare() {
    # Fix symbol links
    mkdir -p usr/autodesk/maya2022/lib
    ln -sf /usr/lib/libssl.so.1.1 usr/autodesk/maya2022/lib/libssl.so.10
    ln -sf /usr/lib/libcrypto.so.1.1 usr/autodesk/maya2022/lib/libcrypto.so.10
    ln -sf /usr/lib/libffi.so.7.1.0 usr/autodesk/maya2022/lib/libffi.so.6

    # Fix tmp directory
    ln -sf /tmp usr/tmp

    # Move destop file
    sed -i 's/maya/maya2022/g' usr/autodesk/maya2022/desktop/Autodesk-Maya.desktop
    mkdir -p usr/share/applications
    mv usr/autodesk/maya2022/desktop/Autodesk-Maya.desktop usr/share/applications/maya.desktop

    # Remove redundant file
    rm usr/autodesk/maya2022/desktop/Autodesk-Maya.directory
}

package() {
    mv opt usr var $pkgdir/
    mv $pkgdir/usr/autodesk/maya2022/bin/ADPClientService $pkgdir/usr/autodesk/maya2022/bin/ADPClientService_NOTHANKYOU
    touch $pkgdir/usr/autodesk/maya2022/lib/libmd.so
    mv $pkgdir/usr/autodesk/maya2022/bin/maya.bin $pkgdir/usr/autodesk/maya2022/bin/maya.bin.orig
    #       src                                             dest                                       patch
    bspatch $pkgdir/usr/autodesk/maya2022/bin/maya.bin.orig $pkgdir/usr/autodesk/maya2022/bin/maya.bin $srcdir/maya.patch
    chmod +x $pkgdir/usr/autodesk/maya2022/bin/maya.bin
}
