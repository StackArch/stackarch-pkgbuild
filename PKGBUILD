# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=doc8
pkgbase=python-$_pyname
pkgname=(python-$_pyname)
pkgver=0.9.0
pkgrel=1
pkgdesc="Style checker for Sphinx (or other) RST documentation"
arch=(any)
url="https://github.com/pycqa/doc8"
license=(Apache)
makedepends=(
	python
	python-docutils
	python-restructuredtext-lint
	python-stevedore
	python-pygments
	python-setuptools
)
checkdepends=(
	python-toml
	python-mock
	python-nose
	python-pytest
	python-testtools
)
source=(https://pypi.io/packages/source/${_pyname::1}/$_pyname/$_pyname-$pkgver.tar.gz)
md5sums=('c87d4c7a333053cd25edeba729f328ab')
sha256sums=('380b660474be40ce88b5f04fa93470449124dbc850a0318f2ef186162bc1360b')
sha512sums=('ebff512dfffb7d21d9173f0ff6ca282810334abfbd9c95570dba4e27796e79bc8d14fd2914c029a3cbf235766305dfa37ca565e2e20d32c63ea741f8ce4d1ae2')

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
