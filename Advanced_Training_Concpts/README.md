

### To learn GRADient Class activation maps, Weight Updates, Optimizers & LR Schedulers concepts, based on ResNet18 with modifications, Layer Normalization on CIFAR10 dataset.

## model

https://github.com/dataplusplus-ai/torch_cv_wrapper/blob/main/model/resnet.py

## utils

https://github.com/dataplusplus-ai/torch_cv_wrapper/tree/main/utils

## main

https://github.com/dataplusplus-ai/torch_cv_wrapper/blob/main/main.py

## training logs

Epoch 32:
Loss=0.6806079149246216 Batch_id=195 LR=0.00188 Accuracy=80.29: 100%|██████████| 196/196 [06:28<00:00,  1.98s/it]
Test set: Average loss: 0.0020, Accuracy: 8287/10000 (82.87%)

Epoch 33:
Loss=0.4209621846675873 Batch_id=195 LR=0.00146 Accuracy=80.99: 100%|██████████| 196/196 [06:29<00:00,  1.99s/it]
Test set: Average loss: 0.0019, Accuracy: 8439/10000 (84.39%)

Epoch 34:
Loss=0.535122275352478 Batch_id=195 LR=0.00109 Accuracy=81.64: 100%|██████████| 196/196 [06:29<00:00,  1.99s/it]
Test set: Average loss: 0.0018, Accuracy: 8544/10000 (85.44%)

Epoch 35:
Loss=0.4303179383277893 Batch_id=195 LR=0.00076 Accuracy=82.44: 100%|██████████| 196/196 [06:31<00:00,  2.00s/it]
Test set: Average loss: 0.0017, Accuracy: 8496/10000 (84.96%)

Epoch 36:
Loss=0.42171064019203186 Batch_id=195 LR=0.00049 Accuracy=83.04: 100%|██████████| 196/196 [06:29<00:00,  1.99s/it]
Test set: Average loss: 0.0017, Accuracy: 8571/10000 (85.71%)

Epoch 37:
Loss=0.43836545944213867 Batch_id=195 LR=0.00028 Accuracy=83.66: 100%|██████████| 196/196 [06:28<00:00,  1.98s/it]
Test set: Average loss: 0.0017, Accuracy: 8573/10000 (85.73%)

Epoch 38:
Loss=0.48999953269958496 Batch_id=195 LR=0.00012 Accuracy=83.98: 100%|██████████| 196/196 [06:28<00:00,  1.98s/it]
Test set: Average loss: 0.0017, Accuracy: 8605/10000 (86.05%)

Epoch 39:
Loss=0.2924918532371521 Batch_id=195 LR=0.00003 Accuracy=83.96: 100%|██████████| 196/196 [06:28<00:00,  1.98s/it]
Test set: Average loss: 0.0016, Accuracy: 8611/10000 (86.11%)

Epoch 40:
Loss=0.42605534195899963 Batch_id=195 LR=0.00000 Accuracy=84.39: 100%|██████████| 196/196 [06:28<00:00,  1.98s/it]
Test set: Average loss: 0.0016, Accuracy: 8611/10000 (86.11%)

## Misclassified images 

![image](https://user-images.githubusercontent.com/45157166/143600403-3f75d3be-b714-4ddd-8510-35797beb0580.png)


## GRADCAM of these misclassified images 

![image](https://user-images.githubusercontent.com/45157166/143600603-42a56288-7f56-482b-a73d-66dacb9ee6c3.png)

![image](https://user-images.githubusercontent.com/45157166/143600673-e0754abe-3e3f-4a2f-87cb-6cc96daa6c4f.png)


