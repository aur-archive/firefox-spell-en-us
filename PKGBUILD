pkgname=firefox-spell-en-us
_file=199568
pkgver=7.0.1
pkgrel=2
pkgdesc="English (US) spellchecking dictionary for Firefox."
arch=('any')
url="https://addons.mozilla.org/firefox/addon/3497/"
license=('MPL')
depends=('firefox')
makedepends=('unzip')
source=($pkgname-$pkgver.xpi::https://addons.mozilla.org/firefox/downloads/file/$_file/united_states_english_spellchecker-$pkgver.xpi)
noextract=($pkgname-$pkgver.xpi)
sha1sums=('933d1dfaafecf9be772f83a859f9acb86b736f4b')

build() {
  cd "$srcdir"
  [[ -d $pkgname-extract ]] || \
    mkdir $pkgname-extract
  unzip -q -d $pkgname-extract \
    $pkgname-$pkgver.xpi
}

package() {
  cd "$srcdir/$pkgname-extract"
  local emid=$(sed -n '/.*<em:id>\(.*\)<\/em:id>.*/{s//\1/p;q}' install.rdf)
  local dstdir="$pkgdir/usr/lib/firefox/browser/extensions/$emid"
  install -d "$dstdir"
  cp -R * "$dstdir"
  find "$pkgdir" -type d -exec chmod 0755 {} \;
  find "$pkgdir" -type f -exec chmod 0644 {} \;
}

# vim:set ts=2 sw=2 et:
