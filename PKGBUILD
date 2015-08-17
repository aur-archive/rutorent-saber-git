# Contributor: Guten <ywzhaifei@gmail.com>

pkgname=rutorent-saber-git
pkgver=20120221
pkgrel=1
pkgdesc="a rutorrent plugin to auto download files into home laptop."
arch=("i686" "x86_64")
url="https://github.com/GutenYe/saber"
license=("MIT-LICENSE")
groups=()
depends=("rutorrent")
makedepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=()
md5sums=()

_gitroot="git://github.com/GutenYe/saber.git"
_gitname="saber"

build() {
  cd ${srcdir}
  msg "Connecting to GIT server...."

  if [ -d ${_gitname}/.git ] ; then
    cd ${_gitname}

    # Change remote url to anongit
    if [ -z $( git branch -v | grep anongit ) ] ; then
        git remote set-url origin ${_gitroot}
    fi
    
    git pull origin
    msg "The local files are updated."
  else
    git clone ${_gitroot} ${_gitname}
  fi
  msg "GIT checkout done or server timeout"
}

package() {
  p_plugins="${pkgdir}/srv/http/rutorrent/plugins"
  cd ${srcdir}/${_gitname}/rutorrent

  mkdir -p $p_plugins/saber
  cp -r * $p_plugins/saber
}

# vim:set ts=2 sw=2 et:
