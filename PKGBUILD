# Maintainer: Fabiano Rosas <fabianorosas@gmail.com>
pkgname=thinarch-git
pkgver=r30.f09eae4
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
  ls
  install --backup=numbered -Dm644 server/dhcp/dhcpd.conf    $pkgdir/etc/dhcpd.conf
  install --backup=numbered -Dm644 server/tftp/tftpd.service $pkgdir/usr/lib/systemd/system/tftpd.service
  install --backup=numbered -Dm644 server/nfs/exports        $pkgdir/etc/exports
  install -Dm755 thinarch $pkgdir/usr/bin/thinarch
}
