---
layout: page
title: Pedestrian Multiple Object Tracking Using Deep Learning
description: Examining the viability of Deep Neural  Network (DNN) based Multi-Object Tracking approaches for tracking pedestrians.
img: assets/img/projects/Pedestrain_tracking.png
importance: 1
category: Master Thesis
---

In this thesis, the aim is to examine the viability of Deep Neural  Network (DNN) based Multi-Object Tracking approaches for tracking  pedestrians. The tracking results are used for Autonomous Driver Assistance System (ADAS). The process of tracking multiple agents  across video is termed as Multiple Object Tracking (MOT). Using only  pedestrian detection for ADAS is inferior to using pedestrian tracking  to determine the next action to be taken. By tracking pedestrians, one  can predict their next position with great accuracy. Furthermore,  pedestrians may not be detected in certain instances such as occlusion, and thus the system fails to deliver the stability needed  for safety priorities. For detecting the pedestrians, a custom version  of YOLO v3 is applied.

The most common problems that arise in tracking  are ID switches and losing track of objects due to occlusion. Two  tracking methods Deep SORT and SORT-OH are utilised to track  pedestrians. The Deep SORT approach uses motion feature obtained by  Kalman filter and appearance feature obtained using CNN feature  encoder developed for Person Re-ID. SORT-OH is an approach that  handles occlusion and re-identifies targets using geometric cues. By  the means of ablation study, it is found that Re-Identification plays  a critical role in obtaining good tracking results. Also by using  different object detectors DPM, SDP and Faster R-CNN, it could be  concluded that the quality of detection plays a vital role in the  performance of the Object Tracking approach. Both Deep SORT with DNN based Re-ID and SORT-OH with geometric cue-based Re-ID features  perform similarly, demonstrating the potential of DNN techniques in  object tracking. Both the MOT methods obtained good results by  minimizing ID switches and handling occlusion, even in a difficult  situation with blur and varying illumination.

Based on the results obtained through research work it can be concluded that DNN based methods can be used as a viable alternative in the MOT pipeline. The tracking outcomes of two implemented ways are shown in Table demonstrating that DeepSORT, a MOT strategy that uses DNN-based Re-ID, is equivalent to SORT OH, which uses geometric cues for Re-ID.

<table>
<tr>
<td colspan=1>
Overall tracking performance comparing two MOT methods on MOT 17 data set using average of DPM, SDP and Faster R-CNN object detectors
</td>
|Methods | IDF1 | MT | FM | MOTP | MOTA |
|--- | --- | --- | --- |--- |--- |
|Deep SORT | 51.30% | 272 | 3091 | 0.151 | 43.20% |
|SORT OH | 52.80% | 369 | 2869 | 0.16 | 45.40% |
</tr>

DNN based methods can assist MOT in detection and Re-ID stages. As stated by results from the Table below Target Re-Identification plays a vital role in improving the performance of MOT. Target Re-Identification contributes to a large increase in performance. MOTA increases from 20.5% to 43.2%. Target Re-Identification task allows pedestrians to be tracked robustly by reducing fragmentation, reducing ID switches and increasing number of tracks tracked. Also, the comparison of appearance features in Figure 4.1 between DNN based Re-ID feature, RGB and HSV colour space illustrates the robustness of Re-ID features. Tight clusters in the visualisation represent the robustness of the Re-ID feature.

Comparing the tracking results present in Table 4.2, 4.3, and 4.4, it is clear that the tracking-by-detection approaches rely tediously on the quality of detections. MOTA increases from 22.2% DPM detector to 61.3% SDP by just changing detection used for tracking. Good detection quality allows the tracking to perform good but in a difficult situation such as poor illumination or high occlusion, it is not possible to get good detection. Therefore more emphasis on other components of the tracking pipeline will allow the approach to work across a wider compilation of scenarios.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Caption photos easily. On the left, a road goes through a tunnel. Middle, leaves artistically fall in a hipster photoshoot. Right, in another hipster photoshoot, a lumberjack grasps a handful of pine needles.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This image can also have a caption. It's like magic.
</div>

You can also put regular text between your rows of images.
Say you wanted to write a little bit about your project before you posted the rest of the images.
You describe how you toiled, sweated, *bled* for your project, and then... you reveal it's glory in the next row of images.


<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
</div>


The code is simple.
Just wrap your images with `<div class="col-sm">` and place them inside `<div class="row">` (read more about the <a href="https://getbootstrap.com/docs/4.4/layout/grid/">Bootstrap Grid</a> system).
To make images responsive, add `img-fluid` class to each; for rounded corners and shadows use `rounded` and `z-depth-1` classes.
Here's the code for the last row of images above:

{% raw %}
```html
<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
```
{% endraw %}
