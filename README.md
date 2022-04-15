# Where is Waldo in this picture?
![]()

# Finding Waldo by using image labeling:
A 3 dimensional image (i.e. RGB) is converted into a 2 dimensional grayscale image by taking a normalized average of the red, green, and blue channel values. This combines the luminance of each color band into a reasonable (in other words, fast!) grayscale approximation. 

Next, histogram thresholding was applied to the image to find a good threshold for foreground objects. Since most values of the histogram were extreme (i.e. near 1) and since Waldo is primarily red, I decided on a color threshold of 0.33. This meant that that luminance values less than 0.33 would be one and all other values would be zero, in a square footprint pattern of 3 by 3.The square footprint patten was morphologically closed using skimage's closing method, which is defined as a dilation(i.e. increasing foreground pixels) followed by an erosion(i.e. decreasing foreground pixels). 

After removing artifacts with skimage's clear boarder method, the regions were labeled by connecting pixels that were in the same neighborhood and had the same value which for 2 dimensional images would be either 1 or 2 based orthogonal connectivity. I used the default setting so full connectivity was used. 

Lastly each labeled image-region was computed with skimage's regionprops method. After many different trials, the number of pixels in the labeled region was decided to be greater than or equal to 1980 and less than 2405. And Waldo was found and labeled, as seen below!
 
# End Result
![]()

# References
[Image labeling](https://scikit-image.org/docs/dev/auto_examples/segmentation/plot_label.html)
[RGB TO Grayscale](https://www.kdnuggets.com/2019/12/convert-rgb-image-grayscale.html)
