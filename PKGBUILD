# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: namelessjon <jonathan.stott@gmail.com>
# Contributor: Alessio Sergi <asergi at archlinux dot us>

pkgname=libsodium
pkgver=1.0.18
pkgrel=2
pkgdesc="P(ortable|ackageable) NaCl-based crypto library"
arch=('x86_64')
url="https://github.com/jedisct1/libsodium"
license=('custom:ISC')
makedepends=('minisign')
source=("https://download.libsodium.org/libsodium/releases/libsodium-$pkgver.tar.gz"{,.minisig})
sha512sums=('17e8638e46d8f6f7d024fe5559eccf2b8baf23e143fadd472a7d29d228b186d86686a5e6920385fe2020729119a5f12f989c3a782afbd05a8db4819bb18666ef'
            'cfd15c48d9a86db35c490bbe0e0c2629a2aa0ab8156efbaa74859df046aa872f0dc190d062e4efdc68c7d62dbe8afeabcc5310e26a74530840b36e80f029b7a8')
_validminisignkey='RWQf6LRCGA9i53mlYecO4IzT51TGPpvWucNSCh1CBM0QTaLn73Y7GFO3'

prepare() {
  minisign -Vm $pkgname-$pkgver.tar.gz -P $_validminisignkey
}

build() {
  cd "$pkgname-$pkgver"

  ./configure --prefix=/usr
  make
}

check() {
  cd "$pkgname-$pkgver"
  make check
}

package() {
  cd "$pkgname-$pkgver"
  make DESTDIR="$pkgdir" install

  # install license
  install -d -m 755 "$pkgdir/usr/share/licenses/$pkgname"
  install -m 644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
