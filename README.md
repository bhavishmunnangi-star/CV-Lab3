Computer Vision Lab 3 – Average Image Filtering
Overview

This project demonstrates average (mean) filtering on a grayscale image using Python, OpenCV, NumPy, and Matplotlib.

Average filtering is a basic image-processing technique used for smoothing images and reducing noise. The filter replaces each pixel with the average value of the pixels in its surrounding neighborhood.

In this lab, average filters of three different sizes are applied:

3×3 filter

5×5 filter

7×7 filter

The project demonstrates the filtering process using both OpenCV's built-in filter2D() function and a manually implemented average filter.

Technologies Used

Python

OpenCV (cv2)

NumPy

Matplotlib

Google Colab

Input Image

The program reads a grayscale image named:

/content/images.jpg


The image is loaded using OpenCV:

img = cv2.imread('/content/images.jpg', 0)


The 0 parameter loads the image in grayscale mode.

Method 1: OpenCV Average Filtering

Three averaging kernels are created using NumPy:

blur3 = np.ones((3,3), np.float32) / 9
blur5 = np.ones((5,5), np.float32) / 25
blur7 = np.ones((7,7), np.float32) / 49


These kernels are applied to the image using OpenCV's filter2D() function:

blur3x3 = cv2.filter2D(img, -1, blur3)
blur5x5 = cv2.filter2D(img, -1, blur5)
blur7x7 = cv2.filter2D(img, -1, blur7)


The original image and filtered results are then displayed together for comparison.

Method 2: Manual Average Filtering

The second part implements average filtering without using OpenCV's filtering function.

For every pixel, a surrounding region is extracted according to the selected kernel size. The average of all pixels in that region is calculated and assigned to the output image.

For example, for a 3×3 filter:

Average = Sum of 9 neighboring pixels / 9


The implementation uses zero-padding around the image:

padded = np.pad(image, pad, mode='constant', constant_values=0)


The filtering operation is performed using nested loops over the image.

Filter Sizes
Filter	Number of Pixels	Effect
3×3	9	Mild smoothing
5×5	25	Moderate smoothing
7×7	49	Stronger smoothing

As the filter size increases, more neighboring pixels contribute to the output pixel. Therefore, larger filters generally produce a smoother and more blurred image, while also reducing fine details.

Output

The program displays four images:

Original grayscale image

Image after 3×3 average filtering

Image after 5×5 average filtering

Image after 7×7 average filtering

This allows the effect of different kernel sizes to be visually compared.

How to Run
Using Google Colab

Open the notebook in Google Colab.

Upload images.jpg to the /content/ directory.

Run the cells sequentially.

The filtered images will be displayed using Matplotlib.

Required Libraries

Install the required packages if they are not already available:

pip install opencv-python numpy matplotlib

Conclusion

This experiment demonstrates the basic concept of spatial-domain image smoothing using average filters. The results show that increasing the kernel size from 3×3 to 7×7 increases the smoothing effect and reduces image details.

The lab also provides a comparison between using a built-in OpenCV filtering function and implementing the average filtering operation manually using NumPy and Python loops.
