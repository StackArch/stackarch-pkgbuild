# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=yappi
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=1.3.2
pkgrel=1
pkgdesc="Yet Another Python Profiler"
arch=(x86_64 i686 arm armv6h armv7h aarch64)
url="https://github.com/sumerc/yappi"
license=(MIT)
makedepends=(
	python
	python-gevent
	python-setuptools
	python2
	python2-gevent
	python2-setuptools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('5ffe300828cdf046a1b0e0450f555d9d')
sha256sums=('a51d3e6e5563cc74b5bb82ed6e7bd44a9c1a7eae3d97e4d52e9465edb3a8da8d')
sha512sums=('66744d065ad910225b6c0f17eddbbde72b485081d5e66dc299d1bcce8217811ddd2b280c4a6976007af9a4848f18a0d0ea7fa684a46f71cb9df72c70ec1d8b45')

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

## Test was broken
#check(){
#	pushd $_pyname-$pkgver
#	python -m pytest
#	popd
#	pushd $_pyname-$pkgver-py2
#	python2 -m pytest
#	popd
#}

_package_python(){
	depends=(
		python
		python-gevent
	)
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

_package_python2(){
	depends=(
		python2
		python2-gevent
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
