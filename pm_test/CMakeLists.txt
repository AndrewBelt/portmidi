# CMake file to build tests in this directory: pm_test

if(WIN32)
include(../pm_win/static.cmake)
endif(WIN32)

macro(make_a_test name)
  add_executable(test_${name} ${name}.c)
  target_link_libraries(test_${name} portmidi-static ${PM_NEEDED_LIBS})
  add_dependencies(test_${name} portmidi-static)
endmacro(make_a_test)

make_a_test(test)
make_a_test(midithread)
make_a_test(midithru)
make_a_test(sysex)
make_a_test(latency)
make_a_test(mm)
make_a_test(midiclock)
make_a_test(qtest)
make_a_test(fast)
