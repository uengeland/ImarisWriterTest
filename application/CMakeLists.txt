list(APPEND imaris_tgts
  ImarisWriterTest
  ImarisWriterTestSimple
)

foreach(imaris_tgt ${imaris_tgts})

  add_executable(${imaris_tgt}
    ${imaris_tgt}.cxx
  )

  target_include_directories(${imaris_tgt}
    PRIVATE 
      ${CMAKE_CURRENT_SOURCE_DIR}
      ${CMAKE_BINARY_DIR}/Writer/src
  )

  target_link_directories(${imaris_tgt}
    PRIVATE ${CMAKE_BINARY_DIR}/Writer/src/ImarisWriter-build
  )

  target_link_libraries(${imaris_tgt}
    PRIVATE 
      bpImarisWriter96
  )

  add_dependencies(${imaris_tgt} ImarisWriter)  

endforeach()

make_directory(${CMAKE_CURRENT_BINARY_DIR}/out)

add_test(NAME ImarisWriterTest 
  COMMAND ImarisWriterTest -sizex 400 -sizey 400 -sizez 10 -sizet 10 -sizec 10 -type 16bit -threads 8 -outputpath out -randseed 33 -compression 1 img16.ims
  #WORKING_DIRECTORY .
)

add_test(NAME ImarisWriterTestSimple
  COMMAND ImarisWriterTestSimple "${CMAKE_CURRENT_BINARY_DIR}/out/simple.ims"
)