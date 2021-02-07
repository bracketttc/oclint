




ADD_SUBDIRECTORY(lib)

IF(MINGW)
    ADD_EXECUTABLE(oclint-${OCLINT_VERSION_RELEASE}
        main.cpp
        reporters_windows_port.cpp
        rules_windows_port.cpp
        )
ELSE()
    ADD_EXECUTABLE(oclint-${OCLINT_VERSION_RELEASE}
        main.cpp
        reporters_dlfcn_port.cpp
        rules_dlfcn_port.cpp
        )
ENDIF()
TARGET_LINK_LIBRARIES(oclint-${OCLINT_VERSION_RELEASE}
    OCLintDriver
    OCLintRuleSet
    OCLintCore
    clangStaticAnalyzerFrontend
    clangStaticAnalyzerCheckers
    clangStaticAnalyzerCore
    clangRewriteFrontend
    clangRewrite
    clangCrossTU
    clangIndex
    ${CLANG_LIBRARIES}
    ${REQ_LLVM_LIBRARIES}
    ${CMAKE_DL_LIBS}
    )

IF(TEST_BUILD)
    TARGET_LINK_LIBRARIES(oclint-${OCLINT_VERSION_RELEASE}
        ${PROFILE_RT_LIBS}
        )
    ADD_SUBDIRECTORY(test)
ENDIF()

IF(DOC_GEN_BUILD)
    ADD_EXECUTABLE(oclint-docgen
        main_docgen.cpp
        rules_dlfcn_port.cpp
        )
    TARGET_LINK_LIBRARIES(oclint-docgen
        OCLintDriver
        OCLintRuleSet
        OCLintCore
        clangStaticAnalyzerFrontend
        clangStaticAnalyzerCheckers
        clangStaticAnalyzerCore
        clangRewriteFrontend
        clangRewrite
        ${CLANG_LIBRARIES}
        ${REQ_LLVM_LIBRARIES}
        ${CMAKE_DL_LIBS}
        )
ENDIF()
