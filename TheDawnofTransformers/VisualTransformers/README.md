
### code reference

https://github.com/jeonsworld/ViT-pytorch/blob/main/models/modeling.py

### Vision Transformers

Transformer-based architectures for Computer Vision Tasks is proposed in the paper https://arxiv.org/abs/2010.11929  'An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale' by Alexey Dosovitskiy, Lucas Beyer, Alexander Kolesnikov, Dirk Weissenborn, Xiaohua Zhai, Thomas Unterthiner, Mostafa Dehghani, Matthias Minderer, Georg Heigold, Sylvain Gelly, Jakob Uszkoreit, Neil Houlsby.

Transformers have been used immensively for NLP tasks, and CNN/Resnet-like architectures have been the state of the art for Computer Vision. This paper mainly discusses the strength and versatility of vision transformers, and their efective use in image recognition which can even beat the state-of-the-art CNN.

The following classes are implemented in the code.

Embeddings

Encoder

Block

Attention

MLP

The sequence of the operations are

Input -> CreatePatches -> ClassToken, PatchToEmbed , PositionEmbed -> Transformer -> ClassificationHead -> Output

Embedding

![image](https://user-images.githubusercontent.com/45157166/147869733-601ce55a-12a1-4704-a9e3-cdde2d41282d.png)

* Break-down the image into patches, 16x16 patches in this case and flatten them.

* These patches are projected using a normal linear layer, a Conv2d layer is used for this for performance gain. This is obtained by using a kernel_size and stride equal to the patch_size. Intuitively, the convolution operation is applied to each patch individually. So, we have to first apply the conv layer and then flat the resulting images.

* Next add the cls token and the position embedding. The cls token is just a number placed in front of each sequence (of projected patches). cls_tokens is a torch Parameter randomly initialized, in the forward the method it is copied B (batch) times and prepended before the projected patches using torch.cat

* For the model to know the original position of the patches, we need to pass the spatial information. In ViT we let the model learn it. The position embedding is just a tensor of shape 1, n_patches + 1(token), hidden_size that is added to the projected patches. In the forward function below, position_embeddings is summed up with the patches (x)


### Encoder

The resulting tensor is passeed into a Transformer. In ViT only the Encoder is used, the Transformer encoder module comprises a Multi-Head Self Attention ( MSA ) layer and a Multi-Layer Perceptron (MLP) layer. The encoder combines multiple layers of Transformer Blocks in a sequential manner. The sequence of the operations is as follows -

Input -> TB1 -> TB2 -> .......... -> TBn (n being the number of layers) -> Output

![image](https://user-images.githubusercontent.com/45157166/147869851-8a2ae4ca-7e14-44a7-81d6-c73f6e6013a3.png)

Block
The Block class combines both the attention module and the MLP module with layer normalization, dropout and residual connections. The sequence of operations is as follows :-

Input -> LayerNorm1 -> Attention -> Residual -> LayerNorm2 -> FeedForward -> Output
  |                                   |  |                                      |
  |-------------Addition--------------|  |---------------Addition---------------|
  
  
### Attention

Attention Module is used to perform self-attention operation allowing the model to attend information from different representation subspaces on an input sequence of embeddings. The sequence of operations is as follows :-

Input -> Query, Key, Value -> ReshapeHeads and Transpose Key,Query,Value -> Query * Transpose(Key) -> Softmax -> Dropout -> attention_scores * Value -> ReshapeHeadsBack and Concatenate -> Dropout - > Output

![image](https://user-images.githubusercontent.com/45157166/147869923-4db99edf-0bb5-48a1-a12e-64447d3589aa.png)

Before passing the tensors to the attension block, we have a normalization layer where Layer Norm is applied
Layer normalization can be thought of similar to batch normalization. Basically, we take each of the neurons activation and subtract the mean from them, we then divide the value with the standard deviation and finally add a small value to the denominator just to make sure that it never lands up being zero. One difference is that the mean and variances for the layer normalization are calculated along the last dimension (axis=-1) instead of the first batch dimension (axis=0). Pytoch provide a inbuilt function nn.LayerNorm for this. Layer normalization prevents the range of values in the layers from changing too much, which allows faster training and better generalization ability.

The attention takes three inputs, the queries, keys, and values, reshapes and computes the attention matrix using queries and values and use it to “attend” to the values. In this case, we are using multi-head attention meaning that the computation is split across n heads with smaller input size.

We have 4 fully connected layers, one for queries, keys, values, and two dropout.

the product between the queries and the keys is taken to know “how much” each element is the sequence in important with the rest. Then, we use this information to scale the values.

attention is finally the softmax of the resulting vector divided by a scaling factor based on the size of the embedding.

The resulting vector is then multipled with the values, to get the context

Which is then reshaped and concatenated back, to return the attention_output and weight

### MLP
The attension output is passed to MLP, which is two sequential linear layers with GELU activation function applied to the output of self attention operation. The sequence of operations is as follows :-

Input -> FC1 -> GELU -> Dropout -> FC2 -> Output

![image](https://user-images.githubusercontent.com/45157166/147870061-ad05c3e8-8ad7-406a-a989-819d4f1a6214.png)

Gaussian Error Linear Unit (GELu), an activation function used in the most recent Transformers – Google's BERT and OpenAI's GPT-2. The paper is from 2016, but is only catching attention up until recently. Seems to be state-of-the-art in NLP, specifically Transformer models – i.e. it performs best and avoids vanishing gradients problem.

This activation function takes the form of this equation:

![image](https://user-images.githubusercontent.com/45157166/147870083-51307dfe-3dc7-4d87-9169-000c3cbef978.png)

It has a negative coefficient, which shifts to a positive coefficient. So when x is greater than zero, the output will be x, except from when x = 0 to x = 1, where it slightly leans to a smaller y-value.



Explanation reference

https://towardsdatascience.com/implementing-visualttransformer-in-pytorch-184f9f16f632









