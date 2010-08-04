add_ocaml_library( ocamltest-examples 
    SOURCES example
    )

add_ocaml_executable( ocamltest-examples-test
    SOURCES example_test
    LIBRARIES ocamltest-examples ocamltest
    OCAMLCOPTS -thread
    PACKAGES threads
    RUN_POST_BUILD
    )
