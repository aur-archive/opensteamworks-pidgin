# Maintainer: onny <onny@project-insanity.org>
# Contributor: onny <onny@project-insanity.org>

pkgname=opensteamworks-pidgin
pkgver=1.0
pkgrel=4
pkgdesc="A plugin to connect to Steam Friends/Steam IM (purple plugin). "
url=('https://code.google.com/p/pidgin-opensteamworks')
arch=('i686' 'x86_64')
license=('GPL3')
makedepends=('svn')
depends=('json-glib')
source=("http://schmatzler.de/wp-content/Makefile"
"https://pidgin-opensteamworks.googlecode.com/files/icons.zip")
md5sums=('42727afa5892d8bd65c6d2c6389ab884'
	 '3ca20e24013b4355ec50bd32f2899539')
build() {
  svn checkout http://pidgin-opensteamworks.googlecode.com/svn/trunk/ "$srcdir/pidgin-opensteamworks-read-only"
  cd $srcdir/pidgin-opensteamworks-read-only/steam-mobile
  if [ "$CARCH" = "x86_64" ]; then
    cp "$srcdir/Makefile" .
  fi
  make
}
package() {
  mkdir -p $pkgdir/usr/lib/purple-2
  install -D -m755 $srcdir/pidgin-opensteamworks-read-only/steam-mobile/libsteam.so $pkgdir/usr/lib/purple-2/
  mkdir -p "$pkgdir/usr/share/pixmaps/pidgin/protocols"
  cp -r "$srcdir/16" "$srcdir/48" "$pkgdir/usr/share/pixmaps/pidgin/protocols"
}
