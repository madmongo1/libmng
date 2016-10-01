project(libmng)
cmake_minimum_required(VERSION 3.0.2)

set(SRC
libmng.h
libmng_callback_xs.c
libmng_chunk_descr.c
libmng_chunk_descr.h
libmng_chunk_io.c
libmng_chunk_io.h
libmng_chunk_prc.c
libmng_chunk_prc.h
libmng_chunk_xs.c
libmng_chunks.h
libmng_cms.c
libmng_cms.h
libmng_conf.h
libmng_data.h
libmng_display.c
libmng_display.h
libmng_dither.c
libmng_dither.h
libmng_error.c
libmng_error.h
libmng_filter.c
libmng_filter.h
libmng_hlapi.c
libmng_jpeg.c
libmng_jpeg.h
libmng_memory.h
libmng_object_prc.c
libmng_object_prc.h
libmng_objects.h
libmng_pixels.c
libmng_pixels.h
libmng_prop_xs.c
libmng_read.c
libmng_read.h
libmng_trace.c
libmng_trace.h
libmng_types.h
libmng_write.c
libmng_write.h
libmng_zlib.c
libmng_zlib.h
)

add_library(mng ${SRC})

set (sysincs)
foreach (i ${CMAKE_INSTALL_PREFIX})
  list (APPEND sysincs "${i}/include")
  message (STATUS "${i}/include")
endforeach ()

target_include_directories(mng
SYSTEM BEFORE
PUBLIC $<BUILD_INTERFACE:${sysincs}> $<INSTALL_INTERFACE:include>
)

install(TARGETS mng
RUNTIME DESTINATION bin
LIBRARY DESTINATION lib
ARCHIVE DESTINATION lib)

install(FILES libmng.h libmng_conf.h libmng_types.h DESTINATION include)

