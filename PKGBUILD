# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=osc-placement
pkgname=python-$_pyname
pkgver=3.1.0
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
md5sums=('08fe683243cb98f234a0281150b9bd08')
sha256sums=('351058aaad44ee80de907d1afb1e62421874e0bee6de028f44896ec3eb207e08')
sha512sums=('0560e3a5642a76acc430688bce817dd9ac247127769657091dc6d70746f14af68d34f2cd196967550d64e80e69db1e402ee9d365c8faee4121fec0b5aeb84040')

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
