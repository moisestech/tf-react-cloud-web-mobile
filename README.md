# tf-react-cloud-web-mobile

## Deploying Deep Learning Models on Web and Mobile

**Train an image classifier using deep learning, and deploy the model.**

<p float="left">
  <a href="https://www.manning.com/liveproject/deploying-a-deep-learning-model-on-web-and-mobile-applications?utm_source=dataumbrella&utm_medium=affiliate&utm_campaign=liveproject_pattaniyil_02_03_21&utm_content=published&a_aid=dataumbrella&a_bid=187b748d">
  <img src="./assets/images/manning_project.png" width="50%" height="100%" style="padding:1px;border:thick solid black;" align="top"> 
  </a>
</p>

<p float="left">
  <p>📱 Here is what the mobile app looks like.</p>
  <a href="https://food-classifier-demo.herokuapp.com">
  <img src="https://raw.githubusercontent.com/moisestech/tf-react-cloud-web-mobile/main/assets/imgs/food-classifier-mobile-app-demo.png" width="50%" height="100%" style="padding:1px;border:thick solid black;" align="top"> 
  </a>
  
  <a href="https://play.google.com/store/apps/details?id=com.rsnp.foodclassifier">
  <img src="https://raw.githubusercontent.com/moisestech/tf-react-cloud-web-mobile/main/assets/imgs/food-classifier-web-app-demo.gif"         width="45%" height="30%" style="padding:1px;border:thick solid black;"> 
  </a>
</p>

---

## **Project Scope**

1. Train a deep learning model using TensorFlow
2. Export that model
3. Optimize the model for latency
4. Deploy the model to both web and mobile platforms

### Create Model

- Machine learning engineer tasked with building a deep learning image classification model.
- Deploy the model to both web and mobile.

### Create Web App

- The application takes a photo of a food item, then returns the image name with an associated probability.
- The app can be a helpful in aiding in food recognition.
- The application will run on a website and also smartphones.

## **Tasks**

### Create Model Steps

- [ ] Train a deep learning model using TensorFlow.
- [ ] Store that model on a server and locally.

### Create Web/App Steps

- [ ] Create a web application that allows users to upload an image or URL of a food item and return the predicted image class name with some probability.
- [ ] Create a mobile application that allows users to take a photo or upload an image from their phone and returns the predicted image class name with some probability.

## **Techniques employed**

- **Colab:** Train deep learning models using GPU
- **TensorFlow/Keras:** Open source libraries to perform deep learning
- **TensorFlow.js:** Use the TensorFlow ecosystem to deploy the deep learning model
- **Expo/ReactNative:** Create the web application
- **Heroku/GitHub Pages:** Create the web application
- **Docker:** Deploy the web application
- **Expo:** Deploy the mobile application
- Mobile phone
- **Node.js/NVM:** Deploy the mobile application

---

## **Project outline**

- The project consists of 3 parts.

### 1. Building an image classifier

- [ ] Create a Colab notebook
  - [Get started using: Intro to Colab 101](https://colab.research.google.com/github/ROZBEH/rozbeh.github.io/blob/master/colab_101.ipynb)
- [ ] Table comparing metrics on different model architectures
- [ ] Perform deep learning image classification using pre-trained models and experiment with some fine-tuning.
- [ ] Evaluate the inference quality, size and accuracy of the ResNet and mobile-optimized models like MobileNet.

#### Required Python Libraries setup

- **Matplotlib:** To do visualizations
- **PIL Image:** To display images in the notebook
- **Wget:** To download data from a server to working environment
- **TensorFlow:** To train a deep learning model
- **Keras:** For user-friendly implementation of TensorFlow
- **Watermark:** To show which versions of libraries are being used

### 2. Deploying a web application

- [ ] Link to Heroku web application
- [ ] Link to GitHub repo
- [ ] Optimize the trained model for serving on the web.

- Deploy the model in 2 ways to the app:

  - [ ] running on the **server**
    - For the server deployment, you will learn how to deploy the model as a service using **Docker**, and run on **Heroku**.
  - [ ] running on the **browser** natively
    - For the browser, you will serve the model using **TensorFlow.js** as a static site on GitHub pages.

### 3. Deploying a mobile application

- [ ] Link to GitHub repo
- [ ] Screenshot of mobile application

- [ ] Convert the model to run on your mobile device using **Expo/React Native**.
- [ ] Convert the trained model to a format needed for **tfjs-native**.

---

## **Dataset**

- The Food 101 data is used for this project, which includes 101 food categories for a total of 101,000 images. Thus, each class has 1,000 images, of which 250 are manually reviewed test images, and 750 are training images. The categories of the ETHZ Food 101 are the 101 most popular categories from the food picture sharing website foodspotting.com. The labels of food categories were chosen from the top 101 most popular dishes.

### Data citation

- Bossard, Lukas and Guillaumin, Matthieu and Van Gool, Luc, Food 101 Mining Discriminative Components with Random Forests, European Conference on Computer Vision, 2014.

---

## **Recommended resources**

- [Deep Learning with Python]() by _François Chollet_
- [Deep Learning for Vision Systems]() by _Mohamed Elgendy_
- [Deep Learning with JavaScript]() by _Shanqing Cai, Stanley Bileschi, and Eric D. Nielsen with François Chollet_
- [React Native in Action]() by _Nader Dabit_
- [Transfer Learning With TensorFlow Hub]()
- [Deploying Deep Learning Models on Web and Mobile (using fastai PyTorch)]() by _Nidhin Pattaniyil and Reshama Shaikh_
- [Sample Mobile Classification App]() by _Yuefeng Zhang_
