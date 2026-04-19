# Maintainer: Muflone http://www.muflone.com/contacts/english/
# Contributor: Piotr Rogoża <rogoza dot piotr at gmail dot com>

pkgbase=gimp-help
pkgver=3.0.2
pkgrel=1
arch=('any')
url='https://docs.gimp.org/'
license=('GFDL-1.2-or-later')
makedepends=('python' 'docbook-xsl')
options=(!strip !zipman)
source=("https://download.gimp.org/gimp/help/${pkgbase}-${pkgver}.tar.bz2")
sha256sums=('1dbfe008e5f42dacc15d587d8f2c837833e7a0247d52335320046a60d4499a24')

_languages=(
  'bg     "Bulgarian"'
  'ca     "Catalan"'
  'cs     "Czech"'
  'da     "Danish"'
  'de     "German"'
  'el     "Greek"'
  'en     "English"'
  'en_GB  "English (United Kingdom)"'
  'eo     "Esperanto"'
  'es     "Spanish"'
  'fa     "Faroese (Persian)"'
  'fi     "Finnish"'
  'fr     "French"'
  'hr     "Croatian"'
  'hu     "Hungarian"'
  'it     "Italian"'
  'ja     "Japanese"'
  'ko     "Korean"'
  'lt     "Lithuanian"'
  'nl     "Dutch"'
  'nn     "Norwegian"'
  'pl     "Polish"'
  'pt     "Portuguese"'
  'pt_BR  "Brazilian Portuguese"'
  'ro     "Romanian"'
  'ru     "Russian"'
  'sk     "Slovak"'
  'sl     "Slovenian"'
  'sv     "Swedish"'
  'tr     "Turkish"'
  'uk     "Ukrainian"'
  'zh_CN  "Chinese (simplified)"'
)

_package() {
  _locale="$1"
  _language="$2"
  pkgdesc="${_language} help files for Gimp"
  install -dm755 "${pkgdir}/usr/share/gimp/3.0/help/${_locale}"
  cp -rL "${srcdir}/${pkgbase}-${pkgver}/html/${_locale}" \
    "${pkgdir}/usr/share/gimp/3.0/help"
}

build(){
  cd "${pkgbase}-${pkgver}"
  ./configure --prefix=/usr --without-gimp
  make
}

for _lang in "${_languages[@]}"
do
  _locale=${_lang%% *}
  _pkgname=${pkgbase}-${_locale,,}

  pkgname+=(${_pkgname})
  eval "package_${_pkgname}() {
    _package ${_lang}
  }"
done
