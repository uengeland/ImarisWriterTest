add_executable(ImarisWriter96Test
  bpImarisWriter96TestProgram.c
)

target_include_directories(ImarisWriter96Test
  PRIVATE 
    ${CMAKE_BINARY_DIR}/Writer/src/ImarisWriter/interfaceC
)

target_link_directories(ImarisWriter96Test
  PRIVATE ${CMAKE_BINARY_DIR}/Writer/src/ImarisWriter-build
)

target_link_libraries(ImarisWriter96Test
  PRIVATE 
    bpImarisWriter96
)

add_dependencies(ImarisWriter96Test ImarisWriter)

add_test(NAME ImarisWriter96Test
  COMMAND ImarisWriter96Test
)