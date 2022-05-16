cmake_minimum_required(VERSION 3.10.2)
project(qcbor
	DESCRIPTION "QCBOR"
	LANGUAGES C
	VERSION 1.0.0)

set(REQUIRED_QCBOR_COMPILER_CP_FLAG "-pedantic" "-Wall" "-O3" "-ffunction-sections")

set(SOURCE
	src/ieee754.c
	src/qcbor_decode.c
	src/qcbor_encode.c
	src/qcbor_err_to_str.c
	src/UsefulBuf.c
) 

add_library(qcbor STATIC ${SOURCE})

target_compile_options(qcbor
    PRIVATE
	${COMPILER_CP_FLAG}
	${QCBOR_COMPILER_CP_FLAG}
	${REQUIRED_QCBOR_COMPILER_CP_FLAG}
)

target_include_directories(qcbor
    PUBLIC
        $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/inc>
)
