# Script generated with Bloom
pkgdesc="ROS - Log4cpp maintained by Orocos developers This version of log4cpp deviates from the official release by adding custom category factories. Orocos requires this for setting up real-time logging."
url='http://log4cpp.sourceforge.net/'

pkgname='ros-kinetic-log4cpp'
pkgver='2.9.0_1'
pkgrel=1
arch=('any')
license=('LGPL v2.1 or later'
)

makedepends=('cmake'
)

depends=('ros-kinetic-catkin'
)

conflicts=()
replaces=()

_dir=log4cpp
source=()
md5sums=()

prepare() {
    cp -R $startdir/log4cpp $srcdir/log4cpp
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

