# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=flake8-import-order
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=0.18.1
pkgrel=1
pkgdesc="Flake8 and pylama plugin that checks the ordering of import statements."
arch=(any)
url="https://github.com/PyCQA/flake8-import-order"
license=(LGPL3)
makedepends=(
	flake8
	python
	python-pycodestyle
	python-setuptools
	python2
	python2-enum34
	python2-flake8
	python2-pycodestyle
	python2-setuptools
)
checkdepends=(
	flake8
	pylama
	python-pytest
	python-pycodestyle
	python2-pytest
	python2-flake8
	python2-pycodestyle
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('c1a3f2e4cf05f1ddf9002074276c123b')
sha256sums=('a28dc39545ea4606c1ac3c24e9d05c849c6e5444a50fb7e9cdd430fc94de6e92')
sha512sums=('f7c6e53d1033214f774b6b169deff2872e6eb36a3656cdd723449561611ad90c0be5fbbd822e1bba9e93f64f83f40fa3823aa5a21c22b9df0b3426f8182239f2')

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

check(){
	pushd $_pyname-$pkgver
	python -m pytest
	popd
	## Test for python2 was broken (pylama2)
	#pushd $_pyname-$pkgver-py2
	#python2 -m pytest
	#popd
}

_package_python(){
	depends=(
		flake8
		python
		python-pycodestyle
		python-setuptools
	)
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
}

_package_python2(){
	depends=(
		python2
		python2-enum34
		python2-flake8
		python2-pycodestyle
		python2-setuptools
	)
	cd $_pyname-$pkgver-py2
	python2 setup.py install --root "$pkgdir" --optimize=1
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
