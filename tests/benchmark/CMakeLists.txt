add_executable(benchmarks
  main.cc
  benchmark_helpers.cc
  benchmark_helpers.h
  counter_bench.cc
  gauge_bench.cc
  histogram_bench.cc
  registry_bench.cc
  summary_bench.cc
)

target_link_libraries(benchmarks PRIVATE prometheus-cpp)
target_include_directories(benchmarks PRIVATE ${PROJECT_SOURCE_DIR}) # fixme

target_link_libraries(benchmarks PRIVATE Google::Benchmark)

add_test(NAME benchmarks COMMAND $<TARGET_FILE:benchmarks>)
