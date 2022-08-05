---
layout: page
title: Pedestrian Multiple Object Tracking Using Deep Learning
description: Examining the viability of Deep Neural  Network (DNN) based Multi-Object Tracking approaches for tracking pedestrians.
img: assets/img/projects/Pedestrain_tracking.png
importance: 1
---

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Pedestrain_tracking.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  Overall tracking flow.
</div>

The goal of this thesis project was to investigate the viability of Deep Neural Network (DNN)-based Multi-Object Tracking approaches for tracking pedestrians. The tracking data is used in the Autonomous Driver Assistance System (ADAS). Multiple Object Tracking refers to the process of tracking multiple agents across video (MOT). The use of pedestrian detection alone for ADAS is inferior to the use of pedestrian tracking to determine the next action to be taken. Tracking pedestrians allows one to predict their next location with high accuracy. Furthermore, pedestrians may be missed in certain situations, such as occlusion, and the system fails to provide the stability required for safety priorities. A customized version of YOLO v3 is used to detect pedestrians.

The most common tracking issues are ID switches and losing track of objects due to occlusion. Deep SORT and SORT-OH tracking methods are used to track pedestrians. The Deep SORT method makes use of motion features obtained through the Kalman filter and appearance features obtained through the CNN feature encoder developed for Person Re-ID. SORT-OH is a method for dealing with occlusion and re-identifying targets using geometric cues. It has been discovered through ablation research that Re-Identification is critical in obtaining good tracking results. Using different object detectors DPM, SDP, and Faster R-CNN, it was also possible to conclude that detection quality is important in the performance of the Object Tracking approach.

Both Deep SORT with DNN based Re-ID and SORT-OH with geometric cue-based Re-ID features perform similarly, demonstrating the potential of DNN techniques in object tracking. Both the MOT methods obtained good results by  minimizing ID switches and handling occlusion, even in a difficult  situation with blur and varying illumination.

Based on the findings of the research, it is possible to conclude that DNN-based methods can be used as a viable alternative in the MOT pipeline. The tracking results of two implementation methods on open source data shows that a MOT strategy that employs DNN-based Re-ID, is equivalent to SORT OH, which employs geometric cues for Re-ID.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/DS_Vs_SOH.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  Overall tracking performance comparing two MOT methods on MOT 17 data set using average of DPM, SDP and Faster R-CNN object detectors.
</div>

DNN-based methods can help MOT during the detection and Re-ID stages. Target Re-Identification, as shown in the graph below, plays a critical role in improving MOT performance. Target Re-Identification contributes significantly to improved performance. The MOTA rises from 20.5 percent to 43.2 percent. The Target Re-Identification task makes it possible to track pedestrians more reliably by reducing fragmentation, reducing ID switches, and increasing the number of tracks tracked. Furthermore, a comparison of appearance features between DNN-based Re-ID features, RGB, and HSV color spaces demonstrates the robustness of Re-ID features. Tight clusters in the visualization represent the Re-ID feature's robustness.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Effectiveness_REID.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Ablation test to evaluate Effectiveness of Re-ID features.
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/Visualization_REID.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  Visualization of RGB histogram features, HSV histogram features
  and our Re-ID features.
</div>

When the tracking results it is clear that the tracking-by-detection approaches rely excessively on detection quality. MOTA increases from 22.2 percent DPM detector to 61.3 percent SDP by simply changing the tracking detection. Good detection quality allows tracking to perform well, but it is impossible to achieve good detection in difficult situations such as poor illumination or high occlusion. As a result, putting more emphasis on other components of the tracking pipeline will allow the approach to work across a broader range of scenarios.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/DS_Result.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  Continuous frame of sequence illustrating how well ID switch are handled by DeepSORT.
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/projects/SOH_Result.PNG" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
  Continuous frame of sequence illustrating how well ID switch are handled by SORT-OH.
</div>
