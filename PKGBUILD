# Maintainer: bilibili_xiaok <the_xiaok@qq.com>
# Contributor: msojocs <jiyecafe@gmail.com>
# Contributor: YidaozhanYa <yidaozhan_ya@outlook.com>

pkgname=bilibili-linux
_pkgname=bilibili
pkgver=1.6.1
pkgrel=3
pkgdesc='Bilibili unofficial desktop client'
license=('custom')
depends=('ffmpeg' 'electron19' 'libappindicator-gtk3')
arch=('any')
url='https://github.com/msojocs/bilibili-linux'
source=("https://github.com/msojocs/bilibili-linux/releases/download/v${pkgver}-${pkgrel}/bilibili-v${pkgver}-${pkgrel}-x86_64.tar.gz"
        "${_pkgname}"
        "${_pkgname}.svg"
        "${_pkgname}.desktop")
sha256sums=('7617189b6433129e021b93ee29e6d3a9d1c6b382b92891a0b0738b2dfe52cc34'
            '313b8ffcbc8a63ce6d53a427edc044bcff36464ba6cadbb29173266145bd20b5'
            '3a7935d2d13d62fad68b4ee5aaa4832e6a202b379f2be2f80d3723f8f3993192'
            'e7e40fd93448b1c0b953deaa0829625b30e8f36f61140fa2a5e09012bc459fcb')

package() {
    install -Dm644 "${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"
    install -Dm644 "${_pkgname}.svg" "$pkgdir/usr/share/icons/hicolor/scalable/apps/${_pkgname}.svg"
    install -Dm644 "${srcdir}/app/app.asar" "${pkgdir}/usr/share/${_pkgname}/${_pkgname}.asar"
    install -Dm644 "${srcdir}/app/app-update.yml" "${pkgdir}/usr/share/${_pkgname}/app-update.yml"
    install -Dm755 "${_pkgname}" "${pkgdir}/usr/bin/${_pkgname}"
    cp -r "${srcdir}/app/extensions" "${pkgdir}/usr/share/${_pkgname}/extensions"
}
