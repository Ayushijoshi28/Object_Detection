# Object Detection using OpenCV and skimage
This repository contains code for real-time object detection using OpenCV and skimage libraries in Python. The code captures video from the default camera (Webcam) and detects objects of a specific color (blue) in the live feed. It then draws bounding boxes around the detected objects and displays the annotated video in real-time.

## Output

![Screenshot (9)](https://github.com/Ayushijoshi28/Object_Detection/assets/88037464/cbf8a4e5-8300-4782-9e0e-0426ef9588c1)



## Prerequisites
Make sure you have the following libraries installed in your Python environment:

OpenCV (cv2)

plotly

plotly.express (px)

skimage


## How it works
1. The code captures frames from the default camera using cv2.VideoCapture(0).
2. Each frame is converted to grayscale using cv2.cvtColor() to facilitate color subtraction.
3. The blue channel of the original frame is subtracted from the grayscale frame, resulting in an image with blue objects appearing brighter while other colors become darker.
4. A binary thresholding operation is applied to the subtracted image, converting it into a binary image where pixels with intensity greater than 55 become white, representing the detected blue objects.
5. Small white regions (objects) in the binary image are removed using skimage.morphology.remove_small_objects() with a minimum size threshold of 150 pixels.
6. Small holes inside the remaining white regions are removed using skimage.morphology.remove_small_holes() with a minimum size threshold of 350 pixels.
7. A dilation operation is performed on the processed binary image using cv2.dilate() with an elliptical kernel of size (10, 10) to fill gaps in the detected regions.
8. Connected components in the binary image are labeled using skimage.measure.label().
9. The bounding box coordinates for the largest detected object are obtained using skimage.measure.regionprops() and a rectangle is drawn around it on the original frame.
10. The annotated video is displayed in real-time using cv2.imshow().

    
## Usage
1. Clone the repository and navigate to the project directory.
2. Run the object_detection.py script.
3. The script will start capturing video from your default camera and display the live feed with bounding boxes around the detected blue objects.
4. To exit the program, press the 'x' key.

## Contribution
If you encounter any issues or have suggestions for improvements, feel free to open an issue or submit a pull request.

Happy coding!
