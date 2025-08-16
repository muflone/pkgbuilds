# Maintainer: Muflone http://www.muflone.com/contacts/english/
# Contributor: Brian Bidulock <bidulock@openss7.org>
# Contributor: John D Jones III AKA jnbek <jnbek1972 -_AT_- g m a i l -_Dot_- com>

pkgname=perl-glib-object-introspection
_perl_namespace=Glib
_perl_module=Object-Introspection
pkgver=0.051
pkgrel=4
pkgdesc="Dynamically create Perl language bindings"
arch=('x86_64')
url="https://metacpan.org/release/${_perl_namespace}-${_perl_module}"
license=('LGPL-2.1-or-later')
makedepends=('gobject-introspection' 'perl-extutils-depends' 'perl-extutils-pkgconfig' 'perl-cairo-gobject')
depends=('glib-perl' 'gobject-introspection-runtime')
source=("https://cpan.metacpan.org/authors/id/X/XA/XAOC/${_perl_namespace}-${_perl_module}-${pkgver}.tar.gz"
         fix-tests.patch)
sha512sums=('93ebe81b586270cbeca4296bfdd1d337d931b6349ca16a8e50bfc631c89a77d93f4d8076289e91bdcec0fdb732a2900b2a6c5e78e571c0c0fd4c7f5239cc0de5'
            '9b4eacf4d7be40886f5f083c996743c9968cb9380846716217752dd6704f39b02ca8928daedc6aba7e5c4783e7e568282ec349dc1bbe51dc55f43ed88a607f42')
options=('!emptydirs')

prepare() {
  cd "${_perl_namespace}-${_perl_module}-${pkgver}"
  patch -p1 -i ../fix-tests.patch
}

build() {
  cd "${_perl_namespace}-${_perl_module}-${pkgver}"
  unset PERL5LIB PERL_MM_OPT PERL_MB_OPT PERL_LOCAL_LIB_ROOT
  export PERL_MM_USE_DEFAULT=1 PERL_AUTOINSTALL=--skipdeps
  perl Makefile.PL
  make
}

check() {
  cd "${_perl_namespace}-${_perl_module}-${pkgver}"
  unset PERL5LIB PERL_MM_OPT PERL_MB_OPT PERL_LOCAL_LIB_ROOT
  export PERL_MM_USE_DEFAULT=1
  make test
}

package() {
  cd "${_perl_namespace}-${_perl_module}-${pkgver}"
  unset PERL5LIB PERL_MM_OPT PERL_MB_OPT PERL_LOCAL_LIB_ROOT
  make pure_install INSTALLDIRS=vendor DESTDIR="${pkgdir}"
  # Delete unuseful files
  find "${pkgdir}" -name '.packlist' -delete
}
