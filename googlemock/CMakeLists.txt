project( googlemock )

set( HEADERS
    "include/gmock/gmock-actions.h"
    "include/gmock/gmock-cardinalities.h"
    "include/gmock/gmock-function-mocker.h"
    "include/gmock/gmock-generated-actions.h"
    "include/gmock/gmock.h"
    "include/gmock/gmock-matchers.h"
    "include/gmock/gmock-more-matchers.h"
    "include/gmock/gmock-nice-strict.h"
    "include/gmock/gmock-spec-builders.h"
    "include/gmock/internal/gmock-internal-utils.h"
    "include/gmock/internal/gmock-port.h"
    "include/gmock/internal/gmock-pp.h"
    "include/gmock/internal/custom/gmock-generated-actions.h"
    "include/gmock/internal/custom/gmock-matchers.h"
    "include/gmock/internal/custom/gmock-port.h"

)

set( SOURCES
    "src/gmock-all.cc"
)

add_library( ${PROJECT_NAME} STATIC
    ${HEADERS}
    ${SOURCES}
)

target_include_directories( ${PROJECT_NAME}
    PUBLIC
        ${SOURCE_DIR}/external/gtest/googlemock/include
        ${SOURCE_DIR}/external/gtest/googletest/include
    PRIVATE
        ${SOURCE_DIR}/external/gtest/googlemock/
)

target_link_libraries( ${PROJECT_NAME}
    PUBLIC
        ${CMAKE_THREAD_LIBS_INIT}
)

install( TARGETS ${PROJECT_NAME}
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

# The trailing slash is important
install( DIRECTORY ${CMAKE_INSTALL_INCLUDEDIR}/ DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
)
