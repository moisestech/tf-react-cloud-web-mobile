# Understand the Internals of the Repo

The repo contains both the backend code and the frontend code.

Backend

The backend contains 2 files:

app.py: This contains the FastAPI web routes that expose the prediction endpoint and serve the static files. The core model prediction happens in helper.py.
helper.py: This loads the model.h5 file, performs the inference, and returns the prediction. Below, you’ll see the core inferencing logic in helper.py:
import tensorflow as tf
from PIL import Image

# Load the model.

classifier = tf.keras.models.load_model("assets/model_tf/model.h5")

# Load the labels.

with open(f"assets/classes.json") as f:
labels = json.load(f)

# Parse an image from url/file.

image: PIL.Image.Image = Image.open(...)

# Resize the input image.

target_size = 224
image = image.resize(target_size)

# Preprocess the image so it is betweeen [-1,1].

image = tf.keras.preprocessing.image.img_to_array(image)
image = tf.keras.applications.mobilenet_v2.preprocess_input(image)

# Convert the input to a batch size of 1.

image = np.expand_dims(image, axis=0)

# Pass to model.

result = classifier.predict(image)

result = sorted(
list(zip(
labels
, np.squeeze(result).tolist()
)
)
, key=lambda x: x[1]
, reverse=True
)
Frontend

The React frontend app is composed of 2 main screens, Home and About.

The core inferencing logic is defined in ModelService.tsx.

The class contains both server-side inference and browser-based inference code.

Server side inference

To make a call to the FastAPI backend for server-side inference, use:

// Load the image.

const imgUrl = ...
const response = await fetch(imgUrl);
const data = await response.blob();

// Prepare the image for post endpoint.
const metadata = {
type: 'image/jpeg'
};

const imageData = new File([data], 'upload.jpeg', metadata)
const data = new FormData();
data.append('file', args.imageData);

// Make a call to the backend.
const resPromise = await axios.post'/api/predict_image', data);
Browser inference

Below, you can see code that loads the model in the browser.

const modelAssetUrl = '/assets/model_tfjs/model.json'
const mobilenet = await tf.loadGraphModel(modelAssetUrl);
mobilenet.predict(tf.zeros([1, this.image_size, this.image_size, 3]));
Below is the code used for inference.

const element: HTMLImageElement = ...;

let imageTensor = tf.browser.fromPixels(element)
.resizeBilinear([this.image_size, this.image_size])
.toFloat();

// Normalize the image from [0, 255] to [-1, 1].
const offset = tf.scalar(127.5);
const normalized = imageTensor.sub(offset).div(offset);

// Reshape to a single-element batch so we can pass it to predict.
const batched = normalized.reshape([1, this.image_size, this.image_size, 3]);

// Make a prediction through mobilenet.
mobilenet.predict(batched);
