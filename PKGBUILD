pkgname=qalculate-gtk
pkgver=3.19.0
pkgrel=1
pkgdesc="GTK+ frontend for libqalculate"
arch=('x86_64')
url="http://qalculate.github.io/"
screenshot='http://qalculate.github.io/images/qalculate-keypad.png'
license=('GPL')
depends=("libqalculate>=${pkgver}" 'gtk3>=3.10' 'gdk-pixbuf2' 'systemd')
makedepends=('intltool')
source=(https://github.com/Qalculate/$pkgname/releases/download/v$pkgver/$pkgname-$pkgver.tar.gz)
md5sums=('71a7b4fca86cffa5ce358bc559d358f6')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  msg "### configure"
  ./configure --prefix=/usr || return 1
  msg "### make"
  make || return 1
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  msg "### make install"
  make DESTDIR="${pkgdir}" install || return 1
  _docdir=${pkgdir}/usr/share/doc/${pkgname}
  _licdir=${pkgdir}/usr/share/licenses/${pkgname}
  install -dm755 ${_docdir} ${_licdir}
  install -Dpm644 AUTHORS ChangeLog INSTALL NEWS README TODO ${_docdir}/
  install -Dpm644 COPYING ${_licdir}/
}
