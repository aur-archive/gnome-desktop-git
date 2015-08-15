# Maintainer: Yosef Or Boczko <yoseforb@gnome.org>

_pkgname=gnome-desktop
pkgname=$_pkgname-git
pkgver=3.17.2
pkgrel=1
_realver=3.17.2
pkgdesc="Library with common API for various GNOME modules"
arch=('i686' 'x86_64')
license=('GPL' 'LGPL')
depends=('gsettings-desktop-schemas' 'gtk3' 'xkeyboard-config' 'gdk-pixbuf2' 'glib2' 'libxext' 'libxrandr')
makedepends=('git' 'gtk-doc' 'gnome-common' 'gnome-doc-utils' 'intltool' 'gobject-introspection' 'itstool')
url="http://www.gnome.org"
groups=('gnome')
options=('!libtool')
conflicts=('gnome-desktop')
replaces=('gnome-desktop')
provides=("$_pkgname=$_realver")
source=('git://git.gnome.org/gnome-desktop')
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/gnome-desktop"
  git describe --always | sed 's|-|.|g'
}

build() {
  cd "$srcdir/gnome-desktop"
  ./autogen.sh --prefix=/usr --sysconfdir=/etc \
      --localstatedir=/var --disable-static \
      --libexecdir=/usr/lib/gnome-desktop \
      --with-gnome-distributor="Arch Linux" \
      --enable-gtk-doc
  make
}

package() {
  cd "$srcdir/gnome-desktop"  
  make DESTDIR="$pkgdir" install
}
