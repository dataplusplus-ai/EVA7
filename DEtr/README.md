
# End-to-end object detection with Transformers


DEtectiontransformer is the first object detection framework to successfully integrate Transformers as a central building block in the detection pipeline.

DETR matches the performance of state-of-the-art methods, such as the well-established and highly optimized Faster R-CNN baseline on the challenging COCO object detection dataset, while also greatly simplifying and streamlining the architecture.


![image](https://user-images.githubusercontent.com/45157166/150644457-6079a976-535f-4ead-806e-18f0713ea104.png)


DETR offers a simpler, more flexible pipeline architecture that requires fewer heuristics. Inference can be boiled down to 50 lines of simple Python code using elementary architectural blocks. Moreover, because Transformers have proven to be a powerful tool for dramatically improving performance of models in other domains, we believe additional performance gains and improved training efficiency will be possible with additional tuning.






DETR casts the object detection task as an image-to-set problem. Given an image, the model must predict an unordered set (or list) of all the objects present, each represented by its class, along with a tight bounding box surrounding each one.

This formulation is particularly suitable for Transformers. We chain a convolutional neural network (CNN), which extracts the local information from the image, with a Transformer encoder-decoder architecture, which reasons about the image as a whole and then generates the predictions.

Traditional computer vision models typically use a complex, partly handcrafted pipeline that relies on custom layers in order to localize objects in an image and then extract features. DETR replaces this with a simpler neural network that offers a true end-to-end deep learning solution to the problem.

The DETR framework consists of a set-based global loss, which forces unique predictions via bipartite matching, and a Transformer encoder-decoder architecture. Given a fixed small set of learned object queries, DETR reasons about the relations of the objects and the global image context to directly output the final set of predictions in parallel. Previous attempts to use architectures such as recurrent neural networks for object detection were much slower and less effective, because they made predictions sequentially rather than in parallel.

Transformers’ self-attention mechanisms allow DETR to perform global reasoning on the image as well as on the specific objects that are predicted. For example, the model may look at other regions of the image to help make a decision about the object in a bounding box. It can also make predictions based on relationships or correlations between objects in an image. If DETR predicts that an image contains a person standing on the beach, for example, it knows that a partially occluded object is more likely to be a surfboard. In contrast, other detection models predict each object in isolation.

This pipeline can be extended to related tasks such as panoptic segmentation
, which aims at segmenting distinct foreground objects while simultaneously labeling all the pixels from the background. DETR treats foreground items, such as animals or people, and background items, such as sky or grass, in a truly unified manner.








Followed this code https://opensourcelibs.com/lib/finetune-detr




## Architecture of DEtr

![image](https://user-images.githubusercontent.com/45157166/150644174-45b03a7c-7d49-4687-a49f-bcf78234c8e8.png)


### The CNN Backbone

The CNN backbone generates a feature map from the input image. Then the output of the CNN backbone is converted into a one-dimensional feature map and added to a positional encoding, which is fed into a Transformer consisting of an Encoder and a Decoder in a manner quite similar to the Encoder-Decoder transformer described in the original Transformer paper (http://arxiv.org/abs/1706.03762). The output of this encoder are N number of fixed length embeddings (vectors), where N is the number of objects in the image assumed by the model.

![image](https://user-images.githubusercontent.com/45157166/150644969-88316ead-6a63-4a0f-ad57-4177937a35a0.png)


Assume that our input image xᵢₘ of height H₀, width W₀, and three input channels. CNN backbone consists of a (pretrained) CNN (usually ResNet), which we use to generate C lower dimensional features having width W and height H (In practice, we set C=2048, W=W₀/32 and H=H₀/32). This leaves us with C two-dimensional features, and since we will be passing these features into a transformer, each feature must be reformatted in a way that will allow the encoder to process each feature as a sequence. This is done by flattening the feature matrices into an H⋅W vector, and then concatenating each one.

### The Transformer

The Transformer decoder decodes these embeddings into bounding box coordinates with the help of self and encoder-decoder attention mechanism. The transformer is nearly identical to the original encoder-decoder architecture. The difference is that each decoder layers decodes each of the N (the predefined number of) objects in parallel. The model also learns a set of N object queries which are (similar to the encoder) learned positional encodings.

![image](https://user-images.githubusercontent.com/45157166/150645002-daf9ccbb-a400-4822-bb63-c7bdf1be90cc.png)

Object Queries
These are N learnt positional embeddings passed in as inputs to the decoder. Each of the input embeddings corresponds to one of the final predictions. The decoder transforms these embeddings to give the final prediction. Because all of the inputs are being processed at the same time, the model can globally reason about the final set of objects.

An intuitive way of understanding the object queries is by imagining that each object query is a person. And each person can ask the, via attention, about a certain region of the image. So one object query will always ask about what is in the center of an image, and another will always ask about what is on the bottom left, and so on.

Prediction heads
Finally, the output of the decoder is then fed into a fixed number of Prediction Heads which consist of a predefined number of feed forward networks. The feed-forward neural networks predict the normalized center coordinates, height, and width of the bounding boxes and the linear layer predicts the class label using a softmax function.

An important thing to note here is that since the model predicts a fixed-set of N objects in a single pass through the decoder, where N is way larger than the number of objects in ground-truth data, the author used a special class to represent 'no object was detected in this slot'. This N user has to decide according to their need. Suppose in an image maximum 5 object are there so we can define (N=7,8,..). let’s say N=7, so DETR infers a set of 7 prediction. Out of this 7 prediction 5 prediction will for object and 2 prediction are for ∅(no object) means they will assign to background. Each prediction is a kind of tuple containing class and bounding box (c,b).

Besides the transformer part in architecture, DETR also adopt two major components from previous research.

Bipartite Matching Loss

Parallel Decoding

Bipartite Matching Loss

The transformer will make total of N predictions, and in order to apply loss function during training, the model needs to find which prediction matches to which ground truth. This is done by bipartite matching, which finds a one to one pair between prediction and ground truth label based on ‘matching cost’. Using pair-wise matching cost, predicted boxes are then matched with target box such that the cost is minimum.

Bipartite matching loss is designed based on Hungarian algorithm. Unlike other object detection models where multiple bounding boxes are matched to one ground truth box, DETR uses bipartite matching, which is one-vs-one matching. By performing one-vs-one matching, its able to significantly reduce low-quality predictions, and achieve eliminations of output reductions like NMS.

DETR frameworks uses a set based global loss that enforces unique prediction through bipartite matching.

DETR always infers a fixed set of ‘N’ predictions. Since the number of predicted objects is much larger than the objects in ground-truth data, they pad a vector representing ground-truth data with nulls to represent "no object". Let y denote the ground truth set of objects and y-hat the set of N predictions. The bipartite matching between the ground truth and predicted is achieved by Hungarian algorithm which determines the optimal assignment between ground truth and prediction.

![image](https://user-images.githubusercontent.com/45157166/150645054-55cfdf8a-8999-42c5-b2f9-7cf0a02558a7.png)

The bipartite matching is defined by this eq

![image](https://user-images.githubusercontent.com/45157166/150645132-d4ab7327-3cd2-4448-a466-1ec041f1387b.png)


The above equation, sigma stands for matched result, and L_match stands for matching cost. We want to find a matching result which will result in the lowest total matching cost, and this optimal matching can be done by Hungarian algorithm.

Lmatch the matching loss is the sum of class prediction loss and bounding box difference loss.

![image](https://user-images.githubusercontent.com/45157166/150645152-31ae37ec-daec-4b6c-9fa3-90a8bd840040.png)




The loss function used here is negative log-likelihood for class label and a box. Bounding box loss is a linear combination of ℓ1 loss and IoU (intersection over union) loss to ensure loss is scale-invariant since there could be small and big boxes, the IoU helps mitigate the issue with the ℓ1 loss where the magnitude of loss would be higher for larger boxes compared to smaller ones, even if their relative errors are the same.

### FineTune DETR

Now, lets understand how fine-tuning works, here we are going to fine-tune Facebook's DETR (DEtection TRansformer) on balloon dataset (custom object detection dataset) The goal for the model is to recognize balloons in pictures.

### Dataset

DETR will be fine-tuned on a custom dataset: the balloon dataset. The dataset is taken from here. The balloon dataset comes in the VIA annotation format. However, to prepare the annotations for the model, DETR expects them to be in COCO format.

The following Github repo is used to convert annotations from VIA format to COCO format

There are 61 images in the training set, and 13 images in the validation set.

The directory structure would be as following:

### Training

https://github.com/dataplusplus-ai/EVA7/blob/main/DEtr/finetune_detr.ipynb trained for 150 epochs


 ### Error plots and metrics
 
 Metrics to monitor the training include:

the Average Precision (AP), which is the primary challenge metric for the COCO dataset,
losses (total loss, classification loss, l1 bbox distance loss, GIoU loss),
errors (cardinality error, class error).


![image](https://user-images.githubusercontent.com/45157166/150644098-7db003fd-08cc-4393-a254-d8a62597e4d5.png)

![image](https://user-images.githubusercontent.com/45157166/150644111-f7adbb64-e721-4bae-a2c4-ec7161119d22.png)


### Training Image

![image](https://user-images.githubusercontent.com/45157166/150644054-989b9a5d-0741-46c4-9ed8-2054a82baa83.png)



### validation Image

![image](https://user-images.githubusercontent.com/45157166/151703242-d7005511-32fa-4f8c-99b3-b2d8fa23fe67.png)

