#forked from the existing version, maintained by David Runge
pkgname=libspecbleach-dl1bz
pkgver=0.1.6
pkgrel=3
pkgdesc="C library for audio noise reduction"
arch=(x86_64)
url="https://github.com/dl1bz/libspecbleach"
license=(LGPL2.1)
conflicts=('libspecbleach')
depends=(
  glibc
)
makedepends=(
  fftw
  meson
)
provides=(libspecbleach.so)
#source=($url/archive/v$pkgver/${pkgname%-dl1bz}-v$pkgver.tar.gz)
source=("git+$url.git")
sha512sums=('SKIP')

build() {
  arch-meson ${pkgname%-dl1bz} build
  meson compile -C build
}

check() {
  meson test -C build
}

package() {
  depends+=(
    fftw libfftw3f.so
  )

  meson install -C build --destdir="$pkgdir"
  install -vDm 644 ${pkgname%-dl1bz}/README.md -t "$pkgdir/usr/share/doc/${pkgname%-dl1bz}/"
  install -vDm 644 ${pkgname%-dl1bz}/examples/* -t "$pkgdir/usr/share/doc/${pkgname%-dl1bz}/example/"
}
