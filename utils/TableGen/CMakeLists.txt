set(LLVM_LINK_COMPONENTS Support)

add_tablegen(cppinterop-tblgen CPPINTEROP
  CppInterOpEmitter.cpp
  TableGen.cpp
)

llvm_map_components_to_libnames(LLVM_LIBS
  Core
  Support
  TableGen
  Option
)

target_link_libraries(cppinterop-tblgen PRIVATE ${LLVM_LIBS})
