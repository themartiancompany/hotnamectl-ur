# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_hostnamectl=false
_hostname="false"
_offline="false"
_git="false"
pkgname=hotnamectl
pkgver="0.0.0.0.0.0.0.1.1.1.1.1.1"
_commit='8c4b6472d04255c2df3d872d32781d6be07150d8'
pkgrel=1
_pkgdesc=(
  "Cross-platform hostnamectl"
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
license=(
  AGPL3
)
depends=(
  bash
)
[[ "${_hostnamectl}" == "true" ]] && \
  depends+=(
    "hostnamectl"
  )
_os="$( \
  uname \
    -o)"
optdepends=(
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  optdepends+=(
  )
provides=(
)
conflicts=(
)
[[ "${_hostnamectl}" == "false" ]] && \
  provides+=(
    "hostnamectl"
  )
[[ "${_hostname}" == "false" ]] && \
  provides+=(
    "hostname"
  )
  conflicts+=(
    'inetutils'
  )
makedepends=()
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
_url="${url}"
[[ "${_offline}" == "true" ]] && \
  url="file://${HOME}/${_pkgname}"
[[ "${_git}" == true ]] && \
  makedepends+=(
    "git"
  ) && \
  source+=(
    "${pkgname}-${pkgver}::git+${_url}#tag=${pkgver}"
  ) && \
  sha256sums+=(
    SKIP
  )
[[ "${_git}" == false ]] && \
  source+=(
    "${pkgname}-${pkgver}.tar.gz::${_url}/archive/refs/tags/${pkgver}.tar.gz"
  ) && \
  sha256sums+=(
    'd3c8b0f4c649806c4b138d9938badb6baec7cf5ddda3f128514ddab4e1334dd6'
  )

check() {
  cd \
    "${pkgname}-${pkgver}"
  make \
    -k \
    check
}

package() {
  cd \
    "${pkgname}-${pkgver}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
  ln \
    -s \
    "hotnamectl" \
    "${pkgdir}/usr/bin/hotname"
  if [[ "${_hostnamectl}" == "false" ]]; then
    ln \
      -s \
      "hotnamectl" \
      "${pkgdir}/usr/bin/hostnamectl"
  fi
  if [[ "${_hostname}" == "false" ]]; then
    ln \
      -s \
      "hotnamectl" \
      "${pkgdir}/usr/bin/hostname"
  fi
}

# vim: ft=sh syn=sh et
