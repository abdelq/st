pkgname=st
pkgver=0.7
pkgrel=1
pkgdesc='A simple virtual terminal emulator for X.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'adobe-source-code-pro-fonts')
makedepends=('ncurses')
url="http://st.suckless.org"
source=(http://dl.suckless.org/st/$pkgname-$pkgver.tar.gz
        config.h)
md5sums=('29b2a599cf1511c8062ed8f025c84c63'
         'SKIP')

prepare() {
  cd "$srcdir"/$pkgname-$pkgver
  sed -i '/\@tic /d' Makefile
  cp "$srcdir"/config.h config.h
}

build() {
  cd "$srcdir"/$pkgname-$pkgver
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd "$srcdir"/$pkgname-$pkgver
  make PREFIX=/usr DESTDIR="$pkgdir" TERMINFO="$pkgdir/usr/share/terminfo" install
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -Dm644 README "$pkgdir/usr/share/doc/$pkgname/README"
}
