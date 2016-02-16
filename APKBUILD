# Maintainer: Andreas Streichardt <andreas@arangodb.com>
# Contributor:
pkgname=mesos
pkgver=0.27.0
pkgrel=0
pkgdesc="Apache Mesos"
url="http://mesos.apache.org/"
arch="all"
license="ASL 2.0"
depends=""
depends_dev=""
makedepends="$depends_dev"
install=""
subpackages="$pkgname-dev"
source="http://www.apache.org/dist/$pkgname/$pkgver/$pkgname-$pkgver.tar.gz
	10-timeval.patch	
	20-fstab.patch	
"

_builddir="$srcdir"/$pkgname-$pkgver
prepare() {
	local i
	cd "$_builddir"
	for i in $source; do
		case $i in
		*.patch) msg $i; patch -p1 -i "$srcdir"/$i || return 1;;
		esac
	done
}

build() {
	cd "$_builddir"
	mkdir build
	cd build
	LDFLAGS=-lfts ../configure --prefix=/usr/ \
		--sysconfdir=/etc
	make || return 1
}

package() {
	cd "$_builddir"/build
	make DESTDIR="$pkgdir" install || return 1
}

md5sums="54dae5aeed210fbec8c445af1120ccc2  mesos-0.27.0.tar.gz
c998d31e594cc5b9b6f3bc9ce16654bc  10-timeval.patch
1076ac4ca8c04f1995355beb5f292163  20-fstab.patch"
sha256sums="d5f356ad30ba661bc65af34de3cc54176b0ac90f2c58ad02b802a10e1bab0d55  mesos-0.27.0.tar.gz
ef051481bfb27d08a4ac9e953d44848ff89925cf1d72cc0cab22bb9f42580f51  10-timeval.patch
f0d2716b7bb28fb9c5924379de10e220e115de0013e58b0035fda650565da25c  20-fstab.patch"
sha512sums="369fc5153d13b7380a479d1ed33ff1085e9a4425f5ea7f72a37d7d9fd098333f54f97e91ca9926295abfaa92a33e140528188809254024ac62ce0b31ed137599  mesos-0.27.0.tar.gz
a38ddca38df5779d3381bad437246f0f5c6025e742d12e611fed1b42b4c1127933fa42ffc13a6048e92b9cd19df92dc250250e8569f0edf7049aa552a5487665  10-timeval.patch
80b4f6c55fb8c47392483901ac7280e4efbc581f5b51de617d8a2ef24a1969d07215040dd1eaa0348781a8619ce0d3b50e655f49500ec9b3b21e98e34a485771  20-fstab.patch"
