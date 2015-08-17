# Maintainer: Evan Teitelman <teitelmanevan@gmail.com>

pkgname=wpscan-git
_pkgname=wpscan
pkgver=184
pkgrel=3
pkgdesc='A vulnerability scanner which checks the security of WordPress installations using a black box approach'
optdepends=('typhoeus' 'rspec' 'ruby-progressbar' 'webmock' 'terminal-table'
            'simplecov')
arch=('i686' 'x86_64')
url="http://code.google.com/p/wpscan/"
license=('GPL3')
conflicts=('wpscan')
provides=('wpscan')
depends=('ruby')
makedepends=('git')
source=("git+https://github.com/wpscanteam/wpscan")
md5sums=('SKIP')
options=('!strip')

package() {
  cd "$srcdir/$_pkgname"

  # Base directories.
  install -dm755 "$pkgdir/usr/bin"
  install -dm755 "$pkgdir/usr/share/wpscan"

  cp --no-preserve=ownership -r * "$pkgdir/usr/share/wpscan"

  # Joint script.
  cat > "$pkgdir/usr/bin/wpscan" <<\EOF
#!/bin/sh
localdir=$HOME/.wpscan
mkdir -p "$localdir"
cp -Rf /usr/share/wpscan/* "$localdir"
cd "$localdir"
ruby ./wpscan.rb "$@"
EOF

  chmod +x "$pkgdir/usr/bin/wpscan"
}
