# Deploying a Model for Browser- and Server-based Inference

## **Objective**

- Now that we have **trained our `MobileNetV2`** deep learning model,
  - **we need to deploy it and make it accessible to our users for inference**.
  - In this unit, we will **explore server-based** and **client-based inference**
  - and learn about **when to choose each**.
  - We’ll also learn how to create an **optimized model for the web**. Client-side apps include browser and mobile.
- The **output** from this milestone will be a **web app** that supports **server-side** and **browser-based inference**, deployed on a **cloud** provider like [Heroku]().

---

## **Importance to project**

- When considering whether to run inference on a model via a server or on the client, there are several considerations:

### 1. **Latency/Network connection of user**

- In server-side inference, **once the image/text is received, the inference time is consistent**.

  - However, the total time is determined by the user’s network upload speed. In client-side inference, the inference time is dependent on the hardware that the user is running.

### 2. **Privacy**

- For sensitive data, users might be uncomfortable with sending the data to a server. - Client-side inference allows users to run their workload securely.

### 3. Future updates to models

- A benefit of server-side inference is the ability to deploy new, state-of-the-art models and consistently update them. In client-side inference, deployment of new models is restricted by the user’s expressed update frequency.

### 4. State of the art models vs. mobile optimized

- Due to client hardware and storage restrictions, models that are small and optimized for inference are ideal. Most websites on the web are less than 2 MB of JavaScript code and CSS. The simplest model we created was about 20 MB, which is still not ideal for serving on the web. Therefore, most models currently are served on a server.

- In Milestone 1, you trained a deep learning classifier and saved the model file.

- In Milestone 2, you will convert that model to an optimized format and deploy a web app. You will also learn why we deploy apps on the server and the latency characteristics related to that.

- Building on that, in Milestone 3, you will learn how to build a mobile app and deploy it.

---

## **Workflow**

### 1. **Download the model from Colab to your computer**

- Make a folder called model_tf on your local computer and save the model and labels in that folder. Make sure that the following naming convention is being used:

  - `model.h5`
  - `classes.json`

---

### 2. **Understand why model format conversion is needed**

- The model we created using Colab is in the format "TensorFlow Keras".
- We will need to convert it to the “TensorFlow.js” format because that is needed for client-side inference.

---

### 3. **Set up the virtual environment**

- It is recommended to create a new Python 3.6+ virtual environment for this specific step. These are the 2 requirements for that virtual environment:

  - `Python 3.6+`
  - `TensorFlow.js 2.3.0`

- There are various libraries to set up a virtual environment. Here is the code to create a virtual environment named `dl_env`. This code works, assuming conda is installed.

      conda create -n dl_env python=3.6
      conda activate dl_env
      pip install tensorflowjs==2.3.0

- The virtual environment must be set up with `tensorflowjs` installed within the virtual environment before `tensorflowjs_converter` can be used in the next step.

---

### 4. **Convert the model (artifacts) file**

- These are the options we used for tensorflowjs_converter. You may need to adjust these options depending on your model.

- We are converting the default **tensorflow.js** model for a few reasons.

### **Model shards**

- Our model file is large, and the default **tensorflow.js** breaks the model down into 5 MB shards.

  - For Milestone 3, we need one file, so we are specifying weight_shard_size_bytes of `50,000,000` bytes to get that file.

        --weight_shard_size_bytes=50000000

- Inference-speed optimization using `GraphModel` conversion

- _How does GraphModel conversion boost TensorFlow.js models’ inference speed?_

  - _It’s achieved by leveraging TensorFlow (Python)’s ahead-of-time analysis of the model’s computation graph at a fine granularity._
  - _The computation-graph analysis is followed by modifications to the graph that reduce the amount of computation while preserving the numeric correctness of the graph’s output result._

        tensorflowjs_converter \
         --input_format keras \
         --output_format tfjs_graph_model \
         my/layers-model my/graph-model

### **Inference-speed optimization: Quantization**

- Quantization is a post-training technique to reduce the size of models.

  - Here, we use quantization to decrease the default `32-bit` precision to `16-bit` precision which will reduce the model file size by half.

        --quantize_float16=\*

- We can combine all **3 conversion** steps into this:

      tensorflowjs_converter model.h5 model_tfjs \
      --input_format keras \
      --output_format tfjs_graph_model \
      --weight_shard_size_bytes 50000000 \
      --quantize_float16

- Go into your `model_tf` folder containing your downloaded files, and run the above converter command in your virtual environment.

---

### **5. Setting up your repository for the web app**

- In the above steps, you downloaded the model file and did the required conversion.
  - Next, you will set up a repository on GitHub to host your code and add the converted model file there.

### **a. Get started with a template repository**

- We are providing a template repository of code to get started with your web app.

  - The template repository is one web app that does both server-side and browser-based inference.

- You can fork and clone it under your GitHub account. This is the template repository:
  [deploying-web-app](https://github.com/reshamas/deploying-web-app.git)

### **b. Copy the model file to your forked repository**

- This is the original file from Colab: `model.h5`
- This is the converted tfjs file: `model_tfjs`

- The structure of your forked repository with the model files will look similar to this.
  - Place the original and converted model in the directory `backend/assets`.

```bash
├── backend
│ ├── app.py
│ ├── assets
│ │ ├── classes.json
│ │ ├── model_tf
| | |──├──model.h5
│ │ └── model_tfjs
│ │ ├── group1-shard1of1.bin
│ │ └── model.json
```

### **c. Understand the frameworks for the web app**

- There are various options for serving web apps in Python, including **Flask**, **Django**, and **FastAPI**.

- We will be serving our browser app with **FastAPI** and using **React** for the frontend framework.

  - That is the code available in our template repository.

  - Feel free to customize or use your own template.

### **d. Run the app locally using Docker (see FAQ for more info on Docker)**

- The repo provides a `Docker file` to run the app.

  - Run these commands to launch the app.
  - The first time you run using Docker, it could take up to 10 minutes.
  - This command needs to be run at the base level of your repo where the Docker file is located.

        docker build -t app .
        docker run -p 8000:8000 -t app

- Running the above two commands will start a webserver running locally on your machine.

- The server can be accessed at [http://localhost:8000](http://localhost:8000/)

  - You should be greeted with something like below.

  - Voilà! You have a web app running locally!

![](../assets/imgs/food-classifier-web-app-demo.gif)

- Deploy the app to a cloud platform
- Heroku is a nice, free option for deploying the app.

- Once the Heroku command-line tools are installed, it can be run using the below commands.

- Replace `APP_NAME` with something unique. The below steps could take some time (5 to 10 minutes) depending on your internet upload speed.

        APP_NAME="....."

        heroku login
        heroku container:login

        heroku create $APP_NAME

        heroku container:push web --app ${APP_NAME}

        heroku container:release web --app ${APP_NAME}
        heroku open --app $APP_NAME
        heroku logs --tail --app ${APP_NAME}

Here is our web app as an example: [manning-deploy-imagenet.herokuapp.com]()

- Record the inference times
- Now that the app is running remotely, let’s measure the latency for several sample images. We suggest experimenting with images of different sizes and visiting the site on desktop and mobile.

- Understand the internals of the repo
- To learn more about the internals of the template repository and the inference process, refer to the section Understand the Internals of the Repo.

### Deliverable

- The deliverable is a GitHub repo that contains the source code for your deployed web app.

- To help you get started, feel free to use our template repo.

- In the README.md of your repo, there should be a:

- Link to your Heroku (or other cloud provider) application.

- Table that contains the latency information as described below.

- Upload a link to your deliverable in the Submit Your Work section and click submit. After submitting, the Author’s solution and peer solutions will appear on the page for you to examine.

### Help

- Feeling stuck? Use as little or as much help as you need to reach the solution!

### resources

- [Deep Learning with JavaScript: Neural networks in TensorFlow.js]() by _Shanqing Cai, Stanley Bileschi, Eric D. Nielsenn and Francois Chollet_

  - **Chapter 1, Unit 1.2, Why Combine JavaScript and Machine Learning?**, is helpful for understanding the code in the template repo for deploying the web app.
  - **Chapter 1, Unit 3, Why TensorFlow.js?**
  - **Chapter 12, Unit 2, Model Optimization.**

- [React Native in Action]() by _Nader Dabit_
  - **Chapter 2, Understanding React, is a good intro to React.**

### Additional resources

- TensorFlow.js Converter is the main documentation site for TensorFlow.js converter. This is helpful for converting the Colab model to the needed format for deploying the app.

- Docker is a good tutorial on docker

- Heroku Installation is a useful resource for deploying the app on a free cloud server.

- TFJS MobileNet Example is a nice example from the TensorFlow team on using MobileNet, the pre-trained architecture optimized for mobile deployment.

- FastAPI is a Python async webserver similar to Flask. This provides background on the tool we are using for serving our web app in Python.

- Python virtual environment has various options for setting up virtual environments in Python.

### Tip

- If your model accuracy is high, but the predicted label is incorrect, it could be a mismatch due to the order of the labels in `classes.json` file.
