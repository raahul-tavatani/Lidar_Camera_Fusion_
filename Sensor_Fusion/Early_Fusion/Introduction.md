# Early Fusion for 3D Point Cloud and 2D Image Processing

This repository implements an early fusion approach that combines 3D point cloud data and 2D camera images to detect obstacles.

## Overview

Early fusion is a technique used to combine information from different modalities at an early stage of the pipeline to enhance detection accuracy. The stages in this approach are as follows:

1. **Project the Point Clouds (3D) to the Image (2D)**
   - The 3D point cloud data is projected onto the 2D image plane. This enables the 3D information to be aligned with the 2D view captured by the camera.
   - The point cloud data is mapped into the image space, allowing both the camera and LiDAR (or other 3D sensors) to be used simultaneously.

Here, I'm using the kitti dataset. (https://www.cvlibs.net/datasets/kitti/setup.php)



# Sensor Setup for KITTI Dataset

The following table provides a summary of the sensor setup used in the KITTI dataset, including the sensor type, manufacturer, specifications, and frequency of each sensor.

| Sensor Type                    | Manufacturer          | Model/Description                          | Frequency                     | Specifications                                                                 |
|---------------------------------|-----------------------|--------------------------------------------|-------------------------------|-------------------------------------------------------------------------------|
| **Inertial Navigation System**  | OXTS                  | RT 3003                                    | Continuous (real-time data)   | GPS/IMU system with high-precision positioning and motion tracking.           |
| **Laser Scanner (LiDAR)**       | Velodyne             | HDL-64E                                    | 10 Hz (10 frames per second)  | 64 vertical resolution, 100k points per cycle, 360-degree scan range.         |
| **Grayscale Cameras**           | Point Grey           | Flea 2 (FL2-14S3M-C)                       | 10 Hz (10 frames per second)  | 1.4 Megapixels, 1382 x 512 pixels, cropped to 1382 x 512, dynamic shutter.    |
| **Color Cameras**               | Point Grey           | Flea 2 (FL2-14S3C-C)                       | 10 Hz (10 frames per second)  | 1.4 Megapixels, 1382 x 512 pixels, cropped to 1382 x 512, dynamic shutter.    |
| **Varifocal Lenses**            | Edmund Optics        | NT59-917 (4-8 mm)                          | N/A (Used with cameras)       | 4-8 mm varifocal lenses, adjustable for different focal lengths.              |

## Setup

![image](https://github.com/user-attachments/assets/965983c3-5d02-44e2-a475-bca6158413cc)

The LiDAR axis and Camera axis are on offset and also needs a rotation. So it needs a translation and rotation.


![image](https://github.com/user-attachments/assets/2129e497-b55d-4127-adbf-70e3c7f66983)

## Projecting point on Image

![image](https://github.com/user-attachments/assets/d0f17c8a-d323-45ae-aab9-087749604898)

P = [ f_x   0    c_x   0 ]
    [  0    f_y   c_y   0 ]
    [  0     0     1    0 ]

Ro = [ R_11   R_12   R_13 ]
     [ R_21   R_22   R_23 ]
     [ R_31   R_32   R_33 ]
     
R|t = [ R_11   R_12   R_13   t_1 ]
      [ R_21   R_22   R_23   t_2 ]
      [ R_31   R_32   R_33   t_3 ]

X is point clould data point [ Xi Yi Zi 1]

Y is PCD point mapped on to Pixel

All are homogenous matrices

### To convert the homogenous to euclidain

![image](https://github.com/user-attachments/assets/b981f1db-711a-4b4a-8860-78813b16e373)
![image](https://github.com/user-attachments/assets/94155b4f-d424-4f66-9701-08124b4abdc2)




2. **Detect Obstacles in 2D (Camera)**
   - Obstacles in the 2D camera image are detected using standard computer vision algorithms. This can include object detection techniques such as deep learning-based methods or traditional image processing algorithms.
   - The camera image serves as the basis for detecting obstacles in the 2D plane.

3. **Fuse the Results**
   - After detecting obstacles in the 2D image, the results are fused with the projected 3D point cloud information.
   - The fusion process combines both 3D and 2D data to create a more accurate and robust obstacle detection model. This could involve combining bounding boxes from the image and the spatial data from the point clouds.

