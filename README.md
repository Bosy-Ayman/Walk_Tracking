
# YOLOv8 Person Tracking on Video

This project showcases how to utilize **YOLOv8** to detect and track individuals in a video. The system assigns each detected person a unique ID and visualizes their movement with a colored path.


---

## 📁 Input and Output Files

* **Input Video**: `2863232-uhd_3840_2160_30fps.mp4`
  *(Download from [Pexels](https://www.pexels.com/video/cars-stopping-at-a-pedestrian-crossing-2863232/))*

* **Output Video**: `output_tracked_yolo8.mp4`
  *(Annotated video with bounding boxes, IDs, and trajectories)*

* **YOLO Model**: `yolov8s.pt`
  *(Pre-trained YOLOv8 small model)*

---

## ⚙️ How It Works

### 1. Model Initialization

* Loads YOLOv8s model: `yolov8s.pt`
* Sets confidence threshold: `CONFIDENCE_THRES = 0.3`

### 2. Video Frame Processing

For each frame:

* Detects objects using:
  `model.track(source=frame, persist=True)`

* Filters only "person" class (COCO ID `0`)

* For each detection:

  * Extracts bounding box and tracking ID
  * Draws box and ID label on frame
  * Appends center point to trajectory buffer for that ID

### 3. Output Generation

* Writes each annotated frame to `output_tracked_yolo8.mp4`
* Each ID maintains:

  * A unique consistent color
  * A visible motion path across frames

---

## 🎨 Features

* **Real-time tracking** with YOLOv8 
* **Persistent ID** labeling per person
* **Trajectory visualization** with color-coded paths
* **Color cycling** for distinguishable tracks

---

## 🛠 Customization Options

* Change input video:

  ```
  VIDEO_INPUT_PATH = "your_video.mp4"
  ```

* Adjust detection sensitivity:

  ```
  CONFIDENCE_THRES = 0.5  # for more confident detections
  ```

* Track different classes:

  ```
  if cls != 0: continue  → modify this to include other classes
  ```


## 📽 Sample Output

Each tracked individual will be annotated with:

* **Bounding Box** (colored)
* **Label**: `ID n`
* **Trajectory Line**: recent movement path

---
Output attached in Drive: [Drive](https://drive.google.com/drive/folders/19VyhbFEYEls-AA-vnfllk5P96jjtKTgq)
