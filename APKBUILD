# Contributor: Brian Rosner <brian@brosner.com>
# Maintainer: Brian Rosner <brian@brosner.com>
pkgname=rkt
pkgver=1.20.0
pkgrel=0
pkgdesc="rkt is a container engine for Linux designed to be composable, secure, and built on standards"
url="https://github.com/coreos/rkt"
arch="all"
license="APACHE"
depends=""
depends_dev=""
makedepends="$depends_dev coreutils gzip diffutils cpio bc linux-headers wget file gnupg autoconf automake bash openssl-dev acl-dev"
install="$pkgname.pre-install $pkgname.post-install"
subpackages=""
source="rkt-$pkgver.tar.gz::https://github.com/coreos/rkt/archive/v$pkgver.tar.gz"
builddir="$srcdir/rkt-$pkgver"

build() {
	cd "$builddir"
	./autogen.sh
	./configure \
		--build=$CBUILD \
		--host=$CHOST \
		--prefix=/usr \
		--sysconfdir=/etc \
		--mandir=/usr/share/man \
		--localstatedir=/var \
		--disable-tpm \
		--enable-sdjournal=auto \
		|| return 1
	make || return 1
}

package() {
	cd "$builddir"
	make DESTDIR="$pkgdir" install || return 1
}

md5sums="15b28632ef2c50b473de59fb1bd9a85e  rkt-1.20.0.tar.gz"
sha256sums="3b0a08971cc22004fe8367f8d3e35d5f66fcd0191802b4e35c5c273c1f772096  rkt-1.20.0.tar.gz"
sha512sums="37c46a044838660eb22d74ff5cc16c7d9a29b178a5ccece97d484e4aebfd587a7558d665d2a2162adee859135330d4504a4dca60faf4ce5e3552633924c3b960  rkt-1.20.0.tar.gz"

