# Maintainer: CookieSource <cookiesource@rebornos.org>, Panda <panda@rebornos.org>
# Co maintainer: RebornOS Team <team@rebornos.org>
pkgname=peony-extensions
pkgver=3.2.3
pkgrel=1
pkgdesc="Set of extensions for Peony, the UKUI file manager."
arch=('aarch64' 'x86_64')
url="https://github.com/ukui/peony-extensions"
license=('LGPL3')
depends=('peony')
makedepends=('make' 'qt6-base')
provides=(${pkgname})
conflicts=(${pkgname})
source=($pkgname-$pkgver.tar.gz::https://github.com/ukui/peony-extensions/archive/refs/tags/v$pkgver.tar.gz
        peony-extensions-pro.patch)

sha256sums=('d3826ac89274181c7bb18526028c115ead9ba8be556636ab1dde413fa8a37313'
            'a6c5c51279822bc796ba47854c67dab1efa2ac3fe7ab8a2d3e898e457fa7e95d')

build() {
    cd $srcdir/$pkgname-$pkgver
    # Apply patch to make it buildable
    patch -i $srcdir/peony-extensions-pro.patch
    mkdir build
    cd build
    qmake ..
    make
}

package() {
    mkdir -p ${pkgdir}/usr/lib/peony-extensions/
    cp ${srcdir}/$pkgname-$pkgver/build/*/*.so ${pkgdir}/usr/lib/peony-extensions/
}

 