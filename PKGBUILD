# Maintainer: Fabiano Rosas <fabianorosas@gmail.com>
pkgname=thinarch-git
pkgver=r33.e7a41c9
pkgrel=1
pkgdesc="Arch Linux thin-client server"
arch=('x86_64')
url="https://github.com/fabianorosas/thinarch"
license=('GPL')
depends=("dhcp" "tftp-hpa" "nfs-utils" "devtools" "arch-install-scripts" "btrfs-progs")
makedepends=('git')
conflicts=('thinarch')
provides=('thinarch')
install=thinarch.install
source=("$pkgname"::'git+https://github.com/fabianorosas/thinarch.git')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
  cd "$srcdir/$pkgname"

  install -Dm755 server/thinarch $pkgdir/usr/bin/thinarch

  install -Dm644 {,$pkgdir/etc/thinarch}server/dhcp/dhcpd.conf
  install -Dm644 {,$pkgdir/etc/thinarch}server/tftp/tftpd.service 
  install -Dm644 {,$pkgdir/etc/thinarch}server/nfs/exports

  install -Dm644 client/{ta-mkinitcpio.conf,grub.cfg,hosts} $pkgdir/etc/thinarch/client
}
