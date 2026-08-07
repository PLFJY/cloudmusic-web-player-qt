pkgname=cloudmusic-web-player-qt
pkgver=1.0.0
pkgrel=1
pkgdesc='Unofficial NetEase Cloud Music web player for the desktop'
arch=('x86_64')
url='https://github.com/PLFJY/CloudMusicWebPlayer-Qt'
license=('MIT')
depends=('qt6-base' 'qt6-webengine')
makedepends=('cmake')
source=('CMakeLists.txt' 'main.cpp' 'resources.qrc' 'favicon.png' 'LICENSE' "$pkgname.desktop")
sha256sums=('8eae148b41be040bf4520a03710758830f7360f53adaa8a72453a61f69f4a922'
           '6cc90e05e40de81cd60b19e370c2f79df2632e3bdeb23c67045d943dac83bea6'
           'a08edef36b20017691126ae563ecf5b6f8ad1a06f5830a177c28170c7e668929'
           'ba34b1c0e9287a40a24bb0362bd1c96a2d8d4be40ca260ed3e41edd25cb2103a'
           '7aae378a247fbe7b989fb4c80202702563a33a287eac793e3903f3888fc39bfd'
           '74bf2f36e1387e4658f460255abda16515a2a6191cd96ac94957982e7e77bc62')

build() {
    cmake -S . -B build \
        -DCMAKE_BUILD_TYPE=Release \
        -DCMAKE_INSTALL_PREFIX=/usr \
        -DCMAKE_CXX_FLAGS='-O2 -pipe -march=x86-64 -mtune=generic'
    cmake --build build --parallel
}

package() {
    install -Dm755 "build/cloudmusic-web-player-qt" \
        "$pkgdir/usr/bin/cloudmusic-web-player-qt"
    install -Dm644 favicon.png \
        "$pkgdir/usr/share/icons/hicolor/256x256/apps/cloudmusic-web-player-qt.png"
    install -Dm644 "$pkgname.desktop" \
        "$pkgdir/usr/share/applications/$pkgname.desktop"
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
