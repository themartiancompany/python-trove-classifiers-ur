# Maintainer: Felix Yan <felixonmars@archlinux.org>

pkgname=python-trove-classifiers
pkgver=2023.11.29
_commit=cee14ba8dad864274976ae7a131d7efb8ee96752
pkgrel=1
pkgdesc="Canonical source for classifiers on PyPI (pypi.org)"
url="https://github.com/pypa/trove-classifiers"
license=('Apache')
arch=('any')
depends=('python')
makedepends=('git' 'python-calver' 'python-setuptools')
checkdepends=('python-pytest')
source=("git+https://github.com/pypa/trove-classifiers.git#commit=$_commit")
sha512sums=('SKIP')

build() {
  cd trove-classifiers
  python setup.py build
}

check() {
  cd trove-classifiers
  pytest
  PYTHONPATH="$PWD"/build/lib python -m tests.lib
}

package() {
  cd trove-classifiers
  python setup.py install --root="$pkgdir" --optimize=1
}
