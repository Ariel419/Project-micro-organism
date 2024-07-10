# Project-micro-organism
 
This program aims to identify multiple types of micro-organsim. In fact, they aren't all dangerous and are very useful for human growth. By detecting which micro-organism is which, scientists can use this AI model to exploit them carefully in an experiment.


![Screenshot (1)](https://github.com/Ariel419/Project-micro-organism/assets/174376607/ffc0ecaa-1769-4a42-8603-5f1907a0869c)

description:



## The Algorithm

Add an explanation of the algorithm and how it works. Make sure to include details about how the code works, what it depends on, and any other relevant info. Add images or other descriptions for your project here. 

We employed a convolutional neural network(CNN) named resnet 18, which essentially accelerates the process by which nanocomputers percieve patterns in disparate images of the same object.

The primary model for image classification, imagenet, was already there and was utilised to train new models.

The object could be anything, including, animals,food, emotions and even more as long as it has a distinctive appearance and can be given a name.

When using CNN, the 3 primary component sizes that must be specified are batches, workers and epochs:

1) The number of photographs displayed to the system at once depends on the batch size.
   
 -->' --batch-size=NumberOfBatchFiles'
 
2) The number of workers determines how many batches the machine processes at once.
   
 -->'--workers=NumberOfWorkers'
 
3) The number of times this whole process will occur is indicated by the epochs.

 -->'--epochs=NumberOfEpochs'
 
You may see Train Loss, Train Accuracy, Val Loss, Val Accuracy for each epoch.

1) Train Loss:a statistic that directs the optimisation process during training

2) Train Accuracy:a percentage of correctly prdicted values across the dataset

3) Val Loss: Calculates the error on the training set for every model training iteration

4) Val Accuracy: the proportion of right guesses made over a random set of images

Finally, to print the image with the labels, we can use this command (if the dataset is about cats and dogs):
'imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/cat/01.jpg cat.jpg'

Limitations:

There are certain limitations to the way this CNN fucntions since it is up to the programmers to decide how many epochs are over or under the perfect fit. This is because executing the same images too many times will produce pockets that are way too small to accomodate all of the more broadly applicable patterns in the images, but executing the same images infrequently will produce very few patterns and misclassify images   

1. Add steps for running this project.
2. Make sure to include any required libraries that need to be installed for your project to run.

[View a video explanation here](video link)
