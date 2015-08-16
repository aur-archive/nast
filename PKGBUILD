# Contributor: Mirko Messer <mirk@chao.ch>
# Maintainer: Steven Allen <steven@stebalien.com>

pkgname=nast
pkgver=0.2.0
arch=('x86_64' 'i686')
pkgrel=3
pkgdesc="An open source packet sniffer and a LAN analyzer based on Libnet and Libpcap."
url="http://nast.berlios.de/"
license=("GPL2")
depends=('ncurses' 'libpcap' 'libnet')
makedepends=()
source=(http://download.berlios.de/$pkgname/$pkgname-$pkgver.tar.gz)
md5sums=('77cbab45f5850d6cdb7ecb10e291bfa7')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  sed -i \
      -e 's/libmenu\.a/libmenu.so/g' \
      -e 's/libncurses\.a/libncurses.so/g' \
      -e 's/libnet\.a/libnet.so/g' \
      -e 's/libpcap_a/libpcap_so/g' \
      -e 's/libpcap\.a/libpcap.so/g' \
      ./configure{,.ac}
}
build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --prefix=/usr --mandir='${prefix}/share/man'
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  install -d "$pkgdir/usr/bin" "$pkgdir/usr/share/man/man8"
  make prefix="$pkgdir/usr" install
}
