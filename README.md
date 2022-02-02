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

Next, we get OpenCV for C++. Navigate to a desired directory. Now:
```
# Download and unpack sources
wget -O opencv.zip https://github.com/opencv/opencv/archive/4.x.zip
unzip opencv.zip
```
Now, we should have an unzipped folder `.../opencv-4.x` sitting on disk. Mine is at `/home/ktopolov/repos/opencv-4.x`. First, I add a system variable to hold the OPEN_CV path:
```
export OPENCV_PATH="~/repos/opencv-4.x"
```
You can check to ensure this path has been set by using `echo $OPENCV_PATH`, which should print the path out. **Recommend adding this line to `~/.bashrc` file, to ensure this system variable always exists**. 

Next, I configure and build the project using:
```
# Configure
cmake -S $OPENCV_PATH -B "${OPENCV_PATH}/build"

# Build
cmake --build "${OPENCV_PATH}/build"
```
We should now see exetutables in the "${OPENCV_PATH}/build/bin" folder.

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
pip install -r requirements.txt
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
