# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=osc-placement
pkgname=python-$_pyname
pkgver=2.2.0
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
md5sums=('86ff64adae8e53f3d3c164724075ff92')
sha256sums=('ed933dae950c596ebe8fd2ad878b3eaa521a1ca80a138db34a792dfebd8135c3')
sha512sums=('e70d3c1cd300df3e7ea36b996667a7059f5dc4c77fdd1ad658d145055d4c118863aa75d8654877a21ad9c1df7881d18327704b1ae70ef99caddeb9610d7cf7d5')

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
