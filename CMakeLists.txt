cmake_minimum_required(VERSION 3.15)
project(uwpDepot NONE)

set(UWP_X64_BASE "${CMAKE_CURRENT_LIST_DIR}/x64")

add_library(uwp::libuwp SHARED IMPORTED GLOBAL)
# using SDL3 prefix to avoid a bunch of cmake changes downstream
add_library(SDL3::SDL3 SHARED IMPORTED GLOBAL)

set_target_properties(uwp::libuwp PROPERTIES
	IMPORTED_LOCATION "${UWP_X64_BASE}/bin/libuwp.dll"
	IMPORTED_IMPLIB   "${UWP_X64_BASE}/lib/libuwp.lib"
	INTERFACE_INCLUDE_DIRECTORIES "${UWP_X64_BASE}/include"
)

set_target_properties(SDL3::SDL3 PROPERTIES
	IMPORTED_LOCATION "${UWP_X64_BASE}/bin/SDL3.dll"
	IMPORTED_IMPLIB   "${UWP_X64_BASE}/lib/SDL3.lib"
	INTERFACE_INCLUDE_DIRECTORIES "${UWP_X64_BASE}/include;${UWP_X64_BASE}/include/SDL3"
)
