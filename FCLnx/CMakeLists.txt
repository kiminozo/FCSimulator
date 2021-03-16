cmake_minimum_required(VERSION 3.1.0)

project(fcsimulator VERSION 1.0.0 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

if(CMAKE_VERSION VERSION_LESS "3.7.0")
    set(CMAKE_INCLUDE_CURRENT_DIR ON)
endif()

find_package(Qt5 COMPONENTS Widgets REQUIRED)

add_executable(fcsimulator
        Mapper/mapper_0.cpp 
        Mapper/mapper_1.cpp 
        Mapper/mapper_2.cpp 
        cartridge.cpp 
        controller.cpp 
        cpu.cpp 
        cpu_ram.cpp 
        main.cpp 
        mainwindow.cpp 
        ppu.cpp 
        ppu_bus.cpp
        mainwindow.ui
)

include_directories("${CMAKE_SOURCE_DIR}")

target_link_libraries(fcsimulator 
       Qt5::Widgets 
)