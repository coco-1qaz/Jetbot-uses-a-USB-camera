# Jetbot-uses-a-USB-camera
Run the following command in the jetbot terminal:
```
git clone https://github.com/NVIDIA-AI-IOT/jetcam
cd jetcam
sudo python3 setup.py install
```
Or-download-jetcam-and-run-the-following-command
```
cd jetcam
```
And modify the __init__.py in jetcam in jetcam to:
> **Note:** If you choose to download my library, this step can be skipped
```
from .camera import Camera
from .csi_camera import CSICamera
from .usb_camera import USBCamera
from .utils import bgr8_to_jpeg
```
---
## After that, please run the following code (both methods are needed):
> **Note:** This is already in the /jetbot directory
```
sudo python3 setup.py install
```
---
run
```
from jetcam import USBCamera
camera = USBCamera(width=224, height=224, capture_width=640, capture_height=480, capture_device=0)
```
Keep the video going
```
camera.running = True
def update_image(change):
    image = change['new'] 
    image_widget.value = bgr8_to_jpeg(image)
camera.observe(update_image, names='value')
```
---
Jetbot's changed code instance can be downloaded directly on My Library
