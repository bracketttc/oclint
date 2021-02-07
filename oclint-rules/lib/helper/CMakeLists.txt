IF (NOT MINGW)
    ADD_LIBRARY(OCLintHelper
        AttributeHelper.cpp
        EnforceHelper.cpp
        SuppressHelper.cpp
    )
    TARGET_INCLUDE_DIRECTORIES(OCLintHelper
        PUBLIC
        ../../include
        )
    TARGET_LINK_LIBRARIES(OCLintHelper
        PUBLIC
        OCLintCore
        OCLintRuleSet
        clangParse
    )
ENDIF()
