# Maintainer: PlusMinus

pkgname=evdi
pkgver=1.3.43
pkgrel=1
pkgdesc="A Linux® kernel module that enables management of multiple screens."
arch=('i686' 'x86_64')
url="https://github.com/DisplayLink/evdi"
license=('GPL')
groups=()
depends=(dkms)
makedepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=$pkgname.install
changelog=$pkgname.Changelog
source=($pkgname-$pkgver.tar.gz::https://github.com/DisplayLink/evdi/archive/v$pkgver.tar.gz)
noextract=()
md5sums=('08b08e873f5b4f70929a126427150152')

build() {
  # We only need to build the library in this step, dmks will build the module
  cd "$pkgname-$pkgver/library"

  make
}

package() {
  # Predfine some target folders
  SRCDIR="$pkgdir/usr/src/$pkgname-$pkgver"		# This one is needed for dkms
  LIBNAME=lib$pkgname

  cd "$pkgname-$pkgver"

  install -D -m 755 library/$LIBNAME.so $pkgdir/usr/lib/$LIBNAME.so
  
  install -d $SRCDIR
  install -D -m 755 module/* $SRCDIR
}
