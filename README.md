# TensorFlow Lite Object Detection Android Demo
### Overview
This is a camera app that continuously detects the objects (bounding boxes and classes) in the frames seen by your device's back camera, using a quantized [MobileNet SSD](https://github.com/tensorflow/models/tree/master/research/object_detection) model trained on the [COCO dataset](http://cocodataset.org/). These instructions walk you through building and running the demo on an Android device.

The model files are downloaded via Gradle scripts when you build and run. You don't need to do any steps to download TFLite models into the project explicitly.

Application can run either on device or emulator.

<!-- TODO(b/124116863): Add app screenshot. -->

## Build the demo using Android Studio

### Prerequisites

* If you don't have already, install **[Android Studio](https://developer.android.com/studio/index.html)**, following the instructions on the website.

* You need an Android device and Android development environment with minimum API 21.
* Android Studio 3.2 or later.

### Building
* Open Android Studio, and from the Welcome screen, select Open an existing Android Studio project.

* From the Open File or Project window that appears, navigate to and select the tensorflow-lite/examples/object_detection/android directory from wherever you cloned the TensorFlow Lite sample GitHub repo. Click OK.

* If it asks you to do a Gradle Sync, click OK.

* You may also need to install various platforms and tools, if you get errors like "Failed to find target with hash string 'android-21'" and similar.
Click the Run button (the green arrow) or select Run > Run 'android' from the top menu. You may need to rebuild the project using Build > Rebuild Project.

* If it asks you to use Instant Run, click Proceed Without Instant Run.

* Also, you need to have an Android device plugged in with developer options enabled at this point. See **[here](https://developer.android.com/studio/run/device)** for more details on setting up developer devices.


### Model used
Downloading, extraction and placing it in assets folder has been managed automatically by download.gradle.

If you explicitly want to download the model, you can download from **[here](http://storage.googleapis.com/download.tensorflow.org/models/tflite/coco_ssd_mobilenet_v1_1.0_quant_2018_06_29.zip)**. Extract the zip to get the .tflite and label file.

### Additional Note
_Please do not delete the assets folder content_. If you explicitly deleted the files, then please choose *Build*->*Rebuild* from menu to re-download the deleted model files into assets folder.


Working with Tensorflow Requires Several numerous step as:

Setting up Environment and installation of required Softwares, libraries, packages depending on operating system is used.(preferred ubuntu).

Once We are done with setting up our tool we need to gather data(images of object) that is needed to be detected.

After Gathering required images each image is labeled i.e where our required object lies and respective XML file is generated.

Then data set is split into two parts training data(75-80%) and test data(20-25%) of images.

Afterwards train and test data.csv files are generated then that needs to be read by algorithm for training.

Then we are good to start training but first we need to find out best suited Algorithm for our purpose, mainly used algorithms are SSD , RCNN , YOLO (each one further contains subtypes with having different features,accuracy and computational speed etc respectively). Aside to that only SSD models are supported by tensorflow for mobile support rest can work with laptops and computers only.
Then we start training and training may take different time depending upon algorithm used.

Once training is completed we generate inference graph and graph.pb file.

Graph.pb file is then further converted to file with “.tflite” format which is then used in android and ios for real time detection.
After generating that file i copied that file into assets of tensorflow sample app and changed labelmap file text according to my detetion
