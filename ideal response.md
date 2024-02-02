```python
from PIL import Image

import random

import numpy as np

import matplotlib.pyplot as plt

from scipy.ndimage import label

from skimage import measure

  

image = Image.open("c.png")

  

image = np.array(image)

  

# a method that takes in an image, and returns a dictionary called CC, where CC['PixelIdxList'] is a list

# CC['pixelIDXList][i] contains the i'th white region of the image

## CC['numObjects] contains number of connected components

def connected_components(image):

    CC = {}

    image_copy = np.copy(image).astype(float)

    x = image_copy[0,0,0]+image_copy[0,0,1]+image_copy[0,0,2]

    image_copy = image_copy[:,:,0:3]

    image_copy = (image_copy[:,:,0] + image_copy[:,:,1] + image_copy[:,:,2])/3

    image_copy[image_copy < 255] = 0 #Make all pixel values other than 255 equal to 0

    label = measure.label(image_copy)

    num = np.max(label)

    print(num)

    CC['numObjects'] = num

    CC['PixelIdxList'] = []

    for i in range(1,num+1):

        indices = np.nonzero(label == i)

        # print(indices)

        CC['PixelIdxList'].append(indices)

    return CC

  

def validate_border(indices, image):

    #Iterate over the indices and find out which pixel indices are borderin the component.

    #Meaning find the pixels that have at least one neighbor of pixel value (100,100,100)

    # 8 direction array

    dx = [-1, -1, -1, 0, 0, 1, 1, 1]

    dy = [-1, 0, 1, -1, 1, -1, 0, 1]

    image_copy = np.copy(image).astype(float)

    image_copy = image_copy[:,:,0:3]

    image_copy[True] = 0

    border_pixels = []

    border_neighbors = []

    for i in range(len(indices[0])):

        x = indices[0][i]

        y = indices[1][i]

        for j in range(8):

            new_x = x + dx[j]

            new_y = y + dy[j]

            if new_x >= 0 and new_x < image.shape[0] and new_y >= 0 and new_y < image.shape[1]:

                if image[new_x, new_y, 0] == 100 and image[new_x, new_y, 1] == 100 and image[new_x, new_y, 2] == 100:

                    image_copy[x,y,0:3] = 255.0

                    border_pixels.append((new_x,new_y))

                    border_neighbors.append((x,y))

    #Check if the border_neighbor list is connected togeher

    new_CC = connected_components(image_copy)

    return new_CC['numObjects'] == 1, border_pixels, border_neighbors

def paint_pixels(indices, image):

    for i in range(len(indices[0])):

        x = indices[0][i]

        y = indices[1][i]

        image[x,y,0] = random.randint(0,255)

        image[x,y,1] = random.randint(0,255)

        image[x,y,2] = random.randint(0,255)

    return image

def paint_borders(gray_borders, gray_neighbors,image):

    for i in range(len(gray_borders[0])):

        x = gray_borders[i][0]

        y = gray_borders[i][1]

        neighhbor_x = gray_neighbors[i][0]

        neighbor_y = gray_neighbors[i][1]

        # print(x,y)

        image[x,y,0] = image[neighhbor_x, neighbor_y, 0]

        image[x,y,1] = image[neighhbor_x, neighbor_y, 1]

        image[x,y,2] = image[neighhbor_x, neighbor_y, 2]

    return image

CC = connected_components(image)

gray_borders = []

gray_neighbors = []

for i in range(1, CC['numObjects']+1):

    indices = CC['PixelIdxList'][i-1]

    is_valid, border_pixels, border_neighbors = validate_border(indices, image)

    if(is_valid == True):

        gray_borders.extend(border_pixels)

        gray_neighbors.extend(border_neighbors)

        print("Component number " + str(i) + " is valid")

        image = paint_pixels(indices, image)

  
  

image = paint_borders(gray_borders, gray_neighbors, image)

# print(gray_borders)

#Save image as PNG as output.png

plt.imsave('output.png', image)

plt.imshow(image)

plt.axis('off')  # Optional: to hide axes for a cleaner view

plt.show()
```