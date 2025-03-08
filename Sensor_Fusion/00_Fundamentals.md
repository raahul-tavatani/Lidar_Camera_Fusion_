# 9 Types of Sensor Fusion Algorithms (https://www.thinkautonomous.ai/blog/9-types-of-sensor-fusion-algorithms/)

In autonomous vehicles, Sensor Fusion is the process of fusing data coming from multiple sensors. This step is mandatory in robotics as it provides more reliability, redundancy, and ultimately, safety.


## I - Sensor Fusion by Abstraction Level



## Low Level Fusion 
Early Fusion (Used now a days, due to high processing power)
![image](https://github.com/user-attachments/assets/e27aec33-a87e-4998-ba60-17685293d682)
### Steps :
1. Project lidar points onto the Image.
2. Detect Objects using 2D object detection algorithm.
3. Fuse Points and detections by extracting the points from the 2D bounding boxes.
4. Calculate the avg distances of points in the bounding boxes.

## Mid and High level Fusions - Late Fusion
![image](https://github.com/user-attachments/assets/a04fce78-7469-4563-af77-7b9fa94e1431)
### Steps :
1. Detect objects in 2D.
2. Detect objects in 3D (Lidar PCD).
3. Project the 3D bounding boxes on the image.
4. Fuse the data and IoU.
5. Finally calculate the distance.

### Low Level Fusion - Fusing the RAW DATA
- Low-level fusion combines raw data from multiple sensors, e.g., point clouds from LiDARs and pixels from cameras.
- **Advantages**: High potential for the future.
- **Challenges**: Huge computational requirements.

### Mid Level Fusion - Fusing the DETECTIONS
- Fuses objects detected independently by sensors.
- **Advantages**: Relatively easy to understand.
- **Challenges**: Heavily dependent on detectors, failure risks, if one sensor fails.

### High Level Fusion - Fusing the TRACKS
- Fuses both object detections and their trajectories.
- **Advantages**: Simplified process.
- **Challenges**: Risk of losing too much information.

![image](https://github.com/user-attachments/assets/b38f3c95-cf35-4c7c-91ab-f4bd0bdbd6cd)

## II - Sensor Fusion by Centralization Level

![image](https://github.com/user-attachments/assets/8586b476-ab5f-466e-b63c-f802029a4e4f)


- **Centralized**: One central unit handles fusion.
- **Decentralized**: Each sensor fuses data and forwards it.
- **Distributed**: Sensors process data locally, send it for further fusion.

## III - Sensor Fusion by Competition Level

### Competitive Fusion
- Sensors meant for the same purpose, such as RADAR and LiDAR detecting pedestrians.

### Complementary Fusion
- Uses different sensors to gather information not obtainable from a single sensor.

### Coordinated Fusion
- Combines two or more sensors working together for an enhanced view.
