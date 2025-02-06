cmake_minimum_required(VERSION 3.12...3.31)
project(sdlgpu3_template)

include(cmake/get_cpm.cmake)

CPMAddPackage("gh:TheLartians/Ccache.cmake@1.2.5")
CPMAddPackage("gh:libsdl-org/SDL#release-3.2.2")
CPMAddPackage(
  NAME SDL_shadercross
  GITHUB_REPOSITORY libsdl-org/SDL_shadercross
  GIT_TAG 7207bab784e18aebd734751d4de1b4c4d16aa88a
  OPTIONS
    "SDLSHADERCROSS_VENDORED ON"
)
CPMAddPackage(
  NAME imgui
  GITHUB_REPOSITORY ocornut/imgui
  VERSION 1.91.8-docking
  DOWNLOAD_ONLY YES
)
if(imgui_ADDED)
  file(GLOB imgui_sources
    ${imgui_SOURCE_DIR}/*.cpp
    ${imgui_SOURCE_DIR}/backends/imgui_impl_sdl3.cpp
    ${imgui_SOURCE_DIR}/backends/imgui_impl_sdlgpu3.cpp
  )
  add_library(imgui STATIC ${imgui_sources})
  target_include_directories(imgui SYSTEM PUBLIC
    $<BUILD_INTERFACE:${imgui_SOURCE_DIR}>
    $<BUILD_INTERFACE:${imgui_SOURCE_DIR}/backends>
  )
  target_link_libraries(imgui PRIVATE
    SDL3::SDL3
    SDL3_shadercross::SDL3_shadercross
  )
endif()

add_executable(${PROJECT_NAME}
  src/main.cpp
)
target_include_directories(${PROJECT_NAME} PRIVATE)
target_link_libraries(${PROJECT_NAME} PRIVATE
  SDL3::SDL3
  SDL3_shadercross::SDL3_shadercross
  imgui
)