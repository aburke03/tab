# CMakeList.txt : Top-level CMake project file, do global configuration
# and include sub-projects here.
#

cmake_minimum_required (VERSION 3.19)
set(CMAKE_CXX_STANDARD 20)

# Enable Hot Reload for MSVC compilers if supported.
if (POLICY CMP0141)
  cmake_policy(SET CMP0141 NEW)
  set(CMAKE_MSVC_DEBUG_INFORMATION_FORMAT "$<IF:$<AND:$<C_COMPILER_ID:MSVC>,$<CXX_COMPILER_ID:MSVC>>,$<$<CONFIG:Debug,RelWithDebInfo>:EditAndContinue>,$<$<CONFIG:Debug,RelWithDebInfo>:ProgramDatabase>>")
endif()

# Project descriptors
project ("TabInventorySystem"
		VERSION 1.0.0
		DESCRIPTION <"An inventory management system">
)

# Add directory for project files
add_subdirectory ("code")

set(GLFW_BUILD_DOCS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_TESTS OFF CACHE BOOL "" FORCE)
set(GLFW_BUILD_EXAMPLES OFF CACHE BOOL "" FORCE)

add_subdirectory(code/third-party/glfw)

# uncomment the lines below to enable the Catch2 testing infrastructure
# enable_testing()
# include(CTest)
#
# target_compile_definitions(project PRIVATE CATCH_CONFIG_MAIN)
# add_test(NAME project COMMAND project)
