#!/bin/bash

# Created from the original package by

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Mantainer: ObserverOfTime <chronobserver@disroot.org>
# based on lib32-numactl

_relname=numactl
pkgname=lib32-libnuma
pkgver=2.0.14
pkgrel=3
pkgdesc='Simple NUMA policy support 32-bit version. Libraries only'
arch=('x86_64')
url='https://github.com/numactl/numactl'
license=('LGPL2.1' 'GPL2')
depends=(
  'perl'
   'numactl'
    'lib32-gcc-libs'
    )
conflicts=(
  'lib32-numactl'
  )
creplaces=(
  'lib32-numactl'
  )
provides=(
  "lib32-numactl=${pkgver}"
  )
source=(
  "$url/releases/download/v${pkgver}/${_relname}-${pkgver}.tar.gz"
  )
sha512sums=(
  '28b95985d6b2f26c5f6f15fe235224c998c86f534adf5fdaa355a292cf2fd65515c91ba2a76c899d552d439b18ea1209a1712bd6755f8ee3a442f3935993b2e6'
  )

build() {
  cd "$srcdir/$_relname-${pkgver/_/-}"
  export CC='gcc -m32' CXX='g++ -m32' \
         PKG_CONFIG_PATH='/usr/lib32/pkgconfig'
  ./configure \
    --prefix=/usr \
    --libdir=/usr/lib32 \
    --host=i686-unknown-linux-gnu
  make
}

package() {
  cd "$srcdir/$_relname-${pkgver/_/-}"
  make DESTDIR="$pkgdir" install
  rm -rf "$pkgdir"/usr/{share,bin,include}
}

 
