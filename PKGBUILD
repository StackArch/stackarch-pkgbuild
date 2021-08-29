# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=codecov
pkgbase=python-$_pyname
pkgname=(python{,2}-$_pyname)
pkgver=2.1.12
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
md5sums=('990a20da8998c7ca8ad204512c1e4e92')
sha256sums=('a0da46bb5025426da895af90938def8ee12d37fcbcbbbc15b6dc64cf7ebc51c1')
sha512sums=('9d364844dc864996e7d65d6210c7bca345a67d5aa61bcdd351591f0aeadcd2662101e59449e8a86b8341d9fc840889cb635b2c41c6287001b598ee1647c86b02')

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
