project(rpmalloc LANGUAGES C)

add_library(rpmalloc OBJECT "rpmalloc/rpmalloc.c" "rpmalloc/rpmalloc.h")

set_target_properties(rpmalloc PROPERTIES C_STANDARD 11 C_STANDARD_REQUIRED ON)

if(WIN32)
	target_sources(rpmalloc PUBLIC "rpmalloc/rpnew.h")
	target_compile_options(rpmalloc PRIVATE /experimental:c11atomics)
endif()