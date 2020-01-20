cmake_minimum_required(VERSION 3.10)

# Define project name / version 
project(Foo VERSION 1.0.0)

# Add the GNU install directories
include(GNUInstallDirs)

# specify the C++ standard
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED True)
set(CMAKE_BUILD_TYPE Release)

# Set the library source files
set(SOURCE_FILES 
    Include/Foo/Foo.hpp
    Source/Foo.cpp
)

# Generate the library
add_library(${PROJECT_NAME} SHARED ${SOURCE_FILES})

target_include_directories(${PROJECT_NAME}
    PUBLIC 
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/Include>
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}>
)

# Generate a library with version number and link
set_target_properties(${PROJECT_NAME} PROPERTIES
    VERSION ${PROJECT_VERSION}
    SOVERSION 1
)

# Share the version with the library code trough 
target_compile_definitions(${PROJECT_NAME} PRIVATE
    FOO_MAJOR_VERSION=${PROJECT_VERSION_MAJOR}
    FOO_MINOR_VERSION=${PROJECT_VERSION_MINOR}
)

install(DIRECTORY "Include/${PROJECT_NAME}/"
    # Must match the INSTALL_INTERFACE of include directories, see above.
    DESTINATION "${CMAKE_INSTALL_INCLUDEDIR}/${PROJECT_NAME}"
)

# Instalation
install(TARGETS ${PROJECT_NAME}
    EXPORT ${PROJECT_NAME}_Targets
    ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

# Enable google test
# option(BUILD_TESTS "Build the tests" ON)
# if(BUILD_TESTS)
#     enable_testing()
#     add_subdirectory(googletest)
#     add_subdirectory(Test)
# endif()
