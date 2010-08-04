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

# TODO: add RPM stuff
