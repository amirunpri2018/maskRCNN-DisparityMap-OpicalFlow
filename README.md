# Mask R-CNN with DisparityMap and OpicalFlow
Using Disparity Map and Optical Flow info to extract features from the detected objects by maskRCNN.

![maskRCNN with DisparityMap and OpicalFlow](https://i.imgur.com/kweos0Q.png)

 ## Citation:
 ```
@misc{rateke:2020.2,
    author = {Rateke, Thiago and Wangenheim, Aldo von},
    title = {Road obstacles positional and dynamic features extraction combining object detection, stereo disparity maps and optical flow data},
    journal={Machine Vision and Applications},
    year = {2020},
    month={Sep},
    day={25},
    volume={31},
    number={7},
    pages={73},
    issn={1432-1769},
    doi={10.1007/s00138-020-01126-w},
    url={https://doi.org/10.1007/s00138-020-01126-w}
}
```
 - [Original Paper](https://rdcu.be/b7I4f)
 

## Disparity Map: 
First of all you need to build the disparity map images. To do this, we use the Stereo Vision code in filteredDisparityMap.cpp

To compile, type in your terminal: g++ filteredDisparityMap.cpp -lopencv_core -lopencv_videoio -lopencv_highgui -lopencv_imgcodecs -lopencv_imgproc -lopencv_calib3d -lopencv_features2d -lopencv_ximgproc -o veRun

![Disparity Map](https://i.imgur.com/272ZWIP.png)

**Caution**: It has absolute path in the Disparity Map code for the rectified images that should be used for the construction of the Disparity Map. You will need to change the absolute paths or change to use argv.

If you need to calibrate your stereo setup or rectify your images see the code in https://github.com/thiagortk/stereoVision.

## Optical Flow: 
It's  computed in the code along with maskRCNN. We use the FarneBack algorithm available in OpenCV. We use the Disparity Map previously computed.

![Optical Flow](https://i.imgur.com/gjI1yCr.png)

## Mask R-CNN:
Example edited from: https://www.learnopencv.com/deep-learning-based-object-detection-and-instance-segmentation-using-mask-r-cnn-in-opencv-python-c/

![Mask R-CNN](https://i.imgur.com/DXkW2uM.png)

**Download and extract the model files**: <br/>
wget http://download.tensorflow.org/models/object_detection/mask_rcnn_inception_v2_coco_2018_01_28.tar.gz <br/>
tar zxvf mask_rcnn_inception_v2_coco_2018_01_28.tar.gz

## Images:
For the images used here, 2 datasets were used:
 - KITTI dataset [1].
 - CaRINA dataset [2].
 
## REFERENCES:
- [1] - GEIGER, A. et al. Vision meets robotics: The kittidataset. Int. J. Rob. Res., Sage Publications, Inc., ThousandOaks, CA, USA, v. 32, n. 11, p. 1231–1237, sep 2013. Doi:hhttp://dx.doi.org/10.1177/0278364913491297i. Url: http://www.cvlibs.net/datasets/kitti/raw_data.php </br>
- [2] - SHINZATO, P. Y. et al. Carina dataset: An emerging-country urban scenario benchmark for road detection systems.In:2016 IEEE 19th International Conference on IntelligentTransportation Systems (ITSC). [S.l.:  s.n.], 2016. p. 41–46.Doi:hhttp://dx.doi.org/10.1109/ITSC.2016.7795529i. Url: http://www.lrm.icmc.usp.br/dataset  </br>
