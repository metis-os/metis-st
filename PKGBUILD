# Maintainer: iyamnabeen <iym.nabeen@gmail.com>

pkgname=metis-st
_pkgname=metis-st
pkgver=1
pkgrel=0
pkgdesc="suckless's simple terminal with vim-bindings, transparency, xresources, for @metis-os "
url='https://github.com/metis-os/metis-st'
arch=('i686' 'x86_64')
license=('MIT')
options=('zipman')
depends=('libxft')
makedepends=('ncurses' 'libxext' 'git')
optdepends=('metis-dmenu')
source=(git+https://github.com/metis-os/metis-st)
sha1sums=('SKIP')

provides=("${_pkgname}")
conflicts=("${_pkgname}")


prepare() {
	cd $srcdir/${_pkgname}
	sed -i '/tic /d' Makefile
}

build() {
	cd "${_pkgname}"
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
	cd "${_pkgname}"
	make PREFIX=/usr DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
	install -Dm644 Xdefaults "${pkgdir}/usr/share/doc/${pkgname}/Xdefaults.example"
}
