# Ubuntu machine learning setup

## Installing NVIDIA drive and CUDA toolkit

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update 

sudo apt-get install -y build-essential
sudo apt-get install nvidia-390
sudo apt-get install cuda-nvidia-toolkit
```

## Installing CUDA

```
curl -O https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1604/x86_64/cuda-8-0_8.0.61-1_amd64.deb

sudo dpkg -i cuda-repo-ubuntu1604_8.0.61-1_amd64.deb 
sudo apt-get update
sudo apt-get install -y cuda

```

Set CUDA paths

```
echo "export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}" >> ~/.bashrc
echo "export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64\${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}" >> ~/.bashrc

source ~/.bashrc
```

## Installing CUDNN

Download CUDNN at https://developer.nvidia.com/rdp/cudnn-download.

```
tar xvzf cudnn-8.0-linux-x64-v5.1.tgz 
sudo cp -P cuda/include/cudnn.h /usr/local/cuda-8.0/include
sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda-8.0//lib64
sudo chmod u+w /usr/local/cuda-8.0//include/cudnn.h
sudo chmod a+r /usr/local/cuda-8.0//lib64/libcudnn*
```

## Installing Tensorflow, Keras and OpenCV

```
pip install tensorflow-gpu==1.4 keras opencv-python
```