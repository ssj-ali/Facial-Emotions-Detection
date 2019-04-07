# Facial-Emotions-Detection
It's my first try on Neural network. My idea is to make an android app that detects facial emotions of the user and displays the content accordingly. Lol;)
Currently it detects only three expressions i.e Happy, Angry & Sad. I am working on it to make it more precise and then I will add more emotions.

## Steps:
1. Install Python (Anaconda recommended for Windows)
2. Install all the necessary modules like numpy. Most likely, you will get all thse libraries preinstalled if you are using Anaconda.
3. After installing Anaconda, run Anaconda command prompt
4. Copy paste these two lines:

```
pip install tensorflow`
pip install opencv-python
```
Now tensorflow and opencv is installed
opencv is used to open webcam while tensorflow is used for training the model.

**Note:** I'm using the "Frontal Face Alt" Classifier for detecting the presence of Face in the WebCam. This file is included with this repository. You can find the other classifiers
Please note that 'haarcascade_frontalface_alt.xml' is the classifier. It is nothing but a pretrained model that finds the faces in the input data either from images, videos or during runtime.

6. Now download all the files I have uploaded here as a zip and then unzip it. **Make sure that everything remains in the same folder named 'Facial-Emotions-Detection'**
7. Now download atleast 100 images of every emotions you want to add and **keep them somwhere else (other than our main folder i.e Facial-Emotions-Detection)**
8. This is because the pictures you have downloaded may contain multiple faces or contain un-necessary objects. You can crop all the faces one by one by yourself or you can do this by running a simple python script. Just open the **face_crop.py** using Spyder(if you have anaconda) or any other editor (IDLE or Notepad).
9. Before running **face_crop.py**, commit this changes in the code:
```
## directory where you have dowloaded the images:
directory = "C:\\Users\\Asus\\Downloads\\angrypics\\"

## directory where the cropped images to be saved:
f_directory = "C:\\Users\\Asus\\Downloads\\croppedangrypics\\"
```
It was just an example. You have to do this for every emotions folder. 

10. Now copy all the cropped-images group-wise and paste it under the sub-folders of the folder **emotions**
 **Note that the sub-folder names are the labels which you will see at output (ie opencv window). Obviously you can add as many emotions as you want by just adding subfolders and placing relevant images in that.**
 So our training dataset (in this case it is the folder **emotions**) is complete.
 
 11. Now, its time to train our model. 
 Go to Anaconda Command Prompt, **change the directory** to our main folder i.e **Facial-Emotions-Detection**. Google it if you dont know how to change directories
 
 12. This step may take some time. Copy paste the commands given below:
 ```
 python retrain.py --output_graph=retrained_graph.pb --output_labels=retrained_labels.txt --architecture=MobileNet_1.0_224 --image_dir=emotions
 ```
 Note: For this purpose I have used **Mobilenet Model** which is quite fast and not as accurate as **Inception V3**.
 
 13. It's all done. You can notice that two new files have been added to the folder named as 'retrained_graph.pb' and 'retrained_labels.txt'.
 
14. Only thing that is left is to see it working. Open Anaconda Command Prompt & run the following code:
```
python label.py
```
Cheers!!






**Note:** If you are getting this error "ImportError: numpy.core.multiarray failed to import"  update numpy, run this in anaconda command prompt
```
pip install -U numpy
```
 **Note:** The training of the model may not get completed due to some corruptec image. Just notice the error message and see the image name where it is getting struck. Delete that image from the sub-folders and restart from the step 12.
