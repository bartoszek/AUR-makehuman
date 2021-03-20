# Maintainer: Lukas Jirkovsky <l.jirkovsky@gmail.com>
pkgname=makehuman
pkgver=1.2.0
pkgrel=1
pkgdesc="Parametrical modeling program for creating human bodies"
arch=('any')
url="http://www.makehumancommunity.org/"
license=('AGPL3')
depends=('python' 'python-numpy' 'python-pyqt5' 'python-opengl' 'qt5-svg')
source=("https://github.com/makehumancommunity/makehuman/archive/v${pkgver}.tar.gz"
        "makehuman.desktop" "makehuman.sh")
sha256sums=('df6904f1b5a78acfa8363f2b2a3b8fcf9c83c0b321475e39408f802461beb16b'
            '17b97857ae3f14a0375a7e5ef7be59699f442eeb926204ff53d8e629efc73755'
            '18c100d2691b4bfdb45acaecbbdf4cc1623b0d064c549c53c212996cb94a1508')

build() {
	cd "$srcdir/${pkgname}-${pkgver}/makehuman"

	# Build as detailed on readme
	python download_assets_git.py
	python compile_models.py
	python compile_proxies.py
	python compile_targets.py
}

package() {
	cd "$srcdir/${pkgname}-${pkgver}"

	# No standard UNIX structure so install in opt
	install -d -m755 "$pkgdir/opt/makehuman"
	cp -R makehuman/* "$pkgdir/opt/makehuman"

	# Creates a symlink to the binary
	install -d m755 "$pkgdir/usr/bin"
	ln -s "/opt/makehuman/makehuman.py" "$pkgdir/usr/bin/makehuman"
}
