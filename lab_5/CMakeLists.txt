cmake_minimum_required(VERSION 3.13)

project(lab_5)

set(CMAKE_CXX_COMPILER "g++")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall") # включаем все ворнинги 

# Добавляем цель для сборки и запуска тестов
add_executable(test test.cpp)
target_link_libraries(test gtest)
# Кастомные цели для запуска main и тестов
add_executable(main main.cpp)

add_custom_target(start_test
    COMMAND ./test
    DEPENDS test
    WORKING_DIRECTORY ${CMAKE_BINARY_DIR}
)

add_custom_target(start_main
    COMMAND ./main
    DEPENDS main
    WORKING_DIRECTORY ${CMAKE_BINARY_DIR}
)

