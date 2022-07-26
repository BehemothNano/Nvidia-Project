# Nut Recognition

 The goal of this project was to train ResNet 18 to recognize different types of nuts as some nuts look alike, which isn't good for people with allergies. It's quite basic, and not super accurate, but it seems to work well enough.

## Running this project

1. Enter the following line into a terminal or command prompt window, and enter the password when prompted. Afterwards, ssh into the Jetson.
```
scp archive.zip <remote username>@<ip>:/home/<remote username>/jetson-inference/python/training/classification
```
2. Then enter the following lines to put the files in the correct places, run the model, and view the output:
```
cd jetson-inference/python/training/classification

unzip archive.zip

cd archive

mv nuts_dataset ../data/nuts

mv nuts_model ../models/nuts

cd ..

NET=models/nuts

DATASET=data/nuts

imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/<test image class>/1.jpg name.jpg

scp <remote username>@<ip>:/home/<remote username>/jetson-inference/python/training/classification/name.jpg C:\Users\<host username>\Downloads
```
### Dataset source:
https://www.kaggle.com/datasets/gpiosenka/tree-nuts-image-classification?resource=download
