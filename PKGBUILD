# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=python-ironicclient
pkgname=$_pyname
pkgver=5.0.1
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
md5sums=('5121fdd0c23bf39f5f4563268cb7c5ed')
sha256sums=('ed16b06c9e4ee4a0abb83e3df5f3a4b85728b81ce9ddfeda1149c4dfbc09aa63')
sha512sums=('394765b7b50ad7bec5e7517f0114118ba705c06f17bf562d18891011bfc6ad85938813817800d12d7c4f0f0336cfb611e37ba52e1920f48162a59559d5ee09d1')

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
