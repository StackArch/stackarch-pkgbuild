# Maintainer: BigfootACA <classfun.cn>

_pyname=reno
pkgname=python-$_pyname
pkgver=3.4.0
pkgrel=1
pkgdesc="OpenStack RElease NOtes manager"
arch=(any)
url="https://docs.openstack.org/reno/"
license=(Apache)
depends=(
	python-pbr
	python-yaml
	python-dulwich
)
checkdepends=(
	python-docutils
	python-stestr
	python-testscenarios
	python-testtools
	python-sphinx
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)

export PBR_VERSION=$pkgver

build(){
	cd $_pyname-$pkgver
	python setup.py build
}

check(){
	cd $_pyname-$pkgver
	rm reno/tests/test_cache.py
	rm reno/tests/test_scanner.py
	rm reno/tests/test_semver.py
	stestr run
}

package(){
	cd $_pyname-$pkgver
	python setup.py install --root="$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
sha256sums=('5e77ce1707c7e3e1b0e9e72abe2d32c59af44df00a588601e2e362bad1b0fb41')
