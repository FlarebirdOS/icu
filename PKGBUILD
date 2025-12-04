pkgname=icu
pkgver=78.1
pkgrel=2
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
source=(https://github.com/unicode-org/icu/releases/download/release-${pkgver}/icu4c-${pkgver}-sources.tgz)
sha256sums=(6217f58ca39b23127605cfc6c7e0d3475fe4b0d63157011383d716cb41617886)

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
