cmake_minimum_required(VERSION 3.11)

include("cmake/HunterGate.cmake")

HunterGate(
    URL "https://github.com/ruslo/hunter/archive/v0.23.214.tar.gz"
    SHA1 "e14bc153a7f16d6a5eeec845fb0283c8fad8c358"
    LOCAL
)

project(public VERSION 0.0.1)
set(CMAKE_CXX_STANDARD 14)

add_executable(public_client public.cpp)

set(config_install_dir "lib/cmake/${PROJECT_NAME}")
set(include_install_dir "include")
set(targets_export_name "${PROJECT_NAME}Targets")
set(namespace "${PROJECT_NAME}::")

install(
    TARGETS public_client
    EXPORT "${targets_export_name}"
    LIBRARY DESTINATION "lib"
    ARCHIVE DESTINATION "lib"
    RUNTIME DESTINATION "bin"
    INCLUDES DESTINATION "${include_install_dir}"
)

install(
    EXPORT "${targets_export_name}"
    NAMESPACE "${namespace}"
    DESTINATION "${config_install_dir}"
)