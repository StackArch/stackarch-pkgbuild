# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=python-barbicanclient
pkgname=$_pyname
pkgver=5.1.0
pkgrel=1
pkgdesc="Client Library for OpenStack Barbican Key Management API"
arch=('any')
url="https://docs.openstack.org/python-barbicanclient/latest/"
license=(Apache)
depends=(
	python
	python-pbr
	python-requests
	python-six
	python-cliff
	python-keystoneauth1
	python-oslo-i18n
	python-oslo-serialization
	python-oslo-utils
)
checkdepends=(
	python-hacking
	python-coverage
	python-fixtures
	python-requests-mock
	python-stestr
	python-testtools
	python-oslotest
	python-nose
	python-oslo-config
	python-openstackclient
	python-sphinxcontrib-svg2pdfconverter
)
makedepends=(
	python
	python-setuptools
)
source=("https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz")
md5sums=('e13b389215c72ab0cfd57457b33c939c')
sha256sums=('e6b6b7bfa7d773dc891de7873e5e5a336f7f9f8ac90a6a726e1f7674f8fe8af4')
sha512sums=('b18af90725e2fcc3394e55fa901d950375b36db95df497f77360a8832f6dc20e787039fafe75ee8f8aa8ae8acc8c0f63db60822dee6820d9639e4acb9d3a719e')

export PBR_VERSION=$pkgver

build(){
	cd $_pyname-$pkgver
	python setup.py build
}

package(){
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
