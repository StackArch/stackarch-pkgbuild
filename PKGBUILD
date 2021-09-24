pkgname=mod_wsgi
pkgver=4.9.0
pkgrel=1
pkgdesc="Python WSGI adapter module for Apache"
arch=(x86_64 i686 arm armv6h armv7h aarch64)
url="http://www.modwsgi.org/"
license=(Apache)
depends=(apache python)
makedepends=(apache python)
conflicts=(mod_wsgi2)
source=($pkgname-$pkgver.tar.gz::https://github.com/GrahamDumpleton/mod_wsgi/archive/refs/tags/$pkgver.tar.gz)
md5sums=('3849425d78e716511388a5894cc00479')
sha256sums=('0a6f380af854b85a3151e54a3c33b520c4a6e21a99bcad7ae5ddfbfe31a74b50')
sha512sums=('9dc34d431171321094a9713444895d9754eff4e69ad1e86c8d3cd77bc1ca0a4c10b697e7f8cf14902d6bfaf205c8842e62fa944bb38f66f1c54fd36af95a09d6')

build(){
	cd "$pkgname-$pkgver"
	./configure \
		--prefix=/usr \
		--with-apxs=/usr/bin/apxs \
		--with-python=/usr/bin/python
	make
}

package(){
	cd "$pkgbase-$pkgver"
	make DESTDIR="$pkgdir" install
}
