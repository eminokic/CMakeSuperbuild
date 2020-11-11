cmake_minimum_required(VERSION 3.14)
project(CMaizeSuperbuild)
include(ExternalProject)

set(installDir ${CMAKE_CURRENT_BINARY_DIR}/install)

ExternalProject_Add( rootDependency 
...
INSTALL_DIR ${installDir}
CMAKE_ARGS -DCMAKE_INSTALL_PREFIX: PATH = <INSTALL_DIR>
)

ExternalProject_Add( givenDependency2 
...
INSTALL_DIR ${installDir} 
CMAKE_ARGS -DCMAKE_INSTALL_PREFIX: PATH = <INSTALL_DIR>
           -DCMAKE_PREFIX_PATH: PATH = <INSTALL_DIR>
)

ExternalProject_Add( givenDependencyN
...
INSTALL_DIR ${installDir} 
CONFIGURE_COMMAND <SOURCE_DIR>/configure --prefix <INSTALL_DIR>
)
