# Digital-Image-Fundamentals
### 1. Image showing with the help of Mathplotlib and PLW 
![image](https://github.com/Shawon5030/Digital-Image-Fundamentals/assets/149573785/c63fd934-826a-4412-b41e-e109d2301d0e)


Install Required Libraries
 First you need to make sure you have Matplotlib and Pillow installed. You can install them using pip:


Import the library 

     from PIL import Image
     import numpy as np
     import matplotlib.pyplot as plt
     from skimage import color, filters 

1st step <br/>
     image = Image.open(image_path)
<br/> First line defines a variable named image_path and assigns the string 'Cat.png' to it. This string represents the file path of the image you want to open and display. You need to ensure that the file path is correct and that the image file exists in the specified location. <br/>

2nd step<br/>
      image = Image.open(image_path) <br/>
Here, the Image.open() function from the Pillow library is used to open the image located at the path specified by the image_path variable. The opened image is then stored in a variable named image.

3rd step <br/>
Display the image using Matplotlib<br/>
      plt.imshow(image) <br/>
This line uses Matplotlib's imshow() function to display the image stored in the image variable. Matplotlib is a popular data visualization library in Python, and imshow() is used to display images. The image to be displayed is passed as an argument to this function.<br/>

4th step <br/>
      plt.axis('off')
This line turns off the axis for the displayed image. By default, Matplotlib displays axis ticks and labels around the image, but in many cases, such as displaying standalone images, you may want to turn them off for a cleaner appearance.<br/>

5th step <br/>
      plt.show()
Finally, this line displays the image on the screen. When you run this code, a window will pop up showing the image. This line is necessary to actually show the image; without it, the image would be processed but not displayed.<br/>



### 2. Image show in histogram ###
![image](https://github.com/Shawon5030/Digital-Image-Fundamentals/assets/149573785/3459e5d6-e263-432b-b880-6752ea105101)


     import numpy as np
     import matplotlib.pyplot as plt
These lines import the necessary libraries: NumPy as np for numerical operations and Matplotlib.pyplot as plt for plotting.<br/>


     def image_show_in_histo(image_path):
This line defines a function named image_show_in_histo() that takes an image_path as an argument.<br/>


     image = Image.open(image_path)
Here, the Image.open() function from the Pillow library is used to open the image located at the path specified by the image_path variable. The opened image is then stored in a variable named image.<br/>

     array_image = np.array(image)
This line converts the opened image into a NumPy array, which allows for easy manipulation and analysis of the image data.<br/>

     plt.figure(figsize=(10, 5))
This line creates a new figure with a specified size (width: 10 inches, height: 5 inches) for plotting the color histograms.<br/>

     for i, color in enumerate(['r', 'g', 'b']):
This line iterates over each color channel in the image: red, green, and blue. The enumerate() function is used to loop over the channels while also getting the index i.<br/>

    hist, bins = np.histogram(array_image[:, :, i].flatten(), 256, [0, 256])
Here, the NumPy histogram() function is used to compute the histogram of the current color channel (array_image[:, :, i]). It calculates the frequency of each pixel value within the range of [0, 256).<br/>

plt.plot(hist, color=color)<br/>
This line plots the histogram of the current color channel (hist) with the specified color.<br/>


    plt.title("Color Histogram")
    plt.xlabel("Pixel Value")
    plt.ylabel("Frequency")\
    plt.show()
These lines add a title to the histogram, label the x-axis and y-axis, and then display the histogram plot.<br/>

# 3. Edge detection with Sobel #
![image](https://github.com/Shawon5030/Digital-Image-Fundamentals/assets/149573785/a731ef29-07c2-444c-ba27-faed23b50e5d)


    def edge_detect(image):
This line defines a function named edge_detect() that takes an image as an argument.<br/>


    gray_image = color.rgb2gray(np.array(image))
Here, the input image is converted to a grayscale image using the color.rgb2gray() function from scikit-image. The np.array() function is used to convert the image to a NumPy array before applying the conversion function.<br/>


    edge_sobel = filters.sobel(gray_image)
This line applies the Sobel edge detection filter to the grayscale image using the filters.sobel() function from scikit-image. This filter enhances the edges in the image, making them more prominent.<br/>


    plt.imshow(edge_sobel, cmap='gray')
This line displays the edge-detected image using Matplotlib's imshow() function. The cmap='gray' argument specifies that the colormap to be used is grayscale, ensuring that the image is displayed in grayscale.<br/>


    plt.axis('off')
This line turns off the axis for the displayed image. By default, Matplotlib displays axis ticks and labels around the image, but in many cases, such as displaying standalone images, you may want to turn them off for a cleaner appearance.<br/>


    plt.show()
Finally, this line displays the edge-detected image on the screen. This line is necessary to actually show the image; without it, the image would be processed but not displayed.<br/>


edge_detect(image)
This line calls the edge_detect() function with the image variable as an argument, applying edge detection to the input image.<br/>

# 4 . Image rotate 180 deg #
![image](https://github.com/Shawon5030/Digital-Image-Fundamentals/assets/149573785/9a385326-91df-47fb-8d82-5b5826ecc6ea)


     image_rotate = image.rotate(180)
This line rotates the image object by 180 degrees clockwise using the rotate() method provided by the Pillow (PIL) library. The rotated image is then assigned to a new variable named image_rotate.


     plt.imshow(image_rotate)
Here, plt.imshow() function from Matplotlib is used to display the rotated image. It takes image_rotate as input and plots it as an image.


   plt.axis('off')
This line turns off the axis for the displayed image. By default, Matplotlib displays axis ticks and labels around the image, but in many cases, such as displaying standalone images, you may want to turn them off for a cleaner appearance.


    plt.show()
Finally, this line displays the image on the screen. When you run this code, a window will pop up showing the rotated image. This line is necessary to actually show the image; without it, the image would be processed but not displayed.

# 5  . Plot Surface #
![image](https://github.com/Shawon5030/Digital-Image-Fundamentals/assets/149573785/415e3b42-73f7-4836-8ed3-a8524ab8d668)

    gray_image = np.array(image.convert('L'))
This line converts the image to grayscale using the convert() method with the argument 'L', which converts the image to grayscale (mode 'L') using PIL (Python Imaging Library). Then, the grayscale image is converted to a NumPy array using np.array().


    x = np.arange(0, gray_image.shape[1])
    y = np.arange(0, gray_image.shape[0])
These lines create NumPy arrays x and y representing the coordinates of the image pixels along the x and y axes, respectively. The length of these arrays is determined by the shape of the grayscale image.


    x, y = np.meshgrid(x, y)
This line creates 2D grids of coordinates using np.meshgrid(), which is a function that generates coordinate matrices from coordinate vectors. This is often used to create 2D grids suitable for plotting in 3D.



    fig = plt.figure(figsize=(10, 5))
    ax = fig.add_subplot(111, projection='3d')
These lines create a new figure and add a 3D subplot to it using Matplotlib. The figsize parameter specifies the size of the figure in inches.


    ax.plot_surface(x, y, gray_image, rstride=1, cstride=1, cmap=plt.get_cmap("gray"), linewidth=0)
This line plots a 3D surface using the plot_surface() method of the subplot (ax). It takes the mesh grid x, y, and the grayscale image gray_image as input. The parameters rstride and cstride control the step size for the rows and columns, respectively. cmap specifies the colormap used for coloring the surface, in this case, grayscale. linewidth is set to 0 to remove any lines separating the surface patches.


   ax.set_xlabel("X Axis")
   ax.set_ylabel("Y Axis")
   ax.set_zlabel("Z Axis")
   ax.set_title("3D Surface")
These lines set the labels for the x, y, and z axes, as well as the title of the plot.


    plt.show()
Finally, this line displays the 3D surface plot.

# 6 . Visual Intensity Array of the Image #

![image](https://github.com/Shawon5030/Digital-Image-Fundamentals/assets/149573785/20edc7fd-ceeb-4552-adac-7f8f51a3439b)

    image_array = np.array(gray_image)
This line converts the grayscale image (gray_image) into a NumPy array using np.array(). This is done to perform further operations on the image data as a NumPy array.


    plt.imshow(image_array, cmap='gray')
Here, plt.imshow() function from Matplotlib is used to display the image represented by the image_array. The cmap='gray' argument specifies that the colormap used should be grayscale.


    plt.colorbar(label='Pixel Intensity')
This line adds a colorbar to the plot, which indicates the pixel intensity values corresponding to the grayscale levels. The label='Pixel Intensity' argument specifies the label for the colorbar.


   plt.title('Visual Intensity Array of the Image')
This line sets the title of the plot to 'Visual Intensity Array of the Image'.


   plt.axis('off')
This line hides the axis for the plot, providing a cleaner appearance.


   plt.show()
Finally, this line displays the plot with the grayscale image and colorbar. When you run this code, it will show the grayscale image along with a colorbar indicating the pixel intensity values.
