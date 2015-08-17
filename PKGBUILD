# Maintainer: Evan Teitelman <teitelmanevan@gmail.com>
# Contributor: Jens Pranaitis <jens@chaox.net>
# Contributor: Francesco Piccinno <stack.box@gmail.com>

pkgname=rfidiot-kali-git
_gitname=rfidiot
pkgver=0kali2
pkgrel=2
pkgdesc="An open source python library for exploring RFID devices."
url="http://rfidiot.org"
license=('GPL')
makedepends=('git' 'python2-distribute')
depends=('python2' 'openssl')
arch=('any')
source=('git://git.kali.org/packages/rfidiot.git')
md5sums=('SKIP')

pkgver() {
  cd $_gitname
  git describe --always | sed 's|.*-||'
}

build() {
	cd "$_gitname"
}

package() {
	cd "$_gitname"
	python2 setup.py install --root="$pkgdir/" --optimize=1

	# Change shebang lines
	sed -i '1s/python$/python2/' "$pkgdir/usr/bin/"*.py

	# Strip extensions and add the 'rfidiot-' prefix
	for file in "$pkgdir/usr/bin"/*.py ; do
		mv "$file" "$(dirname "$file")/rfidiot-$(basename "${file%.*}")"
	done
}
