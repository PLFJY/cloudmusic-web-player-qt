pkgname=cloudmusic-web-player-qt
pkgver=1.0.0
pkgrel=2
pkgdesc='Unofficial NetEase Cloud Music web player for the desktop'
arch=('x86_64')
url='https://github.com/PLFJY/CloudMusicWebPlayer-Qt'
license=('MIT')
depends=('qt6-base' 'qt6-webengine')
makedepends=('cmake')
source=('CMakeLists.txt' 'main.cpp' 'resources.qrc' 'favicon.png' 'LICENSE' "$pkgname.desktop")
sha256sums=('SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP' 'SKIP')

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
