# Evaluating Different Models Using Transfer Learning

Important! Be sure to read Start Project before beginning. It contains crucial information for your work.

Objective

Use transfer learning and TensorFlow 2 to train at least 2 models on the Food 101 data set. The purpose is to get experience using a pre-trained model and learn how to evaluate models based on accuracy, number of parameters, training time, and model size.

The output from the image classifier you’ll train in Milestone 1 is a model file, which will be used as input to Milestones 2 and 3, to deploy the web and mobile applications.

Importance to project

Transfer learning is an important technique in deep learning, as it allows you to use state-of-the-art models trained on large data sets and optimize them for your problem.

Not all model architectures are optimized for every use case, such as reduced latency versus highest accuracy.

In this milestone, we will evaluate a regular model like VGG19 vs. a mobile-optimized model, such as MobileNetV2. Then, we’ll evaluate them on criteria like accuracy, model size, and time.

Our goal in this project is to create web and mobile applications. We will try different architectures and models, compare them, and choose a model that works best in terms of speed and size for deployment.

Getting Started with Colab

Colaboratory, or Colab for short, allows you to write and execute Python in your browser with:

Zero configuration required
Free access to GPUs
Easy sharing
Here’s a guide for Getting Started With Colab.

Requirements

Create a Google account if you don’t have one.
Sign in with your Google Gmail account.
Subsetting the data

The full dataset has 101 classes (5GB), which will take some time to run. You will want to subset your data for a couple of reasons:

You can reduce training time while experimenting and tweaking the code. This is a good practice in any data science project.
You can save computing costs by reducing GPU time. In practice, you or your company would be paying for a GPU server and training on a smaller data set while experimenting saves costs.
Begin by training three classes. Once the code is closer to completion, you can increase the number of classes of the data set.

Workflow

Set up your development environment with a GPU. Google Colab is a free option that is recommended.
Download the subset of the Food-101 dataset.
The subset is composed of 3 classes (apple_pie, caesar_salad, falafel). The size of the file is 154MB.

There are a number of pre-trained models available in TensorFlow 2 / Keras. Explore these available models:
small (VGG19)
intermediate (ResNet50)
mobile-friendly (MobileNetV2)
Look at the size of the model, its expected training accuracy, depth, etc.

Split your data into training and validation using tf.keras.preprocessing.image.ImageDataGenerator
Train a large model family, such as VGG19/ResNet50, using pre-trained ImageNet weights.
Train a mobile-friendly model family like MobileNet using pre-trained ImageNet weights.
Save the model and classes. There are various formats to save the model and list of classes. We saved the model in h5 format, giving it the name model.h5. We saved the list of classes as a JSON file with the name classes.json.
These model and classes files will be used as input for Milestone 2 when creating the web app.

Deliverable

The deliverable is a Jupyter Notebook containing:

Code to download the subset of the Food-101 dataset
Code to train a large model such as VGG19/ResNet50 models using transfer learning
Code to train a mobile-friendly model like MobileNetV2 using transfer learning
Table comparing models with respect to accuracy, number of parameters, and model size
Code to save the MobileNetV2 model, which will be used in later milestones to create web and mobile applications
Note: Use TensorFlow 2.

Upload a link to your deliverable in the Submit Your Work section and click submit. After submitting, the Author’s solution and peer solutions will appear on the page for you to examine.

Your notebook should include a table like this:

Help

Feeling stuck? Use as little or as much help as you need to reach the solution!

resources
These resources will help you understand how to use transfer learning.

Deep Learning with Python by François Chollet
Chapter 5, Unit 3, Using a Pretrained Convnet.

Deep Learning for Vision Systems by Mohamed Elgendy
Chapter 6, Transfer Learning, Units 2 through 8.

Deep Learning for Vision Systems by Mohamed Elgendy
Chapter 3, Convolutional Neural Networks. This includes pooling global averages and detailed info on layers.

Additional resources

Transfer learning with a pre-trained ConvNet, from the TensorFlow documentation on fine-tuning will also help you understand how to use transfer learning.

"Why do we need to include_top=False?”

Save and load models

About VGG and ResNet

To find a list of all models available to fine-tune, look at the Keras docs on available models.

Food-101 data set from ETH Zürich University

A good resource to getting started is the official TensorFlow tutorial on finetuning: Transfer learning with a pre-trained ConvNet
help

partial solution

full solution

Improve accuracy: fine-tuning (OPTIONAL)

Experiment with fine-tuning the model. Unfreeze some layers and retrain the model. Compare the accuracy, number of parameters, training time and model size.
