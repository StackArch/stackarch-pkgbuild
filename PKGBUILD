# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=python-barbicanclient
pkgname=$_pyname
pkgver=5.4.0
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
md5sums=('be552810231988d576e9cfcd69b86580')
sha256sums=('b29327c74e886c61b08501a1c5fc387dd56fa45df9976f5dd04441940805059a')
sha512sums=('29697032f2df8f463875550ed8454d9d9cd8bb5ad2b9e7432f527d1c8581ee4c1457eee4c11b71d5103b2036de0e7c41f5857d7aff393a87495f9f7a4bdbfd90')

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
