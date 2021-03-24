# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=simplegeneric
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=0.8.1
pkgrel=1
pkgdesc="Simple generic functions (similar to Python's own len(), pickle.dump(), etc.)"
arch=(any)
url="http://cheeseshop.python.org/pypi/simplegeneric"
license=(ZPL)
makedepends=(
	python
	python2
	python-setuptools
	python2-setuptools
)
checkdepends=(
	python-nose
	python2-nose
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.zip)
md5sums=('f9c1fab00fd981be588fc32759f474e3')
sha256sums=('dc972e06094b9af5b855b3df4a646395e43d1c9d0d39ed345b7393560d0b9173')
sha512sums=('74c25d4e04fe197058cb43fabe3702cc5901989dc0b0bcf7511369f4f3d90fd98e4225174db0680c8f39389914f82824bdbdaf4c302b53998fbabbf0dba393e4')

prepare(){
	cp -a $_pyname-$pkgver{,-py2}
}

check(){
	pushd $_pyname-$pkgver
	python setup.py test
	popd
	pushd $_pyname-$pkgver-py2
	python2 setup.py test
	popd
}

_package_python(){
	depends=(python)
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
}

_package_python2(){
	depends=(python2)
	cd $_pyname-$pkgver-py2
	python setup.py install --root "$pkgdir" --optimize=1
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
