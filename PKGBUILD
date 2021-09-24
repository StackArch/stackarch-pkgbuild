# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=crudini
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=0.9.3
pkgrel=1
pkgdesc="A utility for manipulating ini files"
arch=(any)
url="https://www.pixelbeat.org/programs/crudini/"
license=(GPL2)
depends=(
	python
	python-iniparse
	python2
	python2-iniparse
)
makedepends=(
	python-setuptools
	python2-setuptools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('489f4d69c05225b308d6269094cf4ef8')
sha256sums=('5767d267aec5161d0b3bb535955749ec4df634b5ab0917a9132a1d8ea71a1b3a')
sha512sums=('594dc60fab8d95246edc3ec01f45b895bc2a93abb26896803046a5588166f43fa2f5a90c0b6b12d632ea6e6490890390323263b0db4ea985201756c4f651e5a9')

prepare(){
	cp -a $_pyname-$pkgver{,-py2}
}

build(){
	pushd $_pyname-$pkgver
	python setup.py build
	popd
	pushd $_pyname-$pkgver-py2
	python2 setup.py build
	popd
}

_package_python(){
	depends=(
		python
		python-iniparse
	)
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
}

_package_python2(){
	depends=(
		python2
		python2-iniparse
	)
	cd $_pyname-$pkgver-py2
	python2 setup.py install --root "$pkgdir" --optimize=1
	for i in "$pkgdir"/usr/bin/*
	do mv -v ${i}{,2}
	done
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
