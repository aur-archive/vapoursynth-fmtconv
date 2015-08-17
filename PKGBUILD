# Maintainer:  Gustavo Alvarez <sl1pkn07@gmail.com>

_plug=fmtconv
pkgname=vapoursynth-${_plug}
pkgver=r8
pkgrel=3
pkgdesc="Plugin for Vapoursynth: ${_plug}"
arch=('i686' 'x86_64')
url="http://forum.doom9.org/showthread.php?t=166504"
license=('custom:WTFPL')
depends=('vapoursynth')
source=("http://ldesoras.free.fr/src/vs/${_plug}-${pkgver}.zip")
md5sums=('fa822a77d78620529b6febfe01ba7c26')

prepare() {
  rm -fr build
  cp -R src build
}

build() {
  cd build
  echo "all:
	  g++ -shared -march=native -mtune=native -O2 -pipe -fstack-protector --param=ssp-buffer-size=4 -msse2 -fPIC -o libfmtconv.so AvstpWrapper.cpp main.cpp fmtc/*.cpp fstb/*.cpp vsutl/*.cpp -I." > Makefile
  make
}

package(){
  cd build
  install -Dm755 "lib${_plug}.so" "${pkgdir}/usr/lib/vapoursynth/lib${_plug}.so"
  install -d "${pkgdir}/usr/share/doc/vapoursynth/plugins/${_plug}/"
  install -m644 ../doc/*.{png,html,css} "${pkgdir}/usr/share/doc/vapoursynth/plugins/${_plug}/"
  install -Dm644 ../doc/license.txt "${pkgdir}/usr/share/licenses/${pkgname}/license.txt"
}

