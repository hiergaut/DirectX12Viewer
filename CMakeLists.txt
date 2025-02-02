cmake_minimum_required(VERSION 3.16)

project(DirectX12Viewer LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /UMBCS /D_UNICODE /DUNICODE")
#SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /SUBSYSTEM:CONSOLE")
#SET(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /SUBSYSTEM:WINDOWS /D_WINDOWS")


#find_package(DirectXTK12 REQUIRED)
add_subdirectory(DirectXTK12)

file(GLOB sources *.cpp *.hpp *.h)
# file(GLOB_RECURSE sources *.cpp *.hpp *.h)

add_executable(${PROJECT_NAME} WIN32 ${sources})

target_link_libraries(${PROJECT_NAME} PRIVATE DirectXTK12 d3d12 dxgi dxguid DirectXTK12)
# target_link_libraries(${PROJECT_NAME} PRIVATE ${CMAKE_SOURCE_DIR}/DirectXTK12)
# target_link_libraries(${PROJECT_NAME} PRIVATE ${CMAKE_SOURCE_DIR}/DirectXTK12 ${CMAKE_BINARY_DIR}/bin/CMake/DirectXTK12)

include(GNUInstallDirs)
install(TARGETS ${PROJECT_NAME}
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)

