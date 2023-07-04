cmake_minimum_required (VERSION 3.16)

project ("imgui")
file(GLOB_RECURSE headers CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.h")
file(GLOB_RECURSE sources CONFIGURE_DEPENDS "${CMAKE_CURRENT_SOURCE_DIR}/imgui/*.cpp")

add_library (imgui OBJECT
	${IMGUI_SOURCES}
	${IMGUI_PLATFORM_SOURCES}
	${IMGUI_RENDERER_SOURCES}
)

target_include_directories (imgui PUBLIC
	${CMAKE_CURRENT_SOURCE_DIR}/imgui
	${CMAKE_CURRENT_SOURCE_DIR}/imgui/backends
)