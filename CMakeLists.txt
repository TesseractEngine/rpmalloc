project(rpmalloc LANGUAGES C)

add_library(rpmalloc OBJECT "rpmalloc/rpmalloc.c" "rpmalloc/rpmalloc.h")
target_include_directories(rpmalloc PUBLIC "rpmalloc")

set_target_properties(rpmalloc PROPERTIES C_STANDARD 11 C_STANDARD_REQUIRED ON)

if(WIN32)
	target_sources(rpmalloc PUBLIC "rpmalloc/rpnew.h")
	target_compile_options(rpmalloc PRIVATE /experimental:c11atomics)
endif()

target_compile_definitions(rpmalloc PUBLIC RPMALLOC_FIRST_CLASS_HEAPS=1)