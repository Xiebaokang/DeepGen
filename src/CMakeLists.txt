set(outName "deepgen")

include_directories("${Python_INCLUDE_DIRS}")
if(COMPILE_AS_PYMODULE)
    add_definitions(-DCOMPILE_AS_PYMODULE)
    message("==== compile deepgen as Lib ====")
    add_library(${outName} SHARED main.cc)
    target_link_libraries(${outName} dg_runtime ${Python_LIBRARIES} pthread)
else()
    message(WARNING "==== [DebugOnly] compile deepgen as Exe ====")
    add_executable(${outName} test.cc)
    target_link_libraries(${outName} dg_runtime pthread)
endif()