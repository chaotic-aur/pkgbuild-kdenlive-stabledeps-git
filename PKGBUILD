# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Antonio Rojas <arojas@archlinux.org>
# Contributor: Sergej Pupykin <pupykin.s+arch@gmail.com>
# Contributor: Zuf <kontakt.zuf@gmail.com>
# Contributor: Darwin Bautista <djclue917@gmail.com>
# Contributor: Gustavo Alvarez <sl1pkn07@gmail.com>

pkgname=kdenlive-stabledeps-git
pkgver=22.03.70.r15337
pkgrel=1
pkgdesc='A non-linear video editor for Linux using the MLT video framework'
arch=(x86_64)
url='https://apps.kde.org/kdenlive/'
license=(GPL)
depends=(qt5-networkauth knewstuff knotifyconfig kfilemetadata purpose mlt breeze-icons frei0r-plugins)
makedepends=(extra-cmake-modules kdoctools v4l-utils doxygen qt5-tools)
conflicts=(${pkgname%-stabledeps-git} kdenlive-git)
provides=(${pkgname%-stabledeps-git} kdenlive-git)
optdepends=('ffmpeg: for FFmpeg plugin'
            'dvgrab: for firewire capture'
            'recordmydesktop: for screen capture'
            'opencv: for motion tracking'
            'plasma-desktop-git: theme configuration'
            'opentimelineio: timeline export/import')
source=("git+https://invent.kde.org/multimedia/${pkgname%-stabledeps-git}")
sha256sums=('SKIP')

pkgver() {
  cd ${srcdir}/${pkgname%-stabledeps-git}
  _ver="$(cat CMakeLists.txt | grep RELEASE_SERVICE_VERSION | cut -d '"' -f2 | tr '\n' '.' | cut -d "." -f 1-3)"
  echo "$(echo ${_ver}).r$(git rev-list --count HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-stabledeps-git} \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
