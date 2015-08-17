# Contributor: Andrew Gallant <andrew@pytyle.com>
# Maintainer: Andrew Gallant
pkgname=pytyle3-git
pkgver=20120226
pkgrel=1
pkgdesc="An automatic tiler that is compatible with Openbox Multihead"
arch=('any')
url="http://burntsushi.net/X11/pytyle"
license=('GPL')
groups=()
makedepends=('git')
depends=('python2>=2.7' 'xpybutil-git')
source=()
noextract=()
install=pytyle3.install
md5sums=()

_gitroot="git://github.com/BurntSushi/pytyle3.git"
_gitname=pytyle3
_gitbranch="master"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ]; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  if [ -d "$srcdir/$_gitname-build" ]; then
    rm -r "$srcdir/$_gitname-build"
  fi
  cp -r "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  msg "Clone finished, checking out branch $_gitbranch"
  git checkout $_gitbranch

  python2 ./setup.py install --root=$pkgdir || return 1
}
