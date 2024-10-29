# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Felix Yan <felixonmars@archlinux.org>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=trove-classifiers
pkgname="${_py}-${_pkg}"
pkgver=2024.1.8
_commit=e5c379567a6a5d67c5a2505d6429faca5b69fc45
pkgrel=1
pkgdesc="Canonical source for classifiers on PyPI (pypi.org)"
_http="https://github.com"
_ns="pypa"
url="${_http}/${_ns}/${_pkg}"
license=(
  'Apache'
)
arch=(
  'any'
)
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  'git'
  "${_py}-calver"
  "${_py}-setuptools"
)
checkdepends=(
  "${_py}-pytest"
)
source=(
  "git+${url}.git#commit=${_commit}"
)
sha512sums=(
  'SKIP'
)

build() {
  cd \
    "${_pkg}"
  "${_py}" \
    setup.py \
    build
}

check() {
  cd \
    "${_pkg}"
  pytest
  PYTHONPATH="$PWD"/build/lib \
  "${_py}" \
    -m \
      tests.lib
}

package() {
  cd \
    "${_pkg}"
  "${_py}" \
    setup.py \
      install \
      --root="${pkgdir}" \
      --optimize=1
}

