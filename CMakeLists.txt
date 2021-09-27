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
    gyro.conf
    DESTINATION /var/lib/gyro
)

install(FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/postinst/gyrod
    DESTINATION /etc/init.d
  	PERMISSIONS OWNER_EXECUTE OWNER_WRITE OWNER_READ GROUP_READ GROUP_EXECUTE WORLD_READ WORLD_EXECUTE
)

set(DEB_PACKAGE_NAME ${CMAKE_PROJECT_NAME})
set(DEB_PACKAGE_VERSION "0.1.0")
set(DEB_PACKAGE_COMMIT "release")
set(DEB_PACKAGE_SECTION "internet")
set(DEB_PACKAGE_DEPENDS "libc6, libsodium23, libssl1.1, libhidapi-libusb0, libstdc++6, libreadline8, libunbound8, libgcrypt20, libgcc-s1, libczmq4")
set(DEB_PACKAGE_DESRCIPTION "gyrod")
set(DEB_PACKAGE_MAINTAINER "Staroy <staroy@pm.me>")
set(CPACK_DEBIAN_PACKAGE_CONTROL_EXTRA "${CMAKE_CURRENT_SOURCE_DIR}/postinst/postinst")

include(deb_packaging.cmake)
