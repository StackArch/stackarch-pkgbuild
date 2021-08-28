# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=statsd
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=3.3.0
pkgrel=2
pkgdesc="A simple statsd client."
arch=(any)
url="https://github.com/jsocol/pystatsd"
license=(MIT)
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
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('b397ccf880f37cf099e775907ebf7a46')
sha256sums=('e3e6db4c246f7c59003e51c9720a51a7f39a396541cb9b147ff4b14d15b5dd1f')
sha512sums=('e2693bc7f179e275c53044d13a4685dd72ebd47adafcab5064e803fbf9e8df4a0f20f61c3695846d3c33178be17dd7286f487213fa2bd8545ed1612e200c8f36')

prepare(){
	cp -a $_pyname-$pkgver{,-py2}
}

check(){
	pushd $_pyname-$pkgver
	python -m nose
	popd
	pushd $_pyname-$pkgver-py2
	python2 -m nose
	popd
}

build(){
	pushd $_pyname-$pkgver
	python setup.py build
	make -C docs man
	popd
	pushd $_pyname-$pkgver-py2
	python2 setup.py build
	popd
}

_package_python(){
	depends=(python)
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE -t "$pkgdir/usr/share/licenses/$pkgname"
	install -Dm644 docs/_build/man/pythonstatsd.1 -t "$pkgdir/usr/share/man/man1"
}

_package_python2(){
	depends=(python2)
	cd $_pyname-$pkgver-py2
	python2 setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE -t "$pkgdir/usr/share/licenses/$pkgname"
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
