pkgname=icu
pkgver=77.1
pkgrel=1
pkgdesc="International Components for Unicode library"
arch=('x86_64')
url="https://icu.unicode.org"
license=(
    'LicenseRef-Unicode-3.0'
    'BSD-2-Clause'
    'BSD-3-Clause'
    'NAIST-2003'
)
depends=(
    'bash'
    'gcc-libs'
    'glibc'
)
makedepends=('python')
source=(https://github.com/unicode-org/icu/releases/download/release-${pkgver//./-}/icu4c-${pkgver//./_}-src.tgz
    ICU-22132.patch)
sha256sums=(588e431f77327c39031ffbb8843c0e3bc122c211374485fa87dc5f3faff24061
    f534b472dd7a6961591466eef542e2c3ad698d3008c9b6af813c66cbc0b4dd8e)

prepare() {
    cd ${pkgname}/source

    # Required fix for thunderbird 115 to show Calendar and sidebar properly
    # https://bugzilla.mozilla.org/show_bug.cgi?id=1843007
    # https://unicode-org.atlassian.net/browse/ICU-22132
    patch -Np1 -i ${srcdir}/ICU-22132.patch
}

build() {
    cd ${pkgname}/source

    local configure_args=(
        ${configure_options}
    )

    ./configure "${configure_args[@]}"

    make
}

package() {
    cd ${pkgname}/source

    make DESTDIR=${pkgdir} install
}
