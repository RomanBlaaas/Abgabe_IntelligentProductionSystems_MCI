# 🛠 Welding Defect Detection with YOLOv8

Dieses Projekt beschäftigt sich mit der Erkennung von Schweißnahtfehlern auf Basis von Bilddaten unter Verwendung des YOLOv8-Modells. Es beinhaltet Datenexploration, Modelltraining und Performance-Analyse, umgesetzt in einer Jupyter-Notebook-Umgebung.

## 🔧 Setup

Alle benötigten Pakete befinden sich in der Datei `requirements.txt`. Installation per:

```bash
pip install -r requirements.txt
```

### 📌 .env Beispiel

```env
ROOT_DIR_DATA=/Pfad/zum/Dataset
ROOT_DIR_RUNS_DETECT=/Pfad/zum/Runs-Verzeichnis
```

## 📂 Projektstruktur

```
├── data/
│   └── The Welding Defect Dataset/
│       ├── train/
│       ├── valid/
│       ├── test/
│       └── data.yaml
├── runs/
│   └── detect/
├── yolov8m.pt
├── sample.ipynb
```

## 🔍 Datenexploration

* Zufällige Bildvorschau aus dem Trainingsdatensatz mit OpenCV und matplotlib.
* Visualisierung der Verteilung der Bilder in `train`, `valid`, `test`.
* Analyse der Label-Dateien (`.txt` YOLO-Format) und Darstellung der Klassendichte mit Seaborn.

## 📊 EDA (Exploratory Data Analysis)

* Balkendiagramm zur Verteilung der Bildanzahl pro Datensatz-Split.
* Auslesen und Aggregation der Labelinformationen.
* Visualisierung der `class_id`-Verteilung im Trainingsdatensatz.

## 🧠 Modelltraining

Das Modell wird mit einem Pretrained-Checkpoint `yolov8m.pt` trainiert:

* Augmentierungen (Mosaic, Mixup, HSV etc.) und Hyperparameter sind explizit gesetzt.
* Der Modellname wird automatisch anhand der Anzahl bestehender Runs generiert.

## 📈 Evaluation

Nach dem Training:

* Laden und Plotten der Metriken aus `results.csv`: Precision, Recall, mAP\@0.5, mAP\@0.5:0.95.
* Beste Werte werden im Plot hervorgehoben.

## 🗄 Visuelle Modellbewertung

* 15 zufällig gewählte Bilder aus dem Testdatensatz.
* Modellvorhersagen werden visualisiert und gespeichert unter `runs/detect/exp_<timestamp>`.
