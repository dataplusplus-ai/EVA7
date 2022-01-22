
##End-to-end object detection with Transformers


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






![image](https://user-images.githubusercontent.com/45157166/150644174-45b03a7c-7d49-4687-a49f-bcf78234c8e8.png)













error plots

![image](https://user-images.githubusercontent.com/45157166/150644098-7db003fd-08cc-4393-a254-d8a62597e4d5.png)

![image](https://user-images.githubusercontent.com/45157166/150644111-f7adbb64-e721-4bae-a2c4-ec7161119d22.png)




Training Image

![image](https://user-images.githubusercontent.com/45157166/150644054-989b9a5d-0741-46c4-9ed8-2054a82baa83.png)



validation Image

https://github.com/dataplusplus-ai/EVA7/blob/main/DEt
