```python
from PIL import Image

import random

import numpy as np

import matplotlib.pyplot as plt

from scipy.ndimage import label

from skimage import measure

  
  
  

# a method that takes in an image, and returns a dictionary called CC, where CC['PixelIdxList'] is a list

# CC['pixelIDXList][i] contains the i'th white region of the image

## CC['numObjects] contains number of connected components

def connected_components(image):

    CC = {} #Dictionary to store the connected components

    image_copy = np.copy(image).astype(float) #Make a copy of the image

    x = image_copy[0,0,0]+image_copy[0,0,1]+image_copy[0,0,2] #Sum RGB values

    image_copy = image_copy[:,:,0:3] #Remove the alpha channel

    image_copy = (image_copy[:,:,0] + image_copy[:,:,1] + image_copy[:,:,2])/3 #Convert to grayscale

    image_copy[image_copy < 255] = 0 #Make all pixel values other than 255 equal to 0

    label = measure.label(image_copy) #Label the connected components

    num = np.max(label) #Find the number of connected components

    CC['numObjects'] = num

    CC['PixelIdxList'] = []

    for i in range(1,num+1):

        indices = np.nonzero(label == i) #Find the indices of the i'th connected component

        CC['PixelIdxList'].append(indices) #Append the indices to the PixelIdxList

    return CC

  

def validate_border(indices, image):

    #Iterate over the indices and find out which pixel indices are neighbor to the border in the component.

    #If it is a closed component with the border, then all neighbor indices will also form a connected component

    # 8 direction array

    dx = [-1, -1, -1, 0, 0, 1, 1, 1]

    dy = [-1, 0, 1, -1, 1, -1, 0, 1]

    image_copy = np.copy(image).astype(float) #Make a copy of the image to check for connected components again

    image_copy = image_copy[:,:,0:3]

    image_copy[True] = 0

    border_pixels = [] #List to store the border pixels

    border_neighbors = [] #List to store the border neighbors whose color we will use to color border in future

    for i in range(len(indices[0])):

        x = indices[0][i]

        y = indices[1][i]

        for j in range(8):

            new_x = x + dx[j]

            new_y = y + dy[j]

            #Check if the new_x and new_y are within the bounds of the image

            if new_x >= 0 and new_x < image.shape[0] and new_y >= 0 and new_y < image.shape[1]:

                #Check if the pixel value is (100,100,100)

                if image[new_x, new_y, 0] == 100 and image[new_x, new_y, 1] == 100 and image[new_x, new_y, 2] == 100:

                    image_copy[x,y,0:3] = 255.0 #Set the pixel value to white

                    border_pixels.append((new_x,new_y))

                    border_neighbors.append((x,y))

    #Check if the border_neighbor list is connected togeher

    new_CC = connected_components(image_copy)

    return new_CC['numObjects'] == 1, border_pixels, border_neighbors #Return True if the border is connected, False otherwise

  

#Method to paint the pixels of the connected component with random colors

def paint_pixels(indices, image):

    for i in range(len(indices[0])):

        x = indices[0][i]

        y = indices[1][i]

        # Set the pixel value to a random color

        image[x,y,0] = random.randint(0,255)

        image[x,y,1] = random.randint(0,255)

        image[x,y,2] = random.randint(0,255)

    return image

#Method to paint the border pixels with the color of the neighbor

def paint_borders(gray_borders, gray_neighbors,image):

    for i in range(len(gray_borders[0])):

        x = gray_borders[i][0]

        y = gray_borders[i][1]

        neighhbor_x = gray_neighbors[i][0]

        neighbor_y = gray_neighbors[i][1]

  

        # paint the border pixel with the color of the neighbor it was previously borderin

        image[x,y,0] = image[neighhbor_x, neighbor_y, 0]

        image[x,y,1] = image[neighhbor_x, neighbor_y, 1]

        image[x,y,2] = image[neighhbor_x, neighbor_y, 2]

    return image

  

random.seed(0) #Set the seed for random number generation

image_path = "your_image.png" #Path to the image

  

image = Image.open(image_path)

image = np.array(image) #Convert the image to a numpy array

  

CC = connected_components(image) #Get the connected components

gray_borders = []

gray_neighbors = []

#Iterate over the connected components and paint the pixels with random colors

for i in range(1, CC['numObjects']+1):

    indices = CC['PixelIdxList'][i-1]

    is_valid, border_pixels, border_neighbors = validate_border(indices, image)

    if(is_valid == True): #If the component is valid, paint the pixels with random colors

        gray_borders.extend(border_pixels) #Add the border pixels to the list

        gray_neighbors.extend(border_neighbors) #Add the border neighbors to the list

        print("Component number " + str(i) + " is valid")

        image = paint_pixels(indices, image)

  

#Paint the border pixels with the color of the neighbor

image = paint_borders(gray_borders, gray_neighbors, image)

  

#Save image as PNG as output.png

plt.imsave('output.png', image)

plt.imshow(image)

plt.axis('off')  # Optional: to hide axes for a cleaner view

plt.show()
```