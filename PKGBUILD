# Maintainer: oriaca <oriaca372m@outlook.jp>
# Maintainer: Jan Alexander Steffens (heftig) <heftig@archlinux.org>
# Maintainer: Jan de Groot <jgc@archlinux.org>

pkgname=freetype2-oriaca
pkgver=2.10.4
pkgrel=1
pkgdesc="Font rasterization library with patch to disable darkening"
url="https://www.freetype.org/"
arch=(x86_64)
license=(GPL)
# adding harfbuzz for improved OpenType features auto-hinting
# introduces a cycle dep to harfbuzz depending on freetype wanted by upstream
depends=(zlib bzip2 sh libpng harfbuzz)
makedepends=(libx11)
provides=(libfreetype.so freetype2)
conflicts=(freetype2)
install=freetype2.install
backup=(etc/profile.d/freetype2.sh)
source=(https://download-mirror.savannah.gnu.org/releases/freetype/freetype-$pkgver.tar.xz{,.sig}
        0001-Enable-table-validation-modules.patch
        0002-Enable-subpixel-rendering.patch
        0003-Enable-infinality-subpixel-hinting.patch
        0004-Enable-long-PCF-family-names.patch
        0005-Disable-darkening.patch
        freetype2.sh)
sha256sums=('86a854d8905b19698bbc8f23b860bc104246ce4854dcea8e3b0fb21284f75784'
            'SKIP'
            'f41df4f336d5e82e58733c7a4594476c9216cfc85c096327745a7e1b559e17e1'
            'dc77c1cfee4bf8e7e0690628c95d211df09e0d0750e4c8f075b78b5f105514f7'
            '21a62bc12b848320c686d602d8d4e3bcd51294a9def4dc9c301736e077b59f3f'
            '266384222f87a02fb02b2179828f6c26fe6d7b1fd09d1f7e3734e7fcb09cda2e'
            '277bb251cbdcacd309e88f684dedb9e805244637973d2f58a30b20b601b4e23b'
            'f7f8e09c44f7552c883846e9a6a1efc50377c4932234e74adc4a8ff750606467')
validpgpkeys=(58E0C111E39F5408C5D3EC76C1A60EACE707FDA5) # Werner Lemberg <wl@gnu.org>

prepare() {
  # Rename source dir to allow building the demos
  mv freetype-$pkgver freetype2

  cd freetype2
  patch -Np1 -i ../0001-Enable-table-validation-modules.patch
  patch -Np1 -i ../0002-Enable-subpixel-rendering.patch
  patch -Np1 -i ../0003-Enable-infinality-subpixel-hinting.patch
  patch -Np1 -i ../0004-Enable-long-PCF-family-names.patch
  patch -Np1 -i ../0005-Disable-darkening.patch
}

build() {
  cd freetype2
  ./configure --prefix=/usr --disable-static
  make
}

check() {
  cd freetype2
  make -k check
}

package() {
  cd freetype2
  make DESTDIR="$pkgdir" install
  install -Dt "$pkgdir/etc/profile.d" -m644 ../freetype2.sh
}

# vim:set ts=2 sw=2 et:
