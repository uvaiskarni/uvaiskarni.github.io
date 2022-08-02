---
layout: page
title: Hand Gesture recognition
description: Developed an end to end image classification system using Fast R-CNN Network to predict 6 hand gestures.
img: assets/img/projects/HandGestureRecognition.png
importance: 3
---

The smart hand gesture recognition system can detect six different hand gestures, as listed in table below, and reacts accordingly. The system consists of three subsystems. The input of the system is a video containing a hand gesture, first subsystem processes the video and extract landmarks of the hand in each frame then pass it to the trained machine learning model to decide which hand gesture is present in each frame then the detected gesture will be shown to the user in order to give a voice command to Furhat robot with the detected gesture to do facial expressions and speech sentences depending upon the type of gesture.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Response_Gestures.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
     System responses to gestures
</div>

It has three subsystems: 1.Landmark extraction (First Sub-system), 2.Gesture recognition (Second Sub-system) and 3.Responsive behavior (Third Sub-system). Apart from these a fourth one called end to end subsystem (Specialisation).

1.Landmark extraction (First Sub-system):

This subsystem utilizes a pre-trained model from to detect the keypoints on different hand gesture images. The detector follows the architecture of Convolutional Pose Machines(CPMs). The subsystem 2 which is trained using the provided CSV data-set requires the landmark points to be structured as dorsal and palm points separately. To achieve this a separate SVM classifier is trained on a limited set of frames for each video to distinguish between the input frames as palm and dorsal regions. Then each video is read from the given data-set and the region type is predicted using the trained classifier. After that the pre-trained model[1] is loaded for keypoints detection and the landmark
points are drawn. Based on the region type determined from the classifier the landmark points are structured to be passed to the subsystem 2 model to predict the final gesture type. To connect the subsystem 1 with subsystem 2 the model which was trained in the second subsystem using the CSV data-set is loaded and the gesture type is predicted by passing these landmark points obtained as input.

2.Gesture recognition (Second Sub-system):

Second Subsystem is developed using Keras, a deep learning API where the model is designed with three dense layers and relu activation function in the hidden layers and sigmoid function in the output layer. Stochastic gradient descent(SGD) is used as an optimizer function and categorical cross entropy as loss function. The model is trained for 10 epochs.

3.Responsive behavior (Third Sub-system):

The main functionality in the third subsystem is to react appropriately by Furhat social robot to the detected hand gesture that is detected by first and second subsystems. The initial design was to connect first and second subsystems to Furhat robot via TCP connection. Due to time limit, this feature is replaced by involving a human in the communication by reading the output of the second subsystem and give voice command to Furhat robot in order to react. Furhat robot reactions consists of two aspects: Facial expressions and saying a sentence. The input and output of this subsystem as shown in prior table above.

4.End to End Subsystem (Specialisation):

An Object Detection API to train a Fast Region Convolution Neural Network is used. The reason we chose Fast R-CNN is that it can classify multiple objects with low latency. The input features to the network are raw frames from the videos and output is a CSV file containing the desired class (Hand Gesture) and position of the hand in the frame. The Faster R-CNN has three components:
  – Convolution Layers: To extract features from images.
  – Region Proposal Network: To check whether the desired object is present or not. If the object is present then a bounding box for those object are given out.
  – Classes Detection: Here the bounded region part of the images are classified. It simply flattens the bounding region of the image and passes it through several dense layer and then a final Softmax layer which returns probabilities for each class.

  <div class="row">
      <div class="col-sm mt-3 mt-md-0">
          {% include figure.html path="assets/img/projects/H_01_res.png" title="example image" class="img-fluid rounded z-depth-1" %}
      </div>
  </div>
  <div class="row">
      <div class="col-sm mt-3 mt-md-0">
          {% include figure.html path="assets/img/projects/H_02_res.png" title="example image" class="img-fluid rounded z-depth-1" %}
      </div>
  </div>
  <div class="row">
      <div class="col-sm mt-3 mt-md-0">
          {% include figure.html path="assets/img/projects/H_03_res.png" title="example image" class="img-fluid rounded z-depth-1" %}
      </div>
  </div>
  <div class="caption">
       Results from the end to end subsystems
  </div>
