# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=futurist
pkgname=python-$_pyname
pkgver=2.4.0
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
md5sums=('a104e9a837f83dc5c52c33baddffc47c')
sha256sums=('1c7452e2e8cc542c40c066c7d2be266a7029d9de391055613b4f069caa10a90b')
sha512sums=('f3472a35d26022e9bbb3fc83afd5206fe52e601c6be4e453329ab9aefc6672dd96e7236de1f7eb9058c60a8611a5a8cd0246c085f0f8e3e53c9300e498a0c434')
