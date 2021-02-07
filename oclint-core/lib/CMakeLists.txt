ADD_LIBRARY(OCLintCore
    AbstractResults.cpp
    Constants.cpp
    ResultCollector.cpp
    UniqueResults.cpp
    RawResults.cpp
    RuleBase.cpp
    RuleCarrier.cpp
    Violation.cpp
    ViolationSet.cpp
    )
TARGET_INCLUDE_DIRECTORIES(OCLintCore
    PUBLIC
    ../include
    )

IF (${CMAKE_SYSTEM_NAME} MATCHES "Win")
ADD_LIBRARY(OCLintRuleSet SHARED
    RuleConfiguration.cpp
    RuleSet.cpp
    )
  IF(TEST_BUILD)
    target_link_libraries (OCLintRuleSet --coverage)
  ENDIF()
ELSE()
ADD_LIBRARY(OCLintRuleSet
    RuleConfiguration.cpp
    RuleSet.cpp
    )
ENDIF()
TARGET_INCLUDE_DIRECTORIES(OCLintRuleSet
    PUBLIC
    ../include
    )
