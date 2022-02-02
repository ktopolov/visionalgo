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
sudo apt install -y g++ cmake make wget unzip git
```

# Building  
The C++ portion of the project uses `CMake` to generate Makefile, and then `make` to build the project. It is useful to use the following aliases:  
  
```  
alias run_cmake='cmake -S <PATH_TO_REPO>/c++ -B <PATH_TO_REPO>/c++/build'
alias run_make='make -C <PATH_TO_REPO>/DatabaseSystem/c++/build'
```  
The first command generates the makefile in the `<PATH_TO_REPO>/c++/build` directory. The second navigates to that directory and buiolds the project.  
  
TODO: ADD MORE INFO
