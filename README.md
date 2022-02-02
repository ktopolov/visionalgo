# visionalgo
Vision algorithms using computer vision and machine learning techniques. This project is a multi-language project, based mainly in C++ and Python.
  
# Getting Started
## Dependencies
This will all be Linux-based. 
```
# Update and upgrade packages
sudo apt-get -y update
sudo apt-get -y upgrade
```

First, we install the barebones dependencies:
```
sudo apt install -y g++ cmake make wget unzip git python3.8
```

Next, we get OpenCV for C++. For this, we also need some more dependencies:
```
# Compiler
sudo apt-get install build-essential

# Required
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev

# Optional (if one does not install, omit it and install the rest)
sudo apt-get install libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
```

Now, pull the latest OpenCV repo and the latest contrib repo:
```
cd ~/<my_working_directory>
git clone https://github.com/opencv/opencv.git
git clone https://github.com/opencv/opencv_contrib.git
```

Build:
```
# Make build folder
cd ~/opencv
mkdir build
cd build

# Configure project
cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local ..

# Build
make -j7 # runs 7 jobs in parallel; run as many jobs as you have cores if desired

# Install
sudo make install  # this installs libraries to your machine so you can link them
```

To verify that install worked properly, try:
```
$  pkg-config opencv --cflags 

# Output should be:
-I/usr/local/include/opencv -I/usr/local/include


$  pkg-config opencv --libs 

# Output should be
/usr/local/lib/libopencv_calib3d.so /usr/local/lib/libopencv_contrib.so /usr/local/lib/libopencv_core.so /usr/local/lib/libopencv_features2d.so /usr/local/lib/libopencv_flann.so /usr/local/lib/libopencv_gpu.so /usr/local/lib/libopencv_highgui.so /usr/local/lib/libopencv_imgproc.so /usr/local/lib/libopencv_legacy.so /usr/local/lib/libopencv_ml.so /usr/local/lib/libopencv_nonfree.so /usr/local/lib/libopencv_objdetect.so /usr/local/lib/libopencv_photo.so /usr/local/lib/libopencv_stitching.so /usr/local/lib/libopencv_ts.so /usr/local/lib/libopencv_video.so /usr/local/lib/libopencv_videostab.so
```
If these look good, move forward. We will test later whether OpenCV can be found by tests in our repo.

## Clone Repo
Clone the repository with SSH using:
```
git clone git@github.com:ktopolov/visionalgo.git
```
This will give you a `visionalgo/` folder located at the current working directory. We will call the path to the repo `<path-to--visionalgo>`.

## Create Python Virtual Environment
You should have installed `python 3.8` in the previous step. To ensure this was done, use `python --version`. This should print out something like:
```
(base) ktopolov@DESKTOP-4RQJPCR:~/venvs$ python --version
Python 3.8.8
```
Notice the (base) next to my name. This is the active environment. Run:
```
python -m venv <desired-venv-path>
```
If the previous step showed a Python version other than 3.8, simply find the `python.exe` located inside of the Python 3.8 install location, and replace the previous command with:
```
<path-to-python3.8install>/bin/python -m venv <desired-venv-path>
```
Now, we have a virtual environment. Activate it using:
```
source <desired-venv-path>/bin/activate
```
Likely you want to either add that command to your `~/.bashrc`, or add an alias for it, to setup your dev environment whenever working this project.

Lastly, we need a one-time install of the Python packages required for the project. Running `pip --version` should show that you have a `pip` package installer located inside of your newly-created virtual environment. The `<path-to-visionalgo>/python` folder contains a `requirements.txt` file listing all Python package dependencies needed for the project.

*  Prior to installing, you should see that `pip list` shows that a very minimal list of Python packahges are installed in the environment.
*  To install required packages, simply run (while your venv is activated):
```
pip install -r <path-to-visionalgo>/python/requirements.txt
```
*  After this completes, you should be able to see that `pip list` shows all of the downloaded packages.

# Building  
The C++ portion of the project uses `CMake` to build the project. To configure the project (only need to run either for first time OR if project structure changes, new folder added, etc.), run:
```
cmake -S <PATH_TO_REPO>/c++ -B <PATH_TO_REPO>/build
```
To build the project, which should be done any code is modified, run:
```
cmake --build <PATH_TO_REPO>/build
```
Now, you should have compiled executables located in the `<PATH_TO_REPO>/build` folder. For ease, use aliases like these:
```  
alias vision-configure='cmake -S <PATH_TO_REPO>/c++ -B <PATH_TO_REPO>/build'
alias vision-build='cmake --build <PATH_TO_REPO>/build'
``` 
