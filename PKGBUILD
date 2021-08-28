# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=pyscss
_pycname=pyScss
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=1.3.7
pkgrel=2
pkgdesc="pyScss, a Scss compiler for Python"
arch=(x86_64 i686 arm armv6h armv7h aarch64)
url="http://github.com/Kronuz/pyScss"
license=(MIT)
makedepends=(
	pcre
	python
	python-six
	python-setuptools
	python2
	python2-six
	python2-setuptools
)
source=(https://pypi.io/packages/source/${_pycname::1}/$_pycname/$_pycname-$pkgver.tar.gz)
md5sums=('c75fa4ea88d3c9df57a11679f337a939')
sha256sums=('f1df571569021a23941a538eb154405dde80bed35dc1ea7c5f3e18e0144746bf')
sha512sums=('8f369d91536394c780ae65b17f74852522f3ee60621c539e25327005baaf0cee9176088ea0558721017aa22b47c2c08c6d37e0b5b26ad3a91965aef4b8606d15')

prepare(){
	cp -a $_pycname-$pkgver{,-py2}
	sed -i '1s/ python$/ python2/g' $(find $_pycname-$pkgver-py2 -name '*.py')
}

build(){
	pushd $_pycname-$pkgver
	python setup.py build
	popd
	pushd $_pycname-$pkgver-py2
	python2 setup.py build
	popd
}

_package_python(){
	depends=(
		pcre
		python
		python-six
	)
	cd $_pycname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

_package_python2(){
	depends=(
		pcre
		python2
		python2-six
	)
	cd $_pycname-$pkgver-py2
	python2 setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
	for i in "$pkgdir"/usr/bin/*
	do mv -v ${i}{,-2}
	done
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
