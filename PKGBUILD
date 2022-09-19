# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=futurist
pkgname=python-$_pyname
pkgver=2.4.1
pkgrel=1
pkgdesc="Code from the future, delivered to you in the now."
arch=(any)
url="https://docs.openstack.org/futurist/"
license=(Apache)
depends=(
	python-pbr
	python-six
	python-monotonic
	python-prettytable
	python-pre-commit
	python-wheel
)
checkdepends=(
	python-eventlet
	python-oslotest
	python-stestr
	python-testrepository
	python-testscenarios
	python-testtools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)

export PBR_VERSION=$pkgver

build(){
	cd $_pyname-$pkgver
	python setup.py build
}

check(){
	cd $_pyname-$pkgver
	stestr run
}

package(){
	cd $_pyname-$pkgver
	python setup.py install --root="$pkgdir" --optimize=1
	install -Dm644 LICENSE -t "$pkgdir/usr/share/licenses/$pkgname"
}
md5sums=('3d541a8c1e13c2b7cde000a85eab295c')
sha256sums=('9c1760a877c0fe3260d04b6a6d4352a6d25ac58e483f1d6cd495e33dc3740ff7')
sha512sums=('39a5ccdbfd3f513356ef6f951ba2c53048b43fd7084001e025a776a4ceca8f53e9759711f3e0548b6bebd94c8760be095117084990e72e5284db0c09e0df7003')
