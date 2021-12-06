
## ResNets and Higher Receptive Fields
LR Schedulers- OneCycleLR ResNets, and Higher Receptive Fields and to perform a convolution based on custom resnet architecture on CIFAR10 dataset.

## Modules 
 torch_cv_wrapper which has utils, main, gradcom, lr_finder,model python files is built to perform object detection based on PyTorch on CIFAR10 dataset.


## Model details
The notebook is here 

with a test accuracy of 92.89% at 24th epoch

Epochs - 24
LR Scheduler - OneCycleLR

## Data Augmentation 

RandomCrop(32, padding=4)
CutOut(8x8)
Horizontal Flip
