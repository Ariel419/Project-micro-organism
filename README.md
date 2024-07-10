# Project micro-organism
 
This program aims to identify multiple types of micro-organsim. In fact, they aren't all dangerous and are very useful for human growth. By detecting which micro-organism is which, scientists can use this AI model to exploit them carefully in an experiment.


![Screenshot (1)](https://github.com/Ariel419/Project-micro-organism/assets/174376607/ffc0ecaa-1769-4a42-8603-5f1907a0869c)

description:



## The Algorithm

We employed a **convolutional neural network(CNN)** named *resnet 18*, which essentially accelerates the process by which nanocomputers percieve patterns in disparate images of the same object.

The primary model for image classification, **imagenet**, was already there and was utilised to train new models.

The object could be **anything**, including, animals,food, emotions and even more as long as it has a **distinctive appearance** and can be given a name.

This image shows how Convolutional Neural Network works:

![image](https://github.com/Ariel419/Project-micro-organism/assets/174376607/2a6212d8-561d-4385-a8d2-81058f2d636c)


When using CNN, the 3 primary component sizes that must be specified are batches, workers and epochs:

1) The number of photographs displayed to the system at once depends on the **batch size**.
   
 -->' --batch-size=NumberOfBatchFiles'
 
2) The number of **workers** determines how many batches the machine processes at once.
   
 -->'--workers=NumberOfWorkers'
 
3) The number of times this whole process will occur is indicated by the **epochs**.

 -->'--epochs=NumberOfEpochs'
 
You may see Train Loss, Train Accuracy, Val Loss, Val Accuracy for each epoch.

1) **Train Loss**:a statistic that directs the optimisation process during training

2) **Train Accuracy**:a percentage of correctly prdicted values across the dataset

3) **Val Loss**: Calculates the error on the training set for every model training iteration

4) **Val Accuracy**: the proportion of right guesses made over a random set of images

Finally, to print the image with the labels, we can use this command (if the dataset is about cats and dogs):
'imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/cat/01.jpg cat.jpg'

# Limitations

There are certain limitations to the way this CNN functions since it is up to the programmers to decide how many epochs are over or under the perfect fit.
This is because executing the same images too many times will **overfit** the data and become **less able to generalise** to new scenarios. 
However, if you employ a small amount of epochs, the model may **undefit** the data and **miss the fundamental patterns** and perhaps **misclassify images** that belong in other classes. The best method for identifying the ideal ratio, is by **experimenting**.

As we can see by this image, anything between 0 to 6 epochs is in a **unregular pattern** and not accurate enough. 

![image](https://github.com/Ariel419/Project-micro-organism/assets/174376607/1b0757c7-e8c9-4e75-91b1-dba3ada52c51)


# Running this project

1) **Chose the image classification** you would like to pursue in your program. In my case, I chose the dataset of **micro-organism**. Each image saved from the dataset needs to be different from the other files in the dataset.

2) Chose **minimum** 100 images for each micro-organism.

3) On **visual studio code**, go to 'jetson-inference/python/training/classification/models' and create a new folder called 'micro-org1'

4) Inside the 'micro-org1' folder, make 3 folers called **train, test, val** without forgetting the file named **labels.txt**

5) Write in the file labels.txt a list in alphabetical order of the chosen micro-organism

6) Each of the test, train and val folders should have a folder named after each micro-organisms. Such as Yield, Euglena or Hydra. 

7) The micro-organism folder should have **10%** of the images for each chosen micro-organism in **test** and **val**, while the other **80%** should be in **train**.

8) Make sure to then go back into 'jetson-inference' and proceed by going into './docker/run.sh', this command will create a new container and run it or even take an image if needed.

9) Inside of the docker container,  change directories so you are in 'jetson-inference/python/training/classification' and paste 'python3 train.py --model-dir=models/micro-org1 data/micro-org1'. This script contains the code that will train the model.

10) You can then chose how the model runs with:
    '--batch-size=NumberOfBatchFiles'
    '--workers=NumberOfWorkers'
    '--epochs=NumberOfEpochs'

11) When the program finished running the number of epochs chosen, make sure you are in the 'docker container' and in 'jetson-inference/python/training/classification'

12) You can then run this script: 'python3 onnx_export.py --model-dir=models/micro-org1'. This program will save the training as 'resnet18.onnx' to your 'micro-org1 folder'

13) Use 'Ctrl+D' to exit the docker container so we can then change docker to the nano to see if the training actually works.

14) Go into the 'jetson-inference/python/training/classification' directory and then input 'ls models/micro-org1/' to make sure that the model is on the nano

15) Set the **NET** and **DATASET** variables as followed : 'NET=models/micro-org1' and 'DATASET=data/micro-org1'

16) Finally run 'imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/Hydra/Image_11.jpg micro-org3.jpg' to see your image chosen labelled correctly with the type of **micro-organism's name** and **percentage of accuracy**.

