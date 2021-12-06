
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
## training logs

Epoch 1:
Loss=1.9105336666107178 Batch_id=97 LR=0.05598 Accuracy=29.99: 100%|██████████| 98/98 [00:54<00:00,  1.78it/s]
Test set: Average loss: 0.0037, Accuracy: 3254/10000 (32.54%)

Epoch 2:
Loss=1.3634164333343506 Batch_id=97 LR=0.11480 Accuracy=46.06: 100%|██████████| 98/98 [00:55<00:00,  1.78it/s]
Test set: Average loss: 0.0030, Accuracy: 4558/10000 (45.58%)

Epoch 3:
Loss=0.9226760864257812 Batch_id=97 LR=0.18741 Accuracy=61.29: 100%|██████████| 98/98 [00:55<00:00,  1.78it/s]
Test set: Average loss: 0.0021, Accuracy: 6349/10000 (63.49%)

Epoch 4:
Loss=0.7135415077209473 Batch_id=97 LR=0.24596 Accuracy=68.25: 100%|██████████| 98/98 [00:54<00:00,  1.78it/s]
Test set: Average loss: 0.0025, Accuracy: 5576/10000 (55.76%)

Epoch 5:
Loss=0.8716841340065002 Batch_id=97 LR=0.26800 Accuracy=69.76: 100%|██████████| 98/98 [00:54<00:00,  1.79it/s]
Test set: Average loss: 0.0030, Accuracy: 5298/10000 (52.98%)

Epoch 6:
Loss=0.807977557182312 Batch_id=97 LR=0.26614 Accuracy=70.89: 100%|██████████| 98/98 [00:54<00:00,  1.79it/s]
Test set: Average loss: 0.0020, Accuracy: 6366/10000 (63.66%)

Epoch 7:
Loss=0.7919117212295532 Batch_id=97 LR=0.26067 Accuracy=72.32: 100%|██████████| 98/98 [00:54<00:00,  1.79it/s]
Test set: Average loss: 0.0021, Accuracy: 6604/10000 (66.04%)

Epoch 8:
Loss=0.8361509442329407 Batch_id=97 LR=0.25174 Accuracy=72.55: 100%|██████████| 98/98 [00:54<00:00,  1.80it/s]
Test set: Average loss: 0.0020, Accuracy: 6475/10000 (64.75%)

Epoch 9:
Loss=0.7878806591033936 Batch_id=97 LR=0.23961 Accuracy=72.88: 100%|██████████| 98/98 [00:54<00:00,  1.80it/s]
Test set: Average loss: 0.0023, Accuracy: 6277/10000 (62.77%)

Epoch 10:
Loss=0.6994244456291199 Batch_id=97 LR=0.22459 Accuracy=73.06: 100%|██████████| 98/98 [00:54<00:00,  1.80it/s]
Test set: Average loss: 0.0026, Accuracy: 6002/10000 (60.02%)

Epoch 11:
Loss=0.7122523188591003 Batch_id=97 LR=0.20710 Accuracy=74.03: 100%|██████████| 98/98 [00:54<00:00,  1.81it/s]
Test set: Average loss: 0.0037, Accuracy: 5139/10000 (51.39%)

Epoch 12:
Loss=0.7527581453323364 Batch_id=97 LR=0.18762 Accuracy=74.57: 100%|██████████| 98/98 [00:54<00:00,  1.81it/s]
Test set: Average loss: 0.0019, Accuracy: 6739/10000 (67.39%)

Epoch 13:
Loss=0.6730099320411682 Batch_id=97 LR=0.16668 Accuracy=75.12: 100%|██████████| 98/98 [00:54<00:00,  1.81it/s]
Test set: Average loss: 0.0019, Accuracy: 6863/10000 (68.63%)

Epoch 14:
Loss=0.7236506342887878 Batch_id=97 LR=0.14484 Accuracy=75.67: 100%|██████████| 98/98 [00:54<00:00,  1.81it/s]
Test set: Average loss: 0.0018, Accuracy: 6992/10000 (69.92%)

Epoch 15:
Loss=0.7216722369194031 Batch_id=97 LR=0.12271 Accuracy=76.78: 100%|██████████| 98/98 [00:54<00:00,  1.81it/s]
Test set: Average loss: 0.0015, Accuracy: 7446/10000 (74.46%)

Epoch 16:
Loss=0.5682244300842285 Batch_id=97 LR=0.10089 Accuracy=77.53: 100%|██████████| 98/98 [00:54<00:00,  1.81it/s]
Test set: Average loss: 0.0015, Accuracy: 7528/10000 (75.28%)

Epoch 17:
Loss=0.6836804151535034 Batch_id=97 LR=0.07997 Accuracy=78.88: 100%|██████████| 98/98 [00:53<00:00,  1.82it/s]
Test set: Average loss: 0.0021, Accuracy: 6481/10000 (64.81%)

Epoch 18:
Loss=0.5987664461135864 Batch_id=97 LR=0.06052 Accuracy=79.97: 100%|██████████| 98/98 [00:53<00:00,  1.82it/s]
Test set: Average loss: 0.0012, Accuracy: 7855/10000 (78.55%)

Epoch 19:
Loss=0.48867717385292053 Batch_id=97 LR=0.04308 Accuracy=81.55: 100%|██████████| 98/98 [00:53<00:00,  1.82it/s]
Test set: Average loss: 0.0017, Accuracy: 7155/10000 (71.55%)

Epoch 20:
Loss=0.4445016086101532 Batch_id=97 LR=0.02812 Accuracy=83.54: 100%|██████████| 98/98 [00:53<00:00,  1.82it/s]
Test set: Average loss: 0.0013, Accuracy: 7837/10000 (78.37%)

Epoch 21:
Loss=0.459189236164093 Batch_id=97 LR=0.01605 Accuracy=86.03: 100%|██████████| 98/98 [00:53<00:00,  1.82it/s]
Test set: Average loss: 0.0009, Accuracy: 8494/10000 (84.94%)

Epoch 22:
Loss=0.28029733896255493 Batch_id=97 LR=0.00719 Accuracy=88.98: 100%|██████████| 98/98 [00:53<00:00,  1.82it/s]
Test set: Average loss: 0.0007, Accuracy: 8751/10000 (87.51%)

Epoch 23:
Loss=0.20826689898967743 Batch_id=97 LR=0.00179 Accuracy=91.79: 100%|██████████| 98/98 [00:53<00:00,  1.82it/s]
Test set: Average loss: 0.0006, Accuracy: 9021/10000 (90.21%)

Epoch 24:
Loss=0.2200206071138382 Batch_id=97 LR=0.00000 Accuracy=93.48: 100%|██████████| 98/98 [00:53<00:00,  1.82it/s]
Test set: Average loss: 0.0006, Accuracy: 9024/10000 (90.24%)


## Misclassified images

![image](https://user-images.githubusercontent.com/45157166/144909422-733dd45b-deaf-43f9-b2a6-24d3e1d406cd.png)

## plots

![image](https://user-images.githubusercontent.com/45157166/144909519-fcc3747e-017f-409a-9596-4859614dc088.png)

## gradcam of misclassified images

![image](https://user-images.githubusercontent.com/45157166/144909634-dd5b80fe-c9b5-4fac-a619-04a000e97a39.png)

![image](https://user-images.githubusercontent.com/45157166/144909707-744219b9-cdc1-423b-bb55-0db130bcca68.png)



