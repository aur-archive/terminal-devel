# Maintainer: Xavier Devlamynck <magicrhesus@ouranos.be>

pkgname=terminal-devel
pkgver=0.4.7
pkgrel=1
pkgdesc="A modern terminal emulator primarly for the Xfce desktop environment (Development Version)"
arch=('i686' 'x86_64')
license=('GPL2')
url="http://www.xfce.org/projects/terminal/"
groups=('xfce4-devel') 
depends=('exo-devel>=0.5.4' 'vte' 'dbus-glib' 'startup-notification' 'hicolor-icon-theme')
makedepends=('pkgconfig' 'intltool')
conflicts=('terminal' 'terminal-git')
options=('!libtool')
install=terminal.install
source=(http://archive.xfce.org/src/apps/terminal/0.4/Terminal-${pkgver}.tar.bz2
        bug-7595-go-menu-single-tab-sensitivity.patch)
md5sums=('34daa0090e1bc9014a5b9849103a129f'
         '043774c11e2f8c1c424510847dc82fae')

build() {
  cd ${srcdir}/Terminal-${pkgver}
  # Add upstream patch for Xfce bug #7595
  # (Only make go menu action sensitive if tabs)
  patch -Np1 -i ${srcdir}/bug-7595-go-menu-single-tab-sensitivity.patch

  ./configure --prefix=/usr \
	--sysconfdir=/etc \
	--libexecdir=/usr/lib/xfce4 \
	--localstatedir=/var \
	--disable-static \
	--disable-debug
  make
}

package() {
  cd ${srcdir}/Terminal-${pkgver}
  make DESTDIR=${pkgdir} install
}
