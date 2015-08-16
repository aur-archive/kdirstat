# Maintainer: Andreas B. Wagner <AndreasBWagner@pointfree.net>
# Contributor: Natan Vivo <nvivo.misc at gmail dot com>
# Contributor: Lone_Wolf <lonewolf@xs4all.nl>
# AUR Category: kde
pkgname=kdirstat
pkgver=2.5.3
pkgrel=7
pkgdesc="KDirStat is a graphical disk usage utility, very much like the Unix "du" command."
arch=('i686' 'x86_64')
url="http://kdirstat.sourceforge.net/"
license="GPL2"
depends=('kdelibs3' 'optipng')
source=(http://kdirstat.sourceforge.net/download/$pkgname-$pkgver.tar.bz2
kdirstat-2.5.3-gcc43.patch
kdirstat.desktop)
md5sums=('58dd06602bed70936ece233bd8c32f2a'
'2ebeafd9b055af91be90149f1623574b'
'a89c24c4834a4dba7450749118beedae')

build() {
	cd $srcdir/$pkgname-$pkgver
	rm -f config.cache
	patch -p1 -i $startdir/kdirstat-2.5.3-gcc43.patch
	LDFLAGS="-L/opt/qt/lib -L/opt/kde/lib -lqt-mt" ./configure --prefix=/opt/kde --with-qt-dir=/opt/qt --without-arts 
	make
}
package() {
	cd $srcdir/$pkgname-$pkgver
	make DESTDIR=$pkgdir install
	mkdir -p $pkgdir/usr/share/applications
	cp -f $srcdir/kdirstat.desktop $pkgdir/usr/share/applications/kdirstat.desktop
}

