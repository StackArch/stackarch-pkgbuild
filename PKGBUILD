# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=iniparse
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=0.5
pkgrel=1
pkgdesc="Accessing and Modifying INI files"
arch=(any)
url="https://github.com/candlepin/python-iniparse"
license=(MIT)
depends=(
	python
	python-six
	python2
	python2-six
)
makedepends=(
	python-setuptools
	python2-setuptools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('2054bab923df21107652d009f2373789')
sha256sums=('932e5239d526e7acb504017bb707be67019ac428a6932368e6851691093aa842')
sha512sums=('b3f10d1b36497c3c5c71cb0a1ac73d74d8944f4ad3b7acc4a4b0246c2f1a20c184d9af20bbb3cb8ec4f57fddfb5e103b92688847debb4200ef0583353d7f9556')

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
		python-six
	)
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/"$pkgname"/LICENSE
	mv "$pkgdir"/usr/share/doc/{${_pyname}*,${pkgname}}
}

_package_python2(){
	depends=(
		python2
		python2-six
	)
	cd $_pyname-$pkgver-py2
	python2 setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/"$pkgname"/LICENSE
	mv "$pkgdir"/usr/share/doc/{${_pyname}*,${pkgname}}
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
