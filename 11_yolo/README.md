
## OpenCV Yolo:
Followed the steps listed here https://pysource.com/2019/06/27/yolo-object-detection-using-opencv-with-python/

Took a image with object which is there in COCO data set (search for COCO classes to learn).

Ran this image through the code above and the notebook here https://github.com/dataplusplus-ai/EVA7/blob/main/11_yolo/openCV_yoloV3/yolov3_object_detection.ipynb



Uploaded the annotated image by YOLO OpenCV.

## Training Custom Dataset on Colab for YoloV3

Refer to this Colab File https://colab.research.google.com/drive/1LbKkQf4hbIuiUHunLlvY-cc0d_sNcAgS

Refer to this GitHub Repo https://github.com/theschoolofai/YoloV3

Download this dataset https://drive.google.com/file/d/1sVSAJgmOhZk6UG7EzmlRjXfkzPxmpmLy/view

Collect and add 25 images for the following 4 classes into the dataset shared:

class names are hardhat, vest, mask and boots, its also listed in custom.names file

follow exact rules to make sure that you can train the model. Steps are explained in the README.md file on github repo link above.

Once additional 100 images are added, train the model

Next,

Download a very small (~10-30sec) video from youtube which shows the 4 classes.

Use ffmpeg to extract frames from the video.

Infer on these images using detect.py file.

python detect.py --conf-three 0.3 --output output_folder_name

Use ffmpeg to convert the files in your output folder to video

Upload the video to YouTube.

The notebook here https://github.com/dataplusplus-ai/EVA7/blob/main/11_yolo/custom_yolov3_training/YoloV3_CustomData.ipynb
