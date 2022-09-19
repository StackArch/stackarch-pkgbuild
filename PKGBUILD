# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=doc8
pkgbase=python-$_pyname
pkgname=(python-$_pyname)
pkgver=1.0.0
pkgrel=1
pkgdesc="Style checker for Sphinx (or other) RST documentation"
arch=(any)
url="https://github.com/pycqa/doc8"
license=(Apache)
makedepends=(
	python
	python-wheel
	python-docutils
	python-restructuredtext-lint
	python-stevedore
	python-pygments
	python-setuptools
)
checkdepends=(
	python-toml
	python-mock
	python-pytest
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('7ff8578cbdbefebbf48abd6a0c25a2fe')
sha256sums=('1e999a14fe415ea96d89d5053c790d01061f19b6737706b817d1579c2a07cc16')
sha512sums=('98ad904a994536de80d6e89a221e3d7159d5188a0f57d07961f646e0591f81790f06c624ef90c32e28ff89ecf9e39b2b052363995aaece6a4e30f643c37964b9')

prepare(){
	pushd $_pyname-$pkgver
	echo 'from setuptools import setup; setup();' > setup.py
	popd
}

build(){
	pushd $_pyname-$pkgver
	python setup.py build
	popd
}

check(){
	pushd $_pyname-$pkgver
	python -m pytest
	popd
}

_package_python(){
	depends=(
		python
		python-docutils
		python-restructuredtext-lint
		python-stevedore
		python-pygments
	)
	cd $_pyname-$pkgver
	python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

eval "package_python-${_pyname}(){ _package_python; }"
