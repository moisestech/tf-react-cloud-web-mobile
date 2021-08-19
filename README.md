# tf-react-cloud-web-mobile

Deploying Deep Learning Models don Web and Mobile

<p float="left">
  <a href="https://www.manning.com/liveproject/deploying-a-deep-learning-model-on-web-and-mobile-applications?utm_source=dataumbrella&utm_medium=affiliate&utm_campaign=liveproject_pattaniyil_02_03_21&utm_content=published&a_aid=dataumbrella&a_bid=187b748d">
  <img src="./assets/images/manning_project.png" width="50%" height="100%" style="padding:1px;border:thick solid black;" align="top"> 
  </a>
</p>

<p float="left">
  <p>Here is what the mobile app looks like.</p>
  <a href="https://food-classifier-demo.herokuapp.com">
  <img src="../assets/imgs/food-classifier-mobile-app-demo.png" width="50%" height="100%" style="padding:1px;border:thick solid black;" align="top"> 
  </a>
  
  <p>Here is the web application in action.</p>
  <a href="https://play.google.com/store/apps/details?id=com.rsnp.foodclassifier">
  <img src="../assets/imgs/food-classifier-web-app-demo.gif"         width="45%" height="30%" style="padding:1px;border:thick solid black;"> 
  </a>
</p>

---

## Start Project

- filling the role of a data scientist or machine learning engineer tasked with building a deep learning image classification model.
- You will expand on your role of data scientist, adding some data engineering skills to your toolset by deploying the model to both web and mobile.

- You will create an application that will take a photo of a food item, then return the image name with an associated probability.
- This can be a helpful application to aid in food recognition. This application will run on a website on your computer and also on your phone.
- You could be working in a broad range of fields and have some experience in computation and machine learning.

### You will

- Train a deep learning model using TensorFlow.
- Store that model on a server and locally.
- Create a web application that allows users to upload an image or URL of a food item and return the predicted image class name with some probability.
- Create a mobile application that allows users to take a photo or upload an image from their phone and returns the predicted image class name with some probability.
- This liveProject will benefit data scientists, machine learning engineers, and data engineers.
- If you’re a data scientist, you’ll develop techniques for deploying and demonstrating your models.
- The beauty of this project is you will create an application that is deployed and accessible for others to use on their smart phone.

## Techniques employed

- These are some of the technologies and concepts you will become familiar with in this project.
- We provide detailed instructions and references to aid in completing each item.
- These tools will expand your data science skillset.
- The key to being a successful data scientist isn’t knowing every tool, but rather being flexible as you explore and work with new technologies in this ecosystem.

- **Colab:** Train deep learning models using GPU
- **TensorFlow/Keras:** Open source libraries to perform deep learning
- **TensorFlow.js:** Use the TensorFlow ecosystem to deploy the deep learning model
- **Expo/ReactNative:** Create the web application
- **Heroku/GitHub Pages:** Create the web application
- **Docker:** Deploy the web application
- **Expo:** Deploy the mobile application
- Mobile phone
- **Node.js/NVM:** Deploy the mobile application

## Project outline

- The project consists of 3 parts. As each milestone emphasizes different skills, the deliverables for each will vary:

### 1. Building an image classifier

- Create a Colab notebook
  - [Get started using: Intro to Colab 101](https://colab.research.google.com/github/ROZBEH/rozbeh.github.io/blob/master/colab_101.ipynb)
- Table comparing metrics on different model architectures
- You will perform deep learning image classification using pre-trained models and experiment with some fine-tuning.
- You will experiment with models like ResNet and mobile-optimized models like MobileNet. You will learn to evaluate a model on its inference, size, and accuracy.

### 2. Deploying a web application

- Link to Heroku web application
- Link to GitHub repo
- Given the trained model from Milestone 1, you will optimize the model for serving on the web.

- There are 2 ways to deploy an app:

  - running on the server
  - running on the browser natively

- For the server deployment, you will learn how to deploy the model as a service using Docker, and run on Heroku.

- For the browser, you will serve the model using TensorFlow.js as a static site on GitHub pages.

### 3. Deploying a mobile application

- Link to GitHub repo
- Screenshot of mobile application

- Convert the model to run on your mobile device using Expo.
- You will take the model trained from Milestone 1 and convert it to a format needed for tfjs-native.
- You will be provided with boiler plate code to use their transformed model in a Expo/React Native project. Expo/React Native is a cross-platform mobile development library.

- The skills are covered in the following order:

1. Train a deep learning model using TensorFlow
2. Export that model
3. Optimize the model for latency
4. Deploy the model to both web and mobile platforms

---

Each section builds upon the previous and will expand your skillset in both data science and data engineering.

As you go through the project, keep in mind the overall objective: **Train an image classifier using deep learning, and deploy the model.**

---

## Prerequisites

- The liveProject is for intermediate Python programmers who know the basics of data science and some experience training an image classifier using deep learning who want to improve their experience of deploying models into production.

### TOOLS

- Intermediate Python
- Basic Git
- Basics of TensorFlow

### TECHNIQUES

- Basic machine learning techniques
- Basics of neural networks

## Dataset

- The Food 101 data is used for this project, which includes 101 food categories for a total of 101,000 images. Thus, each class has 1,000 images, of which 250 are manually reviewed test images, and 750 are training images. The categories of the ETHZ Food 101 are the 101 most popular categories from the food picture sharing website foodspotting.com. The labels of food categories were chosen from the top 101 most popular dishes.

### Data citation

- Bossard, Lukas and Guillaumin, Matthieu and Van Gool, Luc, Food 101 Mining Discriminative Components with Random Forests, European Conference on Computer Vision, 2014.

## Required setup

- The following Python libraries will be used in this project. Again, you don’t need working experience with all of these, as you can pick up the basics by reading documentation and putting them to use.

- **Matplotlib:** To do visualizations
- **PIL Image:** To display images in the notebook
- **Wget:** To download data from a server to working environment
- **TensorFlow:** To train a deep learning model
- **Keras:** For user-friendly implementation of TensorFlow
- **Watermark:** To show which versions of libraries are being used

## How to use help

- At points in the project workflow the author has created different levels of help designed to get you past the tricky parts.

- The beginnings of these Help sections offer useful resources. Some of these resources might have already been referenced in the project workflow. All of them contain useful information for your project.

- After that, you’ll see help options you can click on if needed. If you prefer a challenge and don’t want help, then you can ignore this part. But if you’re stuck and could use a hand, we’re here for you. The samples below show you what the help system looks like. Go ahead and click on the options now.

- By the way, the FAQs page and the chat system are also available to give you a hand. Look at each of these if you get stuck.

## Resources

- In this section, you’ll find topic-specific reading material curated by the author. You can access these passages with live links embedded in the project.

- help
- partial solution
- full solution

## Recommended resources

- Deep Learning with Python by François Chollet
- Deep Learning for Vision Systems by Mohamed Elgendy
- Deep Learning with JavaScript by Shanqing Cai, Stanley Bileschi, and Eric D. Nielsen with François Chollet
- React Native in Action by Nader Dabit
- Transfer Learning With TensorFlow Hub
- Deploying Deep Learning Models on Web and Mobile (using fastai PyTorch) by Nidhin Pattaniyil and Reshama Shaikh
- Sample Mobile Classification App by Yuefeng Zhang

- Additional resources and tutorials are provided throughout the project. Feel free to use any resources you can find to complete the project. If you run into problems or have questions, refer to the Frequently Asked Questions (FAQs) section.
