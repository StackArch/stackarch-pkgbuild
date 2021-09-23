# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=python-barbicanclient
pkgname=$_pyname
pkgver=5.2.0
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
md5sums=('c8a18c81ce5369014e3638db6c4e1b43')
sha256sums=('9e69572aa11700c41fc126b26de5a7f79d3f0638bd81a61676597cd0e7cee702')
sha512sums=('de9d063bf5e79347d0457b8fa69ed0d307fb4cd2b7dff23f156eab16521b3048283b9a7fdb1f464efe04cc4fd28e2072fe965a3e097842d1704f36bb83e7e3a2')

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
