pkgname=bomi
pkgver=0.9.11
pkgrel=1
pkgdesc="Powerful and easy-to-use GUI multimedia player based on mpv"
arch=('x86_64')
url="http://$pkgname-player.github.io"
license=('GPL')
provides=('bomi')
install=$pkgname.install
depends=('qt5-base' 'qt5-declarative' 'qt5-x11extras' 'qt5-quickcontrols' 'icu'
         'libdvdread' 'libdvdnav' 'libcdio-paranoia' 'libcdio'
         'alsa-lib' 'pulseaudio' 'jack' 'libchardet' 'libbluray'
         'mpg123' 'libva' 'libgl' 'fribidi' 'libass' 'ffmpeg')
makedepends=('mesa' 'gcc' 'pkg-config' 'python3' 'qt5-tools')
optdepends=('libaacs: AACS decryption for Blu-ray support'
            'libbdplus: BD+ decryption for Blu-ray support'
            'youtube-dl: streaming website support including YouTube')
source=($pkgname-$pkgver.tar.gz::https://github.com/xylosper/bomi/archive/v$pkgver.tar.gz)
md5sums=('27eada1e9e01742067e5ed9e3b80395e')
#options=(debug !strip)

build() {
  cd "$srcdir/$pkgname-$pkgver"
  ./configure --prefix=/usr --enable-jack --enable-cdda --enable-pulseaudio
  sed -i 's/--disable-cplayer/--disable-cplayer --disable-rubberband/g' build-mpv
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make DEST_DIR=$pkgdir install
}
