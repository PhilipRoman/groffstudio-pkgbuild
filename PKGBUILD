pkgname=groffstudio-git

pkgver=r2.9746731

pkgrel=1

pkgdesc="An IDE for groff"

arch=('x86_64')

url='https://groff.tuxproject.de/'

license=('CDDL')

depends=('gtk2' 'groff')

makedepends=('lazarus' 'git')

source=("git+https://github.com/dertuxmalwieder/groffstudio")

md5sums=('SKIP')

pkgver() {
	cd "groffstudio"
	( set -o pipefail
		git describe --long 2>/dev/null | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
		printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
	)
}

build() {
	cd "groffstudio/src"
	lazbuild --lazarusdir=/usr/lib/lazarus/ groffstudio.lpi
}

package() {
	cd "groffstudio/src"
	install -D -m755 groffstudio -t "$pkgdir/usr/bin/"
}
