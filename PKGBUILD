# Maintainer: Samuel D <samuel.dawant@alumni.umons.ac.be>

pkgname=dstds
_dstuser=dstds
pkgver=1.0.1
pkgrel=1
pkgdesc="Dedicated server for Don't Starve Together"
arch=('x86_64')
depends=(
    'lib32-gcc-libs'
    'lib32-libcurl-gnutls'
    'lib32-glibc'
    'lib32-libidn2'
    'lib32-libssh2'
    'lib32-libpsl'
    'lib32-nettle'
    'lib32-gnutls'
    'lib32-zlib'
    'lib32-libunistring'
    'lib32-openssl'
    'lib32-p11-kit'
    'lib32-libtasn1'
    'lib32-gmp'
    'lib32-libffi'
    'screen'
    'steamcmd'
)
source=(
    "dstds"
)
sha256sums=(
    "c1554992f12aa97a39cd9a01f2181004db5728d2cdb57a9d9f6118e44d619a48"
)


# prepare() {
# }

# build() {
# }

package() {
    install -Dm755 dstds           "${pkgdir}/usr/bin/dstds"
}
