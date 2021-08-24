# Understand the Internals of the Repo

- The app is composed of two screens, **Home** and **About**.

- The code for the **Home screen** is defined in `HomeScreen.tsx`.

- The Home screen contains logic for image selection, display prediction, and timing information. The core inferencing logic is delegated to ModelService.tsx.

The code for the About screen is defined in AboutScreen.tsx.

The AboutScreen.tsx renders a simple markdown file defined in config.tsx. Edit this config file to update the info displayed on the screen and other parameters used in the app such as image size, number of predictions, precision of the probability, and title.

The core inferencing logic is defined in ModelService.tsx.

To initialize the TensorFlow.js model, ModelService.tsx calls the below code in the create method.

const modelJSON = require('../assets/model_tfjs/model.json');
const modelWeights = require('../assets/model_tfjs/group1-shard1of1.bin');
const modelClasses = require("../assets/model_tfjs/classes.json")
const imageSize = 224;
const model = await tf.loadGraphModel(bundleResourceIO(modelJSON, modelWeights));
model.predict(tf.zeros([1, imageSize, imageSize, 3]));
Below is the core code used for getting a prediction from an image used in classifyImage.

// Load the model.
const model:tf.GraphModel = ...

// Load the image.
const imageAssetPath = Image.resolveAssetSource(imagePath)
const imgB64:string = await FileSystem.readAsStringAsync(imageAssetPath.uri, {
encoding: FileSystem.EncodingType.Base64,
});
const imgBuffer = tf.util.encodeString(imgB64, 'base64').buffer;
let imageTensor:tf.Tensor3D = decodeJpeg (new Uint8Array(imgBuffer) )

// Resize the image.
const imageSize = 224;
imageTensor = imageTensor.resizeBilinear([imageSize, imageSize]).toFloat();

// Normalize the image from [0, 255] to [-1, 1].
const offset = tf.scalar(127.5);
const normalized = img.sub(offset).div(offset);
const preProcessedImage = normalized.reshape([1, imageSize, imageSize, 3]);

const predictionsTensor:tf.Tensor = model.predict(preProcessedImage) as tf.Tensor;
