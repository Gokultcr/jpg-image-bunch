# jpg-image-bunch

This code is used to read a set of images of individual trees of four different species, resize them, and save them to a file as a serialized Bunch object using joblib.\n
**
import os
import numpy as np
import joblib
import cv2 **    These lines import the necessary libraries for the code to run.

**
dire = "D:/Individual_Trees_photos/exatctcrop"
categories = ['European beech', 'European silver fir', 'Norway spruce', 'Sessile oak']
**  These lines define the directory where the images are stored and the categories of the different species of trees. 


**
SIZE = 200
images = []
labels = []
**   These lines define the size of the images after resizing and create empty lists to store the images and their labels.

**
for category in categories:
    path = os.path.join(dire, category)
    label = categories.index(category)
    
    for img in os.listdir(path):
        imgpath = os.path.join(path, img)
        tree_img = cv2.imread(imgpath, 0)
        try:
            tree_img = cv2.resize(tree_img, (SIZE, SIZE))
            images.append(tree_img)
            labels.append(label)
        except Exception as e:
            pass
**   These lines loop through each category of trees and read in each image from the corresponding directory. Each image is resized and added to the images list, while the corresponding label is added to the labels list. Any exceptions thrown during the resizing process are ignored.

**
images = np.array(images)
labels = np.array(labels)
** These lines convert the images and labels lists to NumPy arrays.

**
feature_names = ['images']
target_names = categories
** These lines define the feature and target names for the Bunch object.

**
data = {}
data["data"] = images
data["target"] = labels
data["feature_names"] = feature_names
data["target_names"] = target_names
** These lines create a dictionary to store the data, with the images and labels arrays as the data and target values, respectively. The feature and target names are also added to the dictionary.

**
joblib.dump(data, 'tree_images.joblib')
** This line saves the dictionary as a serialized Bunch object to a file named 'tree_images.joblib; using the joblib.dump() function.



