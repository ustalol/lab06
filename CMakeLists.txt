cmake_minimum_required(VERSION 3.10...3.27)
project(MyProject VERSION 1.0.0 LANGUAGES CXX)

set(CPACK_PACKAGE_NAME "solver")
set(CPACK_PACKAGE_VENDOR "YourCompany")
set(CPACK_PACKAGE_CONTACT "contact@yourcompany.com")
set(CPACK_PACKAGE_VERSION ${PROJECT_VERSION})
set(CPACK_RESOURCE_FILE_LICENSE "${CMAKE_CURRENT_SOURCE_DIR}/License.rtf")
set(CPACK_VERBATIM_VARIABLES YES)

if(UNIX AND NOT APPLE)
    set(CPACK_GENERATOR "DEB;RPM")
    set(CPACK_DEBIAN_PACKAGE_MAINTAINER "Maintainer <maintainer@example.com>")
    set(CPACK_DEBIAN_PACKAGE_DEPENDS "libfmt-dev")
    set(CPACK_RPM_PACKAGE_REQUIRES "libfmt-devel")
endif()

if(WIN32)
    set(CPACK_GENERATOR "WIX")
    set(CPACK_WIX_PRODUCT_GUID "A0A0A0A0-A0A0-A0A0-A0A0-A0A0A0A0A0A0")
    set(CPACK_WIX_UPGRADE_GUID "B0B0B0B0-B0B0-B0B0-B0B0-B0B0B0B0B0B0")
    set(CPACK_WIX_LICENSE_RTF "${CMAKE_CURRENT_SOURCE_DIR}/License.rtf")
    set(CPACK_WIX_CULTURES "en-US")
endif()

if(APPLE)
    set(CPACK_GENERATOR "DragNDrop")
    set(CPACK_DMG_VOLUME_NAME "Solver")
endif()

add_subdirectory(formatter_lib)
add_subdirectory(formatter_ex_lib)
add_subdirectory(solver_lib)
add_subdirectory(hello_world_application)
add_subdirectory(solver_application)

install(DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR}/ DESTINATION include
        FILES_MATCHING PATTERN "*.h")

include(CPack)
