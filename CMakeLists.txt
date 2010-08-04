cmake_minimum_required( VERSION 2.6 )
set( CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/../cmake" )

project( ocamltest )
set( ocamltest_VERSION_MAJOR 0 )
set( ocamltest_VERSION_MINOR 1 )

find_package( OCaml REQUIRED )
include( UseOCaml )

execute_process( COMMAND ocamlfind printconf destdir
    COMMAND sed -e "s,/usr/,,"
    OUTPUT_VARIABLE OCAML_DESTDIR
    OUTPUT_STRIP_TRAILING_WHITESPACE
    )
set( CMAKE_OCAML_PKGINSTALLDIR ${OCAML_DESTDIR} )

add_subdirectory( main )
add_subdirectory( examples )

include( InstallRequiredSystemLibraries )
set( CPACK_PACKAGE_VENDOR "Citrix Systems Ltd." )
set( CPACK_RESOURCE_FILE_LICENSE "${CMAKE_CURRENT_SOURCE_DIR}/LICENSE" )
set( CPACK_PACKAGE_DESCRIPTION_SUMMARY "OCaml unit test framework." )
set( CPACK_PACKAGE_DESCRIPTION_FILE "${CMAKE_CURRENT_SOURCE_DIR}/rpm-description.txt" )
set( CPACK_PACKAGE_VERSION_MAJOR "${ocamltest_VERSION_MAJOR}" )
set( CPACK_PACKAGE_VERSION_MINOR "${ocamltest_VERSION_MINOR}" )
set( CPACK_PACKAGE_VERSION_PATCH "0" )
set( CPACK_GENERATOR "RPM" )
set( CPACK_SOURCE_GENERATOR "RPM" )
include( CPack )
