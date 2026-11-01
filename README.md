# Experiment 02 -- Image Acquisition Using Web Camera

### Name :Santhose Arockiaraj J
### Reg no: 212224230248

## Aim

To acquire an image using a web camera and display the captured image
and video. To resize and rotate the video frames using OpenCV.

## Procedure

1.  Import the required libraries: OpenCV (`cv2`), Matplotlib,
    `clear_output`, and `time`.
2.  Initialize the webcam using `cv2.VideoCapture(0)`.
3.  Capture a frame from the webcam and save it as `my.jpeg` using
    `cv2.imwrite()`.
4.  Read the saved image using `cv2.imread()` and display it using
    Matplotlib.
5.  Capture and display video frames continuously for a specified number
    of iterations.
6.  Resize each video frame using `cv2.resize()` and display the resized
    frames.
7.  Rotate each video frame by 90 degrees clockwise using `cv2.rotate()`
    and display the rotated frames.
8.  Release the webcam using `cap.release()` after each operation.

## Program

``` python
import cv2
import matplotlib.pyplot as plt
from IPython.display import clear_output
import time

# i) Capture and display an image using the webcam
cap = cv2.VideoCapture(0)
ret, frame = cap.read()

if ret:
    cv2.imwrite("my.jpeg", frame)

cap.release()

captured_image = cv2.imread("my.jpeg")

if captured_image is not None:
    plt.imshow(captured_image[:, :, ::-1])
    plt.title("Captured Frame")
    plt.axis("off")
    plt.show()

# ii) Display the video
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break

    frame_rgb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis("off")
    plt.show()
    time.sleep(0.05)

cap.release()

# iii) Display the video by resizing the frames
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break

    resized_frame = cv2.resize(frame, (100, 150))
    frame_rgb = cv2.cvtColor(resized_frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis("off")
    plt.show()
    time.sleep(0.05)

cap.release()

# iv) Rotate and display the video
cap = cv2.VideoCapture(0)

for i in range(50):
    ret, frame = cap.read()
    if not ret:
        break

    rotated_frame = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)
    frame_rgb = cv2.cvtColor(rotated_frame, cv2.COLOR_BGR2RGB)
    clear_output(wait=True)
    plt.imshow(frame_rgb)
    plt.axis("off")
    plt.show()
    time.sleep(0.05)

cap.release()
```

## Output

**Image Acquisition:**

<img width="677" height="545" alt="image" src="https://github.com/user-attachments/assets/a539f355-e072-4bd7-806f-73a99f48fd99" />


**Video Display:**

<img width="415" height="317" alt="image" src="https://github.com/user-attachments/assets/f30e737d-fa70-4d11-bd7b-2fa94b843631" />

**Resized Video:** 

<img width="228" height="313" alt="image" src="https://github.com/user-attachments/assets/1ab325a7-d04d-4edd-a129-3ee6c0102d9f" />

**Rotated Video:**
   
<img width="243" height="316" alt="image" src="https://github.com/user-attachments/assets/ea1c5449-11b2-4ff1-8526-c767e92bb107" />


*Note: The output is displayed live when the program is executed with a
working webcam. The notebook contains visual outputs for these
operations.*

## Result

Thus, an image was successfully acquired using the web camera, and the
video was displayed in its original, resized, and 90-degree clockwise
rotated forms using OpenCV.
