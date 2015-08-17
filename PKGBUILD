#Maintainer: max-k <max-k AT post DOT com>

pkgname=php-aws-sdk
_pkgname=sdk
pkgver=2.4.12
pkgrel=2
pkgdesc='Enables PHP developers to easily work with Amazon Web Services.'
arch=('any')
url="http://aws.amazon.com/sdkforphp/"
license=('APACHE')
depends=('php>=5.3.3' 'guzzle>=3.0.3' 'pear-channel-aws')
makedepends=('php-pear>=1.4.0')
options=('!strip')
noextract=(${_pkgname}-${pkgver}.tgz)
source=(http://pear.amazonwebservices.com/get/${_pkgname}-${pkgver}.tgz http://pear.amazonwebservices.com/channel.xml)
md5sums=('f425e262ff59d5686de8caa3878376bb'
         '4c6820d314fd005212fcd46192302de7')

package() {
  cd ${srcdir}
  local _PEARDIR="${pkgdir}/usr/share/pear"
  local _PEAROPTS="-D php_dir=${_PEARDIR} -D doc_dir=${_PEARDIR}/doc"
  local _PEAROPTS="${_PEAROPTS} -D test_dir=${_PEARDIR}/test"
  local _PEAROPTS="${_PEAROPTS} -D data_dir=${_PEARDIR}/data"
  pear ${_PEAROPTS} channel-add channel.xml
  pear ${_PEAROPTS} install -O -n ${_pkgname}-${pkgver}.tgz
  rm -r ${_PEARDIR}/{.channels,.depdb*,.filemap,.lock}
  rm -r ${_PEARDIR}/.registry/{.channel.__uri,.channel.*.php.net}
}

