# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>

pkgname=pulseaudio-policy-enforcement
pkgver=14.2
pkgrel=1
pkgdesc="Pulseaudio module for enforcing policy decisions in the audio domain"
arch=('x86_64' 'aarch64')
url="https://github.com/sailfishos/pulseaudio-policy-enforcement/"
license=('LGPLv2+')
depends=('pulseaudio-hybris')
makedepends=('automake' 'autoconf' 'pulsecore-headers' 'pulseaudio-modules-nemo' 'libatomic_ops')
source=("pulseaudio-policy-enforcement::git+https://github.com/sailfishos/pulseaudio-policy-enforcement"
	"0001-fix_build.patch")
sha256sums=('SKIP'
	    'e8016cde30ff5d7a0f4e6cacf791fe7ff8bf15f7b94b0fd557b79a89fe6ffcc1')

prepare() {
    cd pulseaudio-policy-enforcement
    echo "14.2" > .tarball-version
    patch -p1 --input="${srcdir}/0001-fix_build.patch"
}

build() {
  cd pulseaudio-policy-enforcement
  ./bootstrap.sh --prefix=/usr \
    --sysconfdir=/etc \
    --sbindir=/usr/bin \
    --with-module-dir=/usr/lib/pulse-14.2/modules/ \
    --disable-static
    make
}

package() {
  cd pulseaudio-policy-enforcement
  make DESTDIR="${pkgdir}" install
}
