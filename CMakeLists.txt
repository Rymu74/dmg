cmake_minimum_required(VERSION 2.6)

project (DMG)

# We want win32 executables to build staticly by default, since it's more difficult to keep the shared libraries straight on Windows
IF(WIN32)
	SET(BUILD_STATIC ON CACHE BOOL "Force compilation with static libraries")
ELSE(WIN32)
	SET(BUILD_STATIC OFF CACHE BOOL "Force compilation with static libraries")
ENDIF(WIN32)

IF(BUILD_STATIC)
	SET(CMAKE_FIND_LIBRARY_SUFFIXES ".a")
ENDIF(BUILD_STATIC)

include_directories (${PROJECT_SOURCE_DIR}/includes)

add_subdirectory (common)
add_subdirectory (dmg)
add_subdirectory (hfs)

install(FILES README.markdown DESTINATION . RENAME README.txt)
install(FILES LICENSE DESTINATION . RENAME LICENSE.txt)

IF(WIN32 OR APPLE)
	SET(CPACK_GENERATOR "ZIP")
ELSE(WIN32 OR APPLE)
	SET(CPACK_GENERATOR "TBZ2")
ENDIF(WIN32 OR APPLE)

SET(CPACK_PACKAGE_DESCRIPTION_SUMMARY "dmg")
SET(CPACK_PACKAGE_VENDOR "iPhone Dev Team")
SET(CPACK_PACKAGE_VERSION_MAJOR "0")
SET(CPACK_PACKAGE_VERSION_MINOR "5")
SET(CPACK_PACKAGE_VERSION_PATCH "8")
SET(CPACK_PACKAGE_EXECUTABLES "dmg" "Apple DMG utility")
SET(CPACK_PACKAGE_EXECUTABLES "hfsplus" "Apple HFS+ utility")
INCLUDE(CPack)

