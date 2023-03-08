# jpg-image-bunch

This code is used to read a set of images of individual trees of four different species, resize them, and save them to a file as a serialized Bunch object using joblib.

## Dependencies
This code requires the following libraries:

* os
* numpy
* joblib
* cv2

## Usage
1. First, make sure that all the required libraries are installed.
2. Clone this repository and navigate to the root directory.
3. Make sure that the images of the trees are stored in the 'D:/Individual_Trees_photos/exatctcrop' directory, and that the directory contains subdirectories for each of the four species of trees.
4. Run the  file using a Python interpreter.
5. After the code finishes executing, a serialized Bunch object will be saved to a file named tree_images.joblib.
