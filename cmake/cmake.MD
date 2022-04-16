# Upgrade / Install Cmake

#### Update your system
```
$ sudo apt update
```

#### Make sure your in your home directory
```
$ cd $HOME
```

#### Check current cmake version
```
$ cmake --version
```


#### Remove current cmake
```
$ sudo apt remove --purge cmake
$ hash -r
```

#### depends
```
$ sudo apt install g++ make
$ sudo apt install build-essential libssl-dev
```
#### Installing CMake
```
$ wget https://github.com/Kitware/CMake/releases/download/v3.23.1/cmake-3.23.1.tar.gz
$ tar -zxvf cmake-3.23.1.tar.gz
$ cd cmake-3.23.1
$ ./bootstrap
$ make
$ sudo make install
```

### check version
$ cmake --version

#### Cleanup
$ sudo $HOME
$ rm -rf cmake-3.23.1
$ rm cmake-3.23.1.tar.gz

###### END OF DOCUMENT
