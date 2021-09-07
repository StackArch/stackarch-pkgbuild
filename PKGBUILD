# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=sphinxcontrib-apidoc
pkgname=python-$_pyname
pkgver=0.3.0
pkgrel=1
pkgdesc="A Sphinx extension for BibTeX style citations"
arch=(any)
url="https://github.com/sphinx-contrib/apidoc"
license=(BSD)
depends=(
	python-pbr
	python-sphinx
)
makedepends=(python-setuptools)
checkdepends=(
	python-nose
	python-sphinx-testing
)
source=("https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz")

build(){
	cd $_pyname-$pkgver
	python setup.py build
}


package(){
	cd $_pyname-$pkgver
	python setup.py install --root="$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

md5sums=('baf2ad8a88918b04b54d0655aa273a82')
sha256sums=('729bf592cf7b7dd57c4c05794f732dc026127275d785c2a5494521fdde773fb9')
sha512sums=('043f9b36eaff7b3f6d23c834dd3947e2b029c66010b3862f1658f03e0fb6c4aac3304f49465dd515a30107a685dc704a0e319675c9d7b27897445a2c315d07a1')
