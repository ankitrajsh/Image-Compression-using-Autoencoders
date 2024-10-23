# Image Compression using Autoencoder

This project demonstrates the implementation of an autoencoder for compressing images. Autoencoders are neural networks used to learn efficient data representations in an unsupervised manner. Here, we use a convolutional autoencoder to reduce the dimensionality of images for compression purposes.

## Project Structure

- **Autoencoder Architecture**: A convolutional autoencoder model is used with an encoder-decoder structure. The encoder compresses the input image, and the decoder reconstructs the image from its compressed representation.
- **Image Processing**: Input images are preprocessed (resized and normalized) before being fed into the model.
- **Training**: The autoencoder is trained using custom images where the input and output are the same, as this is a reconstruction task.
- **Evaluation**: After training, the model is evaluated on how well it can compress and reconstruct images.

## Requirements

Install the required dependencies by running:

```bash
pip install -r requirements.txt
```

### Model Architecture

The autoencoder consists of two main parts: the **Encoder** and the **Decoder**.

### Encoder
The encoder is responsible for compressing the input image into a lower-dimensional representation. It consists of:
- **Convolutional layers**: Extract features from the input image using `ReLU` activation.
- **Max pooling layers**: Downsample the image, reducing its dimensionality while retaining important features.

### Decoder
The decoder reconstructs the original image from the compressed representation. It consists of:
- **Convolutional layers**: Use `ReLU` activation to learn and reconstruct features from the compressed image.
- **UpSampling layers**: Upscale the compressed image back to its original dimensions.
- **Sigmoid activation**: In the final layer, this generates pixel values between 0 and 1, ensuring the output image is a grayscale image.

## Usage

### 1. Prepare the dataset:
Place your input images in a directory (e.g., `images/`). The images will be resized to `(256x256)` and converted to grayscale before being used in the model.

### 2. Train the model:
To train the autoencoder, run the following code:

```python
autoencoder.fit(input_images, input_images,  # Input and output are the same
                epochs=50,
                batch_size=256,
                shuffle=True,
                validation_split=0.2)
```
### 3. Image Preprocessing:
Images are resized to `256x256` and normalized (pixel values scaled between 0 and 1) before being fed into the model.

```python
from tensorflow.keras.preprocessing.image import load_img, img_to_array

def preprocess_image(image_path):
    img = load_img(image_path, target_size=(256, 256), color_mode='grayscale')
    img_array = img_to_array(img) / 255.0  # Normalize pixel values to range [0, 1]
    return img_array
```
### 4. Evaluate the autoencoder:
To evaluate the performance of the autoencoder, visualize the compressed and reconstructed images using the code:
## Acknowledgments

- [Keras Documentation](https://keras.io/)
- [TensorFlow Documentation](https://www.tensorflow.org/)


