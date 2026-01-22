# Maintainer: Fabio 'Lolix' Loli <fabio.loli@disroot.org> -> https://github.com/FabioLolix

pkgname=rsdkv4-git
pkgver=r676.7a23c39
pkgrel=1
pkgdesc="Complete decompilation of Sonic 1 & Sonic 2 (2013) & Retro Engine (v4)"
arch=('powerpc' 'powerpc64' 'powerpc64le' 'espresso')
url="https://github.com/RSDKModding/RSDKv4-Decompilation"
license=(custom)
depends=(glibc gcc-libs sdl2 glew libvorbis libglvnd)
makedepends=(git cmake)
options=('!debug' 'strip')
source=("rsdkv4::git+https://github.com/RSDKModding/RSDKv4-Decompilation.git")
sha256sums=('SKIP')

prepare() {
  cd rsdkv4
  git submodule init
  git -c protocol.file.allow=always submodule update
}

build() {
  cmake -B build -S "rsdkv4" -Wno-dev \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr

  cmake --build build
}

package() {
  #DESTDIR="$pkgdir" cmake --install build
  install -D build/RSDKv4 -t "${pkgdir}/usr/bin"
  install -dm755 "$pkgdir/usr/share/icons"
  cp -r "$srcdir/rsdkv4/RSDKv4/RSDKv4 Decomp Icon.ico" "$pkgdir/usr/share/icons/RSDKv4.ico"

  install -D rsdkv4/LICENSE.md -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
