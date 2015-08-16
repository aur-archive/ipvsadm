# Contributor: Judd Vinet <jvinet@zeroflux.org>
pkgname=ipvsadm
pkgver=1.25
pkgrel=2
pkgdesc="The IP Virtual Server administration utility"
arch=('i686' 'x86_64')
url="http://www.linuxvirtualserver.org/software/ipvs.html"
license=('GPL')
depends=('iptables' 'libnl' 'popt')
backup=('etc/conf.d/ipvsadm')
options=('!makeflags')
source=(http://www.linuxvirtualserver.org/software/kernel-2.6/ipvsadm-${pkgver}.tar.gz ipvsadm ipvsadm.conf.d)
md5sums=('772a053f5fe888cd25784c5f55d31fc3' 'a8254be4e3b93f4cebe3d3d92515e5ee'\
         '3a7bc36ca81db2e0373abf9b90369d4f')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}
  make INCLUDE="-I/usr/src/linux-`uname -r`/include -I.. -I." || return 1
  make BUILD_ROOT=${pkgdir} MANDIR=usr/share/man install || return 1
  install -D -m755 ../ipvsadm ${pkgdir}/etc/rc.d/ipvsadm
  install -D -m644 ../ipvsadm.conf.d ${pkgdir}/etc/conf.d/ipvsadm
  install -d -m755 ${pkgdir}/etc/ipvsadm
}
