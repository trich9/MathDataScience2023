```python
import requests
from PIL import Image
from io import BytesIO
import matplotlib.pyplot as plt

# Replace 'your_image_url' with the actual URL of the image you want to load
image_url = 'https://imageio.forbes.com/specials-images/imageserve/5d6586c068cb0a0008c08f54/Michael-Jordan/0x0.jpg?format=jpg&height=1963&width=1963'
response = requests.get(image_url)
image = Image.open(BytesIO(response.content))

# Display the image
plt.imshow(image)
plt.axis('off') # hide axis
plt.show()

# Resize the image to 224x224
resized_image = image.resize((224, 224))

# Display the resized image
plt.imshow(resized_image)
plt.axis('off')  # Turn off axis labels and ticks
plt.show()

# Convert the image to grayscale
grayscale_image = resized_image.convert("L")

# Display the grayscale image
plt.imshow(grayscale_image, cmap='gray')
plt.axis('off')  # Turn off axis labels and ticks
plt.show()

import numpy as np
import cv2
import matplotlib.pyplot as plt

# Assuming 'resized_image' is your resized image from earlier
image = np.array(resized_image)

# Create 10 random filters
filters = [np.random.randn(3, 3) for _ in range(10)]

# Create a figure to display filters and feature maps
plt.figure(figsize=(15, 5))

# Display each filter and corresponding feature map
for i, filter in enumerate(filters):
    # Apply the filter to the image
    feature_map = cv2.filter2D(image, -1, filter)

    # Plot the filter
    plt.subplot(2, 10, i + 1)
    plt.imshow(filter, cmap='gray')
    plt.axis('off')

    # Plot the corresponding feature map
    plt.subplot(2, 10, i + 11)
    plt.imshow(feature_map, cmap='gray')
    plt.axis('off')

plt.show()
