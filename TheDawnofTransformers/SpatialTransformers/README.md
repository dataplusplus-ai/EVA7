

## Spatial Transformer

The spatial transformer module consists of layers of neural networks that can spatially transform an image. These spatial transformations include cropping, scaling, rotations, and translations etc

CNNs perform poorly when the input data contains so much variation. One of the solutions to this is the max-pooling layer. But then again, max-pooling layers do not make the CNN invariant image translation.

In STNs, the transformer module knows where to apply the transformation to properly scale, resize, and crop and image. We can apply the STN module to the input data directly, or even to the feature maps (output of a convolution layer). In simple words, we can say that the spatial transformer module acts as an attention mechanism and knows where to focus on the input data.

## Architecture

The architecture of a Spatial Transformer Network is based on three important parts.

The localization network.

Parameterized sampling grid.

Differentiable image sampling.

![image](https://user-images.githubusercontent.com/45157166/147868606-3fd614d7-acd5-40e6-b830-5c08dd4528ee.png)

### Localisation Network

The localization network takes the input feature map and outputs the parameters of the spatial transformations that should be applied to the feature map. The localization network is a very simple stacking of convolutional layers.

In the above figuare, U is the feature map input to the localization network. It outputs θ which are the transformation parameters that are regressed from the localization network. The final regression layers are fully-connected linear layers. Tθ is the transformation operation using the parameters θ.

### Parameterized Sampling Grid

Parameterized Sampling Grid mainly generates a sampling grid that is consistent with the picture pixels, and multiplies it with theta matrix to gradually learn to fully correspond to the tilt recognition object

### Differentiable image sampling.

Differentable Image Sampling is mainly used to obtain the original image pixels corresponding to the sampling points to form a V feature map to complete the output of the V feature map

### Training Logs

Test set: Average loss: 1.8873, Accuracy: 3391/10000 (34%)

Train Epoch: 2 [0/50000 (0%)]	Loss: 1.956846
Train Epoch: 2 [32000/50000 (64%)]	Loss: 1.817448

Test set: Average loss: 1.6500, Accuracy: 4077/10000 (41%)

Train Epoch: 3 [0/50000 (0%)]	Loss: 1.953962
Train Epoch: 3 [32000/50000 (64%)]	Loss: 1.513095

Test set: Average loss: 1.5240, Accuracy: 4518/10000 (45%)

Train Epoch: 4 [0/50000 (0%)]	Loss: 1.809420
Train Epoch: 4 [32000/50000 (64%)]	Loss: 1.447081

Test set: Average loss: 1.4666, Accuracy: 4722/10000 (47%)

Train Epoch: 5 [0/50000 (0%)]	Loss: 1.636911
Train Epoch: 5 [32000/50000 (64%)]	Loss: 1.631306

Test set: Average loss: 1.4484, Accuracy: 4870/10000 (49%)

Train Epoch: 6 [0/50000 (0%)]	Loss: 1.852893
Train Epoch: 6 [32000/50000 (64%)]	Loss: 1.505792

Test set: Average loss: 1.3621, Accuracy: 5140/10000 (51%)

Train Epoch: 7 [0/50000 (0%)]	Loss: 1.475788
Train Epoch: 7 [32000/50000 (64%)]	Loss: 1.225690

Test set: Average loss: 1.3162, Accuracy: 5321/10000 (53%)

Train Epoch: 8 [0/50000 (0%)]	Loss: 1.506767
Train Epoch: 8 [32000/50000 (64%)]	Loss: 1.489542

Test set: Average loss: 1.3520, Accuracy: 5235/10000 (52%)

Train Epoch: 9 [0/50000 (0%)]	Loss: 1.847830
Train Epoch: 9 [32000/50000 (64%)]	Loss: 1.390532

Test set: Average loss: 1.3124, Accuracy: 5412/10000 (54%)

Train Epoch: 10 [0/50000 (0%)]	Loss: 1.258712
Train Epoch: 10 [32000/50000 (64%)]	Loss: 1.475420

Test set: Average loss: 1.2546, Accuracy: 5652/10000 (57%)

Train Epoch: 11 [0/50000 (0%)]	Loss: 1.264124
Train Epoch: 11 [32000/50000 (64%)]	Loss: 1.262613

Test set: Average loss: 1.2632, Accuracy: 5578/10000 (56%)

Train Epoch: 12 [0/50000 (0%)]	Loss: 1.335502
Train Epoch: 12 [32000/50000 (64%)]	Loss: 1.201537

Test set: Average loss: 1.2137, Accuracy: 5799/10000 (58%)

Train Epoch: 13 [0/50000 (0%)]	Loss: 1.312249
Train Epoch: 13 [32000/50000 (64%)]	Loss: 1.205030

Test set: Average loss: 1.2561, Accuracy: 5666/10000 (57%)

Train Epoch: 14 [0/50000 (0%)]	Loss: 1.542765
Train Epoch: 14 [32000/50000 (64%)]	Loss: 1.265275

Test set: Average loss: 1.1241, Accuracy: 6060/10000 (61%)

Train Epoch: 15 [0/50000 (0%)]	Loss: 0.994999
Train Epoch: 15 [32000/50000 (64%)]	Loss: 1.176323

Test set: Average loss: 1.1408, Accuracy: 6041/10000 (60%)

Train Epoch: 16 [0/50000 (0%)]	Loss: 1.081319
Train Epoch: 16 [32000/50000 (64%)]	Loss: 1.151411

Test set: Average loss: 1.1641, Accuracy: 5915/10000 (59%)

Train Epoch: 17 [0/50000 (0%)]	Loss: 1.192728
Train Epoch: 17 [32000/50000 (64%)]	Loss: 1.077485

Test set: Average loss: 1.1065, Accuracy: 6206/10000 (62%)

Train Epoch: 18 [0/50000 (0%)]	Loss: 1.112859
Train Epoch: 18 [32000/50000 (64%)]	Loss: 0.980755

Test set: Average loss: 1.1135, Accuracy: 6170/10000 (62%)

Train Epoch: 19 [0/50000 (0%)]	Loss: 1.294413
Train Epoch: 19 [32000/50000 (64%)]	Loss: 1.284916

Test set: Average loss: 1.1058, Accuracy: 6124/10000 (61%)

Train Epoch: 20 [0/50000 (0%)]	Loss: 1.094502
Train Epoch: 20 [32000/50000 (64%)]	Loss: 0.943720

Test set: Average loss: 1.0630, Accuracy: 6352/10000 (64%)

Train Epoch: 21 [0/50000 (0%)]	Loss: 1.399007
Train Epoch: 21 [32000/50000 (64%)]	Loss: 1.133119

Test set: Average loss: 1.0428, Accuracy: 6440/10000 (64%)

Train Epoch: 22 [0/50000 (0%)]	Loss: 1.035173
Train Epoch: 22 [32000/50000 (64%)]	Loss: 0.887680

Test set: Average loss: 1.0736, Accuracy: 6304/10000 (63%)

Train Epoch: 23 [0/50000 (0%)]	Loss: 1.052839
Train Epoch: 23 [32000/50000 (64%)]	Loss: 1.268270

Test set: Average loss: 1.0608, Accuracy: 6356/10000 (64%)

Train Epoch: 24 [0/50000 (0%)]	Loss: 0.983308
Train Epoch: 24 [32000/50000 (64%)]	Loss: 1.065331

Test set: Average loss: 1.0403, Accuracy: 6424/10000 (64%)

Train Epoch: 25 [0/50000 (0%)]	Loss: 1.092985
Train Epoch: 25 [32000/50000 (64%)]	Loss: 0.987251

Test set: Average loss: 1.0586, Accuracy: 6369/10000 (64%)

Train Epoch: 26 [0/50000 (0%)]	Loss: 0.887423
Train Epoch: 26 [32000/50000 (64%)]	Loss: 1.109474

Test set: Average loss: 1.0202, Accuracy: 6555/10000 (66%)

Train Epoch: 27 [0/50000 (0%)]	Loss: 0.975946
Train Epoch: 27 [32000/50000 (64%)]	Loss: 0.696065

Test set: Average loss: 1.0179, Accuracy: 6523/10000 (65%)

Train Epoch: 28 [0/50000 (0%)]	Loss: 0.855089
Train Epoch: 28 [32000/50000 (64%)]	Loss: 0.733290

Test set: Average loss: 1.0245, Accuracy: 6585/10000 (66%)

Train Epoch: 29 [0/50000 (0%)]	Loss: 1.177302
Train Epoch: 29 [32000/50000 (64%)]	Loss: 0.929199

Test set: Average loss: 1.0284, Accuracy: 6563/10000 (66%)

Train Epoch: 30 [0/50000 (0%)]	Loss: 1.037169
Train Epoch: 30 [32000/50000 (64%)]	Loss: 1.133814

Test set: Average loss: 1.0758, Accuracy: 6341/10000 (63%)

Train Epoch: 31 [0/50000 (0%)]	Loss: 1.064659
Train Epoch: 31 [32000/50000 (64%)]	Loss: 0.840118

Test set: Average loss: 1.0425, Accuracy: 6435/10000 (64%)

Train Epoch: 32 [0/50000 (0%)]	Loss: 1.094867
Train Epoch: 32 [32000/50000 (64%)]	Loss: 0.795158

Test set: Average loss: 1.0314, Accuracy: 6492/10000 (65%)

Train Epoch: 33 [0/50000 (0%)]	Loss: 1.004608
Train Epoch: 33 [32000/50000 (64%)]	Loss: 0.961755

Test set: Average loss: 1.0505, Accuracy: 6386/10000 (64%)

Train Epoch: 34 [0/50000 (0%)]	Loss: 0.962030
Train Epoch: 34 [32000/50000 (64%)]	Loss: 1.181293

Test set: Average loss: 1.0225, Accuracy: 6534/10000 (65%)

Train Epoch: 35 [0/50000 (0%)]	Loss: 0.908549
Train Epoch: 35 [32000/50000 (64%)]	Loss: 0.958693

Test set: Average loss: 1.0237, Accuracy: 6513/10000 (65%)

Train Epoch: 36 [0/50000 (0%)]	Loss: 0.907936
Train Epoch: 36 [32000/50000 (64%)]	Loss: 0.697703

Test set: Average loss: 0.9769, Accuracy: 6661/10000 (67%)

Train Epoch: 37 [0/50000 (0%)]	Loss: 0.834435
Train Epoch: 37 [32000/50000 (64%)]	Loss: 1.042879

Test set: Average loss: 1.0552, Accuracy: 6490/10000 (65%)

Train Epoch: 38 [0/50000 (0%)]	Loss: 0.897793
Train Epoch: 38 [32000/50000 (64%)]	Loss: 0.856798

Test set: Average loss: 0.9779, Accuracy: 6700/10000 (67%)

Train Epoch: 39 [0/50000 (0%)]	Loss: 0.880660
Train Epoch: 39 [32000/50000 (64%)]	Loss: 0.948920

Test set: Average loss: 1.0207, Accuracy: 6515/10000 (65%)

Train Epoch: 40 [0/50000 (0%)]	Loss: 0.792147
Train Epoch: 40 [32000/50000 (64%)]	Loss: 0.927382

Test set: Average loss: 1.0252, Accuracy: 6486/10000 (65%)

Train Epoch: 41 [0/50000 (0%)]	Loss: 0.650937
Train Epoch: 41 [32000/50000 (64%)]	Loss: 1.026688

Test set: Average loss: 0.9990, Accuracy: 6646/10000 (66%)

Train Epoch: 42 [0/50000 (0%)]	Loss: 0.774015
Train Epoch: 42 [32000/50000 (64%)]	Loss: 0.737488

Test set: Average loss: 0.9965, Accuracy: 6618/10000 (66%)

Train Epoch: 43 [0/50000 (0%)]	Loss: 0.838117
Train Epoch: 43 [32000/50000 (64%)]	Loss: 0.886423

Test set: Average loss: 1.0239, Accuracy: 6505/10000 (65%)

Train Epoch: 44 [0/50000 (0%)]	Loss: 0.766375
Train Epoch: 44 [32000/50000 (64%)]	Loss: 0.950142

Test set: Average loss: 1.0015, Accuracy: 6625/10000 (66%)

Train Epoch: 45 [0/50000 (0%)]	Loss: 0.578457
Train Epoch: 45 [32000/50000 (64%)]	Loss: 1.009891

Test set: Average loss: 1.0393, Accuracy: 6481/10000 (65%)

Train Epoch: 46 [0/50000 (0%)]	Loss: 1.144128
Train Epoch: 46 [32000/50000 (64%)]	Loss: 0.806893

Test set: Average loss: 1.0321, Accuracy: 6521/10000 (65%)

Train Epoch: 47 [0/50000 (0%)]	Loss: 0.576759
Train Epoch: 47 [32000/50000 (64%)]	Loss: 0.813684

Test set: Average loss: 0.9962, Accuracy: 6614/10000 (66%)

Train Epoch: 48 [0/50000 (0%)]	Loss: 0.804050
Train Epoch: 48 [32000/50000 (64%)]	Loss: 0.697098

Test set: Average loss: 1.0106, Accuracy: 6575/10000 (66%)

Train Epoch: 49 [0/50000 (0%)]	Loss: 0.824746
Train Epoch: 49 [32000/50000 (64%)]	Loss: 0.646134

Test set: Average loss: 1.0112, Accuracy: 6636/10000 (66%)

Train Epoch: 50 [0/50000 (0%)]	Loss: 0.808927
Train Epoch: 50 [32000/50000 (64%)]	Loss: 0.715981

Test set: Average loss: 1.0168, Accuracy: 6532/10000 (65%)



### Visuaization of STN results

![image](https://user-images.githubusercontent.com/45157166/147873039-9a0d64d5-3898-4f43-8390-47996855bb0f.png)

