# Maintainer: Simon Doppler (dopsi) <dop.simon_at_gmail.com>

# Former maintaining team :
# (Contributor) Nick B <Shirakawasuna at gmail _dot_com>
# (Maintainer) moostik <mooostik_at_gmail.com>
pkgname=qelectrotech
pkgver=0.8.0
pkgrel=1
pkgdesc="An electric diagram editor"
arch=('i686' 'x86_64')
url="https://qelectrotech.org/"
license=('GPL2')
depends=('qt5-svg' 'hicolor-icon-theme' 'desktop-file-utils' 'kwidgetsaddons' 'kcoreaddons')

# tk needed for "qet_tb_generator plugin"
optdepends=('tk')

sha512sums=('28a59aaf62c2bb9550861a727538b8e1e7582e318f5591c5dd10890d094a2c37324ec4cf900846593a22644828bc677dbcf17af24908712c148b3dbe7b5ba738'
            '7a8b99b7a5f59685638490149351977a52ba42998efb38f3394693e8642c451bb2894bdbd859b82ccef88c81fd7c92717725b4c292df201c78ff2ec3855b2da4')

source=(
  "https://git.tuxfamily.org/qet/qet.git/snapshot/qet-$pkgver.zip"
  'install-dir.patch'
)

_tarname="qet-$pkgver"

prepare() {
  cd "$srcdir/$_tarname"
  patch < "$srcdir/install-dir.patch"
  sed -i 's/gzip \-9n/gzip -9nf/' "$srcdir/$_tarname/man/compress_man_pages.sh"
}

build() {
  cd "$srcdir/$_tarname"
  qmake-qt5
  make
}

package() {
  cd "$srcdir/$_tarname"
  make INSTALL_ROOT="$pkgdir" install
  mv "$pkgdir/usr/doc" "$pkgdir/usr/share/doc"
}

