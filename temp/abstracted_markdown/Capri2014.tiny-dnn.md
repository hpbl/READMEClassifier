@abstr_image   
  


* * *

@abstr_hyperlink @abstr_hyperlink @abstr_hyperlink @abstr_hyperlink 

**tiny-dnn** is a C++ @abstr_number implementation of deep learning. It is suitable for deep learning on limited computational resource, embedded systems and IoT devices.

| **`Linux/Mac OS`** | **`Windows`** | |------------------|-------------| | @abstr_hyperlink | @abstr_hyperlink |

## Table of contents

  * Features
  * Comparison with other libraries
  * Supported networks
  * Dependencies
  * Build
  * Examples
  * Contributing
  * References
  * License
  * Gitter rooms



Check out the @abstr_hyperlink for more info.

## What's New

  * @abstr_number / @abstr_number / @abstr_number @abstr_hyperlink 
  * @abstr_number / @abstr_number / @abstr_number @abstr_hyperlink 
  * @abstr_number / @abstr_number / @abstr_number tiny-dnn is now moved to organization account, and rename into tiny-dnn :)
  * @abstr_number / @abstr_number / @abstr_number @abstr_hyperlink 



## Features

  * reasonably fast, without GPU 
    * with TBB threading and SSE/AVX vectorization
    * @abstr_number . @abstr_number % accuracy on MNIST in @abstr_number minutes training (@Core i @abstr_number - @abstr_number M)
  * portable & header-only 
    * Run anywhere as long as you have a compiler which supports C++ @abstr_number 
    * Just include tiny_dnn.h and write your model in C++. There is nothing to install.
  * easy to integrate with real applications 
    * no output to stdout/stderr
    * a constant throughput (simple parallelization model, no garbage collection)
    * work without throwing an exception
    * @abstr_hyperlink 
  * simply implemented 
    * be a good library for learning neural networks



## Comparison with other libraries

Please see @abstr_hyperlink .

## Supported networks

### layer-types

  * core 
    * fully-connected
    * dropout
    * linear operation
    * power
  * convolution 
    * convolutional
    * average pooling
    * max pooling
    * deconvolutional
    * average unpooling
    * max unpooling
  * normalization 
    * contrast normalization (only forward pass)
    * batch normalization
  * split/merge 
    * concat
    * slice
    * elementwise-add



### activation functions

  * tanh
  * sigmoid
  * softmax
  * rectified linear(relu)
  * leaky relu
  * identity
  * exponential linear units(elu)



### loss functions

  * cross-entropy
  * mean squared error
  * mean absolute error
  * mean absolute error with epsilon range



### optimization algorithms

  * stochastic gradient descent (with/without L @abstr_number normalization and momentum)
  * adagrad
  * rmsprop
  * adam



## Dependencies

Nothing. All you need is a C++ @abstr_number compiler.

## Build

tiny-dnn is header-only, so _there's nothing to build_. If you want to execute sample program or unit tests, you need to install @abstr_hyperlink and type the following commands:

@abstr_code_section 

Then open .sln file in visual studio and build(on windows/msvc), or type `make` command(on linux/mac/windows-mingw).

Some cmake options are available:

|options|description|default|additional requirements to use| |-----|-----|----|----| |USE_TBB|Use @abstr_hyperlink for parallelization|OFF @abstr_number | @abstr_hyperlink | |USE_OMP|Use OpenMP for parallelization|OFF @abstr_number | @abstr_hyperlink | |USE_SSE|Use Intel SSE instruction set|ON|Intel CPU which supports SSE| |USE_AVX|Use Intel AVX instruction set|ON|Intel CPU which supports AVX| |USE_AVX @abstr_number |Build tiny-dnn with AVX @abstr_number library support|OFF|Intel CPU which supports AVX @abstr_number | |USE_NNPACK|Use NNPACK for convolution operation|OFF| @abstr_hyperlink | |USE_OPENCL|Enable/Disable OpenCL support (experimental)|OFF| @abstr_hyperlink | |USE_LIBDNN|Use Greentea LinDNN for convolution operation with GPU via OpenCL (experimental)|OFF| @abstr_hyperlink | |USE_SERIALIZER|Enable model serialization|ON @abstr_number |-| |USE_DOUBLE|Use double precision computations instead of single precision|OFF|-| |USE_ASAN|Use Address Sanitizer|OFF|clang or gcc compiler| |USE_IMAGE_API|Enable Image API support|ON|-| |USE_GEMMLOWP|Enable gemmlowp support|OFF|-| |BUILD_TESTS|Build unit tests|OFF @abstr_number |-| |BUILD_EXAMPLES|Build example projects|OFF|-| |BUILD_DOCS|Build documentation|OFF| @abstr_hyperlink | |PROFILE|Build unit tests|OFF|gprof|

@abstr_number  tiny-dnn use c++ @abstr_number standard library for parallelization by default

@abstr_number  If you don't use serialization, you can switch off to speedup compilation time.

@abstr_number  tiny-dnn uses @abstr_hyperlink as default framework to run unit tests. No pre-installation required, it's automatically downloaded during CMake configuration.

For example, type the following commands if you want to use intel TBB and build tests: @abstr_code_section 

## Customize configurations

You can edit include/config.h to customize default behavior.

## Examples

construct convolutional neural networks

@abstr_code_section construct multi-layer perceptron(mlp)

@abstr_code_section 

another way to construct mlp

@abstr_code_section 

more sample, read examples/main.cpp or @abstr_hyperlink page.

## Contributing

Since deep learning community is rapidly growing, we'd love to get contributions from you to accelerate tiny-dnn development! For a quick guide to contributing, take a look at the Contribution Documents.

## References

[ @abstr_number ] Y. Bengio, @abstr_hyperlink arXiv: @abstr_number . @abstr_number v @abstr_number , @abstr_number 

[ @abstr_number ] Y. LeCun, L. Bottou, Y. Bengio, and P. Haffner, @abstr_hyperlink Proceedings of the IEEE, @abstr_number , @abstr_number - @abstr_number .

other useful reference lists: \- @abstr_hyperlink \- @abstr_hyperlink 

## License

The BSD @abstr_number -Clause License

## Gitter rooms

We have a gitter rooms for discussing new features & QA. Feel free to join us!

**developers** |  https://gitter.im/tiny-dnn/developers   
---|---  
**users** |  https://gitter.im/tiny-dnn/users 
