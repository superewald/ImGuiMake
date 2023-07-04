cmake_minimum_required (VERSION 3.16)

project ("imgui")
file(GLOB_RECURSE headers CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.h")
file(GLOB_RECURSE sources CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.cpp")

set (IMGUI_PLATFORM_BACKEND "win32" CACHE STRING "Specify which imgui platform backend to use")
set (IMGUI_RENDERER_BACKEND "d3d11" CACHE STRING "Specify which imgui renderer backend to use")

set (IMGUI_SOURCES
	imgui/imgui.cpp
	imgui/imgui.h
	imgui/imconfig.h
	imgui/imgui_demo.cpp
	imgui/imgui_draw.cpp
	imgui/imgui_internal.h
	imgui/imgui_tables.cpp
	imgui/imgui_widgets.cpp
)

set (IMGUI_PLATFORM_SOURCES
	imgui/backends/imgui_impl_${IMGUI_PLATFORM_BACKEND}.cpp
	imgui/backends/imgui_impl_${IMGUI_PLATFORM_BACKEND}.h
)

set (IMGUI_RENDERER_SOURCES
	imgui/backends/imgui_impl_${IMGUI_RENDERER_BACKEND}.cpp
	imgui/backends/imgui_impl_${IMGUI_RENDERER_BACKEND}.h
)

add_library (imgui OBJECT
    ${IMGUI_SOURCES}
    ${IMGUI_PLATFORM_SOURCES}
    ${IMGUI_RENDERER_SOURCES}
)

target_include_directories (imgui PUBLIC
	${CMAKE_CURRENT_SOURCE_DIR}/imgui
	${CMAKE_CURRENT_SOURCE_DIR}/imgui/backends
)