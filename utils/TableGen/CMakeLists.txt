set(LLVM_LINK_COMPONENTS Support)

add_tablegen(cppinterop-tblgen CPPINTEROP
  CppInterOpEmitter.cpp
  TableGen.cpp
)

if(MSVC)

  set(MSVC_EXPORTLIST_TBLGEN
    ?find_first_not_of@StringRef@llvm@@QEBA_KV12@_K@Z
    ?split@StringRef@llvm@@QEBAXAEAV?$SmallVectorImpl@VStringRef@llvm@@@2@DH_N@Z
    ?write@raw_ostream@llvm@@QEAAAEAV12@PEBD_K@Z
    ?getValueAsString@Record@llvm@@QEBA?AVStringRef@2@V32@@Z
    ?getValueAsListOfDefs@Record@llvm@@QEBA?AV?$vector@PEBVRecord@llvm@@V?$allocator@PEBVRecord@llvm@@@std@@@std@@VStringRef@2@@Z
    ?getAllDerivedDefinitions@RecordKeeper@llvm@@QEBA?AV?$ArrayRef@PEBVRecord@llvm@@@2@VStringRef@2@@Z
    ?report_fatal_error@llvm@@YAXAEBVTwine@1@_N@Z
    ?errs@llvm@@YAAEAVraw_fd_ostream@1@XZ
    ?ParseCommandLineOptions@cl@llvm@@YA_NHPEBQEBDVStringRef@2@PEAVraw_ostream@2@PEBD_N@Z
    ?AddLiteralOption@cl@llvm@@YAXAEAVOption@12@VStringRef@2@@Z
    ?getGeneralCategory@cl@llvm@@YAAEAVOptionCategory@12@XZ
    ??0Option@cl@llvm@@IEAA@W4NumOccurrencesFlag@12@W4OptionHidden@12@@Z
    ?addArgument@Option@cl@llvm@@QEAAXXZ
    ?addOccurrence@Option@cl@llvm@@UEAA_NIVStringRef@3@0_N@Z
    ?error@Option@cl@llvm@@QEAA_NAEBVTwine@3@VStringRef@3@AEAVraw_ostream@3@@Z
    ??0GenericOptionValue@cl@llvm@@QEAA@XZ
    ?getOptionWidth@generic_parser_base@cl@llvm@@UEBA_KAEBVOption@23@@Z
    ?printOptionInfo@generic_parser_base@cl@llvm@@UEBAXAEBVOption@23@_K@Z
    ?printGenericOptionDiff@generic_parser_base@cl@llvm@@QEBAXAEBVOption@23@AEBUGenericOptionValue@23@1_K@Z
    ?findOption@generic_parser_base@cl@llvm@@QEAAIVStringRef@3@@Z
    ?mallocForGrow@?$SmallVectorBase@I@llvm@@IEAAPEAXPEAX_K1AEA_K@Z
    ?grow_pod@?$SmallVectorBase@I@llvm@@IEAAXPEAX_K1@Z
    ?llvm_shutdown@llvm@@YAXXZ
    ?EnablePrettyStackTrace@llvm@@YAXXZ
    ??0PrettyStackTraceEntry@llvm@@QEAA@XZ
    ??1PrettyStackTraceEntry@llvm@@UEAA@XZ
    ?print@PrettyStackTraceProgram@llvm@@UEBAXAEAVraw_ostream@2@@Z
   ?PrintStackTraceOnErrorSignal@sys@llvm@@YAXVStringRef@2@_N@Z
   ?TableGenMain@llvm@@YAHPEBDV?$function@$$A6A_NAEAVraw_ostream@llvm@@AEBVRecordKeeper@2@@Z@std@@@Z
  )


  foreach(sym ${MSVC_EXPORTLIST_TBLGEN})
    set(MSVC_EXPORTS_TBLGEN "${MSVC_EXPORTS} /EXPORT:${sym}")
  endforeach(sym ${MSVC_EXPORTLIST_TBLGEN})

  set_property(TARGET cppinterop-tblgen APPEND_STRING PROPERTY LINK_FLAGS "${MSVC_EXPORTS_TBLGEN}")

endif()
