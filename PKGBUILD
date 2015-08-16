# Maintainer:
# Contributor: Tom Newsom <Jeepster@gmx.co.uk>

pkgname=metakit
pkgver=2.4.9.7
pkgrel=6
pkgdesc='Efficient embedded database library with a small footprint'
arch=('x86_64' 'i686')
url='http://www.equi4.com/metakit/'
license=('BSD')
makedepends=('tcl' 'python2')
source=("http://www.equi4.com/pub/mk/$pkgname-$pkgver.tar.gz")
sha256sums=('d1ba361d2d8517925cff5c23e8602822da9c8c347a75a15c225ec656ff7ca94d')

prepare() {
  cd "$pkgname-$pkgver/unix"

  sed -i 's_"${prefix}/include/python2.5"_"${prefix}/include/python2.7"_' configure
  sed -i 's_"${prefix}/lib/python2.5/site-packages"_"${prefix}/lib/python2.7/site-packages"_' configure
}

build() {
  cd "$pkgname-$pkgver/unix"

  ./configure \
    --prefix=/usr \
    --with-python \
    --with-tcl=/usr/include 
  make
}

package() {
  install -d "$pkgdir/usr/lib/python2.7/site-packages"
  make -C "$pkgname-$pkgver/builds" DESTDIR="$pkgdir" install
  install -Dm644 "$srcdir/$pkgname-$pkgver/license.terms" \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
