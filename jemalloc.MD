# how to use jemalloc to heap profile

- download the source code from github
- auto autogen.sh --enable-prof
- ./configure
- make
- env LD_PRELOAD=/path/lib/libjemalloc.so.2 env MALLOC_CONF="prof:true,lg_prof_interval:20,prof_leak:true,prof_final:true"
./mybin
其中：lg_prof_interval:20 为dump间隔，但是size = 2 ^ lg_prof_interval。所以20即为间隔1Mdump一次。
- perl ../../heap_profiler_test/jemalloc/bin/jeprof=--base jeprof.2440335.60.i60.heap ./mybin jeprof.2440335.80.i80.heap
