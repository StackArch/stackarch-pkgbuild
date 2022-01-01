# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=yappi
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=1.3.3
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
md5sums=('48703b6b391fba7fbb98630744203744')
sha256sums=('855890cd9a90d833dd2df632d648de8ccd0a4c3131f1edc8abd004db0625b5e8')
sha512sums=('7c13ecb3e465f4308713f0de111ad53c1c033dc7762848322b15bc9dde815f9843bab31aaf0b1347002083eb54cd39014115f708af171d1d16b88c28c0017ad2')

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
