#mantainer Jens Staal <staal1978@gmail.com>
#original PKGBUILD copied from Pierre Schmitz <pierre@archlinux.de>

pkgname=zlib-musl
pkgver=1.2.8
pkgrel=1
pkgdesc='Compression library zlib built on/for musl libc'
arch=('i686' 'x86_64')
license=('custom')
url="http://www.zlib.net/"
groups=('base-musl-dev')
depends=('musl')
source=("http://zlib.net/current/zlib-${pkgver}.tar.gz")
md5sums=('44d667c142d7cda120332623eab69f40')
options=(staticlibs)

build() {
	cd ${srcdir}/zlib-$pkgver
	CC=musl-gcc ./configure --prefix=/usr/musl --libdir=/usr/musl/lib --sharedlibdir=/usr/musl/lib --includedir=/usr/musl/include	
	make CC="musl-gcc -I/usr/musl/include -L/usr/musl/lib"

	grep -A 24 '^  Copyright' zlib.h > LICENSE
}

check() {
	cd ${srcdir}/zlib-$pkgver
	make test
}

package() {
	cd ${srcdir}/zlib-$pkgver
	make install DESTDIR=${pkgdir}
	install -D -m644 LICENSE ${pkgdir}/usr/share/licenses/musl-zlib/LICENSE
}  
