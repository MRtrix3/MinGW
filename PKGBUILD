# Maintainer: J-Donald Tournier <jdtournier@gmail.com>

_realname=mrtrix3
pkgbase=mingw-w64-${_realname}
pkgname="${MINGW_PACKAGE_PREFIX}-${_realname}"
pkgver=0
pkgrel=1
arch=('x86_64')
pkgdesc="Tools for the analysis of diffusion MRI data (mingw-w64)"
depends=("python"
         "${MINGW_PACKAGE_PREFIX}-qt5-svg"
         "${MINGW_PACKAGE_PREFIX}-fftw"
         "${MINGW_PACKAGE_PREFIX}-libtiff"
         "${MINGW_PACKAGE_PREFIX}-zlib")
makedepends=("git"
             "python"
             "pkg-config"
             "${MINGW_PACKAGE_PREFIX}-gcc"
             "${MINGW_PACKAGE_PREFIX}-qt5-svg"
             "${MINGW_PACKAGE_PREFIX}-fftw"
             "${MINGW_PACKAGE_PREFIX}-libtiff"
             "${MINGW_PACKAGE_PREFIX}-zlib")


license=("MPL")
url="http://www.mrtrix.org/"
source=(
  "${_realname}::git+https://github.com/mrtrix3/${_realname}.git#tag=3.0.8"
  "https://gitlab.com/libeigen/eigen/-/archive/3.3.9/eigen-3.3.9.tar.gz"
)
sha512sums=(
  'SKIP' 
  '16244cc89f2e1879543232b965cbf653b3ccf10e967c8c437a41e27d8320392bdf584d8c24b8a97406ab7d1481d5154da74e0702ec1334ae6a46de83f4573a46'
)


pkgver() {
  cd "${_realname}"
  git describe --abbrev=8 | tr '-' '_'
}

build() {
  cd "${_realname}"
  export EIGEN_CFLAGS="-isystem $(pwd)/../eigen-3.3.9" 
  export LINKFLAGS=-lopengl32 
  export QMAKE=qmake-qt5 
  ./configure
  ./build
}

package() {

  cd "${_realname}"

  rm -rf bin/__pycache__ 
  install -d "${pkgdir}${MINGW_PREFIX}/bin/"
  install -D bin/* "${pkgdir}${MINGW_PREFIX}/bin/"

  for fname in $(find lib/ share/ -type f); do
    install -Dm644 "${fname}" "${pkgdir}${MINGW_PREFIX}/${fname}"
  done
  mkdir -p "${pkgdir}${MINGW_PREFIX}/share/licenses/${_realname}-${pkgver}"
  cp LICENCE.txt "${pkgdir}${MINGW_PREFIX}/share/licenses/${_realname}-${pkgver}"
}

