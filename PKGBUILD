# Maintainer: BigfootACA <bigfoot@classfun.cn>

_pyname=pytest-httpserver
_pycname=${_pyname//-/_}
pkgname=python-${_pyname}
pkgver=1.0.1
pkgrel=1
pkgdesc="Http server for pytest to test http clients"
arch=(any)
url="https://github.com/csernazs/pytest-httpserver/"
license=(MIT)
depends=(
	python
	python-werkzeug
)
makedepends=(
	python-setuptools
	python-pip
	python-wheel
)
checkdepends=(
	python-pytest
	python-pytest-cov
	python-coverage
	python-requests
)
source=(https://pypi.io/packages/source/${_pycname::1}/$_pycname/$_pycname-$pkgver.tar.gz)


build(){
	cd $_pycname-$pkgver
	python setup.py build
}

check(){
	cd $_pycname-$pkgver
	python -m pytest
}

package(){
	cd $_pycname-$pkgver
	PYTHONHASHSEED=0 python setup.py install --root "$pkgdir" --optimize=1
	install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}
md5sums=('1a4638a6987565c5460618a7218046dd')
sha256sums=('e359c5722ce2bd3bb68f4606f57d5c846e52bf7c748a70de4a3097bb91006089')
sha512sums=('f581ba1ef579193f6280cb755353fd2fcaae2d1266e554d9526daec322e5c7db6eadef6b8435405647abe3058edd7a55077bf55e7847ee6fe7062c2eeba218b7')
