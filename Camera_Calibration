# Calibration of Camera using chess Board



![image](https://github.com/user-attachments/assets/9fb1eb18-b93f-4dba-8fd0-c9412dcd933c)


This is the process behind capturing a 3D point in the world, and converting it to a pixel in an image.

As you see, there is an intermediate step called the camera coordinates.

In reality, what we're doing is:
1) Convert the point from the world to the camera coordinates using EXTRINSIC parameters
2) Convert the point from the camera to the pixel coordinates using INTRINSIC parameters.

**What are extrinsic and intrinsic parameters?**

Extrinsic parameters are rotation and translation matrices used to convert something from the world frame to the camera frame.

Intrinsic parameters are the internal camera parameters, such as the focal length, to convert that information into a pixel.

![image](https://github.com/user-attachments/assets/01dd9240-14da-4d71-8990-a2a687915ff2)


In the end, we have a formula to convert a point from the 3D world to a 2D pixel.



These intrinsic and extrinsic matrices are automatically calculated using a process called CAMERA CALIBRATION.
