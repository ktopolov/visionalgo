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
