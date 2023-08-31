# sawForceDimensionSDKROS2

ROS 2 node for sawForceDimensionSDK (https://github.com/jhu-saw/sawForceDimensionSDK).

## Dependencies

First install dependencies for cisst/SAW:
```sh
sudo apt install python3-vcstool python3-colcon-common-extensions libxml2-dev libraw1394-dev libncurses5-dev libncurses5 qtcreator swig sox espeak cmake-curses-gui cmake-qt-gui git subversion gfortran libcppunit-dev libqt5xmlpatterns5-dev
```

You will also need to download and unzip the ForceDimension SDK from the vendor.  See README in https://github.com/jhu-saw/sawForceDimensionSDK.

## ROS build

You can use the ROS 2 VCS python-based tool (`sudo apt install python3-vcstool`) to download all the cisst, sawForceDimensionSDK and ROS 2 specific packages needed for the sawForceDimensionSDK ROS 2 node.  Look for the `.repos` file in this repository and find the link to the raw content.  Then in your ROS 2 workspace, under the `src` directory, use:
```sh
vcs import --input https://raw.githubusercontent.com/jhu-saw/sawForceDimensionSDKROS2/master/force_dimension_sdk.repos
```
Then go back to the root of your ROS 2 workspace and build using:
```sh
colcon build
```

:warning: After you ran `colcon build` once, you will need to use `ccmake` or `cmake-gui` on the build tree for sawForceDimensionSDK.  for ``ccmake``, do:
```sh
  cd ~/ros2_ws/build/sawForceDimensionSDKAll # or whatever your workspace is
  ccmake .
```

In CMake, find the variable `force_dimension_sdk` and set it to point to the ForceDimension SDK you should have already downloaded (see README in https://github.com/jhu-saw/sawForceDimensionSDK).

You will then need to rerun `colcon build` now that CMake knows where the ForceDimension SDK is.

## Using the ROS2 node

Once the code is compiled, you can start the ROS 2 ForceDimension node using:
```
ros2 run force_dimension_sdk force_dimension_sdk
```
