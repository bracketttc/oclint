cmake_minimum_required( VERSION 3.1 )

project( oclint
    VERSION 20.11
    LANGUAGES CXX
    )


SET(CMAKE_MODULE_PATH
    ${CMAKE_MODULE_PATH}
    "${CMAKE_CURRENT_SOURCE_DIR}/oclint-core/cmake"
    )

INCLUDE(OCLintConfig)

add_subdirectory( oclint-core )
add_subdirectory( oclint-metrics )
add_subdirectory( oclint-rules )
add_subdirectory( oclint-reporters )
add_subdirectory( oclint-driver )
