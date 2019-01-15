# MachineSetupPains
Some notes on the usual commands needed to make machines follow our commands...

# GPU + CUDA + CUDNN + tensorflow-gpu PAINS

## Working combination

- https://stackoverflow.com/questions/50622525/which-tensorflow-and-cuda-version-combinations-are-compatible
- https://www.tensorflow.org/install/source#tested_build_configurations

## Check version

### System + GPU

```
lsb_release -a
nvidia-smi
```

### CUDA

```
whereis -b cuda
nvcc --version
/usr/local/cuda/bin/nvcc --version
```

### CUDNN

```
whereis -b cudnn
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
```

### python + tensorflow + ...

```
which python 
which python3
python --version
python -c 'import tensorflow as tf; print(tf.__version__)'
pip list | grep tensorflow
pip show tensorflow
conda list | grep tensorflow
```

## Test correct functioning

### Test tensorflow-gpu

```
import tensorflow as tf
sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))
```

### Test CUDA

- https://devtalk.nvidia.com/default/topic/1027653/jetson-tx2/how-do-i-check-if-i-install-cuda-and-cudnn-successfully-/

```
/usr/local/cuda-8.0/bin/cuda-install-samples-8.0.sh .
cd NVIDIA_CUDA-8.0_Samples/1_Utilities/deviceQuery
make && ./deviceQuery
```

## Installation steps

### (not yet tested) tensorflow-gpu with Conda

- https://towardsdatascience.com/tensorflow-gpu-installation-made-easy-use-conda-instead-of-pip-52e5249374bc

```
conda create --name tf_gpu tensorflow-gpu 
```


