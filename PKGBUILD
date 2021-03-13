# Maintainer: Samuel Dawant <samueld@mailo.com>

pkgname=dstds
pkgver=1.0.0
_dstuser=dstds
pkgrel=1
pkgdesc="Dedicated server for Don't Starve Together"
arch=('x86_64')
license=("LGPL")
makedepends=('steamcmd')
depends=(
    'steamcmd'
    'lib32-libcurl-gnutls' # multilib mirror
    'screen')
optdepends=(
    "tar: needed in order to create world backups"
           )

backup=("etc/conf.d/${pkgname}")
install="${pkgname}.install"


source=("${pkgname}-backup.service"
    "${pkgname}-backup.timer"
    "${pkgname}.service"
    "${pkgname}.sysusers"
    "${pkgname}.tmpfiles"
    "${pkgname}.conf"
    "${pkgname}.sh"
    "caves_worldgenoverridelua.ini"
    "caves_server.ini"
    "master_server.ini"
    "cluster.ini"
       )

_game="dstds"
_server_root="/srv/dstds"

sha256sums=('090da6683c18e2d5921671d56d3d2d30e7eef3a68f3d0763c89d10e751ff695b'
            'e6f742f5e8287ac34966f7fec42237753c26c94ccdc0e5a4e2e0bb324525cfca'
            'b3bd17667aaef6ae3daf332a030b10aa5d2d764138e5d220f3539d8eb49b0f7b'
            'af88257bb98fe3f5ed656557c7ed085ae0b89a04580563ddb5baccc8bb0cf691'
            'b6b241c735fa6a68aad012e5c37a2bf956f13532210aef6e605e4eef2ca5796a'
            '53230a112b6668a3e8868f0f5285b5be9f81c56b8ad76993fa0dcfa1cba21add'
            'edf936070fe623d21e8c19750d122274b463cbfe232785e183dbaea42e2878b6'
            '701a3edcc01b5d41e7d65b3a7a423f0ed13cee3217767a482b5d039989e0e6e5'
            '9f29838489f6b964355def97f54cb4f35c3c39b032430608a6070ca98e20f7cf'
            'e21e20deaf550bcf123e7b0ea1214fec043ca8693d3b2efe12f18b12056b3319'
            'b63a31df2fdb27bfdf4489ac10a106e3bc48447c434ac0bd2fdbf99fb7884ed7')

package() {
    install -Dm644 "${_game}.conf" "${pkgdir}/etc/conf.d/${_game}"
    install -Dm755 "${_game}.sh" "${pkgdir}/usr/bin/${_game}"
    install -Dm644 "${_game}.service" "${pkgdir}/usr/lib/systemd/system/${_game}.service"
    install -Dm644 "${_game}-backup.service" "${pkgdir}/usr/lib/systemd/system/${_game}-backup.service"
    install -Dm644 "${_game}-backup.timer" "${pkgdir}/usr/lib/systemd/system/${_game}-backup.timer"
    install -Dm644 "${_game}.sysusers" "${pkgdir}/usr/lib/sysusers.d/${_game}.conf"
    install -Dm644 "${_game}.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/${_game}.conf"

    # Create default cluster with caves enabled
    install -Dm644 master_server.ini "${pkgdir}${_server_root}/Clusters/cluster_default/Master/server.ini"
    install -Dm644 caves_server.ini "${pkgdir}${_server_root}/Clusters/cluster_default/Caves/server.ini"
    install -Dm644 caves_worldgenoverridelua.ini "${pkgdir}${_server_root}/Clusters/cluster_default/Caves/worldgenoverride.lua"
    install -Dm644 cluster.ini "${pkgdir}${_server_root}/Clusters/cluster_default/cluster.ini"

    # Give the group write permissions and set user or group ID on execution
    chmod g+ws "${pkgdir}${_server_root}"
}
