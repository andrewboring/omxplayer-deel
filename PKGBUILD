# Maintainer: Andrew Boring <andrew@andrewboring.com>
# Contributor: Barry Gilbert <barry@deelmedia.com>
# Based on the original Arch Linux Arm build by:
# Kevin Mihelich <kevin@archlinuxarm.org>
# Contributor: Huulivoide <gmail.com: jesse.jaara>
# Contributor: Jonathan Hudson <daria.co.uk: jh+arch>

buildarch=20

pkgname=omxplayer-deel
pkgver=513.9680058
pkgrel=1
pkgdesc="Command line media player for the RaspberryPi (Deel media verion)."
arch=('armv6h' 'armv7h')
url="https://github.com/deelmedia/omxplayer"
license=(GPL2)
depends=('ffmpeg' 'raspberrypi-firmware' 'fbset')
makedepends=('git' 'boost')
optdepends=('ttf-freefont')
provides=(omxplayer)
conflicts=('omxplayer' 'omxplayer-bin')
source=('git://github.com/deelmedia/omxplayer.git')
md5sums=('SKIP')

pkgver() {
  cd omxplayer
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

prepare() {
  cd "${srcdir}/omxplayer"
}

build() {
  cd "${srcdir}/omxplayer"

  [[ $CARCH == "armv7h" ]] && CFLAGS=`echo $CFLAGS | sed -e 's/vfpv3-d16/neon/'` && CXXFLAGS="$CFLAGS"
  make
}

package() {
  cd "${srcdir}/omxplayer"

  make DESTDIR="${pkgdir}" install
}
