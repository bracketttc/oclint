IF (NOT MINGW)
    ADD_LIBRARY(OCLintUtil
        ASTUtil.cpp
        StdUtil.cpp
    )
    TARGET_INCLUDE_DIRECTORIES(OCLintUtil
        PUBLIC
        ../../include
    )
    TARGET_LINK_LIBRARIES(OCLintUtil
        PUBLIC
        clangBasic
        clangParse
    )
ENDIF()
