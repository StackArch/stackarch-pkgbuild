# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=pyscss
_pycname=pyScss
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=1.4.0
pkgrel=1
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
md5sums=('b28abfbc03d1d69a7fba60d6fce67cfc')
sha256sums=('8f35521ffe36afa8b34c7d6f3195088a7057c185c2b8f15ee459ab19748669ff')
sha512sums=('cd5f47e8e11e2a547741e274e7e8af6ce6df04707f9abeb246dc84f8bf003343df9b60be028cf6497caf17019482d9140d83c382638c4f34d5e6e38b47e6db2d')

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
