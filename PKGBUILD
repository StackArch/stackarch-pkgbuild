# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=flake8-logging-format
pkgname=python-${_pyname}
pkgver=0.7.5
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
md5sums=('6d92ade4a851e3de7d52636fb24dca25')
sha256sums=('54f7e349c934ce5c594f251885bc2240e99f6b48752a672a8fc7e3d1388352bb')
sha512sums=('4c792dc66cd0115086d21a2eb190879d798365fabdffab396f113d31c55f654756d9838b6d5ffc42ae412c3370350241b0a99a942e9db81cb54ab05020bdabca')

build(){
	cd $_pyname-$pkgver
	python setup.py build
}

package(){
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1

}
