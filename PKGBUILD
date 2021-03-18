# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=os-testr
pkgname=python-$_pyname
pkgver=2.0.0
pkgrel=1
pkgdesc="A testr wrapper to provide functionality for OpenStack projects"
arch=(any)
url="https://docs.openstack.org/os-testr/latest/"
license=(Apache)
depends=(
	python2
	python
	python-pbr
	python-stestr
	python-subunit
	python-testtools
)
makedepends=(
	python-openstackdocstheme
	python-reno
	python-sphinx
	python-setuptools
)
checkdepends=(
	python-hacking
	python-coverage
	python-oslotest
	python-testscenarios
	python-ddt
	python-six
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('ffc397c5ffa36e6b143cbd59b813cf40')
sha256sums=('da94f9d5945ba45db57f8f9afdaefc62bc971eed5ce15e059d76a2ff495632fd')
sha512sums=('0ee6a144a75f7742aaf6859161f7918fb908a6783180a022a8698ce4dffeac50bf453c208b47ec784687d88a55739fff822483f404f246f222c24245ed6845ea')

export PBR_VERSION=$pkgver

build(){
	cd $_pyname-$pkgver
	python setup.py build
}

check(){
	cd "$srcdir"/$_pyname-$pkgver
	mkdir root
	python setup.py install --root root --optimize=1
	PATH="${PWD}/root/usr/bin:${PATH}" PYTHONPATH="${PWD}" stestr run
}

package(){
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
