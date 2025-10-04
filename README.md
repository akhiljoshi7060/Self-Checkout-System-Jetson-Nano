# Self-Checkout System Using Jetson Nano

An automated, **vision-based self-checkout system** for fruits and produce using **NVIDIA Jetson Nano**.
It combines **real-time object detection** with **weight measurement** and **cloud database integration** to make supermarket checkout faster and error-free.

---

## ✨ Features

* Real-time fruit/produce detection with **YOLOv8 / TensorFlow Lite**
* **Edge inference on Jetson Nano** for low latency
* **Weight sensing** with Load Cell + HX711 + ESP8266
* **Dynamic pricing** (shop owner updates price in database)
* **Cloud Firebase/SQL integration** for storing bills, prices, and transactions

---

## 📂 Project Structure

* `object_detection_and_image_classification.py` → main detection + classification script
* `TFLite_Read_Image.py` → helper to run TFLite model on sample images
* `test.tflite` → trained model file (TensorFlow Lite)
* `firebase_key.json` → Firebase key (secure, do not expose publicly)
* `Sample_TFLite_model/` → sample models for testing
* `README.md` → project documentation

---

## ⚙️ System Components

| Component                       | Purpose                                |
| ------------------------------- | -------------------------------------- |
| **Jetson Nano**                 | Runs ML inference at edge              |
| **HP w200 Webcam**              | Captures fruit/produce images          |
| **HX711 + Load Cell + ESP8266** | Measures fruit weight, sends to Jetson |
| **Firebase / Cloud SQL**        | Stores items, prices, and billing data |

**Formula:**

```
Item Price = (Price per weight unit) × (Weight measured)
```

---

## 🚀 Setup & Usage

### 1. Clone Repo

```bash
git clone https://github.com/akhiljoshi7060/Self-Checkout-System-Jetson-Nano.git
cd Self-Checkout-System-Jetson-Nano
```

### 2. Install Requirements

```bash
pip install -r requirements.txt
```

### 3. Connect Hardware

* Attach **camera** to Jetson Nano
* Connect **load cell (HX711 + ESP8266)**
* Ensure Firebase/SQL credentials are set correctly

### 4. Run Detection

```bash
python object_detection_and_image_classification.py
```

### 5. Test Model on Image

```bash
python TFLite_Read_Image.py
```

---

## 📊 Training Details

* Input size: **640×640**
* Epochs: **50**
* Augmentations: flip (LR/UD), scale, mosaic, mixup, translate, randaugment

---

## 🛠️ Challenges Faced

* OS crashes on Jetson Nano board during testing
* Load cell calibration issues → inconsistent values
* Mechanical plate mismatch
* Edge-inference performance tuning

---

## 🔮 Future Improvements

* Better calibration + mechanical design
* Expand fruit dataset for robustness
* Add touchscreen checkout interface
* Handle overlapping items and ambiguous classifications

---

## 👨‍💻 Author

* **Akhil Joshi**

---

## 📜 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.
