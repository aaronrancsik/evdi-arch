# Maintainer: PlusMinus

pkgname=evdi
pkgver=1.2.64
pkgrel=3
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
#source=($pkgname-$pkgver-$pkgrel.tar.gz::https://github.com/DisplayLink/evdi/archive/v$pkgver.tar.gz)
source=(b7606bccc0cb9484c2845a3e556faf60ed3c0bff.tar.gz::https://github.com/DisplayLink/evdi/archive/b7606bccc0cb9484c2845a3e556faf60ed3c0bff.tar.gz)
noextract=()
md5sums=('2f229d85de2aa5c1ba6f168a0728ec9d')

build() {
# We only need to build the library in this step, dmks will build the module
mv evdi-b7606bccc0cb9484c2845a3e556faf60ed3c0bff $pkgname-$pkgver
cd "$pkgname-$pkgver/library"

make
}

package() {
# Predfine some target folders
SRCDIR="$pkgdir/usr/src/$pkgname-$pkgver"	# This one is needed for dkms
LIBNAME=lib$pkgname

cd "$pkgname-$pkgver"

install -D -m 755 library/$LIBNAME.so $pkgdir/usr/lib/$LIBNAME.so

install -d $SRCDIR
install -D -m 755 module/* $SRCDIR
}
