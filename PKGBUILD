# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=sphinxcontrib-svg2pdfconverter
pkgname=python-$_pyname
pkgver=1.1.1
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
md5sums=('6ff5f5a169d6da53f5e3f2eb654c58bf')
sha256sums=('c5138cbb069150646fd9fd106034678cf8290f894fc62d580d8ccbdb7ac49481')
sha512sums=('7f06da4373eed8673fc4cd4598a00a7d529adcec7a40649bf79c5b8d5b363455c8a83286e58d783edcba27114ac4687fd15a4be37ec95e331e9abd22bd3cd4b7')

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
