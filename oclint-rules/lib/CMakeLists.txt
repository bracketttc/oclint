ADD_SUBDIRECTORY(helper)
ADD_SUBDIRECTORY(util)

SET (AbstractSource
    AbstractASTMatcherRule.cpp
    AbstractASTRuleBase.cpp
    AbstractSourceCodeReaderRule.cpp
)

IF (MINGW)
    ADD_LIBRARY(OCLintAbstractRule SHARED
        ${AbstractSource}
        helper/AttributeHelper.cpp
        helper/EnforceHelper.cpp
        helper/SuppressHelper.cpp
        util/ASTUtil.cpp
        util/StdUtil.cpp)
    SET_TARGET_PROPERTIES(OCLintAbstractRule
        PROPERTIES RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/bin
    )
ELSE()
    ADD_LIBRARY(OCLintAbstractRule ${AbstractSource})
    TARGET_LINK_LIBRARIES(OCLintAbstractRule
        PUBLIC
        OCLintHelper
    )
ENDIF()
TARGET_INCLUDE_DIRECTORIES(OCLintAbstractRule
    PUBLIC
    ../include
)
TARGET_LINK_LIBRARIES(OCLintAbstractRule
    PUBLIC
    OCLintCore
    OCLintRuleSet
    ${CLANG_LIBRARIES}
    ${REQ_LLVM_LIBRARIES}
)
