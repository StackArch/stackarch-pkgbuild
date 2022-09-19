# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=osc-placement
pkgname=python-$_pyname
pkgver=4.0.0
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
md5sums=('817cc9359a6fa6d304a289ba734251d5')
sha256sums=('c964f953c1b1e8ff1e13cb89d7642552085a737e11ffde17bf7cc98d3d0c7e54')
sha512sums=('306755dc4a09a4cbb97655027c07afce9e165e9bcd007bbd0b8755e938ca9eeaaa670a590db97991d3721e046a0b785947cca7a3340c30cf1d02f087531e896f')

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
