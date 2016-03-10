# Based on: version 0.5.3.git20160228 (git://anonscm.debian.org/collab-maint/w3m.git#commit=692e2c04a0e7e216b670eab6133d68818260d5e8)
# Modified/Patched by: spcmd (https://github.com/spcmd)

pkgname=w3m-spcmd
pkgver=0.5.3.git20160228
pkgrel=1
pkgdesc='Text-based Web browser, as well as pager (with patches: yank, mediaplayer)'
url='http://w3m.sourceforge.net/'
license=('custom')
arch=('i686' 'x86_64')
makedepends=('git' 'imlib2')
optdepends=('imlib2: for graphics support') 
depends=('openssl' 'gc' 'ncurses' 'gpm')
source=("w3m-spcmd.tar.gz")
sha1sums=('SKIP')
conflicts=('w3m')
provides=('w3m')

build() {
	cd "${srcdir}/w3m"
	./configure \
		--prefix=/usr \
		--libexecdir=/usr/lib \
		--enable-image=x11,fb \
		--with-imagelib=imlib2 \
		--with-termlib=ncurses \
		--disable-w3mmailer \

	make
}

package() {
	cd "${srcdir}/w3m"
	make DESTDIR="${pkgdir}" install

	install -d "${pkgdir}"/usr/share/{doc,licenses}/"w3m"
	find doc/* | grep -v CVS | xargs -i install -m644 "{}" "${pkgdir}/usr/share/doc/w3m"
	ln -s ../../doc/"w3m"/README "${pkgdir}/usr/share/licenses/w3m"
}
