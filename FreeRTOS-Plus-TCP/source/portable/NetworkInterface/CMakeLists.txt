add_library( freertos_plus_tcp_network_if_common STATIC )

target_sources( freertos_plus_tcp_network_if_common
  PRIVATE
    Common/phyHandling.c
    include/phyHandling.h
)

target_include_directories( freertos_plus_tcp_network_if_common
  PUBLIC
    include
)

target_compile_options( freertos_plus_tcp_network_if_common
  PRIVATE
    $<$<COMPILE_LANG_AND_ID:C,Clang>:-Wno-conditional-uninitialized>
    $<$<COMPILE_LANG_AND_ID:C,Clang>:-Wno-implicit-int-conversion>
    $<$<COMPILE_LANG_AND_ID:C,Clang>:-Wno-padded>
    $<$<COMPILE_LANG_AND_ID:C,Clang>:-Wno-uninitialized>
    $<$<COMPILE_LANG_AND_ID:C,Clang>:-Wno-unused-but-set-variable>
    $<$<COMPILE_LANG_AND_ID:C,Clang>:-Wno-unused-macros>
)

target_link_libraries( freertos_plus_tcp_network_if_common
  PRIVATE
    freertos_kernel
    freertos_plus_tcp
)

#------------------------------------------------------------------------------
add_subdirectory(libslirp)
add_subdirectory(linux)
add_subdirectory(loopback)
