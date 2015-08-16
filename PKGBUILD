# $Id$
# Maintainer: Swift Geek swift geek (ɐt) g mɐil
# Old Maintainer: Jan de Groot <jgc@archlinux.org>


pkgname='gvfs-obexftp-bluez4' # gvfs-obexftp is already scammy provided by gvfs package, so no need for 'provides' line and also pkgname is like that cuz gvfs has gvfs-obexftp in 'replaces'
pkgdesc="ObexFTP (bluetooth) backend for gvfs. Bluez4"
pkgver=1.18.3
pkgrel=1
arch=('i686' 'x86_64')
license=('LGPL')
depends=("gvfs=$pkgver" 'libgcrypt' 'dbus-glib' 'bluez4' 'obex-data-server')
makedepends=('avahi' 'bluez-libs' 'dbus-glib' 'fuse' 'intltool' 'libarchive' 'libcdio-paranoia' 'libgphoto2' 'libimobiledevice' 'libsoup' 'smbclient' 'udisks2' 'libsecret' 'docbook-xsl' 'gtk3' 'libmtp' 'gnome-online-accounts' 'libbluray')
url="http://www.gnome.org"
options=(!libtool)
install=gvfs-module.install
source=("http://ftp.gnome.org/pub/gnome/sources/gvfs/${pkgver%.*}/gvfs-$pkgver.tar.xz")
sha256sums=('1d829716dcf1c5c016ee0c8aaff4cfd4fc4c719a4125f5c4f206f26c5bdc472c')

build() {
  cd "gvfs-$pkgver"
  autoreconf -fi
  ./configure --prefix=/usr --sysconfdir=/etc \
      --localstatedir=/var --disable-static \
      --libexecdir=/usr/lib/gvfs \
      --with-bash-completion-dir=/usr/share/bash-completion/completions
  make
}

package() {
  cd "gvfs-$pkgver/daemon"
  install -D .libs/gvfsd-obexftp "$pkgdir/usr/lib/gvfs/gvfsd-obexftp"
  install -Dm644 obexftp.mount "$pkgdir/usr/share/gvfs/mounts/obexftp.mount"
}

