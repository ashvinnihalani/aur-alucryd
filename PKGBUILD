# Maintainer: Maxime Gauduin <alucryd@archlinux.org>

pkgname=pantheon-screenshot-git
pkgver=r543.ed4dafa
pkgrel=1
pkgdesc='The Pantheon Screenshot Tool'
arch=('i686' 'x86_64')
url='https://github.com/elementary/screenshot-tool'
license=('GPL3')
groups=('pantheon-unstable')
depends=('cairo' 'gdk-pixbuf2' 'glib2' 'glibc' 'gtk3' 'libcanberra'
         'libgranite.so')
makedepends=('git' 'granite-git' 'intltool' 'meson' 'vala')
provides=('pantheon-screenshot')
conflicts=('pantheon-screenshot')
source=("pantheon-screenshot::git+https://github.com/elementary/screenshot-tool.git")
sha256sums=('SKIP')

pkgver() {
  cd pantheon-screenshot

  echo "r$(git rev-list --count HEAD).$(git rev-parse --short HEAD)"
}

prepare() {
  if [[ -d build ]]; then
    rm -rf build
  fi
  mkdir build
}

build() {
  cd build

  meson ../pantheon-screenshot \
    --buildtype='release' \
    --prefix='/usr'
  ninja
}

package() {
  cd build

  DESTDIR="${pkgdir}" ninja install
}

# vim: ts=2 sw=2 et:
