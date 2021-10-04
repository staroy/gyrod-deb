cmake_minimum_required(VERSION 3.2)

project(gyrod)

install(FILES
    ${CMAKE_INSTALL_PREFIX}/bin/gyrod
    ${CMAKE_INSTALL_PREFIX}/bin/gyro-wallet-cli
    DESTINATION /usr/bin
  	PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
)

install(FILES
    ${CMAKE_INSTALL_PREFIX}/lib/libzyre.so
    ${CMAKE_INSTALL_PREFIX}/lib/libzyre.so.2
    ${CMAKE_INSTALL_PREFIX}/lib/libzyre.so.2.0.1
    DESTINATION /usr/lib
  	PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
)

install(FILES
    postinst/gyrod
    DESTINATION /etc/init.d
  	PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
)

install(FILES
    gyro.conf
    DESTINATION /var/lib/gyro
)

set(DEB_PACKAGE_NAME ${CMAKE_PROJECT_NAME})
set(DEB_PACKAGE_VERSION "0.1.0")
set(DEB_PACKAGE_COMMIT "ubuntu-18.04")
set(DEB_PACKAGE_SECTION "internet")
set(DEB_PACKAGE_DEPENDS "libzmq5;libczmq4;libunbound2;libsodium23;libunwind8;liblzma5;libreadline7;libldns2;libexpat1;libpgm-5.2-0;libhidapi-hidraw0;libhidapi-libusb0;libprotobuf-c1")
set(DEB_PACKAGE_DESRCIPTION "gyrod")
set(DEB_PACKAGE_MAINTAINER "Staroy <staroy@pm.me>")
set(CPACK_DEBIAN_PACKAGE_CONTROL_EXTRA "${CMAKE_CURRENT_SOURCE_DIR}/postinst/postinst")

include(deb_packaging.cmake)
