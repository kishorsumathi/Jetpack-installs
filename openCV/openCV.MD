# OpenCV

#### Update your system
```
$ sudo apt update
```
#### set CUDA location
```
$ sudo sh -c "echo '/usr/local/cuda/lib64' >> /etc/ld.so.conf.d/nvidia-tegra.conf"
$ sudo ldconfig
```

#### Install dependencies
Altinstall of python - if you have installed a version of python that did not come with jetpack you must install numpy and pip VIA the python version you installed. Change version number to fit your needs.

***Skip this command if your using jetpack's python and have not installed another python version.***
```
$ sudo -H python3.9 -m pip install numpy --upgrade numpy
$ sudo -H python3.9 -m pip install --upgrade pip
```
The rest of the dependencies can be installed with apt.
```
$ sudo apt install build-essential cmake git unzip pkg-config zlib1g-dev \
libjpeg-dev libjpeg8-dev libjpeg-turbo8-dev \
libpng-dev libtiff-dev libglew-dev \
libavcodec-dev libavformat-dev libswscale-dev \
libgtk2.0-dev libgtk-3-dev libcanberra-gtk* \
python-dev python-numpy python-pip \
python3-dev python3-numpy python3-pip \
libxvidcore-dev libx264-dev libgtk-3-dev \
libtbb2 libtbb-dev libdc1394-22-dev libxine2-dev \
gstreamer1.0-tools libgstreamer-plugins-base1.0-dev \
libgstreamer-plugins-good1.0-dev \
libv4l-dev v4l-utils v4l2ucp qv4l2 \
libtesseract-dev libxine2-dev libpostproc-dev \
libavresample-dev libvorbis-dev \
libfaac-dev libmp3lame-dev libtheora-dev \
libopencore-amrnb-dev libopencore-amrwb-dev \
libopenblas-dev libatlas-base-dev libblas-dev \
liblapack-dev liblapacke-dev libeigen3-dev gfortran \
libhdf5-dev libprotobuf-dev protobuf-compiler \
libgoogle-glog-dev libgflags-dev -y
```












```
$ sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev libsqlite3-dev wget libbz2-dev
```
#### Make sure your in your home directory
```
$ cd $HOME
```
#### Download Python
Copy the url to the python version you want to install ---> https://www.python.org/downloads/source/

I will be using Python3.9.12 for this guide. Change the link to the version you want if diffrent
```
$ wget https://www.python.org/ftp/python/3.9.12/Python-3.9.12.tgz
```
#### Extract tar
If you have used a different version change ***Python-3.9.12.tgz*** to the version you download
```
$ tar -xf Python-3.9.12.tgz
```
#### Move into dir of extracted tar
If you have used a different version change ***Python-3.9.12*** to the version you download
```
$ cd Python-3.9.12
```
#### Configure Python
```
$ ./configure --enable-optimizations
```
#### Run make with all cores
```
$ make -j $(nproc)
```
#### Install Python
```
$ sudo -H make altinstall
```
### Check that Python installed
If you have used a different version change ***python3.9*** to the version you download
```
python3.9 -c 'import sys; print(sys.version)'
```

#### Clean up after install
If you have used a diffrent version change ***Python-3.9.12*** and ***Python-3.9.12.tgz*** to the version you download
```
$ sudo rm -r Python-3.9.12 && rm Python-3.9.12.tgz
```


# update-alternatives pointing to python

Right now if you or some script tries to use python3 from the command line it will default to the version that came with jetpack. This is fine if you want to call your altinstall of python every time with ***python3.9*** or the version you installed.

Also pip3 will also default to the jetpack version of python3.
```
$ pip3 --version
```
To avoid this you can call pip from python3.9 like so.
```
$ python3.9 -m pip --version
```

However you can fix this behavior with update-alternatives

#### Pointing python3 to python version you installed using update-alternatives
```
$ sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 0
$ sudo update-alternatives --install /usr/bin/python3 python3 /usr/local/bin/python3.9 1
```

Note: if you messed up and need to remove an alturnative ***$ sudo update-alternatives --remove python3 /usr/local/bin/python3.9***

#### configure (select the one you want to have priority, make it auto)
$ sudo update-alternatives --config python3

Now check that pip3 version is working with python3.9 as build scripts can call on pip3, its BAD but it happens.
```
$ pip3 --version
```

However ***Best Practace*** is to always use python -m to use pip for that python version
```
$ python3.9 -m pip --version
```
# Upgrade all pip versions
```
$ python -m pip install --upgrade pip
$ python3.6 -m pip install --upgrade pip
$ python3.9 -m pip install --upgrade pip
```

###### END OF DOCUMENT
