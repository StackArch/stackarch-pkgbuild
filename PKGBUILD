# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=osc-placement
pkgname=python-$_pyname
pkgver=3.1.1
pkgrel=1
pkgdesc="OpenStackClient plugin for the Placement service"
arch=(any)
url="https://docs.openstack.org/osc-placement/latest/"
license=(Apache)
depends=(
	python
	python-pbr
	python-six
	python-keystoneauth1
	python-simplejson
	python-osc-lib
	python-oslo-utils
	python-openstackclient
)
makedepends=(
	python-setuptools
	python-sphinx
	python-sphinx-feature-classification
	python-openstackdocstheme
	python-cliff
	python-reno
	python-whereto
)
checkdepends=(
	python-hacking
	python-coverage
	python-oslotest
	python-stestr
	python-wsgi-intercept
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('8ef72c7ff570bb4d9d70376787467b76')
sha256sums=('8da2845b7ae21a00629d90db7429563198ed213728d5115c5dbc4a5ef7cb9e75')
sha512sums=('0c79ad28a5976f386bc939f06f36254649dda1fc14ecff8f48513aafbd02a23779946afd81aa091aab4e61ac45997c4e6cc270a3edcc82c6e83ff6b41e8efb25')

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
