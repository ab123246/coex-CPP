# CoEx

PyTorch implementation of our paper: 


**Correlate-and-Excite: Real-Time Stereo Matching via Guided Cost Volume Excitation**  
*Authors: [Antyanta Bangunharcana](https://antabangun.github.io/)<sup>1</sup>, Jae Won Cho<sup>2</sup>, Seokju Lee<sup>2</sup>, In So Kweon<sup>2</sup>, Kyung-Soo Kim<sup>1</sup>, Soohyun Kim<sup>1</sup>*  
<sup>1</sup>MSC Lab, <sup>2</sup>RVC Lab, Korea Advanced Institute of Science and Technology (KAIST)  
IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS), 2021

\[[Project page](https://antabangun.github.io/projects/CoEx/)\] | \[[Paper](https://arxiv.org/abs/2304.03560)\]

We propose a Guided Cost volume Excitation (GCE) and top-k soft-argmax disparity regression for real-time and accurate stereo matching. 

# Run CoEx CPP Version
## 	Run the cmake command with respect to absolute path to the PyTorch C++ API
`cmake -DCAFFE2_USE_CUDNN=True -DCMAKE_PREFIX_PATH=/home/Username/libtorch/libtorch ..`

## 	Run the make command
`make`

# Libtorch_install
## 1. Install NVIDIA driver
```
sudo lshw -numeric -C display
sudo apt purge *nvidia*
sudo add-apt-repository ppa:graphics-drivers
sudo apt update
sudo apt upgrade
ubuntu-drivers list
sudo ubuntu-drivers install nvidia:560
```
Prioritize using NVIDIA GPU
`sudo prime-select nvidia`
## 2. Install CUDA
Download CUDA installation runfile
https://developer.nvidia.com/cuda-12-4-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=runfile_local
Download CUDA 12.4
`wget https://developer.download.nvidia.com/compute/cuda/12.4.0/local_installers/cuda_12.4.0_550.54.14_linux.run`
Install
`sudo sh cuda_12.4.0_550.54.14_linux.run`
Add to bashrc
  ```
  ##cuda 12.4
  export PATH=/usr/local/cuda/bin${PATH:+:${PATH}}  
  export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-12.4/lib64/
  export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
  ```
## 3. Install cuDNN
Follow the official website steps directly
Official website:
https://developer.nvidia.com/cudnn-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local
```
  wget https://developer.download.nvidia.com/compute/cudnn/9.4.0/local_installers/cudnn-local-repo-ubuntu2004-9.4.0_1.0-1_amd64.deb
  sudo dpkg -i cudnn-local-repo-ubuntu2004-9.4.0_1.0-1_amd64.deb
  sudo cp /var/cudnn-local-repo-ubuntu2004-9.4.0/cudnn-*-keyring.gpg /usr/share/keyrings/
  sudo apt-get update
  sudo apt-get -y install cudnn
```
Use the following command to verify correct installation
`cat /usr/include/cudnn_version.h | grep CUDNN_MAJOR -A 2`
reference:
https://blog.csdn.net/weixin_45622961/article/details/136636431
## 4. Install cudatoolkit
## 5. Install up to date version of cmake
### Download cmake file and extract
cmake website:
https://cmake.org/download/
### Make file and install
`make ./configure`
`make -j8`
`sudo make install`
reference:
https://blog.csdn.net/qq21497936/article/details/141933927
## Run the cmake command with respect to absolute path to the PyTorch C++ API
`cmake -DCAFFE2_USE_CUDNN=True -DCMAKE_PREFIX_PATH=/home/Username/libtorch/libtorch ..`
## Run the make command
`make`
## Run the code
`./main`
