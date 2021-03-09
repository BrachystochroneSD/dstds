# Maintainer: Samuel Dawant <samueld@mailo.com>

pkgname=dstds
pkgver=1.1.0
_dstuser=dstds
pkgrel=1
pkgdesc="Dedicated server for Don't Starve Together"
arch=('x86_64')
license=("LGPL")
# makedepends=('steamcmd')
depends=('steamcmd' 'lib32-libcurl-gnutls' 'screen')
optdepends=("tar: needed in order to create world backups")
            # "steamcmd: needed to update the binaries of the dedicated server")
source=("dstds")
backup=("etc/conf.d/${pkgname}")
install="${pkgname}.install"


source=("${pkgname}-backup.service"
    "${pkgname}-backup.timer"
    "${pkgname}.service"
    "${pkgname}.sysusers"
    "${pkgname}.tmpfiles"
    "${pkgname}.conf"
    "${pkgname}.sh")

_game="dstds"
_server_root="/srv/dstds"

sha256sums=('090da6683c18e2d5921671d56d3d2d30e7eef3a68f3d0763c89d10e751ff695b'
            'e6f742f5e8287ac34966f7fec42237753c26c94ccdc0e5a4e2e0bb324525cfca'
            'b3bd17667aaef6ae3daf332a030b10aa5d2d764138e5d220f3539d8eb49b0f7b'
            'af88257bb98fe3f5ed656557c7ed085ae0b89a04580563ddb5baccc8bb0cf691'
            'b6b241c735fa6a68aad012e5c37a2bf956f13532210aef6e605e4eef2ca5796a'
            '00837f74e77c1f4381a7758f60948d2ef27f705382a06d5596c2a9b5f682f8a7'
            '8856305d07b6090bdc6d05a7b564f2252807e9a56687ec418365615bf160206c')

# prepare() {
#     mkdir src
#     steamcmd +login anonymous +force_install_dir "src" +app_update 343050 validate +quit
# }

package() {
    install -Dm644 "${_game}.conf" "${pkgdir}/etc/conf.d/${_game}"
    install -Dm755 "${_game}.sh" "${pkgdir}/usr/bin/${_game}"
    install -Dm644 "${_game}.service" "${pkgdir}/usr/lib/systemd/system/${_game}.service"
    install -Dm644 "${_game}-backup.service" "${pkgdir}/usr/lib/systemd/system/${_game}-backup.service"
    install -Dm644 "${_game}-backup.timer" "${pkgdir}/usr/lib/systemd/system/${_game}-backup.timer"
    install -Dm644 "${_game}.sysusers" "${pkgdir}/usr/lib/sysusers.d/${_game}.conf"
    install -Dm644 "${_game}.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/${_game}.conf"

    # Link the log files
    # mkdir -p "${pkgdir}/var/log/"
    # install -dm775 "${pkgdir}/${_server_root}/logs"
    # ln -s "${_server_root}/logs" "${pkgdir}/var/log/${_game}"

    # Give the group write permissions and set user or group ID on execution
    chmod g+ws "${pkgdir}${_server_root}"
}
