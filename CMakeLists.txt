cmake_minimum_required(VERSION 3.1)
project(cpprestsdk-root NONE)
enable_testing()

# Include our extra modules
set(CMAKE_MODULE_PATH ${CMAKE_SOURCE_DIR}/cmake/)

# Configure MSVC Runtime
if(MSVC)
	include(MSVCRuntime)
	if(NOT DEFINED MSVC_RUNTIME)
		set(MSVC_RUNTIME "dynamic")
	endif()
	if(MSVC_RUNTIME STREQUAL "static")
		if(BUILD_SHARED_LIBS)
			message(FATAL_ERROR "Static CRT is only supported in a fully static build")
		endif()
		message(STATUS "Use the MSVC static runtime option carefully!")
	endif()
	configure_msvc_runtime()

	if(NOT DEFINED CMAKE_SUPPRESS_REGENERATION)
		set(CMAKE_SUPPRESS_REGENERATION ON)
	endif()
endif()

add_subdirectory(Release)
