pkgname=nss-mdns
pkgver=0.15.1
pkgrel=3
pkgdesc='glibc plugin providing host name resolution via mDNS'
arch=('x86_64')
url='http://0pointer.de/lennart/projects/nss-mdns'
license=('LGPL2.1')
depends=('glibc' 'avahi')
makedepends=()
source=("https://github.com/avahi/${pkgname}/releases/download/v${pkgver}/${pkgname}-${pkgver}.tar.gz")
sha512sums=('11a82ae9f209326b4501c7e6d33c9932b370c4dcacb64d6783140e25688ad6391bbd113e51ee470fd8be12669124eac331593cfd02a040383b4f964ed6ec6154')
install=nss-mdns.install

build() {
    cd "$pkgname-$pkgver"
    ./configure
    make
}

package() {
    cd "$pkgname-$pkgver"
    make DESTDIR="$pkgdir/" install
    install -Dm644 "LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
    install -Dm644 "README.md" "$pkgdir/usr/share/doc/$pkgname/README.md"
}
