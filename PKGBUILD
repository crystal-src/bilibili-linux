# Maintainer: msojocs <jiyecafe@gmail.com>
# Contributor: YidaozhanYa <yidaozhan_ya@outlook.com>

pkgname=bilibili-bin
_pkgname=bilibili
pkgver=1.1.3
pkgrel=4
pkgdesc='Bilibili desktop client'
license=('custom')
depends=('ffmpeg' 'electron' 'libappindicator-gtk3')
makedepends=('asar' 'p7zip' 'nodejs')
arch=('any')
url='https://app.bilibili.com'
install="${pkgname}.install"
source=("${_pkgname}-${pkgver}.exe::https://dl.hdslb.com/mobile/fixed/bili_win/bili_win-install.exe"
        "${_pkgname}"
        "${_pkgname}.png"
        "${_pkgname}.desktop"
        "extensions-v${pkgver}-${pkgrel}.tar.gz::https://mirror.ghproxy.com/https://github.com/msojocs/bilibili-linux/releases/download/v${pkgver}-${pkgrel}/extensions-v${pkgver}-${pkgrel}.tar.gz"
        "injectExt.js"
        "area-unlimit.sh"
        "fix-other.sh"
        "app-decrypt.js"
        "bridge-decode.js"
        "js-decode.js")
noextract=("${_pkgname}-${pkgver}.exe")
sha256sums=('a05c7080b5f71cf3ca6dbd3d7547d1e060af21e6da05ef28e9c28e9e7dc718ef'
            '7da797cd35bc5060e3bfa4ba37681cbbd2201a499477772c008f9f1e691b6ea0'
            '33cba5d0271d5783f353e60dacc01d2edc6629ca760d35427189e316a48f911f'
            'ce35cd6352cdeb248407093eec542dffe4a9a8bb9cab658cee9620752bb34895'
            'd5ce84b9ae0391cba8ffadc648c0bbf41c7a595bc080b599db886246692f0ff1'
            '76fd49617a113799140f1d386f692e6632d84cb7729bf0a482c2ba6b0a379460'
            'ecab58c72159b393c95c40440e3e605813821d2f3bdb35e57d2c337f5abf8e50'
            'fa3d8c2b682745186e3f05322e16cfe9b138394cfcf20bdef8d5b0737fb553dc'
            'aee325dfdb8d13b6d4ea0dfdf6d27ff3ccc39ecb4a1cd4532349d4ab05e01042'
            '9399099c831d97d1f0f85e90adf78eab85b2a00d532b1d428392bb7f77f3b56c'
            '04283a0427fe556ce6045d233328c5f864f7a72c42ba0c64adc71abd99b407ee')
prepare(){
    7z x "${_pkgname}-${pkgver}.exe" -o"tmp/bili" "\$PLUGINSDIR/app-64.7z"
    7z x "tmp/bili/\$PLUGINSDIR/app-64.7z" -o"tmp/bili" "resources"
    rm -rf "tmp/bili/\$PLUGINSDIR/app-64.7z" "tmp/bili/resources/elevate.exe"
    mkdir -p tools
    for file in *.sh app-decrypt.js bridge-decode.js js-decode.js; do
        mv $file tools;
    done
    mkdir -p res/scripts
    mv injectExt.js res/scripts
}
_log() {
    echo -e "\e[1;34m$@\e[0m"
}
build(){
    for script in fix-other.sh area-unlimit.sh; do
        _log "run ${script}"
        "${srcdir}/tools/${script}"
    done
    mv tmp/bili/resources/* app
}
package() {
    install -Dm644 "${_pkgname}.desktop" "${pkgdir}/usr/share/applications/${_pkgname}.desktop"
    install -Dm644 "${_pkgname}.png" "$pkgdir/usr/share/icons/hicolor/512x512/apps/${_pkgname}.png"
    install -Dm644 "${srcdir}/app/app.asar" "${pkgdir}/usr/share/${_pkgname}/${_pkgname}.asar"
    install -Dm644 "${srcdir}/app/app-update.yml" "${pkgdir}/usr/share/${_pkgname}/app-update.yml"
    install -Dm755 "${_pkgname}" "${pkgdir}/usr/bin/${_pkgname}"
    cp -r "${srcdir}/app/extensions" "${pkgdir}/usr/share/${_pkgname}/extensions"
}
