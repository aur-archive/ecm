# Contributor: Slash <demodevil5 at yahoo dot com>
# Contributor: Nathan Owe <ndowens.aur at gmail dot com>
# Contributor: Christoph Zeiler <rabyte*gmail>

pkgname=ecm
pkgver=1.03
pkgrel=3
pkgdesc="Converts CD image files into a lossless format optimized for compression tools"
arch=('i686' 'x86_64' 'mips64el')
url="http://www.neillcorlett.com/ecm/"
license=('GPL3')
depends=('glibc' 'shared-mime-info')
provides=('unecm')
install=ecm.install
source=( 'ecm.desktop' 'unecm.desktop' 'ecmfiles.xml' \
"ftp://ftp.netbsd.org/pub/pkgsrc/distfiles/cmdpack-${pkgver}-src.tar.gz")
md5sums=('3afc84852f0cfcb32199031da14a23f8'
         '900958150b5d501fb1485e876d291582'
         '9ae4d929a7dcedfcb188ca2bd28c0f3b'
         '79f62f20dc5ccb68d9a130e17798bb7f')

build() {
    cd ${srcdir}/cmdpack-${pkgver}-src/src/

    gcc -O9 -Wall -Wextra -Werror -fomit-frame-pointer "ecm.c" -s -o "ecm"
}

package() {
    cd ${srcdir}/cmdpack-${pkgver}-src/src/

    # Install ecm Binary and symlinks
    install -Dm755 ecm ${pkgdir}/usr/bin/ecm
    ln -s /usr/bin/ecm ${pkgdir}/usr/bin/unecm

    # Install KDE4 Service Menu Files
    install -D -m 644 $srcdir/ecmfiles.xml \
        $pkgdir/usr/share/mime/application/ecmfiles.xml

    install -D -m 644 $srcdir/ecm.desktop \
        $pkgdir/usr/share/kde4/services/ServiceMenus/ecm.desktop

    install -D -m 644 $srcdir/unecm.desktop \
        $pkgdir/usr/share/kde4/services/ServiceMenus/unecm.desktop
}
