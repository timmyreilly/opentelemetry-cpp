

Trying to follow install instructions: 
```
-- Found Threads: TRUE  
CMake Error at /usr/share/cmake-3.16/Modules/FindPackageHandleStandardArgs.cmake:146 (message):
  Could NOT find GTest (missing: GTEST_LIBRARY GTEST_INCLUDE_DIR
  GTEST_MAIN_LIBRARY)
Call Stack (most recent call first):
  /usr/share/cmake-3.16/Modules/FindPackageHandleStandardArgs.cmake:393 (_FPHSA_FAILURE_MESSAGE)
  /usr/share/cmake-3.16/Modules/FindGTest.cmake:205 (FIND_PACKAGE_HANDLE_STANDARD_ARGS)
  CMakeLists.txt:413 (find_package)


-- Configuring incomplete, errors occurred!
See also "/workspaces/opentelemetry-cpp/opentelemetry-cpp/build/CMakeFiles/CMakeOutput.log".
See also "/workspaces/opentelemetry-cpp/opentelemetry-cpp/build/CMakeFiles/CMakeError.log".
```

This is probably what you need: 

`Performing Test CMAKE_HAVE_LIBC_PTHREAD`

https://stackoverflow.com/questions/64514666/what-does-performing-test-cmake-have-libc-pthread-failed-actually-mean

You can go into an interactive session of the docker container 

Get info about your local build environment with `lsb_release -a`

And info about the docker_run.sh interactive environment with cat /etc/os-release

And linux kernal version for both environments: 

`uname -r`

One of the cherished reasonable linux guides: https://www.cyberciti.biz/faq/how-to-check-os-version-in-linux-command-line/ 


Okay all that probably doesn't matter unless you have Bazel. 
https://docs.bazel.build/versions/main/install-ubuntu.html

This worked in the docker container but probably shouldn't...
```
 bazel build examples/simple/main.cc
 ```

...these work and actually do something: 

```sh
bazel build //examples/batch:example_simple
bazel-bin/examples/batch/example_simple

bazel build //examples/grpc/client_grpc
bazel build //examples/grpc/server_grpc

bazel-bin/examples/grpc/server_grpc
bazel-bin/examples/grpc/client_grpc
```


# Trying to run tools now: 

```
$ tools/format.sh 
sed: can't read ./.venv/lib/python3.8/site-packages/setuptools/command/launcher: No such file or directory
sed: can't read manifest.xml: No such file or directory
sed: can't read ./.venv/lib/python3.8/site-packages/setuptools/script: No such file or directory
sed: can't read (dev).tmpl: No such file or directory
```

