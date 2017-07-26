# Welcome to the Ubuntu16.04 Setting wiki!
**The GPU-enabled version of TensorFlow has the following requirements:  
64-bit Linux  
Python 3.5  
CUDA 8.0 (CUDA 8.0 required for Pascal GPUs)  
cuDNN v5.1**  

# Nvidia driver install  
sudo add-apt-repository ppa:graphics-drivers/ppa  
sudo apt update  
sudo apt-get install nvidia-375  
reboot  
**(i dont know why latest ver driver dont match cudnn v5.1)**  

# Nvidia Tool kit install  
**at first you need to install Cuda toolkit  
Select Linux, x86_64, Ubuntu, 16.04, deb (local).  
Navigate to https://developer.nvidia.com/cuda-downloads.**  
cd Downloads/  
sudo dpkg -i cuda-repo-ubuntu1604-8-0-local-ga2_8.0.61-1_amd64.deb  
sudo apt-get update  
sudo apt-get install cuda  
  
export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}  
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64\${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}  

# Check Nvidia  
cd /usr/local/cuda-8.0/samples/5_Simulations/nbody  
sudo make  
./nbody  

# Cudnn download 
**Once the CUDA Toolkit is installed, download cuDNN v5.1 Library for Linux and install by following the official documentation. (Note: You will need to register for the Accelerated Computing Developer Program).  
Steps for cuDNN v5.1 for quick reference as follow:  
Once downloaded, navigate to the directory containing cuDNN:**  
  
cd Downloads/  
tar -xzvf cudnn-8.0-linux-x64-v5.1.tgz  
sudo cp cuda/include/cudnn.h /usr/local/cuda/include  
sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64  
sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*  

# install tensorflow
sudo apt-get install libcupti-dev  
sudo python get-pip.py  
sudo apt-get update && sudo apt-get -y upgrade  
sudo apt-get install python-pip  
sudo apt-get install python-pip python-dev  
sudo apt-get install python3-pip python3-dev  
pip3 install tensorflow-gpu  
pip install --upgrade pip  
  
# Check Tensorflow 
python3  
**(Python code)**  
import tensorflow as tf  
hello = tf.constant('Hello, TensorFlow!')  
sess = tf.Session()  
print(sess.run(hello))  
  
# install CNTK  
**result of many and many install(lol), binary script installation is the best way.  
https://docs.microsoft.com/en-us/cognitive-toolkit/setup-linux-binary-script**  
  
**Step 1: Download the appropriate binary package from CNTK Releases page. Unpack the tar.  
Note: Choose a GPU binary download only if your machine has an NVidia GPU.**  
   
**Step 2: Run bash Installation script  
Below we assume that you have unpacked the CNTK Binary package to /home/username. Please use the following commands,   depending on your preferred CNTK Python version**  
  
cd /home/username/cntk/Scripts/install/linux  
./install-cntk.sh  
  
# check CNTK  
source "/home/username/cntk/activate-cntk"  
cd cntk/Tutorials/  
NumpyInterop/FeedForwardNet.py  
