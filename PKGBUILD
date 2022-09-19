# Maintainer: Anthony25 <Anthony Ruhier>
#
# Thanks to Jeremy "Ichimonji10" Audet <ichimonji10 at gmail dot com> for
# his PKGBUILD that served as a base for this one

_pyname=ncclient
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=0.6.13
pkgrel=1
pkgdesc="Python library for NETCONF clients"
arch=(any)
url="http://ncclient.org/"
license=(Apache)
makedepends=(
	python
	python-six
	python-lxml
	python-paramiko
	python-selectors2
	python-setuptools
	python2
	python2-six
	python2-lxml
	python2-paramiko
	python2-setuptools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('b269c9e1db60cb3a2998f8e31434a1bb')
sha256sums=('f9f8cea8bcbe057e1b948b9cd1b241eafb8a3f73c4981fbdfa1cc6ed69c0a7b3')
sha512sums=('46f2bed7b578170d31b5574477f1d946a3768b9b1487e6b3541c3a4c763f65903c6115af590b38af1e8e352c82f11791b79984daf9ec28265fbdc946aa660ad1')

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

_package_python(){
	depends=(
		python
		python-six
		python-lxml
		python-paramiko
		python-selectors2
	)
	depends=(python)
	cd "$_pyname-$pkgver"
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

_package_python2(){
	depends=(
		python2
		python2-six
		python2-lxml
		python2-paramiko
	)
	cd "$_pyname-$pkgver-py2"
	python2 setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
