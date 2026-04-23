set(LLVM_LINK_COMPONENTS
  Support
  TableGen
  TableGenCommon
)

add_tablegen(cppinterop-tblgen CPPINTEROP
  CppInterOpEmitter.cpp
  TableGen.cpp
)
