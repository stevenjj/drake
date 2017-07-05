# Branch Fork Notes
This branch starts at the tag I added called `working_examples` which tags the last known commit where the drake examples are still present.

## My Installation Notes
````
1.Perform preliminary steps:

sudo apt-get remove ros-indigo-octomap ros-indigo-fcl

sudo apt-get install ros-indigo-ackermann-msgs

Make a catkin workspace:
mkdir -p ~/dev/drake_catkin_workspace/src

cd ~/dev/drake_catkin_workspace/src
#git clone drake:

git clone https://github.com/RobotLocomotion/drake.git

ln -s drake/ros drake_ros_integration

git checkout a36882f98479d9c7bbdb70192534923ecfbf5dcf

2. Install Drake dependencies (trusty) http://drake.mit.edu/ubuntu_trusty.html#build-from-source-trusty

GCC 4.9:

sudo add-apt-repository -y ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install g++-4.9-multilib gfortran-4.9 gfortran

Clang 3.9:

sudo apt-get install --no-install-recommends lsb-core software-properties-common wget
wget -q -O - http://llvm.org/apt/llvm-snapshot.gpg.key | sudo apt-key add -
sudo add-apt-repository -y "deb http://apt.llvm.org/trusty/ llvm-toolchain-trusty-3.9 main"
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install clang-3.9 gfortran

CMake

CMake 3.5 or higher is required. Visit the CMake Download Page to obtain the CMake 3.5 pre-compiled binaries. Extract the archive and add its bin directory to the PATH environment variable. For example, below is a suggested sequence of commands that installs CMake 3.5 into ~/tools/ and then modifies ~/.bashrc with the new PATH environment variable:

mkdir -p ~/tools
cd ~/tools
wget https://cmake.org/files/v3.5/cmake-3.5.2-Linux-x86_64.tar.gz
tar zxvf cmake-3.5.2-Linux-x86_64.tar.gz
rm cmake-3.5.2-Linux-x86_64.tar.gz
cd cmake-3.5.2-Linux-x86_64/bin
echo "export PATH=`pwd`:\$PATH" >> ~/.bashrc

Bazel

wget https://github.com/bazelbuild/bazel/releases/download/0.4.3/bazel_0.4.3-linux-x86_64.deb
echo "0cd6592ac2c5548d566fa9f874a386737e76029f5aabe1f04f8320173a05280d bazel_0.4.3-linux-x86_64.deb" > bazel_0.4.3-linux-x86_64.deb.sha256
sha256sum --check bazel_0.4.3-linux-x86_64.deb.sha256 && sudo dpkg -i bazel_0.4.3-linux-x86_64.deb


Add to ~/.bashrc:

export CC=clang-3.9 CXX=clang++-3.9 FC=gfortran-4.9


Reopen a new terminal


Useful CMAKE flag: -DDISABLE_MATLAB=TRUE

cd ~/dev/drake_catkin_workspace
source /opt/ros/indigo/setup.bash
catkin init
catkin config --cmake-args -DCMAKE_BUILD_TYPE:STRING=RelWithDebInfo -DDISABLE_MATLAB=TRUE
catkin build

````

# Drake

Drake is a toolbox maintained by the Robot Locomotion Group at the MIT Computer Science and Artificial Intelligence Lab (CSAIL). It is a collection of tools for analyzing the dynamics of our robots and building control systems for them in MATLAB and C++, with a heavy emphasis on optimization-based design/analysis.

Please see the github wiki at http://drake.mit.edu for detailed documentation.

====

License:      BSD  (https://raw.github.com/RobotLocomotion/drake/master/LICENSE.TXT)

