# Maintainer  : Minbari <dana_blonda2004@yahoo.com>

pkgname=lib32-ogre
_basename=ogre
pkgver=1.9.0RC1
pkgrel=1
pkgdesc="A scene-oriented. flexible 3D engine written in C++ (32 bit)"
arch=('x86_64')
url="http://www.ogre3d.org"
depends=('lib32-libxaw' 'lib32-zziplib' 'lib32-boost-libs' 'lib32-freeimage' 'lib32-freetype2' 
	 'lib32-libxrandr' 'lib32-ois' 'lib32-nvidia-cg-toolkit' 'lib32-mesa') 
makedepends=('boost' 'cmake' 'graphviz' 'ttf-dejavu')
optdepends=('cppunit: unit testing'
	    'intel-tbb: better threading support'
	    'poco: portability'
	    'boost: for developing with ogre')
license=('custom:MIT')
groups=('lib32')
source=("http://downloads.sourceforge.net/${_basename}/${_basename}_src_v${pkgver//./-}.tar.bz2")


build() {
	cd ${srcdir}

	
	if [ ! -d build ]; then
		mkdir build
	fi
	
	cd build
	
	cmake ../${_basename}_src_v${pkgver//./-} \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DOGRE_BUILD_SAMPLES=FALSE \
		-DOGRE_BUILD_TOOLS=OFF \
		-DOGRE_INSTALL_TOOLS=OFF \
		-DOGRE_INSTALL_DOCS=FALSE \
		-DCMAKE_BUILD_TYPE=Release \
		-DOGRE_LIB_DIRECTORY=lib32 \
		-DCMAKE_C_FLAGS="-m32" \
		-DCMAKE_CXX_FLAGS="-m32" 
		
	make
}

package() 
{
	cd ${srcdir}/build
	
	make DESTDIR=${pkgdir} install
	
	# Remove examples and platform independent files
	rm -rf ${pkgdir}/opt
	rm -rf ${pkgdir}/usr/share
	rm -rf ${pkgdir}/usr/include
}

md5sums=('18d7e35419ee8520cf177cbcaeb034a7')
