#######################################################
#
# glad
#
#######################################################
if(NOT TARGET glad)
  set(glad_BINARY_DIR "${PROJECT_BINARY_DIR}/extern/glad")
  set(glad_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/glad")

  add_library(glad
    ${glad_SOURCE_DIR}/include/glad/gl.h
    ${glad_SOURCE_DIR}/src/gl.cpp)

  target_include_directories(glad
    PUBLIC
    ${glad_SOURCE_DIR}/include)

  set_target_properties(glad
    PROPERTIES POSITION_INDEPENDENT_CODE ON)

  # add target alias for convention
  add_library(glad::glad ALIAS glad)
endif()


#######################################################
#
# stbimage
#
#######################################################
if(NOT TARGET stbimage)
  set(stbimage_BINARY_DIR "${PROJECT_BINARY_DIR}/extern/stb")
  set(stbimage_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/stb")
  add_library(stbimage INTERFACE)
  # Include as #include<stb/stb_{image, resize ...}>
  target_include_directories(stbimage INTERFACE stb)
  add_library(stb::stbimage ALIAS stbimage)
endif()

#######################################################
#
# tinyply
#
#######################################################
if(NOT TARGET tinyply)
  set(tinyply_BINARY_DIR "${PROJECT_BINARY_DIR}/extern/tinyply")
  set(tinyply_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/tinyply")

  add_library(tinyply SHARED
    ${tinyply_SOURCE_DIR}/tinyply.h
    ${tinyply_SOURCE_DIR}/tinyply.cpp)

  target_include_directories(tinyply
    PUBLIC
    ${tinyply_SOURCE_DIR}/include)

  set_target_properties(tinyply
    PROPERTIES POSITION_INDEPENDENT_CODE ON)

  # add target alias for convention
  target_include_directories(tinyply PUBLIC tinyply)
  add_library(tiny::ply ALIAS tinyply)
endif()

#######################################################
#
# Eigen
#
#######################################################
if(NOT TARGET eigen)
  set(eigen_BINARY_DIR "${PROJECT_BINARY_DIR}/extern/eigen")
  set(eigen_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/eigen")

  add_library(eigen INTERFACE)
  target_compile_definitions (eigen INTERFACE "")
  target_include_directories(eigen
    INTERFACE
    $<BUILD_INTERFACE:${eigen_SOURCE_DIR}>
    $<INSTALL_INTERFACE:${INCLUDE_INSTALL_DIR}>)

  add_library(Eigen3::Eigen ALIAS eigen)
endif()

#######################################################
#
# tinyobjloader
#
#######################################################
if(NOT TARGET tinyobjloader)
  set(tinyobjloader_BINARY_DIR "${PROJECT_BINARY_DIR}/extern/tinyobjloader")
  set(tinyobjloader_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/tinyobjloader")

  add_library(tinyobjloader SHARED
    ${tinyobjloader_SOURCE_DIR}/tiny_obj_loader.h
    ${tinyobjloader_SOURCE_DIR}/tiny_obj_loader.cc)

  target_include_directories(tinyobjloader
    PUBLIC
    ${tinyobjloader_SOURCE_DIR}/include)

  set_target_properties(tinyobjloader
    PROPERTIES POSITION_INDEPENDENT_CODE ON)

  # add target alias for convention
  target_include_directories(tinyobjloader PUBLIC tinyobjloader)
  add_library(tiny::objloader ALIAS tinyobjloader)
endif()



#######################################################
#
# imgui
#
#######################################################
if(NOT TARGET imgui)
  set(imgui_BINARY_DIR "${PROJECT_BINARY_DIR}/extern/imgui")
  set(imgui_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/imgui")

  add_library(imgui SHARED
    ${imgui_SOURCE_DIR}/imgui.h
    ${imgui_SOURCE_DIR}/imgui_draw.cpp
    ${imgui_SOURCE_DIR}/imgui_tables.cpp
    ${imgui_SOURCE_DIR}/imstb_rectpack.h
    ${imgui_SOURCE_DIR}/imstb_truetype.h
    ${imgui_SOURCE_DIR}/imgui.cpp
    ${imgui_SOURCE_DIR}/imgui_demo.cpp
    ${imgui_SOURCE_DIR}/imgui_internal.h
    ${imgui_SOURCE_DIR}/imgui_widgets.cpp
    ${imgui_SOURCE_DIR}/imstb_textedit.h)

  target_include_directories(imgui
    PUBLIC
    ${imgui_SOURCE_DIR}/include)

  set_target_properties(imgui
    PROPERTIES POSITION_INDEPENDENT_CODE ON)

  # add target alias for convention
  target_include_directories(imgui PUBLIC imgui)
  add_library(imgui::imgui ALIAS imgui)
endif()


#######################################################
#
# lzfse
#
#######################################################
if(NOT TARGET lzfse)
  set(lzfse_BINARY_DIR "${PROJECT_BINARY_DIR}/extern/lzfse")
  set(lzfse_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/lzfse")
  set(LZFSE_DISABLE_TESTS ON)
  add_subdirectory(lzfse EXCLUDE_FROM_ALL)
  target_include_directories(lzfse PUBLIC lzfse/src)
  add_library(lzfse::lzfse ALIAS lzfse)
endif()




#######################################################
#
# tabulate
#
#######################################################
if(NOT TARGET tabulate)
  set(tabulate_BINARY_DIR "${PROJECT_BINARY_DIR}/extern/tabulate")
  set(tabulate_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/tabulate")

  add_library(tabulate INTERFACE)
  add_library(tabulate::tabulate ALIAS tabulate)
  target_compile_features(tabulate INTERFACE cxx_std_17)
  target_include_directories(tabulate INTERFACE
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
    $<BUILD_INTERFACE:${tabulate_SOURCE_DIR}>)
endif()



#######################################################
#
# rapidjson
#
#######################################################
if(NOT TARGET rapidjson)
  set(rapidjson_BINARY_DIR "${PROJECT_BINARY_DIR}/extern/rapidjson")
  set(rapidjson_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/rapidjson")

  add_library(rapidjson INTERFACE)
  add_library(rapidjson::rapidjson ALIAS rapidjson)
  target_compile_features(rapidjson INTERFACE cxx_std_17)
  target_include_directories(rapidjson INTERFACE
    $<INSTALL_INTERFACE:${CMAKE_INSTALL_INCLUDEDIR}>
    $<BUILD_INTERFACE:${rapidjson_SOURCE_DIR}>)
endif()
