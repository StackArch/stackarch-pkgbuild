# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=codecov
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=2.1.11
pkgrel=1
pkgdesc="Hosted coverage reports for GitHub, Bitbucket and Gitlab"
arch=(any)
url="https://github.com/codecov/codecov-python"
license=(Apache)
makedepends=(
	python
	python-requests
	python-coverage
	python2
	python2-requests
	python2-coverage
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('8ab9cc6162ee6833b157aef483a1a323')
sha256sums=('6cde272454009d27355f9434f4e49f238c0273b216beda8472a65dc4957f473b')
sha512sums=('bfc1bb3f85baca8de5b3058434242709c6bc4e5e5579490b7b88e308467767718e6e11a0464ea682bbbc4ff279c47b5bafb55b537660c0eb3df48bd5ac4e3d6e')

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
		python-requests
		python-coverage
	)
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

_package_python2(){
	depends=(
		python2
		python2-requests
		python2-coverage
	)
	cd $_pyname-$pkgver-py2
	python2 setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
	for i in "$pkgdir"/usr/bin/*
	do mv -v ${i}{,-2}
	done
	sed -i '1s/python$/python2/g' $(find "$pkgdir" -type f)
}

eval "package_python-${_pyname}(){ _package_python; }"
eval "package_python2-${_pyname}(){ _package_python2; }"
