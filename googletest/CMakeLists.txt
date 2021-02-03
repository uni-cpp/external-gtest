project( gtest )

set( HEADERS
    "include/gtest/gtest-death-test.h"
    "include/gtest/gtest.h"
    "include/gtest/gtest-matchers.h"
    "include/gtest/gtest-message.h"
    "include/gtest/gtest-param-test.h"
    "include/gtest/gtest_pred_impl.h"
    "include/gtest/gtest-printers.h"
    "include/gtest/gtest_prod.h"
    "include/gtest/gtest-spi.h"
    "include/gtest/gtest-test-part.h"
    "include/gtest/gtest-typed-test.h"
    "include/gtest/internal/gtest-death-test-internal.h"
    "include/gtest/internal/gtest-filepath.h"
    "include/gtest/internal/gtest-internal.h"
    "include/gtest/internal/gtest-param-util.h"
    "include/gtest/internal/gtest-port-arch.h"
    "include/gtest/internal/gtest-port.h"
    "include/gtest/internal/gtest-string.h"
    "include/gtest/internal/gtest-type-util.h"
    "include/gtest/internal/custom/gtest.h"
    "include/gtest/internal/custom/gtest-port.h"
    "include/gtest/internal/custom/gtest-printers.h"
)

set( SOURCES
    "src/gtest-all.cc"
)

add_library( ${PROJECT_NAME} STATIC
    ${HEADERS}
    ${SOURCES}
)

target_include_directories( ${PROJECT_NAME}
    PUBLIC
        ${SOURCE_DIR}/external/gtest/googletest/include
    PRIVATE
        ${SOURCE_DIR}/external/gtest/googletest/
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

######################################################################################

project ( gtest-main )

set( HEADERS
    ""
)

set( SOURCES
    "src/gtest_main.cc"
)

add_library( ${PROJECT_NAME} STATIC
    ${HEADERS}
    ${SOURCES}
)

target_include_directories( ${PROJECT_NAME}
    PUBLIC
        ${SOURCE_DIR}/external/gtest/googletest/include
    PRIVATE
        ${SOURCE_DIR}/external/gtest/googletest/
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

