# Maintainer: bilibili_xiaok <the_xiaok@qq.com>
# Contributor: msojocs <jiyecafe@gmail.com>
# Contributor: YidaozhanYa <yidaozhan_ya@outlook.com>

pkgname=bilibili-linux
_pkgname=bilibili
pkgver=1.7.2
pkgrel=1
pkgdesc='Bilibili unofficial desktop client'
license=('custom')
depends=('ffmpeg' 'electron19' 'libappindicator-gtk3')
arch=('any')
url='https://github.com/msojocs/bilibili-linux'
source=("https://github.com/msojocs/bilibili-linux/releases/download/v${pkgver}-${pkgrel}/bilibili-v${pkgver}-${pkgrel}-x86_64.tar.gz"
        "${_pkgname}.svg"
        "${_pkgname}.desktop")
sha256sums=('47addbfa12d9ad385d0ffc8a039d0fad9a817bf2f41726fd0b214db104e9a054'
            '3a7935d2d13d62fad68b4ee5aaa4832e6a202b379f2be2f80d3723f8f3993192'
            'bc6d8f56b3d928f40800556def5101e8f6e54796b636747bc1111d1b09ee082f')

package() {
    install -Dm644 "${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"
    install -Dm644 "${_pkgname}.svg" "$pkgdir/usr/share/icons/hicolor/scalable/apps/${_pkgname}.svg"
    install -Dm644 -t "${pkgdir}/usr/lib/${_pkgname}" "${srcdir}/app/app.asar"
    install -Dm644 -t "${pkgdir}/usr/lib/${_pkgname}" "${srcdir}/app/app-update.yml"
    cp -r "${srcdir}/app/extensions" "${pkgdir}/usr/lib/${_pkgname}/extensions"
}
