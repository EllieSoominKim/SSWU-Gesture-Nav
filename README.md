# SSWU Gesture Nav 🖐️💻

[English](README.md) | [한국어](README.ko.md)

A browser-based shortcut tool that recognizes gestures via webcam to automatically open pre-defined websites in a new tab. It utilizes an image classification model trained with Google's Teachable Machine and runs via TensorFlow.js.

## 📺 Demo

[▶️ Watch Demo Video](https://drive.google.com/file/d/1MbhxkCxRtlWEpIQS9_mOURxL9ogOnunT/view?usp=sharing)

## 📌 Overview

This project is a personal shortcut tool designed to let you open specific websites (such as university portals, LMS, libraries, etc.) automatically by recognizing distinct actions (e.g., waving a hand, specific poses) through a webcam. It operates entirely within the browser without requiring any separate software installations.

## ✨ Workflow & Features

1. Clicking the "Start System" button loads the Teachable Machine model and activates the webcam.
2. It analyzes the webcam stream in real-time and recognizes a registered action class when the prediction confidence hits **95% or higher**.
3. It instantly opens the URL mapped to the recognized gesture in a new tab.
4. To prevent multiple duplicate windows from flooding the browser, a **5-second debounce cooldown** is applied, blocking immediate consecutive triggers for the same repeated gesture.

## 🛠️ Tech Stack

| Technology | Role |
| --- | --- |
| [TensorFlow.js](https://www.tensorflow.org/js) | Executes the machine learning model directly in the browser |
| [Teachable Machine](https://teachablemachine.withgoogle.com/) | Trains and hosts the image classification model |

## 🚀 How to Use

### 1. Train Your Model
Go to the [Teachable Machine Image Project](https://teachablemachine.withgoogle.com/train/image), train your desired actions (classes), export/publish your model, and copy the generated model URL.

### 2. Configure the Model URL
Open your `index.html` file and replace the value of the `URL` constant with your own trained model address.

```javascript
// index.html
const URL = "YOUR_OWN_MODEL_URL";
```

### 3. Map Gestures to Websites
In the `SITES` object, pair each class name with the specific website URL you want to open. Make sure the class names match the exact spelling and casing used in Teachable Machine.

```javascript
// index.html
const SITES = {
    "ClassName1": "https://example.com/",
    "ClassName2": "https://example2.com/"
};
```

### 4. Run the Application
Simply open the `index.html` file in your web browser, grant the necessary webcam permissions, and click the "Start System" button to begin using it.

## ⚙️ Customization

The example code in this repository comes with preconfigured links for a specific university (Sungshin Women's University) portal, LMS, and library. Feel free to completely customize and rewrite the keys and values in the `SITES` object to fit your own daily routine and personal preferences.

## 🔒 Notes & Security

- While this tool processes webcam feeds in real-time, it never stores or uploads any video data or prediction results to external servers. All computations happen locally and securely inside your browser.
- The recognition accuracy heavily depends on the quality and diversity of the image samples used during model training.
- This is a personal project developed for educational and self-learning purposes.
