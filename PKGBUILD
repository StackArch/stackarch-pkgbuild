# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=os-traits
pkgname=python-$_pyname
pkgver=2.5.0
pkgrel=1
pkgdesc="A library containing standardized trait strings"
arch=(any)
url="https://docs.openstack.org/os-traits/latest/"
license=(Apache)
depends=(
	python
	python-pbr
)
makedepends=(
	python-setuptools
	python-sphinx
	python-openstackdocstheme
	python-reno
)
checkdepends=(
	python-hacking
	python-coverage
	python-oslotest
	python-stestr
	python-testscenarios
	python-testtools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('1f97fdf548f195c4ab8b8e8a7e0dd221')
sha256sums=('6168dcda9e6f971432a46aca8e88712dcdb85aecaacc95a8bfe8777cd358da0b')
sha512sums=('55fcebf4c9340e4c783c3a6e6636555d90950b172a51925b34119a17ebd3d880d031f60aa1fdf4183ba9d98c2782be01154868b3f1a6b75389728561c77ca5db')

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
