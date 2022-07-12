# Maintainer: Antonio Rojas <arojas@archlinux.org>

pkgname=sip
pkgver=6.6.2
pkgrel=2
epoch=1
arch=(x86_64)
pkgdesc='A tool that makes it easy to create Python bindings for C and C++ libraries'
url='https://www.riverbankcomputing.com/software/sip/intro'
license=('custom:"sip"')
depends=(python-toml python-packaging python-setuptools python-ply)
source=(https://pypi.python.org/packages/source/s/sip/$pkgname-$pkgver.tar.gz
        sip-fix-exceptions.patch::https://riverbankcomputing.com/hg/sip/raw-rev/1430b279a3c9
        https://github.com/kikislater/sip-patch/commit/ac9bac78229713048cde95835bc1bd56da5cc7eb.patch)
sha256sums=('0e3efac1c5dfd8e525ae57140927df26993e13f58b89d1577c314f4105bfd90d'
            'bdd73d3188004b1e430dc21595b8dde3de99ac29b7d523328347b9d1b01f669a'
            '72fa9fbb001b7c6a7232e75f68f5be6fd694d8877d9233e4485767ced5a10c7d')
options=(debug)

prepare() {
  patch -d $pkgname-$pkgver -p1 < sip-fix-exceptions.patch
# Fix  Qgis 3.26.0 build
  patch -d $pkgname-$pkgver -p1 < ac9bac78229713048cde95835bc1bd56da5cc7eb.patch
}

build() {
  cd $pkgname-$pkgver
  python setup.py build
}

package() {
  cd $pkgname-$pkgver
  python setup.py install --skip-build --root="$pkgdir" --optimize=1
}