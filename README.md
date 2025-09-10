# 🟦 Face Detection with MTCNN

## Overview

This project demonstrates **face detection using the MTCNN library** in Python. It detects faces in images, draws bounding boxes around them, and shows the confidence of each detection.

---

## 🛠️ Requirements

* Python 3.x
* [MTCNN](https://pypi.org/project/mtcnn/)
* OpenCV
* Matplotlib
* Numpy

Install dependencies using:

```bash
pip install mtcnn opencv-python matplotlib numpy
```

---

## 📂 Usage

1. **Load an image**:

```python
from matplotlib import pyplot as plt

img = plt.imread('/path/to/your/image.jpg')
if img.shape[-1] == 4:
    img = img[..., :3]
```

2. **Initialize MTCNN detector**:

```python
from mtcnn import MTCNN
detector = MTCNN()
```

3. **Detect faces**:

```python
faces = detector.detect_faces(img, min_face_size=20)
```

4. **Draw bounding boxes with confidence**:

```python
from matplotlib.patches import Rectangle

plt.imshow(img)
ax = plt.gca()
for face in faces:
    x, y, width, height = face['box']
    confidence = face['confidence']
    rect = Rectangle((x, y), width, height, color='blue', fill=False, lw=3)
    ax.add_patch(rect)
    ax.text(x, y-10, f"{confidence:.2f}", color='red', fontsize=12, weight='bold')
plt.axis('off')
plt.show()
```

5. **Save the output image**:

```python
plt.savefig('output_detected_faces.png')
```

---

## ⚙️ Features

* Detects multiple faces in an image
* Displays bounding boxes and confidence scores
* Works with images containing RGBA or RGB channels
* Adjustable `min_face_size` for detecting smaller faces
* Save output image with bounding boxes and confidence scores
---

## 🔗 References

* [MTCNN GitHub](https://github.com/ipazc/mtcnn)
* [Facial Detection Paper](https://arxiv.org/abs/1604.02878)
