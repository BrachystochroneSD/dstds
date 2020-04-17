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
    'steamcmd'
)
source=(
    "dstds"
)
sha256sums=(
    "522950de97108d5995f15f81b9d6ddfaed7be5843b5ba5ba61a8e5e688b5151d"
)


# prepare() {
# }

# build() {
# }

package() {
    install -Dm755 dstds           "${pkgdir}/usr/bin/dstds"
}
