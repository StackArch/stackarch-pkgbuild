pkgname=etcd
pkgver=3.5.0
pkgrel=1
pkgdesc="A highly-available key value store for shared configuration and service discovery."
arch=(x86_64 i686 arm armv6h armv7h aarch64)
url="https://github.com/etcd-io/etcd"
license=(Apache)
depends=(glibc)
makedepends=(go git)
backup=(etc/conf.d/etcd)
source=(
	https://github.com/etcd-io/"${pkgname}"/archive/v"${pkgver}".tar.gz
	etcd.conf
	etcd.service
	sysusers.conf
)
md5sums=('e21c108ea8cacf6e994296c38a0b3bcd'
         '990b54ca04014a28f65ec5d5dda71503'
         'f7007f79a89373c6bb04ff440075c8f1'
         '85652942595044bce58da76fafd06333')
sha256sums=('f30f68c52a7547af08be7d166884c94885ea8a593c1c1e814c89b24148ee1921'
            'fa98f53791b5f922828e12c2e1146ef2c9f402367474b05144f6e17f8cb16a0d'
            '2b271e4a59c489928e70c420f4bdf54c513be610b127eb4cbda4aa78fe0a4cd7'
            'd6540be435a1753dcccc56bb1c04369064dab69b809be2a8652f03a77cdeb109')
sha512sums=('ea332fe99c9bce842dc9919b7cf676db2024adf83c23c37dcd8db48bc2a2d3f98879893701644a2317dea69dc15f747f42f5473f14f4343fe7aee9a6b4ebceca'
            'a4843be558e401fa6c612c88059fbe83025eb86077bec70331bc43b7dd48cc09fd186f0ea9d4b45c802a617d5f771752bb2ed8113ce02a6b6eaaabd926e227e9'
            'ba86a25348ed28788c4a0a3820f761554a5d8883d03b8f97d666110a9dc6f981ba05a22f51995b91067cd87aa11fb160354cfa9b2c5e3d97553c79a567ebb578'
            '5d569dcd730732509adb9496201d3895ae2f2a6ae67f7543428f190cf0b405352486d7a32a1ac69c6c4ef37606eb1fae74e89c032a8ae48ebbc3b24a3476f8e2')

build(){
	export CGO_CPPFLAGS="${CPPFLAGS}"
	export CGO_CFLAGS="${CFLAGS}"
	export CGO_CXXFLAGS="${CXXFLAGS}"
	export CGO_LDFLAGS="${LDFLAGS}"
	export GO_BUILD_FLAGS="-trimpath -buildmode=pie -mod=readonly -modcacherw"
	export GO_LDFLAGS="-linkmode=external -extldflags=${LDFLAGS}"
	cd "${pkgname}-${pkgver}"
	go mod tidy
	./build.sh
}

package(){
	cd "${srcdir}"
	install -Dm644 etcd.conf "${pkgdir}"/etc/conf.d/"${pkgname}"
	install -Dm644 etcd.service "${pkgdir}"/usr/lib/systemd/system/"${pkgname}".service
	install -Dm644 sysusers.conf "${pkgdir}"/usr/lib/sysusers.d/"${pkgname}".conf
	cd "${pkgname}-${pkgver}"
	install -Dm755 bin/etcd "${pkgdir}"/usr/bin/etcd
	install -Dm755 bin/etcdctl "${pkgdir}"/usr/bin/etcdctl
	install -Dm644 LICENSE "${pkgdir}"/usr/share/licenses/"${pkgname}"/LICENSE
}
