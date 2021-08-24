# TensorFlow Lite

- **TensorFlow Lite** is an open source, deep learning framework for on-device and **embedded device inference**.

- TensorFlow Lite was released in Nov `2015`. **TensorFlow.js** for **React Native** was released February, `2020`.

- TensorFlow Lite is more optimized than **TensorFlow.js**. However it requires that the developer create separate **Android** and **iOS** codebases which need to be written using Java and Swift respectively.

- Our current project is written in **React Native** which is cross-platform. As a result, we need less code, but the steps may not be optimized.

- We used **TensorFlow.js** for **React** because the learning curve is lower.

- To build a more optimized app, you may want to explore **TensorFlow Lite**. **TensorFlow Lite** is also referred as **TFLite**.

## **Timing** This table shows how much more efficient **TFLite** can be compared to **TensorFlow.js** for prediction.

### Reference

- [TensorFlow Examples for iOS and Android](https://github.com/tensorflow/examples/tree/master/lite/examples/image_classification)
