Cmake_minimum_required(VERSION 3.10)

# Projekt Name:
project(vulkan_tutorial)

# cpp version:
set(CMAKE_CXX_STANDARD 11)

#output dir:
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY "$(PROJECT_SOURCE_DIR)/bin")

#Dateien(?):
set(SOURCE_FILES src/main.cpp src/simple_logger.cpp src/vulkan_base/vulkan_device.cpp src/vulkan_base/vulkan_swapchain.cpp)

# find SDL2
add_subdirectory(libs/SDL)

# Find Vulkan
find_package(Vulkan REQUIRED)

# vulkan_tutorial Exe target
add_executable(vulkan_tutorial ${SOURCE_FILES})
target_include_directories(vulkan_tutorial PUBLIC libs/SDL/include)
target_link_libraries(vulkan_tutorial PUBLIC SDL2-static)
target_include_directories(vulkan_tutorial PUBLIC ${Vulkan_INCLUDE_DIRS})
target_link_libraries(vulkan_tutorial PUBLIC ${Vulkan_LIBRARIES})