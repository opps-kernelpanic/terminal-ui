# CMakeLists.txt
cmake_minimum_required(VERSION 3.10)
project(terminal-ui)

find_package(PkgConfig REQUIRED)
pkg_check_modules(LVGL REQUIRED lvgl)
pkg_check_modules(LIBDRM REQUIRED libdrm)
pkg_check_modules(DBUS REQUIRED dbus-1)

include_directories(${LVGL_INCLUDE_DIRS})
link_directories(${LVGL_LIBRARY_DIRS})

include_directories(${DBUS_INCLUDE_DIRS})
link_directories(${DBUS_LIBRARY_DIRS})

include_directories(include)
file(GLOB_RECURSE SRC_FILES "src/*.c")

add_executable(terminal-ui ${SRC_FILES})

target_link_libraries(terminal-ui lvgl)
target_link_libraries(terminal-ui ${LIBDRM_LIBRARIES})
target_link_libraries(terminal-ui ${DBUS_LIBRARIES})
target_include_directories(terminal-ui PRIVATE ${LIBDRM_INCLUDE_DIRS})


