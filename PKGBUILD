# Maintainer: Tom Ingleby <tom@ewsting.org>
pkgname='mraa'
pkgver=2.1.0
pkgrel=1
pkgdesc="Low Level Skeleton Library for IO Communication on GNU/Linux platforms."
makedepends=('git' 'cmake' 'swig')
depends=('json-c')
optdepends=('python: for Python support' 'python2: for Python2 support')
url="https://github.com/intel-iot-devkit/mraa"
license=('MIT')
arch=('x86_64' 'i686' 'aarch64')

source=("git+https://github.com/radxa/mraa.git#tag=v$pkgver"
        'https://github.com/eclipse/mraa/commit/aaa0a5cd4e401bde4fb3691dd4e6c70a5c61e031.patch')
md5sums=('SKIP'
         '0efee4cb9906a7ce8dd4d57ad29ffc48')

prepare() {
        cd ${srcdir}/${pkgname}
        patch -Np1 -i "${srcdir}/aaa0a5cd4e401bde4fb3691dd4e6c70a5c61e031.patch"
}

build() {
  mkdir -p mraa/build
  cd mraa/build
  cmake -DCMAKE_INSTALL_PREFIX=/usr \
        -DINSTALLTOOLS=on -DBUILDSWIGNODE=off \
        -DCMAKE_INSTALL_LIBDIR=/usr/lib ../
  make -j
}

package() {
  cd $srcdir/mraa/build
  make DESTDIR="${pkgdir}/" install
}
