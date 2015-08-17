# Maintainer: Patryk Kowalczyk < patryk at kowalczyk dot ws>
     
pkgname=spice
pkgver=0.12.3
pkgrel=1
pkgdesc="SPICE client and server"
arch=('i686' 'x86_64' 'arm')
url="http://spice-space.org"
license=('GPL')
makedepends=(python2-pyparsing)


#BUG - SUPPORT for : error: Package requirements (libcacard >= 0.1.2) were not met:
#	No package 'libcacard' found
if test "$CARCH" == x86_64; then
  makedepends+=(qemu)
fi
if test "$CARCH" == i686; then
  makedepends+=(qemu)
fi


depends=(pixman celt0.5.1 spice-protocol cegui-0.6 alsa-utils libxrandr libxinerama libsasl mesa openssl)

source=(http://spice-space.org/download/releases/$pkgname-$pkgver.tar.bz2)
    
build() {
      cd "$srcdir/$pkgname-$pkgver"
#      sed -i 's,/usr/bin/env python,/usr/bin/python2,' spice-common/spice_codegen.py
#      PYTHON=python2 \
      ./configure --prefix=/usr --enable-opengl --enable-gui --enable-smartcard --enable-client
      make
    }
package() {
      cd "$srcdir/$pkgname-$pkgver"
     
      make DESTDIR="$pkgdir/" install
    }
     
md5sums=('f33a682892f6793169f20298b2296449')
