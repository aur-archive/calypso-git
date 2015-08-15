# Maintainer: Nikolay Amiantov <nikoamia@gmail.com>
# Prev. maintainer: mutantmonkey <mutantmonkey@mutantmonkey.in>
pkgname=calypso-git
pkgver=1.4.r1.g2c5daca
pkgrel=2
pkgdesc="Simple CalDAV/CardDAV server based on Radicale which uses git"
arch=('any')
url="http://keithp.com/blogs/calypso/"
license=('GPL3')
depends=('python2' 'python2-vobject' 'python2-daemon' 'git')
makedepends=('git' 'python2-setuptools')
provides=('calypso')
conflicts=('calypso')
install='calypso.install'
backup=('etc/calypso/config')
source=('git://keithp.com/git/calypso'
        'calypso.service')
sha256sums=('SKIP'
            'eb86b754ec9eb32f213920df57efb171c3b6da8487ab45adfd26397d9201c150')

pkgver() {
  cd "$srcdir/calypso"

  git describe --long | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "$srcdir/calypso"

  sed -i 's/\/usr\/bin\/python/\/usr\/bin\/python2/g' calypso.py
}

package() {
  cd "$srcdir/calypso"

  python2 setup.py install --root="$pkgdir/"
  install -Dm644 "$srcdir/calypso/config" "$pkgdir/etc/calypso/config"
  install -Dm644 "$srcdir/calypso.service" "$pkgdir/usr/lib/systemd/system/calypso.service"
}

# vim:set ts=2 sw=2 et:
