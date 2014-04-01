# Maintainer: Fabiano Rosas <fabianorosas@gmail.com>
pkgname=thinarch
pkgver=1.0
pkgrel=1
pkgdesc="Arch Linux thin-client server"
arch=('x86_64')
#url="https://wiki.archlinux.org/index.php/Diskless_network_boot_NFS_root"
license=('GPL')
depends=("dhcp" "tftp-hpa" "nfs-utils" "devtools" "arch-install-scripts" "btrfs-progs")
install=thinarch.install
source=(dhcpd.conf exports tftpd.service thinarch.install ta-manage)
md5sums=('6f4554e2176734530c3b3453b3e6bb24'
         '75ab2111958fb6957f9a920a47836784'
         'aa170ca00ad48b5053cc26b92e1083e4'
         'ea4981f77ca977070992987c85b67596'
         'ae9187b2c69eed8482a185ad58f79e7b')

package() {
    cd "$srcdir"

    install -Dm644 dhcpd.conf $pkgdir/etc/dhcpd.conf.thinarch
    install -Dm644 tftpd.service $pkgdir/usr/lib/systemd/system/tftpd.service.thinarch
    install -Dm644 exports $pkgdir/etc/exports.thinarch
    install -Dm755 ta-manage $pkgdir/usr/bin/ta-manage
}
