# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=actdiag
pkgname=${_pyname}
pkgver=2.0.0
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
sha512sums=('e955b9b919e137f10ff128d5d8817b2da660b121937cab3386a866a0bff08218b6e777e302a9130616228af6c357c463ceeb12cb95b8734928001d8ad6a90250')

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
