# Based on snapgene-viewer package by Antony Lee <anntzer dot lee at gmail dot com>
# Maintainer: Bitals <me at bitals dot xyz>
# Contributor: Matthijs Tadema <M dot J dot Tadema at gmail dot com>
# Contributor: Lorenzo Gaifas <brisvag at gmail dot com>
pkgname=snapgene
pkgver=7.0.3
_pkgver_major=$(cut -d '.' -f 1 <<<"$pkgver")
_pkgver_major_middle=$(cut -d '.' -f 1-2 <<<"$pkgver")
pkgrel=1
pkgdesc='Software for plasmid mapping, primer design, and restriction site analysis'
arch=('x86_64')
url='http://www.snapgene.com/products/snapgene/'
license=('custom')
# A valid licence is required to use the full version of snapgene
source=("https://cdn.snapgene.com/downloads/SnapGene/"$_pkgver_major".x/"$_pkgver_major_middle"/"$pkgver"/"$pkgname"_"$pkgver"_linux.rpm")
sha512sums=('a8d3bf97ef93a97b92e40cfa1b00e0ff4814536f6cda51147ceab009dc794b7fbf1b9f65667ced8d111774d8381e49620a659aea082de893422e6881bf6d19e7')

package() {
    cd "$pkgdir"
    cp -r "$srcdir/opt" "$pkgdir"
    cp -r "$srcdir/usr" "$pkgdir"
    mkdir "$pkgdir/usr/bin"
    cat <<'EOF' >"$pkgdir/usr/bin/snapgene"
#!/bin/sh
# Snapgene is not localized and genbank exports are invalid in other
# locales, so we just set LANG=C.
LANG=C /opt/gslbiotech/snapgene/snapgene.sh
EOF

    sed -i 's`${INSTALLED_DIR}/snapgene "$@"`QT_QPA_PLATFORM="xcb" ${INSTALLED_DIR}/snapgene "$@"`' "$pkgdir/opt/gslbiotech/snapgene/snapgene.sh"
    
    chmod a+x "$pkgdir/usr/bin/snapgene"

    mkdir -p "$pkgdir/usr/share/licenses/$pkgname"
    ln -s "/opt/gslbiotech/snapgene/resources/licenseAgreement.html" "$pkgdir/usr/share/licenses/$pkgname/LICENSE.html"
}
