cmake_minimum_required(VERSION 3.15)

set(BUILD_SHARED_LIBS  OFF)
set(GLFW_BUILD_EXAMPLES  OFF)
set(GLFW_BUILD_TESTS OFF)
set(GLFW_BUILD_DOCS  OFF)
set(GLFW_INSTALL  OFF)

add_subdirectory(glfw)

add_library(imgui STATIC 
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/imgui_demo.cpp 
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/imgui_draw.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/imgui_tables.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/imgui_widgets.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/imgui.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/backends/imgui_impl_glfw.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/backends/imgui_impl_vulkan.cpp
)

target_include_directories(imgui PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/glfw/include
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui/backends
    ${CMAKE_CURRENT_SOURCE_DIR}/imgui
    ${Vulkan_INCLUDE_DIRS}
)
target_link_libraries(imgui PRIVATE glfw ${Vulkan_LIBRARIES})

set(IMGUI_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/imgui ${CMAKE_CURRENT_SOURCE_DIR}/imgui/backends PARENT_SCOPE)
set(GLFW_INCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/glfw/include PARENT_SCOPE)





