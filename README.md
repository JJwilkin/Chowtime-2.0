# Chowtime-2.0
Steps to reproduce training:

1.  Make a collection of desired images for each class. Preferably over 100 images for each class (100 images of apples, 100 images of pears). Ensure the images vary in lighting and compusure. Place all the images into /images/training
2.  Process all the images and resize them to a 800x600 resolution. This can be done with an included script. In the Chowtime-  2.0 directory, run ```python transform_image_resolution.py -d images/ -s 800 600``` . This will transform all the pictures in the /images directory to 800x600 resolution.

3. Select 20% of the images, ideally an even amount from each class, and transfer them from ```/images/training to /images/test```. These images will be used to test the model. 

4. Using labelling software such as LabelImg (https://github.com/tzutalin/labelImg), create bounding boxes and label according to the class name ('apple',  'pear'). Ensure the name of the labels is consistent and you easily remembered as these names will be used throughout this process. For the labelling process, save the files in the same directory as the images, this will be the default directory when you click "Save" on each image. Ensure to use the PascalVOC format.

5. After labelling is complete, there will be .xml files for each associated image. Tensorflow requires these labels to be formatted in a specific manner, we will use the script generate_tfrecord.py to do this. Open the generate_tfrecord.py in a text editor and navigate to the ```def class_texd_to_int(row_label): ``` function. Here we will need to add our labels for the different classes. ex. ```if row_label =='apple': return 1\ elif row_label =='pear': return 2 \ elif row_label =='orange': return 3 \ else: return None``` would be the code for 3 classes ('apple', 'pear', 'orange').
