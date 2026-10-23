cmake_minimum_required(VERSION 3.21)
project(bx_wiiu LANGUAGES CXX)

get_filename_component(BX_DIR "../.." ABSOLUTE)
add_library(bx STATIC
    ${BX_DIR}/src/allocator.cpp
    ${BX_DIR}/src/bitarray.cpp
    ${BX_DIR}/src/bounds.cpp
    ${BX_DIR}/src/bx.cpp
    ${BX_DIR}/src/commandline.cpp
    ${BX_DIR}/src/debug.cpp
    ${BX_DIR}/src/dtoa.cpp
    ${BX_DIR}/src/easing.cpp
    ${BX_DIR}/src/file.cpp
    ${BX_DIR}/src/filepath.cpp
    ${BX_DIR}/src/hash.cpp
    ${BX_DIR}/src/math.cpp
    ${BX_DIR}/src/mutex.cpp
    ${BX_DIR}/src/os.cpp
    ${BX_DIR}/src/scanner.cpp
    ${BX_DIR}/src/sort.cpp
    ${BX_DIR}/src/string.cpp
    ${BX_DIR}/src/superluminal.cpp
    ${BX_DIR}/src/timer.cpp
    ${BX_DIR}/src/url.cpp
)
target_compile_features(bx PUBLIC cxx_std_20)
target_compile_definitions(bx PUBLIC
    BX_CONFIG_DEBUG=$<IF:$<CONFIG:Debug>,1,0>
    BX_CONFIG_SUPPORTS_THREADING=0
)
target_compile_options(bx PRIVATE -fno-exceptions -fno-rtti)
target_include_directories(bx PUBLIC ${BX_DIR}/include PRIVATE ${BX_DIR}/3rdparty)
