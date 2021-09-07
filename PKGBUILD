# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=futurist
pkgname=python-$_pyname
pkgver=2.3.0
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
md5sums=('4d642f5825a516d676356094179c6d27')
sha256sums=('174ea146adf303d7e5d7d6d34e3a01f4abf0382b03a6f9309bac2e2d54ffbed6')
sha512sums=('fa12314ce1bc12ccb7d8dd0e99a76a63dbd6a1c6560ca976eacb782f2c28a6003aee820d8ea745b59d35280b047e67563b046c761737d76fefb5928fdfba20e9')
