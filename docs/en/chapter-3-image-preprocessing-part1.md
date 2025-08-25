---
source_pdf: 2025_Chapter 3 - Image Preprocessing_Part1.pdf
exporter: pymupdf_markdown
---



<!-- Page 1 / 43 -->

Dr. NG Hsiao Piau
Ng_h_p@nus.edu.sg


<!-- Page 2 / 43 -->

Lecture 3 (Part1) 
Image Preprocessing
2


<!-- Page 3 / 43 -->

Topics 
•
Definitions
•
Gray Level Transformation
•
Histogram Equalization
•
Geometric Transformation
•
Noise and Filtering
3


<!-- Page 4 / 43 -->

Key takeaways 
•
Gray level transforms: negative, thresholding, contrast stretch
•
Histogram equalization: enhances contrast
•
Geometric transforms: pixel mapping + interpolation
•
Noise types: Gaussian, impulse, quantization
•
Filtering: smoothing and edge detection
4


<!-- Page 5 / 43 -->

1. Definitions
•
Image pre-processing refers to operations with images at 
the lowest level of abstraction—both input and output are 
intensity images.
•
The aim of pre-processing is an improvement of the 
image data that suppresses unwilling distortions or 
enhances some image features important for further 
processing.
•
Hence, image pre-processing can be classified into 
image enhancement and image restoration.
5


<!-- Page 6 / 43 -->

•
After image enhancement, the result is more suitable than 
the original image for a specific application.
•
Problem oriented
•
Two categories of approaches
•
Spatial Domain Methods
•
Spatial domain refers to the image plane itself
•
Direct manipulation of pixels in the image
•
Get to see the results after processing
•
Easy to implement but can be computational intensive
•
Frequency Domain Methods
•
Processing techniques are based on modifying the Fourier Transform of an 
image
•
Effective, quite imaginative as you do not see the results immediately after 
processing 
•
Image restoration takes a corrupt/noisy image and 
estimates the clean, original image.
6


<!-- Page 7 / 43 -->

Spatial Domain Methods
•
Spatial domain methods operate directly on the pixels composing an 
image.
•
Image processing function:
f(x, y): input image
g(x, y): processed or output image
T: transfer function - an operator on f(x, y) defined over neighborhood of (x, y)
T can also operate on a set of input images (e.g. pixel-by-pixel averaging for 
noise removal) 
7
( , )
[ ( , )]
g x y
T f x y

Neighborhood about (x, y) is usually a square or rectangular 
area centered at (x, y). The centre of this sub-image moves 
from pixel to pixel during the operation. The operator is applied 
at each location to produce g(x, y).


<!-- Page 8 / 43 -->

Point Processing
•
Point processing is a type of image enhancement, also known 
as pixel brightness transformation. 
•
Neighborhood is 1x1 == the size of pixel neighbor is 0. Point 
processing operates only one pixel. 
•
Transformation is defined pixel by pixel.
•
The transformation T has been referred to as gray-scale 
transformation or gray-level mapping function.
r and s are the gray levels of f(x,y) and g(x,y) at (x,y) respectively.
•
It changes the brightness of a pixel with no consideration of the 
pixel position. 
•
The mapping function can be specified in different ways, such 
as piecewise linear function, or based on the histogram of the 
input image.
8
( )
s
T r



<!-- Page 9 / 43 -->

Point Processing
9
Spatial neighborhoods for grayscale and RGB color images. Observe in (b) that 
a single pair of spatial coordinates, (x,y), addresses the same spatial location in 
all three images.
Source: Digital Image Processing By Gonzalez and Woods, Pearson. 
•
Color: p(i,j) = [ R(i,j) G(i,j) B(i,j) ]
•
RGB/8: R(i,j) = 0..255, G(i,j) = 0..255, B(i,j) = 0..255. 
•
8 bit of data per color channel.


<!-- Page 10 / 43 -->

2. Gray-Scale Transformation
•
The most common gray scale transformation are
• Negative transformation
• Brightness thresholding that results in a black and 
white image
• Piecewise linear function that enhances the image 
contrast between two specific brightness values.
10


<!-- Page 11 / 43 -->

Negative Transformation
•
Also known as negative image. 
It inverts the “color” of an image.
r
s
p(i,j)
L-1
L-1
T(p(i,j))
T(r)
0
r
L
r
T
s




1
)
(
11


<!-- Page 12 / 43 -->

12
for i = 1:a(1)
for j = 1:a(2)
im_out(i,j) = L-1-im(i,j)
end
end  


<!-- Page 13 / 43 -->

Negative Transformation
•
Can we recover the original image by inverting the gray 
scale of a negative image?
s
r
L-1
L-1
T(s)
0
13


<!-- Page 14 / 43 -->

Negative Transformation
•
Example – invert colors of a color image
14


<!-- Page 15 / 43 -->

Obtaining the 
negative of 
image:
(a) gray-level 
transformatio
n function, r
and s denote 
the input and 
output gray 
levels 
respectively; 
(b) an image;
and (c) negative 
of the image.


<!-- Page 16 / 43 -->

Histogram
•
The histogram of an image shows the distribution of the 
pixel values in the image over the intensity (or dynamic) 
range.
•
For a 8-bit gray scale image, the pixel values typically 
from 0  to 255.  
•
The ith item of the histogram is  p(i) = ni /N, i =0..255.
•
It represents the probability of the a randomly chosen 
pixel has the gray level i, where ni is the number of pixels 
of gray level i, and N is the total number of pixels in the 
image. (probability density function).
16


<!-- Page 17 / 43 -->

Histogram: Dark and Bright Images
•
Brightness refers to the overall lightness or darkness of 
an image.
r
L-1
p(r)
Dark image
0
r
L-1
p(r)
Bright image
0
Probability density function (pdf) 
= Number of pixels with intensity r / Total number of pixels
17


<!-- Page 18 / 43 -->

Histogram: Low-contrast and High-contrast 
Images
•
When there are no sharp differences between black and 
white in an image, the image lacks contrast or does not 
have sufficient contrast.
r
L-1
p(r)
Low-contrast image
0
r
L-1
p(r)
High-contrast image
0
18


<!-- Page 19 / 43 -->

Histogram Processing
•
Applying a linear function 
to transform the 
histogram.
A
B
1
-
B
)
B
(
1
A
A
)
A
(
0
)
(















L
f
L
f
r
r
f









r
L-1
p(r)
0
A
B
r
-αA
L-1
L-1
T(r)
0
A
B
19


<!-- Page 20 / 43 -->

Contrast Stretching
•
Contrast stretching is used to change the contrast or 
brightness of an image. 
•
In contrast stretching,
• pixel values below a specified value are considered 
as black (or, have a value 0),
• pixel values above another specified value are 
considered as white, and
• pixel values in between these two values are 
considered as shades of gray. 
•
This is a linear mapping of a subset of pixel values to the 
entire range of grays from black to white.
•
This will produce an image of higher contrast, but some 
details are lost.
20


<!-- Page 21 / 43 -->

Contrast Stretching
r
s
L-1
L-1
T(r)
0
(r1, 0)
(r2, L-1)
Original gray 
scale image
Image after 
contrast stretching
window
21


<!-- Page 22 / 43 -->

Contrast Stretching
•
Using Matlab
% read the input image from disk
model = imread('model_web.jpg');
% convert the input color image to 256 gray level image
modelGray = rgb2gray(model);
colormap(gray(256));
% using image tool to adjust image contrast
imtool(modelGray);
22


<!-- Page 23 / 43 -->

Contrast Stretching
r
s
L-1
L-1
T(r)
0
(r1, 0)
(r2, L-1)
•
To reduce the loss in details of image.
r
s
L-1
L-1
T(r)
0
(r1, s1)
(r2, s2)
piecewise linear function
23


<!-- Page 24 / 43 -->

Piecewise Linear Function
•
A piecewise linear function is a function composed of 
straight line segments, defined by different linear 
expressions over specific intervals of its domain.
•
It is a generalization of typical contrast stretching.
24


<!-- Page 25 / 43 -->

Brightness Thresholding
•
It is a special case of 
piecewise linear function, and 
a simple way for image 
segmentation.
•
A thresholding function will 
map all pixel values below a 
specified threshold to zero 
and all above to 255 for a 8-
bit gray scale image. 
•
Brightness thresholding will 
result in a black-and-white 
image.
r
s
L-1
L-1
T(r)
0
(r1, 0)
(r2, L-1)
1
2
1
1
2
2
0
0
( )
 or 
( )
1
1
r
r
r
r
r
r
s
T r
s
T r
L
r
r
L
r
r

















25


<!-- Page 26 / 43 -->

Contrast stretching:
(a) gray-level 
transformation 
function;
(b) a low-contrast 
image;
(c) result of contrast 
stretching; 
(d) result of 
thresholding. 
The threshold is set 
at r = L/2 with output 
set at L-1 (white) for 
any gray level in the 
input image of L/2 or 
higher and at 0 
(black) for all other 
values.   
26


<!-- Page 27 / 43 -->

Gray Level Slicing
•
To highlight the gray scales between [A,B].
r
L-1
L-1
T(r)
0
A
B
r
L-1
L-1
T(r)
0
A
B
Note that gray scales outside 
[A,B] are diminished
27


<!-- Page 28 / 43 -->

Gray level slicing (or intensity-
level slicing):
(a) transformation function that 
highlights a range [A,B] of 
intensities while diminishing all 
others to a constant, low level; 
(b) transformation function that 
highlights a range [A,B] of 
intensities but preserves all 
others; (c) an image; (d) result 
of using the transformation 
below with the intensities 
between A and B darkened. 
28


<!-- Page 29 / 43 -->

Dynamic Range Compression
• Application of nonlinear 
functions
• Compression of dynamic 
range
• The dynamic range of a 
processed image may 
exceed the capability of 
display device – only the 
brightness parts of image 
are visible.
• c: scaling constant; 
logarithm function performs 
desired compression. 
r
s
L-1
L’ -1
0
(r1, s1)
Nonlinear function
dark
)
1
log(
)
(
r
c
r
T


29
If log(1 +|r|) yields 0 to 6.4, setting c = 255/6.4 will scale the range to 0 to 255 gray levels. 
Dynamic range is 
the range of the 
different between 
the lightest light 
and darkest dark 
of an image. 


<!-- Page 30 / 43 -->

Compression of 
dynamic range:
(a) logarithm gray-
level 
transformation 
function;
(b) image with large 
dynamic range 
(pixel values 
ranging from 0 to 
2.5 x 106;
(c) result after 
transformation.
HDR –
High-Dynamic-Range 
photography
30


<!-- Page 31 / 43 -->

31
Pseudocolor Image Processing – intensity 
(or density) slicing
(a) X-ray image of a weld. (b) Result of color coding. 
(Original image courtesy of X-T E K Systems, Ltd.)
Source: Digital Image Processing By Gonzalez and 
Woods, Pearson. 
Pseudo color Image Processing is a digital
image processing technique where colors are
assigned to grayscale images (intensity images)
to enhance their visualization and interpretation.


<!-- Page 32 / 43 -->

3. Histogram Equalization
•
Histogram equalization is a widely used image technique 
in image enhancement for increasing contrast.
•
It is a method of contrast adjustment using the image’s 
histogram.
•
It involves finding a gray level transformation function 
that creates an output image with a uniform or nearly 
uniform histogram. 
•
The transformation replaces each intensity in the input 
image by a new one. 
•
Transformation matrix is applied to the whole image at 
once.
32


<!-- Page 33 / 43 -->

Histogram Equalization
•
The aim is to create an image with equally distributed 
brightness levels over the whole brightness scale
•
An ideal equalized image has an equal number of pixels 
at all brightness levels, resulting in a straight horizontal 
line on the histogram graph.
33


<!-- Page 34 / 43 -->

Histogram Equalization
•
H(p) = input histogram, input gray-
scale range = [p0, pk]
•
To find a monotonic transformation 
q=T(p) such that G(q) is uniform 
over the output range of [q0, qk].
•
The histograms can be treated as 
a discrete probability density 
function. (Equation 1)
•
Suppose that the image has N
rows and columns, the equalized 
histogram G(q) corresponds to the 
uniform probability density function 
f. (Equation 2)
•
The equalized histogram can be 
obtained for the continuous 
probability density function 
(Equation 3).
•
The desired pixel brightness 
transformation T is the cumulative 
histogram (Equation 4).
•
The discrete approximation to the 
continuous T(p) is given in 
Equation 5.
)
5
(
)
(
)
(
)
4
(
)
(
)
(
)
3
(
)
(
)
(
1
)
2
(
)
(
)1(
)
(
)
(
0
0
0
0
0
2
0
0
2
0
0
0
2
0
2
0
2
0
0

























p
p
i
k
p
p
k
q
q
p
p
k
k
k
k
i
i
k
i
i
q
i
H
N
q
q
p
T
q
q
ds
s
H
N
q
q
p
T
q
ds
s
H
q
q
q
q
N
ds
q
q
N
q
q
N
f
p
H
q
G
34


<!-- Page 35 / 43 -->

35


<!-- Page 36 / 43 -->

Histogram Equalization
•
Example
36


<!-- Page 37 / 43 -->

Histogram Equalization
37


<!-- Page 38 / 43 -->

Matlab Implementation of Histogram 
Equalization
function [im_out, H, Hc, T] = hist_eq(im)
input:
im [m x n] input image
output:
im_out [m x n] equalized image
H [1x256] histogram of the input image
Hc [1x256] cumulative histogram of the input function
T [1x256] transformation function of the intensity 
38


<!-- Page 39 / 43 -->

Matlab Implementation of Histogram 
Equalization
https://www.mathworks.com/help/images/histogram-equalization.html
39


<!-- Page 40 / 43 -->

Histogram Equalization
•
Useful in images with both background and foreground 
are dark or bright.
•
It can reveal good detail in over or under-exposed photographs.
•
The method will provide good view of hard tissue (bone) in x-ray 
image.
•
Disadvantage: global application leads to indiscriminate 
modification of image
•
The method may increase contrast of background noise and 
decrease usable signal.
•
It could not support the need to highligh certain gray level range.
40


<!-- Page 41 / 43 -->

Histogram Specification
•
Histogram Specification is a generalized version of 
histogram equalization
•
A “target” histogram that actually define the desired 
shape of the image histogram is specified. 
•
A nonlinear stretch operation is applied to force the 
image histogram to have that shape. 
41


<!-- Page 42 / 43 -->

Summary
•
Image most frequently represented as multidimensional 
array can be added, subtracted and made equal to 
another image. 
•
Logical operation can also be perform on image.
•
Gray-scale transformations change brightness without 
regard to position in the image. The common gray-scale 
transformations are piecewise linear function, negative 
transformation and brightness thresholding. 
•
The goal of histogram equalization is to create an image 
with equally distributed brightness levels over the whole 
brightness scale.
42


<!-- Page 43 / 43 -->

