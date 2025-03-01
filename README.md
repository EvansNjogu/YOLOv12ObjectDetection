# YOLOv12 Object Detection

This task implements **YOLOv12** for object detection using **Ultralytics YOLO** framework. It involves training the model on the **COCO128 dataset**, visualizing results using TensorBoard and performing inference on images.

## Dataset
I used the **COCO128** dataset, a subset of the **COCO** dataset, which consists of 128 labeled images spanning 80 object categories. The dataset is structured as follows:

```
coco128/
│── 📁images/
│   ├──📁 train2017/
│──📁 labels/
│   ├──📁 train2017/
```

### Dataset Configuration (`data.yaml`)
```yaml
train: train.txt
val: val.txt
test: test.txt
nc: 80
names: ['person', 'bicycle', 'car', 'motorcycle', 'airplane', 'bus', 'train', 'truck', 'boat', 'traffic light', 'fire hydrant', ...]
```


##  Model Training
Train YOLOv12 on COCO128 dataset using the following command:
```bash
!yolo train model=yolov12.pt data=data.yaml epochs=10 imgsz=640 batch=4
```

### Training Logs and Metrics
I monitored training performance using TensorBoard:
- Epoch-wise Performance Graphs

<img src="assets/pg0.png" alt="Performance Graph 1" width="400">

<img src="assets/pg1.png" alt="Performance Graph 2" width="400">

<img src="assets/pg2.png" alt="Performance Graph 3" width="400">

- mAP (mean Average Precision)

<img src="assets/mAP1.png" alt="mAP1" width="400">

<img src="assets/mAP2.png" alt="mAP2" width="400">

- Precision

<img src="assets/precision.png" alt="Precision" width="400">

- Recall

<img src="assets/recall.png" alt="Recall" width="400">

- Loss Functions (Box Loss) Train

<img src="assets/boxlosstrain.png" alt="Train Box Loss" width="400">

- Loss Functions (Class Loss) Train

<img src="assets/clslosstrain.png" alt="Train CLS Loss" width="400">

- Loss Functions (DFL Loss) Train

<img src="assets/dfllosstrain.png" alt="Train DFL Loss" width="400">

- Loss Functions (Box Loss) Validation

<img src="assets/boxlossval.png" alt="Val Box Loss" width="400">

- Loss Functions (Class Loss) Validation

<img src="assets/clslossval.png" alt="Val CLS Loss" width="400">

- Loss Functions (DFL Loss) Validation

<img src="assets/dfllossval.png" alt="Val DFL Loss" width="400">



## Model Inference
Run inference on an image:
```bash
!yolo predict model=runs/detect/train7/weights/best.pt source=horses.jpg
```

**Example Output:**
![Detection Example](/assets/horses.png)


## Results Summary
**Final Model Performance:**
| Metric  | Value |
|---------|--------|
| **mAP@50** | 0.851 |
| **mAP@50-95** | 0.689 |
| **Best Precision** | 0.848 |
| **Best Recall** | 0.779 |


## References
- [Ultralytics YOLO Documentation](https://docs.ultralytics.com/)
- [COCO Dataset](https://cocodataset.org/)

## Contact

For any questions or collaboration opportunities, feel free to reach out at [hey@njoguevans.me](mailto:hey@njoguevans.me).
