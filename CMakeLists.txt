cmake_minimum_required(VERSION 3.16)

project(DirectX12Viewer LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

add_executable(DirectX12Viewer main.cpp)

include(GNUInstallDirs)
install(TARGETS DirectX12Viewer
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
