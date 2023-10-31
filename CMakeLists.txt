cmake_minimum_required(VERSION 3.12)
project(ImGuiExample)

# Set the C++ standard
set(CMAKE_CXX_STANDARD 17)

# Add ImGui source files
add_library(imgui
  imgui.cpp
  imgui_demo.cpp
  imgui_draw.cpp
  imgui_tables.cpp
  imgui_widgets.cpp
  imgui_impl_glfw.cpp
  imgui_impl_opengl3.cpp
)

# Add the executable
add_executable(ImGuiExample main.cc)

# Add ImGui source files
#add_subdirectory(lib/imgui)

# Link ImGui to the executable
target_link_libraries(ImGuiExample PRIVATE imgui)

# Find the required libraries (GLFW)
find_package(glfw3 REQUIRED)
find_package(OpenGL REQUIRED)

# Link GLFW to the executable
target_link_libraries(ImGuiExample PRIVATE glfw)
target_link_libraries(ImGuiExample PRIVATE OpenGL::GL)
#target_link_libraries(ImGuiExample PRIVATE ${OPENGL_LIBRARIES})

# Enable C++17 for the project
set_target_properties(ImGuiExample PROPERTIES CXX_STANDARD 17)
set_target_properties(ImGuiExample PROPERTIES CXX_STANDARD_REQUIRED ON)
