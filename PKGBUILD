pkgname=nss-mdns
pkgver=0.15.1
pkgrel=2
pkgdesc='nss-mdns is a plugin for the GNU Name Service Switch (NSS) functionality of the GNU C Library (glibc) providing host name resolution via Multicast DNS (aka Zeroconf, aka Apple Rendezvous, aka Apple Bonjour), effectively allowing name resolution by common Unix/Linux programs in the ad-hoc mDNS domain .local.'
arch=('x86_64')
url='https://github.com/lathiat/nss-mdns'
license=('GPLv2')
depends=()
makedepends=()
source=("https://github.com/lathiat/nss-mdns/releases/download/v0.14.1/nss-mdns-${pkgver}.tar.gz")
md5sums=('78b96e7360a8af106c609c9c5fc17274')

src_name="nss-mdns-${pkgver}"

build() {
    cd "${src_name}"

    ./configure
    make -j$(nproc)
}

package() {
    cd "${src_name}"
    make DESTDIR="$pkgdir/" install 
}
