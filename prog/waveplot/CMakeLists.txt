set(sources-fpp
  gridcache.F90
  initwaveplot.F90
  molorb.F90
  slater.F90
  waveplot.F90)

list(APPEND FYPP_FLAGS -I${CMAKE_SOURCE_DIR}/prog/dftb+/include)

dftbp_preprocess("${FYPP}" "${FYPP_FLAGS}" "F90" "f90" "${sources-fpp}" sources-f90-preproc)

add_executable(waveplot ${sources-f90-preproc})

target_link_libraries(waveplot dftbplus)

install(TARGETS waveplot DESTINATION ${INSTALL_BIN_DIR})
