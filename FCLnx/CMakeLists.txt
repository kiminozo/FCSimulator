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


# Destination paths below are relative to ${CMAKE_INSTALL_PREFIX}
# install(TARGETS ${PROJECT_NAME}
#     BUNDLE DESTINATION . COMPONENT Runtime
#     RUNTIME DESTINATION ${INSTALL_RUNTIME_DIR} COMPONENT Runtime
#     )

# # Note Mac specific extension .app
# set(APPS "\$ENV{DESTDIR}\${CMAKE_INSTALL_PREFIX}/${PROJECT_NAME}.app")

# # Directories to look for dependencies
# set(DIRS "${CMAKE_BINARY_DIR}")

# # Path used for searching by FIND_XXX(), with appropriate suffixes added
# if(CMAKE_PREFIX_PATH)
#     foreach(dir ${CMAKE_PREFIX_PATH})
#         list(APPEND DIRS "${dir}/bin" "${dir}/lib")
#     endforeach()
# endif()

# # Append Qt's lib folder which is two levels above Qt5Widgets_DIR
# list(APPEND DIRS "${Qt5Widgets_DIR}/../..")

# include(InstallRequiredSystemLibraries)

# message(STATUS "APPS: ${APPS}")
# message(STATUS "QT_PLUGINS: ${QT_PLUGINS}")
# message(STATUS "DIRS: ${DIRS}")

# set(CMAKE_INSTALL_PREFIX ${CMAKE_BINARY_DIR})
# install(CODE "include(BundleUtilities)
#      fixup_bundle(\"${APPS}\" \"${QT_PLUGINS}\" \"${DIRS}\")")

# set(CPACK_GENERATOR "DragNDrop")
# include(CPack)