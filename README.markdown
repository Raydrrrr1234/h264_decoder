# Simple H264 Decoder

This is a simple C++ h264 stream decoder. It is quite fast and more importantly, does not require any other libs to compile/use. The idea is to be easy to use and import to your project, without all the problems of seting up a larger lib like ffstream, gstreamer or libvlc. You just need to compile, add the Decoder.h header (which contains all the interface that you need) and link the libmeerkat_h264_decoder lib.

The idea came from a project that imported the h264 decoder to JavaScript called [Broadway][Broadway_site], which is quite amazing. They used the decoder code from the [Android project][Android_src], but they did an abstraction layer on top (you'll see on all the functions calls that start with broadway). We've used this abstraction layer to make things even easier, but with some small changes for our purpose.

We also added a python wrapper for this lib, which is quite easy to use and (not so much to) compile. However you'll need OpenCV 3.1, Boost and Python 3. We used some code of [pyboostcvconverter][pyboost_git] and [numpy-opencv-converter][numpy_cv], but also had to do some manual changes to fix some memory leak problems when using it with OpenCV 3.0.

Hope you like it :)

[Meerkat team][Meerkat_site]


### Warnings

This was done on a real tight deadline, so it is quite possible that you find some problems/limitations when using this code. We encourage you to open a new Issue relating your problems, so that everyone will be aware of. And better yet, you may do a pull request.

If you submit a pull request, please try to follow the code style of each particular file. There are code in here that originated from several repositories/authors, but we don't think it is a good idea to mix different coding styles in the same file.


### Compilation

To compile the main lib:

```sh
$ mkdir build
$ cd build
$ cmake ..
$ make
```

To compile the test program (it needs OpenCV to generate a RGB image and plot on the screen):

```sh
$ cd test
$ mkdir build
$ cd build
$ cmake ..
$ make
```

Usage example:

```sh
$ ./h264_test ../../data/video_full.avi
```

[Broadway_site]: <https://github.com/mbebenita/Broadway>
[Android_src]: <https://android.googlesource.com/platform/frameworks/av/+/master/media/libstagefright/codecs/on2/h264dec/>
[Meerkat_site]: <http://www.meerkat.com.br/?setLng=en-US>
[pyboost_git]: <https://github.com/Algomorph/pyboostcvconverter>
[numpy_cv]: <https://github.com/spillai/numpy-opencv-converter>