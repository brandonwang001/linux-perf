# how to use jemalloc to heap profile

- download the source code from github
- auto autogen.sh --enable-prof
- ./configure
- make
- env LD_PRELOAD=/path/lib/libjemalloc.so.2 env MALLOC_CONF="prof:true,lg_prof_interval:20,prof_leak:true,prof_final:true" ./mybin
