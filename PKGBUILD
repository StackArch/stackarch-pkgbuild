# Maintainer: Anthony25 <Anthony Ruhier>
#
# Thanks to Jeremy "Ichimonji10" Audet <ichimonji10 at gmail dot com> for
# his PKGBUILD that served as a base for this one

_pyname=ncclient
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=0.6.12
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
	python2-selectors2
	python2-setuptools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('9986cd583cc8173a7e0f50d4439a684e')
sha256sums=('37c8a9f9a44f0346144119ab17ae6559e44b5a991f4c34ea3765c678079e4beb')
sha512sums=('df7923684228c400de81b089d5873a442026434557c239056af9f8d9af06ed1e9763a539cefef4a056d342537cb4a5f27b99be98eb5645ac36f7da217185289a')

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
		python2-selectors2
	)
	cd "$_pyname-$pkgver-py2"
	python2 setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
