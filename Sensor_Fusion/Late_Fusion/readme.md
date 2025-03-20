# LiDAR-Camera Fusion for 3D Object Detection

## Stage 1: Object Detection in 2D (Camera)
- **Import Libraries**: Imports necessary libraries, including OpenCV, YOLOv4, and TensorFlow.
- **Load and Run YOLOv4**: Loads the YOLOv4 model with pre-trained weights and runs object detection on camera images.
- **Create 2D Objects**: Extracts bounding boxes, classes, and confidence scores from YOLOv4 output and stores them as `Object2D` instances.

## Stage 2: Object Detection in 3D (LiDAR)
- **Load 3D Data**: Reads ground truth 3D labels from text files.
- **Create 3D Objects**: Parses label information into `Object3D` instances containing 3D bounding box dimensions, location, and yaw angle in the camera frame.

## Stage 3: Project 3D to 2D (LiDAR)
- **Define LiDAR2Camera**: Creates a `LiDAR2Camera` class to manage projection using calibration data.
- **Project 3D Points**: Implements a function to project 3D points to the 2D image plane.
- **Calculate 3D Bounding Boxes**: Projects the 3D bounding boxes into the image frame.
- **Draw Boxes**: Renders the projected 3D and 2D bounding boxes on the image for visualization.

## Stage 4: Fusion (LiDAR and Camera)
- **Overlay Boxes**: Combines the bounding boxes from both LiDAR and camera on a single image.
- **Calculate IOU**: Computes the Intersection over Union (IOU) for each pair of LiDAR and camera bounding boxes.
- **Hungarian Algorithm**: Uses the Hungarian algorithm to find the best matches between LiDAR and camera boxes based on IOU.

## Stage 5: Create Fused Objects
- **Define FusedObject**: Creates a `FusedObject` class to store the combined information (2D and 3D bounding boxes, category, position, confidence).
- **Build Fused Objects**: Creates a list of `FusedObject` instances based on the matches found in the previous stage.
- **Visualize**: Annotates the final image with fused objects, displaying distance and class information.


___

## Hungarian Method in Tracking
The Hungarian algorithm is a combinatorial optimization algorithm used for solving the assignment problem. In multi-object tracking (MOT), it helps match detected objects between consecutive frames by minimizing the total cost (usually based on IoU or other similarity measures). This ensures accurate tracking of objects over time while handling occlusions and ID switching efficiently.

### Significance in Tracking
Optimal Matching: Finds the best assignment between detections and existing tracks.
Handles Multiple Objects: Efficiently matches many objects in real-time.
Reduces ID Switching: Ensures object identities remain consistent across frames.
Works with IoU and Feature Embeddings: Can incorporate motion models, appearance embeddings, or IoU scores for robust tracking.
Best Deep Learning-Based Tracking Methods
Modern tracking methods integrate deep learning for improved robustness:

#### DeepSORT (Simple Online and Realtime Tracker with Deep Learning)

Uses a CNN-based appearance descriptor + Hungarian matching.
Enhances SORT by reducing ID switches using feature embeddings.
#### FairMOT (Fair Multi-Object Tracking)

Combines detection and tracking into a single model.
Uses a shared backbone for feature extraction and object association.
#### Tracktor++

Uses a pre-trained object detector (e.g., Faster R-CNN) for tracking.
Instead of explicit association, it regresses object positions frame-by-frame.
#### CenterTrack

Uses a heatmap-based object detection network to perform tracking.
Predicts object center locations and offsets to maintain identities
