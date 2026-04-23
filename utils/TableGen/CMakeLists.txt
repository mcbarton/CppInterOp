set(LLVM_LINK_COMPONENTS Support)

add_tablegen(cppinterop-tblgen CPPINTEROP
  CppInterOpEmitter.cpp
  TableGen.cpp
)

target_link_libraries(cppinterop-tblgen
  PRIVATE
  LLVMTableGen
  LLVMSupport
  LLVMCore
  LLVMOption
)
