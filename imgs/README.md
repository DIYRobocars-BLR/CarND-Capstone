## Taffic Light Detection Node
[image1]: ./data/results/ssd_vertical.jpg
[image2]: ./data/results/real_ssd.jpg
Traffic Light Detection is a crucial part in perception module in self-driving car to make the vehicle able to recognise the traffic light's status to take the right action either to stop or continue driving. the on-board vehicle's camera provides this node the image frames to this node and publish the traffic light's status to /traffic_waypoint topic. According to this information the waypoint updater node determines the vehicle's action either to stop, slow down or continue driving.

Our solution is implemetation of deep learning model for the simulator and test site. We used Tensorflow Object Detection API to dettect the traffic light status. We experimented two models `ssd_inception_v2_coc` and `faster_rcnn_inception_v2_coco` for this part. We decided to use for simulator and Carla submissions the `ssd_inception_v2_coc` due to it's performance in detection detection and processing time. This model is a pre-trained model on COCO dataset for 90 diffrent classes. the light traffic is included in the COCO dataset but it just localise the traffic light and doesn't detect its status. Therefore, we re-trained the model on Simulator and site data to make single shot detection. we extracted the train data form the simulator and ROSbag file and modified the model `ssd_inception_v2_coco-sim.config` and `ssd_inception_v2_coco-real.config` file to be suited to our needs. More information about setup and training can be found in  [Traffic Light Detector](https://github.com/Eng-Mo/Traffic-Light-Classifier.git) and the following is the result.       

![title][image1]
![title][image2]

### Latency solution






