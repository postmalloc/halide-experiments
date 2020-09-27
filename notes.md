1. Download the binary from https://github.com/halide/Halide/releases
2. Do `/usr/bin/g++-9 hello.cpp -g -I Halide-10.0.0-x86-64-linux/include -L Halide-10.0.0-x86-64-linux/lib -lHalide -lpthread -ldl -o hello -std=c++11`  
   Note: Does not seem to work with g++-4.8
3. Include the shared libraries  
   `export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/home/linpup/lab/halide-exp/Halide-10.0.0-x86-64-linux/lib`
4. There are multiple versions of libjpeg on my machine, so the image io helpers
   don't seem to work. I just passed `-DHALIDE_NO_JPEG` flag and used png images.
   e.g. ```/usr/bin/g++-9 sobel.cpp -g -I Halide/tools -lHalide `libpng-config --cflags --ldflags` -ljpeg -lpthread -ldl -DHALIDE_NO_JPEG -o sobel -std=c++11```
5. Compiling from source took about 10 minutes, and I installed it directly to
   `/usr/local`
6. The meta-programming feels a lot like programming in tensorflow. You first
   build the pipeline, then `realize` it.