# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=sphinxcontrib-svg2pdfconverter
pkgname=python-$_pyname
pkgver=1.2.0
pkgrel=1
pkgdesc="Sphinx SVG to PDF converter extension"
arch=('any')
url="https://github.com/missinglinkelectronics/sphinxcontrib-svg2pdfconverter"
license=(BSD)
depends=(
	python
	python-pbr
	python-docutils
	python-sphinx
)
optdepends=(
	python-cairosvg
)
makedepends=(
	python
	python-setuptools
)
source=("https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz")
md5sums=('d7e7746f5278de1c5c13a9d94ba1b511')
sha256sums=('60d14562bc7e6f1ad30f1b63a137659508868c87ce182c1d7fc08bee67b5851d')
sha512sums=('97e51362756587e71d35329e937da1d66d9bebbaa3cfa2deef0d5177f39602c6964c48d882435f82311c177e3fa3b394629ef7a9957a9ba5b9ee327b3751592f')

export PBR_VERSION=$pkgver

build(){
	cd $_pyname-$pkgver
	python setup.py build
}

package(){
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE.txt "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
