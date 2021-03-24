# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=flake8-logging-format
pkgname=python-${_pyname}
pkgver=0.6.0
pkgrel=1
pkgdesc="Flake8 extension to validate (lack of) logging format strings"
arch=(any)
url="https://github.com/globality-corp/flake8-logging-format"
license=(Apache)
depends=(
	flake8
	python
)
makedepends=(
	python
	python-setuptools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('7e082dd93304443d4d7db7a6489017ba')
sha256sums=('ca5f2b7fc31c3474a0aa77d227e022890f641a025f0ba664418797d979a779f8')
sha512sums=('d93c1acbfde9945933228d3849a950a8a28b213632698e257c55c0d76d988f7de0106a9e7c92bb1af7c66444aab4fad22d4dad8e56537be076505eff283b9507')

build(){
	cd $_pyname-$pkgver
	python setup.py build
}

package(){
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1

}
