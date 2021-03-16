# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=doc8
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=0.8.1
pkgrel=1
pkgdesc="Style checker for Sphinx (or other) RST documentation"
arch=(any)
url="https://github.com/pycqa/doc8"
license=(Apache)
makedepends=(
	python
	python-chardet
	python-docutils
	python-restructuredtext-lint
	python-six
	python-stevedore
	python-pygments
	python-setuptools
	python2
	python2-chardet
	python2-docutils
	python2-restructuredtext-lint
	python2-six
	python2-stevedore
	python2-pygments
	python2-setuptools
)
checkdepends=(
	python-mock
	python-nose
	python-pytest
	python-testtools
	python2-mock
	python2-nose
	python2-pytest
	python2-testtools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('5d6605ad9f989f58b492a6bdaf2b9b4b')
sha256sums=('4d1df12598807cf08ffa9a1d5ef42d229ee0de42519da01b768ff27211082c12')
sha512sums=('855a00e24daba0c1a7caa4e888411c356570d2f30c7966bb2e566260edff13bc4c35124fd8d4129231bc7a3bec2ed959d23fb52961a5d8f6d1c67cff22bb35de')

prepare(){
	cp -a $_pyname-$pkgver{,-py2}
	sed -i '1s/ python$/ python2/g' $(find $_pyname-$pkgver-py2 -name '*.py')
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
	pushd "$srcdir"/$_pyname-$pkgver
	python -m pytest
	popd
	pushd "$srcdir"/$_pyname-$pkgver-py2
	python2 -m pytest
	popd
}

_package_python(){
	depends=(
		python
		python-chardet
		python-docutils
		python-restructuredtext-lint
		python-six
		python-stevedore
		python-pygments
	)
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

_package_python2(){
	depends=(
		python2
		python2-chardet
		python2-docutils
		python2-restructuredtext-lint
		python2-six
		python2-stevedore
		python2-pygments
	)
	cd $_pyname-$pkgver-py2
	python2 setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
	for i in "$pkgdir"/usr/bin/*
	do mv -v ${i}{,2}
	done
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
