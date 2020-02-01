
set(THIS ${PROJECT_NAME}Test)

set(SOURCE_FILES
    FooTest.cpp
)

add_subdirectory(googletest)

include_directories(../Include)

add_executable(${THIS} ${SOURCE_FILES})

target_link_libraries(${THIS} gtest_main ${PROJECT_NAME})

add_test(NAME ${THIS} COMMAND ${THIS})

