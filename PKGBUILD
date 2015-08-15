# Contributor: Lukasz Jedrzejewski <jedrzejewskiluk at gmail dot com>
pkgname=dcp195c
pkgver=1.1.3_1
_pkgver="${pkgver//_/-}"
pkgrel=2
pkgdesc="CUPS driver for Brother DCP-195 printer"
arch=('any')
license=('custom:Brother Industries')
depends=('cups')
makedepends=('rpmextract' 'sed' 'patch')
url="http://solutions.brother.com/linux/en_us/index.html"
source=(http://www.brother.com/pub/bsc/linux/dlf/${pkgname}lpr-"${_pkgver}".i386.rpm \
    http://www.brother.com/pub/bsc/linux/dlf/${pkgname}cupswrapper-"${_pkgver}".i386.rpm \
    systemd.patch)
md5sums=('6623c534c3805e4b2588921b8a326b3c'
         'ba3bf7b8cb642f58b48576e530769641'
         'b9c97a1b1040dad7463cfe8666871758')

build() {
    cd "$startdir/pkg/dcp195c" || return 1
    for n in $startdir/src/*.rpm; do
        rpmextract.sh "$n" || return 1
    done
    sed -i 's|/etc/init.d|/etc/rc.d|' $pkgdir/opt/brother/Printers/$pkgname/cupswrapper/cupswrapper${pkgname}
    patch -p1 -i $startdir/systemd.patch
}
