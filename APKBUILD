# Contributor: Sasha Gerrand <alpine-pkgs@sgerrand.com>
# Maintainer: Sasha Gerrand <alpine-pkgs@sgerrand.com>
pkgname=leveldb
pkgver=1.18
pkgrel=0
pkgdesc="LevelDB is a fast key-value storage library that provides an ordered mapping from string keys to string values."
url="http://leveldb.org"
arch="all"
license="Commercial"
depends=""
depends_dev=""
makedepends="$depends_dev build-base"
install=""
subpackages="$pkgname-dev $pkgname-doc"
source="leveldb-$pkgver.tar.gz::https://github.com/google/leveldb/archive/v$pkgver.tar.gz"

_builddir="$srcdir"/leveldb-$pkgver
prepare() {
	local i
	cd "$_builddir"
	for i in $source; do
		case $i in
		*.patch) msg $i; patch -p1 -i "$srcdir"/$i || return 1;;
		esac
	done
}

build() {
	cd "$_builddir"
	make || return 1
}

package() {
	local i
	cd "$_builddir"
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
	mkdir -p "$pkgdir/usr/include/$pkgname" || return 1
	install -Dm644 include/$pkgname/*.h "$pkgdir/usr/include/$pkgname/" || return 1
	for i in db port table util; do
		mkdir -p "$pkgdir/usr/include/$pkgname/$i" || return 1
		install -Dm644 $i/*.h "$pkgdir/usr/include/$pkgname/$i/" || return 1
	done
	mkdir -p "$pkgdir/usr/lib/" || return 1
	install -Dm755 libleveldb.a "$pkgdir/usr/lib/" || return 1
	install -Dm755 libleveldb.so.1 "$pkgdir/usr/lib/" || return 1
	install -Dm755 libleveldb.so.1.18 "$pkgdir/usr/lib/" || return 1
}

doc() {
	local i
	mkdir -p "$subpkgdir/usr/share/doc/$pkgname"
	for i in AUTHORS CONTRIBUTING.md NEWS README.md TODO; do
		install -Dm644 "$_builddir/$i" "$subpkgdir/usr/share/doc/$pkgname/"
	done
	install -Dm644 "$_builddir/doc/doc.css" "$subpkgdir/usr/share/doc/$pkgname/"
	install -Dm644 "$_builddir/doc/benchmark.html" "$subpkgdir/usr/share/doc/$pkgname/"
	install -Dm644 "$_builddir/doc/impl.html" "$subpkgdir/usr/share/doc/$pkgname/"
	install -Dm644 "$_builddir/doc/index.html" "$subpkgdir/usr/share/doc/$pkgname/"
	install -Dm644 "$_builddir/doc/log_format.txt" "$subpkgdir/usr/share/doc/$pkgname/"
	install -Dm644 "$_builddir/doc/table_format.txt" "$subpkgdir/usr/share/doc/$pkgname/"
}

md5sums="73770de34a2a5ab34498d2e05b2b7fa0  leveldb-1.18.tar.gz"
sha256sums="4aa1a7479bc567b95a59ac6fb79eba49f61884d6fd400f20b7af147d54c5cee5  leveldb-1.18.tar.gz"
sha512sums="3d9c55a7bf8692914784ec33c273704ce9978496b071c7b661708f049d0d4ccd51a44441f50c3e536725caeb9896575192f52708a4bb1c0222cecdeec89919a3  leveldb-1.18.tar.gz"
