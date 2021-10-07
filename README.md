## ADVANCED  OBJECT IDENTIFICATION  IN IMAGES

<p> Build an object detection and recognition solution which can identify an object spread out across a grid of images with over 90% accuracy. 
The object to be identified shall belong to one of the following categories: </p>
<ul>
 <li> Vehicles such as cars and motorcycles </li>
 <li> Road signage such as zebra crossings and traffic lights </li>
 <li> Structures such as bridges and buildings, and will be provided as an input parameter to the solution</li>
</ul>


## WHAT IS OBJECT DETECTION?

<p> Object detection refers to the capability of computer and software systems to locate objects in an image/scene and identify each object. Object detection has been widely used for face detection, vehicle detection, pedestrian counting, web images, security systems and driverless cars.
</p>

<img src="https://user-images.githubusercontent.com/69414725/136423269-468e94cd-d943-44a1-bb78-b9c45068d54d.jpg">

## YOLO FOR OBJECT DETECTION

<h3> Basic architechure of yolo </h3>

<ul>
   <li> YOLO, short for You Only Look Once is a convolutional neural network architecture designed for the purpose of object detection. </li>
  <li>Image classifiers were used to carry out the task of detecting an object by scanning the entire image to locate the object. </li>
  <li> The process of scanning the entire image begins with a pre-defined window which produces a boolean result that is true if the specified object is present in the scanned section of the image and false if it is not.</li>
  <li> After scanning the entire image with the window , the size of the window is increased which is used for scanning the image again. Systems like deformable parts model (DPM) uses this technique which is called Sliding Window.</li>
  
</ul>

<p> Other detection methods like R-CNN and Fast R-CNN are primarily image classifier networks which are used for object detection with the following steps.</p>
<ol> 
  <li> Use Region Proposal method to generate potential bounding boxes in an image.</li>
  <li>Run the classifier on these boxes.</li>
  <li>After classification, perform post processing to tighten the boundaries of the bounding boxes, remove duplicates.</li>
</ol>

<p>These pipelines prove to be complex and bulky and hard to optimize as each component needs to be trained separately. Also such a pipeline is often very slow during inference.</p>

## How is YOLO different?

<p>YOLO is different from all these methods as it treats the problem of image detection as a regression problem rather than a classification problem and supports a single convolutional neural network to perform all the above mentioned tasks. The unification of all the independent tasks into one network has the following benefits:</p>
<ul>
  <li>SPEED: YOLO is extremely fast comapared to its predecessors as it uses a single convolution network to detect objects. The convolution is performed on the entire input image only once to yield the predictions.</li>  
<li>LESS BACKGROUND MISTAKES: YOLO performs the convolution on the whole image rather than sections of it due to which it encodes contextual information about the classes and their appearances. It makes less mistakes in predicting background patches as objects as it views the entire image and reasons globally rather than locally.</li>
<li>HIGHLY GENERALIZABLE: YOLO learns generalizable representations of objects due to which it can be applied to new domains and unexpected inputs without breaking.
  </li>

</ul>

## NETWORK DESIGN OF YOLO

<ul>
  
 <li> First 20 convolutional layers followed by an average pooling layer and a fully connected layer is pre-trained on the imagenet 1000-class classification dataset.</li>

<li>The pretraining for classification is performed on dataset with resolution 224 x 224the layers comprise of 1x1 reduction layers and 3x3 convolutional layers.</li>

<li>Last 4 convolutional layers followed by 2 fully connected layers are added to train the network for object detection.</li>

<li>Object detection requires more granular detail hence the resolution of the dataset is bumped to 448 x 448.The final layer predicts the class probabilities and bounding boxes.</li>
  </ul>
  
  <p>Object recognition includes all computer vision-related tasks to identify physical objects in images or videos. Putting this into practice is a little more complex.</p>
  <img src="https://user-images.githubusercontent.com/69414725/136426201-78d164ac-4ac9-47a3-bba2-ebde607c49e5.png">




