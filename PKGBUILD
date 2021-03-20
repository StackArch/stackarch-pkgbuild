# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=python-barbicanclient
pkgname=$_pyname
pkgver=5.0.1
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
md5sums=('4d47857de63c409bddc5a55a419cd430')
sha256sums=('039c32c088f5f369882db6933b78955a16b6929a7d99b757df614e0b6a27ed2a')
sha512sums=('5ab164e92b1d2820b5f84b59748e3fdf0733c587e6c4a9a17cb34cb95ab7a3900430790b50ce40b479a9f39e599a0969e3e8d1c5255ed6c595a287019a736663')

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
