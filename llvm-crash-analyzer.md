## Original Paper:  https://cs.brown.edu/people/vpk/papers/retracer.icse16.pdf
Run 'wget https://cs.brown.edu/people/vpk/papers/retracer.icse16.pdf' to download the paper.

## LLVM Crash Analyzer Open Source Repository:
https://github.com/cisco-open/llvm-crash-analyzer

## Port to 18.1.7
The patches have been ported to llvm version 18.1.7 and is available here:
git clone git@github.com:bharsesh/llvm-crash-analyzer.git

## Steps to build llvm-crash-analyzer
git clone git@github.com:bharsesh/llvm-crash-analyzer.git
cd llvm-crash-analyzer
git checkout llvm-18.1.7-crash-analyzer-port
mkdir build
cd build
export CC=/auto/binos-tools/llvm18/llvm-18.0-p2/bin/clang
export CXX=/auto/binos-tools/llvm18/llvm-18.0-p2/bin/clang++
/auto/binos-tools/llvm40/tools/cmake_326/bin/cmake -G "Ninja" -DLLVM_ENABLE_PROJECTS="clang;lldb;llvm-crash-analyzer" -DLLVM_ENABLE_LIBCXX=ON ../llvm -DLLDB_TEST_COMPILER=$CC -DCMAKE_BUILD_TYPE=Release -DCMAKE_C_COMPILER=$CC -DCMAKE_CXX_COMPILER=$CXX -DLLVM_ENABLE_ASSERTIONS=ON
nohup /auto/binos-tools/llvm40/tools/ninja/ninja -j8 >& bld.log
nohup /auto/binos-tools/llvm40/tools/ninja/ninja -j8  check-llvm-crash-analyzer >& test.log

See also README.md

