# Maintainer: éclairevoyant
# Contributor: Hyacinthe Cartiaux <hyacinthe.cartiaux at free dot fr>
# Contributor: zhuqin <zhuqin83 at gmail dot com>

_pkgname=lensfun
pkgname="$_pkgname"2
pkgver=0.3.99.0
pkgrel=1
pkgdesc='Database of photographic lenses and associated library'
arch=('i686' 'x86_64')
url="https://lensfun.github.io/"
license=('LGPL3')
depends=('glibc' 'glib2')
makedepends=('cmake' 'git'  'libpng' 'python-setuptools')
optdepends=('python: for lensfun-update-data and lensfun-add-adapter')
provides=("$_pkgname=0.3.2" "$_pkgname-git")
source=("git+https://github.com/lensfun/$_pkgname.git")
b2sums=('SKIP')

pkgver() {
	grep Version lensfun/libs/lensfun/lensfun.pc | awk '{ printf $2 }'
}

build() {
	cd $_pkgname
	cmake -DCMAKE_INSTALL_PREFIX=/usr \
		-DCMAKE_INSTALL_LIBDIR=lib \
		-DCMAKE_BUILD_TYPE=Release \
		.
	make
}

package() {
	cd $_pkgname
	make DESTDIR="$pkgdir/" install
	cd $pkgdir
	mv usr/bin/g-lensfun{,2}-update-data
	mv usr/bin/lensfun{,2}-add-adapter
	mv usr/bin/lensfun{,2}-update-data
	mv usr/include/lensfun{,2}
	mv usr/lib/liblensfun{,2}.so
	mv usr/lib/pkgconfig/lensfun{,2}.pc
	mv usr/lib/python3.13/site-packages/lensfun{,2}
	sed -e "s/lensfun$/&2/" -i usr/lib/pkgconfig/lensfun2.pc
}
