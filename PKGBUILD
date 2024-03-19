# Based on snapgene-viewer package by Antony Lee <anntzer dot lee at gmail dot com>
# Maintainer: Bitals <me at bitals dot xyz>
# Contributor: Matthijs Tadema <M dot J dot Tadema at gmail dot com>
# Contributor: Lorenzo Gaifas <brisvag at gmail dot com>
pkgname=snapgene
pkgver=7.2.0
_pkgver_major=$(cut -d '.' -f 1 <<<"$pkgver")
_pkgver_major_middle=$(cut -d '.' -f 1-2 <<<"$pkgver")
pkgrel=1
pkgdesc='Software for plasmid mapping, primer design, and restriction site analysis'
arch=('x86_64')
url='https://www.snapgene.com/about'
license=('custom')
depends=('qt6-base'
         'qt6-webchannel'
         'qt6-5compat'
         'qt6-declarative'
         'qt6-positioning'
         'qt6-svg'
         'qt6-webengine'
         'libsm'
         'fontconfig'
         'nspr'
         'xz'
         'expat'
         'glibc'
         'gcc-libs'
         'libc++'
         'libc++abi'
         'dbus'
         'krb5'
         'libxcb'
         'libxkbcommon-x11'
         'xcb-util-image'
         'xcb-util-wm'
         'libx11'
         'libxkbfile'
         'xcb-util-keysyms'
         'xcb-util-renderutil'
         'nss'
         'hicolor-icon-theme'
         'libice'
         'libglvnd'
         'libxext'
         'openssl-1.1'
         'zlib'
)
# A valid licence is required to use the full version of snapgene
source=("https://cdn.snapgene.com/downloads/SnapGene/"$_pkgver_major".x/"$_pkgver_major_middle"/"$pkgver"/"$pkgname"_"$pkgver"_linux.rpm" "snapgene")
sha512sums=('aa6eeb63fe362db47057ba1213b16dbd30bed341f60bcc046bcbd1546ac2a760579a5e7c3c2b7701ab7c928768856db0ca7cd0dc6d53e43c35c05a7f9ddb9b59' 'b6e85e1a3e1ed9d07159b58abf6fecfb76bfd19752b67fbf156baaab696df83aa8b0fcfc49c93263dd56ea2f47926ddc4dac0b4b011f53112426e8545d1197be')

package() {
    cd "$pkgdir"
    cp -r "$srcdir/opt" "$pkgdir"
    cp -r "$srcdir/usr" "$pkgdir"
    mkdir "$pkgdir/usr/bin"
    cp "$srcdir/snapgene" "$pkgdir/usr/bin/"

    sed -i 's`${INSTALLED_DIR}/snapgene "$@"`QT_QPA_PLATFORM="xcb" ${INSTALLED_DIR}/snapgene "$@"`' "$pkgdir/opt/gslbiotech/snapgene/snapgene.sh"
    
    chmod a+x "$pkgdir/usr/bin/snapgene"

    mkdir -p "$pkgdir/usr/share/licenses/$pkgname"
    ln -s "/opt/gslbiotech/snapgene/resources/licenseAgreement.html" "$pkgdir/usr/share/licenses/$pkgname/LICENSE.html"
}
