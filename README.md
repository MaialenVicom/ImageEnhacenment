# IMAGE RECONSTRUCTION

The main objective of this project is to develop an algorithm that improves the quality of the images from a transvaginal probe camera.

## Image quality improvement experimentation

### Context
The device incorporates a camera at the tip of the probe and a screen to display images in real time. However, several factors affect the quality of these images, which can be classified into three categories:

1. Hardware factors: These include limitations in the physical dimensions of the sensor, which reduce light capture and affect the signal-to-noise ratio (SNR); geometric distortion due to the wide-angle lens, which alters the shape of the captured structures; and transmission delay, which can hinder real-time medical procedures.

2. Clinical environment factors: The presence of a prophylactic on the device can generate reflections and optical distortions, while humidity and biological fluids can foul the lens, affecting image sharpness.

3. Image capture factors: They include noise generated by the capture system (motion and compression artifacts), inadequate illumination (excessive, insufficient or non-uniform), low contrast making tissue differentiation difficult, and color problems due to digital sensor limitations, which can generate altered tones and unwanted shadows.

### Metrics for assessing quality improvement
To determine the appropriate level of image quality improvement, it is essential to define what is meant by good quality in an endoscopic image. Since the objective is to facilitate the work of a clinician in guiding the probe, his or her image quality criterion is key to achieving improvement. As this criterion is difficult to describe precisely because of its subjective component, it is proposed to evaluate the images from another approach. For this reason, in addition to the opinion of the professionals, quantitative metrics have also been calculated: 

#### Metrics with Reference (Full-Reference, FR)

These metrics compare a processed image with its original version. They quantify how much an image has been degraded or enhanced after applying a restoration technique. They are used in this project to determine which enhancement methods achieve the best results on degraded images.

##### Fidelity Metrics

They evaluate the pixel-level similarity between the original (reference) image and the generated image.

| Metrics | Description  | Desired value  |
|--------|-------------|----------------|
| **MSE** | Mean square error: measures the average difference between pixels. | Close to 0 |
| **PSNR** | Signal-to-noise ratio: compares signal to background noise. |  Greater than 30 dB |

##### Perceptual Metrics

They take into account human visual perception, and evaluate how differences affect perceived quality.

| Metrics | Description  | Desired value  |
|--------|-------------|----------------|
| **SSIM** | Structural Similarity Index: evaluates structural similarity, luminance and contrast. | Above 0.85 (range 0-1) |
| **LPIPS** | Learned Perceptual Image Patch Similarity: measures perceptual similarity using neural networks.| Low values (< 0.2) | 

---

####  No-Reference (NR) Metrics

These metrics analyze only the degraded or restored image, without the need for comparison with an original image. They are useful when no reference is available, and are used throughout the project to assess the improvement obtained after processing.

##### Métricas Tradicionales

| Metrics | Description  | Desired value  |
|--------|-------------|----------------|
| **Entropy** | Measures the amount of information present in the image. | Greater than 7 (range 0-8) |
| **Contrast** | Calculates the variation in brightness between areas. | Between 40-70% (range 0-100) |
| **Sharpness** | Indicates the clarity of edges and details. | Between 60-70% (range 0-100) |
| **Colorfulness** | Measures the saturation and gamut of colors. | Around 50% (range 0-100) |

##### Neural Network-Based Metrics

Use trained models to simulate human perception of visual quality.

| Metrics | Description  | Desired value  |
|--------|-------------|----------------|
| **BRISK** | Analyzes the image by mimicking the perception of the human eye. | Lower is better (optimal → 0, ideal < 0.2) |
| **NIQE** | Compares the image with a statistical model based on natural images. | Lower is better (optimal → 0, ideal < 0.2) |
| **NIMA** | Score generated by a neural network based on human perception. | 1-4: Low quality, 4-7: Acceptable, 7-10: High quality.|

## Content

Performing image quality enhancement is essential to achieve the best possible visual and quantitative results. Two types of processing methods have been proposed to enhance medical images:   

- **[Traditional methods-based algorithms](https://github.com/MaialenVicom/ImageReconstruction/tree/main/Algorithm%20based%20on%20traditional%20methods)**.

- **[Deep learning based algorithm](https://github.com/MaialenVicom/ImageReconstruction/tree/main/Algorithm%20based%20on%20deep%20learning)**.

To visualize the performance of both algorithms dynamically, you can access the following result visualization interface:
- **[Results visualization interface](https://github.com/MaialenVicom/ImageReconstruction/tree/main/Interface%20for%20result%20display)** ⏩ https://img-reconstruction-zk7tqhrbjkzrdah79lj2ex.streamlit.app/


