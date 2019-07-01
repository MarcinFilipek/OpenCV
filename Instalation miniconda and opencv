#Instalation OpenCV on Raspberry

##Instalacja Miniconda3:

####Instalation conda and add to PATH
cd ~
mkdir Miniconda3
cd Miniconda3
wget http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-armv7l.sh
bash Miniconda3-latest-Linux-armv7l.sh
sudo reboot now

####Need to update python
conda config --add channels conda-forge
conda config --add channels rpi
conda install openblas blas

####Create env with python 3.6
conda create -n uczenie python

####Install numpy
conda install numpy


##Instalacja opencv

####Update
sudo apt-get update
sudo apt-get upgrade
sudo rpi-update

####Dependencies
sudo apt-get install build-essential cmake pkg-config
sudo apt-get install libjpeg-dev libtiff5-dev libjasper-dev libpng12-dev
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
sudo apt-get install libxvidcore-dev libx264-dev
sudo apt-get install libgtk2.0-dev libgtk-3-dev
sudo apt-get install libatlas-base-dev gfortran

####Download opencv
cd ~
wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.4.1.zip
wget -O opencv_contrib.zip https://github.com/Itseez/opencv_contrib/archive/3.4.1.zip
unzip opencv.zip
unzip opencv_contrib.zip

####Build OpenCV
cd ~/opencv-3.4.1/
mkdir build
cd build

####Create start.sh
nano start.sh

================================================start.sh===================================================
PYTHON_DIR=~/miniconda3/envs/uczenie
CONTRIB_DIR=~/opencv_contrib-3.4.1

echo '**Going to do: cmake**'
cmake -D CMAKE_BUILD_TYPE=RELEASE \
	-D CMAKE_INSTALL_PREFIX=/usr/local \
	-D PYTHON3_EXECUTABLE=${PYTHON_DIR}/bin/python3.6 \
	-D PYTHON3_LIBRARY=${PYTHON_DIR}/lib/libpython3.6m.so.1.0 \
	-D PYTHON3_INCLUDE_DIR=${PYTHON_DIR}/include/python3.6m \
	-D PYTHON3_NUMPY_INCLUDE_DIRS=${PYTHON_DIR}/lib/python3.6/site-packages/numpy/core/include/numpy \
	-D PYTHON3_PACKAGES_PATH=${PYTHON_DIR}/lib/python3.6/site-packages \
	-D OPENCV_EXTRA_MODULES_PATH=${CONTRIB_DIR}/modules \
	-D BUILD_opencv_python3=ON ..
	
============================================================================================================

chmod +x start.sh
./start.sh

####Compile and install (Raspberry 2B - Time compilation: 7h)

make
sudo make install
sudo ldconfig
