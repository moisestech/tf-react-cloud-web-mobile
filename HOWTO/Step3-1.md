# Deploying the Mobile App Using React Native

Objective

In Milestone 2, we deployed a web app. In Milestone 3, we will use the same TensorFlow.js converted model and deploy a mobile app. The output from this milestone will be a mobile app that can be viewed on a simulator or your smartphone.

We will be using these tools:

Expo
Smartphone
Simulator (optional)
iPhone simulator (Mac): In order to install the iPhone simulator, Xcode is needed.
Android simulator (Windows, Linux)
Note: The simulators are not required, though they are helpful in developing the app and provide a smoother development experience. Inference time will be longer on the simulator.

Importance to project

The tfjs model file that we used in Milestone 2 for browser inference is also used here in Milestone 3 as input to our mobile app. Milestones 2 and 3 both used the same underlying libraries, including React, Typescript, and TensorFlow.js.

Mobile use is increasing worldwide as mobile phones become more accessible. Apps on mobile are in high demand. Users utilize their mobile devices over their desktop more frequently. The ability to provide a mobile app makes it more accessible and expands the applications of data on mobile.

The benefit of this mobile app is that it is functional without an internet connection, which leads to lower latency and preserves the user’s privacy.

Workflow

Set up the environment.
You will need to install the dependencies yarn and expo. Here are instructions for those installations.

Set up the repo.
We are providing a template repository of code to get started with your mobile app. You can fork and clone it under your GitHub account. This is the template repository: deploying-mobile-app

Copy the model file over to assets/model_tfjs. From Milestone 2, take the converted TensorFlow.js files and copy them to this folder in the template mobile app repo using this directory structure. You should also include the classes.json file in this directory.

| deploying-mobile-app
| ├── assets
| │ ├── model_tfjs
│ │ | ├── classes.json
│ │ | |── group1-shard1of1.bin
│ │ | |── model.json
Get the mobile app running.
Install project dependencies.
yarn
Start the app.
yarn run start
Open the Expo app on your phone.
You will see your project listed under "Recently in Development". Select it.
In the mobile app at the top, you will see "Model Loaded". Once a green checkmark appears, you are ready to test an image.

Test the app.
You can test an image from your camera roll or take a picture of a new image. After you select an image, your screen will display the prediction and inference timing.

Try a few images and compare the inference times. Your terminal will display a log of the process for you to review.

Note: Time to inference will depend on your phone specs.

Understand the internals of the mobile app repo
To learn more about the internals of the template repository and the inference process, refer to section Understand the Internals of the Repo.

Deliverable

The deliverable is a GitHub repo that contains the source code for your deployed mobile app.

To help you get started, feel free to use our template repo. In the README.md of your repo, there should be a:

Screenshot of the mobile app, either from your phone or simulator.
Comparison of the general inference times for mobile browser inference vs. mobile app inference.
Try a few different images, both from your photo library and using your phone camera. Compare inference times for a couple of the images.

Upload a link to your deliverable in the Submit Your Work section and click submit. After submitting, the Author’s solution and peer solutions will appear on the page for you to examine.

Help

Feeling stuck? Use as little or as much help as you need to reach the solution!

resources
Deep Learning with JavaScript: Neural networks in TensorFlow.js by Shanqing Cai, Stanley Bileschi, Eric D. Nielsen , and Francois Chollet
Chapter 12, Unit 3.4, Deploying TensorFlow.js Models in JavaScript-based Mobile Applications.

React Native in Action by Nader Dabit
Chapter 3, Building Your First React Native App, is a good intro to React Native.

Additional resources

Expo: This is a free and open source toolchain built around React Native to help you build native iOS and Android projects using JavaScript and React.

TensorFlow.js for React Native is here

GitHub repo

TensorFlow Lite (Optional)

TensorFlow Lite is optimized for running on edge-device. If you are interested, take a look at example code. We have provided more background in a separate section TensorFlow Lite.
