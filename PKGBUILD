# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=python-ironicclient
pkgname=$_pyname
pkgver=4.8.0
pkgrel=1
pkgdesc="OpenStack Bare Metal Provisioning API Client Library"
arch=('any')
url="https://docs.openstack.org/python-ironicclient/latest/"
license=(Apache)
depends=(
	python
	python-six
	python-pbr
	python-yaml
	python-requests
	python-openstackclient
	python-prettytable
	python-oslo-utils
	python-keystoneauth1
	python-jsonschema
	python-dogpile.cache
	python-appdirs
)
checkdepends=(
	python-coverage
	python-fixtures
	python-requests-mock
	python-oslotest
	python-testtools
	openstack-tempest
	python-stestr
	python-ddt
	python-openstackclient
)
makedepends=(
	python
	python-setuptools
)
source=("https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz")
md5sums=('43e9bc33bc4d41283eb0356dae0e0fcf')
sha256sums=('b55516a72b995f92fb434619cbc1e2effa604c7fcaa6ac4afb8f5af1ea8193a4')
sha512sums=('c784124e59ee836c3349e17f347b59bb96e28afd067b7de2d948563293c16d2f641c15d3312c56c9fed476e1c8c9de65949bfdc139cd9267cb210c5cc70ccbb3')

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
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
