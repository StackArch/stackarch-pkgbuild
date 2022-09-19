# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=yappi
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=1.3.6
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
md5sums=('a1f9ebfe6509e2be92e6e8b303f1a0fa')
sha256sums=('0a73c608a2603570a020a32d4369ba744012bc5267f37e5bd8026fb491abba56')
sha512sums=('24f4608672179be1f6189b4121b74ecc9badb4e24b6ccec19a8636d1ec4ce010deb2f8614da6a5e080fb18b375508d86714ed773ab79b947134f835ea37f64e3')

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
	PYTHONPATH=${PWD}/tests python -m pytest
	popd
	#pushd $_pyname-$pkgver-py2
	#PYTHONPATH=${PWD}/tests python2 -m pytest
	#popd
}

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
