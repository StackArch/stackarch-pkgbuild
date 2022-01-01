# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=actdiag
pkgname=${_pyname}
pkgver=3.0.0
pkgrel=1
pkgdesc="actdiag generates activity-diagram image from text"
arch=(any)
url="http://blockdiag.com/en/actdiag"
license=(Apache)
depends=(
	python
	blockdiag
)
makedepends=(python-distribute)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
sha512sums=('240a687fd0c9f8ee10e66fed9ce8ca3359f3336c1623a05b1394f1444e518c1c325922eb5cd2d6d1a867876ff820b2b1b6f5eb518a6af5d688bd8116b97c9dca')

build(){
	cd $_pyname-$pkgver
	python setup.py build
}

package(){
	optdepends=(python-reportlab)
	cd "$_pyname-$pkgver"
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
