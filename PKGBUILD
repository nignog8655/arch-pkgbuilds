# Author: Adrian Perez de Castro <aperez@igalia.com>
pkgname='signify'
pkgver='6'
pkgrel='1'
pkgdesc='OpenBSD tool to signs and verify signatures on files. Portable version.'
url='https://github.com/aperezdc/signify'
license=('BSD')
arch=('i686' 'x86_64' 'arm')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/aperezdc/${pkgname}/archive/v${pkgver}.tar.gz")
sha1sums=('ba271295849b4f5712a5bd355af714ced48cd43f')
depends=('libbsd')

build () {
	cd "${srcdir}/${pkgname}-${pkgver}"
	if [ -r /etc/makepkg.conf ] ; then
		eval "$(sed -e '/^CFLAGS=/s/^/EXTRA_/p' -e d /etc/makepkg.conf)"
		eval "$(sed -e '/^LDFLAGS=/s/^/EXTRA_/p' -e d /etc/makepkg.conf)"
	fi
	make PREFIX='/usr' LTO=1 \
		EXTRA_CFLAGS="${EXTRA_CFLAGS}" EXTRA_LDFLAGS="${EXTRA_LDFLAGS}"
}

package () {
	cd "${srcdir}/${pkgname}-${pkgver}"
	make PREFIX='/usr' DESTDIR="${pkgdir}" install
}
