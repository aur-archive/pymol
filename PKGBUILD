# Contributions: graysky
# Maintainer: Tomasz Żok <tomasz.zok[at]gmail.com>
pkgname=pymol
pkgver=1.6.0.0
pkgrel=1
pkgdesc="A USER-SPONSORED molecular visualization system on an OPEN-SOURCE foundation"
arch=('i686' 'x86_64')
url="http://pymol.org/"
license=('custom:Python License')
depends=('glut' 'glew' 'libpng>=1.6' 'tcl' 'tk' 'python2' 'freetype2' 'python-pmw' 'mesa')
provides=('pymol')
source=("http://downloads.sourceforge.net/project/pymol/pymol/1.6/pymol-v${pkgver}.tar.bz2")
md5sums=('6f5db5beea7497f5a414c8e0cf1ae53d')

prepare() {
  # suppress non-zero exit code that breaks makepkg
  sed -i '/sys.exit/ s,2,0,' "$srcdir/$pkgname/setup.py"
}

build() {
  cd "$srcdir/$pkgname"
  python2 setup.py build
}

package() {
  cd "$srcdir/$pkgname"
  python2 setup.py install --prefix="usr/" --root="$pkgdir"
  sed -i "s|$pkgdir||g" pymol
  install -D -m755 pymol "$pkgdir/usr/bin/pymol"
}

# vim:set ts=2 sw=2 et:
