# Faster-RCNN
Startup of Vehicle Detection Using Faster RCNN Framework

Step 1: Convert your KITTI dataset same as the format of PASCAL VOC
We can refer to this blog
http://blog.csdn.net/Jesse_Mx/article/details/65634482
and the complete tramsform dataset code has been uploaded.

Step 2: Run the Faster RCNN project
The tutorial can be found via fowllowing link
https://github.com/ruotianluo/pytorch-faster-rcnn

Step 3: Revise the Faster RCNN project to realize vehicle detection and vehicle orientation detection
The corresponding code has been uploaded. 
Implementation details:
1° We should change the class types that are needed to recognize in lib/datasets/pascal_voc.py, and modify the function _load_pascal_annotation(self, index) to add your data information.

2° It is much important to understand the usage/package of training/testing data in Faster RCNN project. The approximate procedure is "data+annotation+affiliated info" ---> "roidb" ---> "blobs" ---> "training data and label". Only understand its machenism can we add the training data that we want flexiblily. The relating files/functions are lib/datasets/imdb.py/append_flipped_images(self), roi_data_layer/minibatch.py, nets/network.py/_predict(self)/_region_proposal(self, net_conv)/_proposal_target_layer(self, rois, roi_scores)/proposal_target_layer()/_sample_rois()...

3° Modify network architechture in nets/network.py/create_architechture()/_init_modules()

4° Modify forward propagation in modle/train_val.py/train_step_with_summary() and train_step()-->/forward()/_predict()/_region_proposal() and _region_classification(), and the /forward()/_add_losses()

5° Modify the test files such as tools/demo.py, model/test.py, nets/network.py/test_image(), etc.

It is my first project to enter the deep learning area and will be quite interesting when finished. Hope you have a good luck.
