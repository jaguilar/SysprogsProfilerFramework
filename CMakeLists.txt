#AUTOMATICALLY GENERATED FILE. DO NOT EDIT!
#Use VisualGDB Project Properties to edit the frameworks used by this project

if(NOT SYSPROGS_PROFILER_FRAMEWORK_PATH AND DEFINED ENV{SYSPROGS_PROFILER_FRAMEWORK_PATH})
    set(SYSPROGS_PROFILER_FRAMEWORK_PATH "$ENV{SYSPROGS_PROFILER_FRAMEWORK_PATH}")
endif()

function(instantiate_sysprogs_frameworks)
    add_library(Profiler INTERFACE)
    target_sources(Profiler INTERFACE
        ${CMAKE_CURRENT_LIST_DIR}/FastSemihosting.cpp
        ${CMAKE_CURRENT_LIST_DIR}/SamplingProfiler.cpp
        ${CMAKE_CURRENT_LIST_DIR}/InstrumentingProfiler.cpp
        ${CMAKE_CURRENT_LIST_DIR}/TestResourceManager.cpp
        ${CMAKE_CURRENT_LIST_DIR}/ProfilerRTOS_FreeRTOS.c
        ${CMAKE_CURRENT_LIST_DIR}/ProfilerDriver_RP2040.cpp
    )

    target_include_directories(Profiler INTERFACE
        ${CMAKE_CURRENT_LIST_DIR}
    )

    target_compile_definitions(Profiler INTERFACE
        FAST_SEMIHOSTING_BUFFER_SIZE=4096
        FAST_SEMIHOSTING_BLOCKING_MODE=1
        FAST_SEMIHOSTING_STDIO_DRIVER=1
        FAST_SEMIHOSTING_PROFILER_DRIVER=1
        PROFILER_RP2040
        USE_FREERTOS_IF_FOUND
    )

    target_link_libraries(Profiler INTERFACE hardware_pio hardware_timer -Wl,-q)
endfunction() #instantiate_sysprogs_frameworks

instantiate_sysprogs_frameworks()
