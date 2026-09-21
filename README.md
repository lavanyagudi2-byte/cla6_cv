https://colab.research.google.com/drive/1NpAi47vXWTF9eDOirNUyVKsE-aiQLTUd#scrollTo=QyU_PdGySvYm&fullscreenOutput=true
# Intensity Level Slicing using Python and OpenCV

## Aim

To perform **Intensity Level Slicing** on an image using Python and OpenCV by highlighting pixels within a specified intensity range.

## Description

Intensity Level Slicing is an image enhancement technique used to highlight a specific range of intensity values in an image.

In this experiment, the intensity range is selected between:

* **Minimum Intensity (`rmin`) = 100**
* **Maximum Intensity (`rmax`) = 200**

Pixels whose intensity values fall within this range are highlighted. Two types of intensity slicing are performed:

1. **Slicing With Background** – The selected intensity range is highlighted while the remaining background is retained.
2. **Slicing Without Background** – The selected intensity range is highlighted while the remaining pixels are suppressed.

## Technologies Used

* Python
* OpenCV
* NumPy
* Pandas
* Matplotlib
* Google Colab

## Input Image

The program uses the image:

```text
Who-Created-Bubu-Dudu.png
```

The image is read as a grayscale image using OpenCV.

```python
img = cv2.imread("/content/Who-Created-Bubu-Dudu.png", 0)
```

## Intensity Range

```python
rmin = 100
rmax = 200
```

The pixels having intensity values between **100 and 200** are selected for slicing.

## Methodology

### 1. Read the Image

The input image is loaded in grayscale format.

```python
img = cv2.imread("/content/Who-Created-Bubu-Dudu.png", 0)
```

### 2. Display the Original Image

Matplotlib is used to display the original grayscale image.

```python
plt.figure(figsize=(3, 3))
plt.imshow(img, cmap='gray')
plt.title('Original Image')
plt.axis('off')
plt.show()
```

### 3. Create Sliced Images

Two output images are created:

```python
slicing_with_bg = img.copy()
slicing_without_bg = np.zeros(img.shape, dtype=np.uint8)
```

The pixels are checked using the selected intensity range.

```python
for i in range(img.shape[0]):
    for j in range(img.shape[1]):
        pixel_value = img[i][j]

        if rmin <= np.mean(pixel_value) <= rmax:
            slicing_with_bg[i][j] = 255
            slicing_without_bg[i][j] = 0
        else:
            slicing_without_bg[i][j] = 255
```

### 4. Display the Results

The original image and sliced images are displayed using Matplotlib.

```python
plt.figure(figsize=(6, 5))

plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(slicing_with_bg, cv2.COLOR_BGR2RGB))
plt.title('Slice With Background')

plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(slicing_without_bg, cv2.COLOR_BGR2RGB))
plt.title('Slice Without Background')

plt.show()
```

## Output

The experiment produces two results:

### Slice With Background

Pixels with intensity values between **100 and 200** are highlighted in white, while the other pixels retain their original intensity values.

### Slice Without Background

Pixels within the selected intensity range are suppressed, while the remaining pixels are displayed in white.

## Applications

Intensity Level Slicing can be used for:

* Image enhancement
* Highlighting specific objects or regions
* Medical image analysis
* Satellite image processing
* Object detection
* Feature extraction
* Image segmentation

## Conclusion

Intensity Level Slicing was successfully performed on the given image using Python and OpenCV. The intensity range from **100 to 200** was selected to highlight specific pixels. Both **slicing with background** and **slicing without background** were implemented successfully. This technique helps in enhancing important regions of an image based on their intensity values.
