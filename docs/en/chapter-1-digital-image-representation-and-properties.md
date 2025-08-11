---
source_pdf: 2025_Chapter 1 - Digital Image Representation and Properties.pdf
exporter: pymupdf_markdown
---



<!-- Page 1 / 62 -->

Dr. NG Hsiao Piau
Ng_h_p@nus.edu.sg


<!-- Page 2 / 62 -->

Lecture 1 
Digital Image Representation and Properties
2


<!-- Page 3 / 62 -->

Topics 
•
Image Representation
•
Image Sampling and Quantization
•
Digital Image Properties
•
Digital Color Images
3


<!-- Page 4 / 62 -->

Key takeaways 
•
Image representation: pixel, brightness, resolution
•
Sampling & quantization: spatial density and gray levels
•
Image properties: connectivity, distance, histogram
•
Thresholding & perception: visual contrast, acuity, illusions
•
Color models: RGB, CMY, HSI, YIQ, and color space
4


<!-- Page 5 / 62 -->

Image Representation 
•
A projection of 3D scene into 2D.
5
Image on human retina or captured by a TV camera or senor. 
(Source: Gonzalez and Woods, 2010)


<!-- Page 6 / 62 -->

Image Representation  
•
Continuous Image Function
•
The image is modeled by a continuous function of two variables 
f(x, y) or three variables f(x, y, t).
• (x, y) gives the coordinate of a plane. t is the time domain.
•
Image function value f correspond to brightness at an image point.
• An intensity image is a 2D image bearing information about 
brightness points.
6
Image can be considered as a 2D light intensity function, f(x,y), 
where x and y are spatial coordinates, and f at (x, y) is related to 
the brightness or color of the image at that point.


<!-- Page 7 / 62 -->

Image Representation  
•
Continuous Image Function
•
The brightness or intensity of the image is determined by
• Illumination component: the amount of light incident on the 
viewing scene.
• Reflection component: the amount of light reflected by the 
object in the scene.
• Example values of typical surfaces: black silk (0.01), 
stainless steel (0.65), silver plate (0.90). Image function 
value f correspond to brightness at an image point.
7


<!-- Page 8 / 62 -->

Image Representation  
•
Image Digitalization
•
An image to be processed by computer must be represented
using appropriate discrete data structure.
• Matrix or 2D array for 2D image
•
Image digitalization is the process of converting an image into a
numerical representation through sampling and quantization.
•
Sampling turns the continuous function f(x,y) into a matrix of N
rows and M columns.
•
Quantization assigns an integer value to each continuous
sample.
8


<!-- Page 9 / 62 -->

Image Representation  
•
Digital Image
•
A
digital
image
(==
raster
or
bitmapped
image)
is
the
representation of a continuous image f(x,y) by a matrix of
discrete sample.
•
The function value at each discrete sample is quantized to be
represented by a finite number of bits.
•
Each element of the matrix of samples is called pixel (for PICture
ELement).
9


<!-- Page 10 / 62 -->

Image Representation  
•
Digital Image
10
0     0     0     0     0    0
0    10   10    10    0   0
0     0    10     0     0   0
0     0    10     0     0   0     
0     0    10     0     0    0
0     0      0     0     0    0
A pixel represents 
brightness at a point.
6 
pixels
6 pixels
A digital image is 
represented by numbers.


















0
0
0
0
0
0
0
0
0
10
0
0
0
0
0
10
0
0
0
0
0
10
0
0
0
0
10
10
10
0
0
0
0
0
0
0
A digital image 
can be 
represented as 
a matrix.


<!-- Page 11 / 62 -->

Image Representation  
•
Pixel
•
Pixel is a point sample of the original image.
•
It is the smallest piece of information in an image - the elemental
part of an image.
•
It has a position relative to other pixels in the image.
•
It has a color capability measured in bits.
•
Pixel is often represented using dot or square.
11


<!-- Page 12 / 62 -->

Image Sampling and Quantization 
•
Digital
image
processing
is
the
use
of
computer
algorithms
to
perform
image
processing
on
digital
images.
•
It is a sub field of digital signal processing.
•
Image sampling and image quantization are examples of
digital image processing.
12


<!-- Page 13 / 62 -->

Image Sampling and Quantization 
13
Sampling
Quantization


<!-- Page 14 / 62 -->

Image Sampling and Quantization 
•
Sampling
14


<!-- Page 15 / 62 -->

Image Sampling and Quantization 
•
Picture Space vs Image Space
15


<!-- Page 16 / 62 -->

Image Sampling and Quantization 
•
Image resolution
•
Image resolution is a measure of sampling density.
• Provides a relationship between pixel dimensions and 
physical dimensions
•
Pixels per inch (ppi)
• If the dimension of an image is 1 inch x 1 inch, and M= N = 8, 
there are 8/1 = 8 pixels per inch. 
• Pixel size = 1/8 = 0.125 inch
• Pixels per cm
16


<!-- Page 17 / 62 -->

Image Sampling and Quantization  
17


<!-- Page 18 / 62 -->

Image Sampling and Quantization 
18


<!-- Page 19 / 62 -->

Image Sampling and Quantization  
•
Raster dimension
19


<!-- Page 20 / 62 -->

Image Sampling and Quantization  
•
Raster dimension
•
Number of pixels in an image (== raster dimension)
• Video Graphics Array (VGA) display = 640 by 480 display;
• M = 640 pixels, N = 480 pixels. 640 x 480 = 307,200 
pixels or 0.3 megapixels
• SVGA: 800 x 600 == 0.4 megapixels
• XGA: 1024 x 768 == 0.8 megapixels 
• 1080i HDTV: 1920 x 1080 == 2.1 megapixels; 16:9 aspect 
ratio
• High resolution digital TV format
• 2K: 2048 x 1536 == 3.1 megapixels; 4:3 aspect ratio
• Used for digital effects in feature films
• Common CCD camera: at least 512 x 256 pixels = 131,072 
pixels
• Digital SLR camera: at least 4 million pixels 
20


<!-- Page 21 / 62 -->

Image Sampling and Quantization  
•
Raster dimension
•
Scaling (or resampling): the process to create an image with 
different dimensions from that of the source image.
•
Scaling image down (or decimation): the process of reducing the 
raster dimension.
• Averaging the values of source pixels contributing to each 
output pixel
•
Scaling image up: the process of increasing the image size to 
create sample points between the original sample samples in the 
source raster.  
• Interpolation – using the values in the sample grid to guess 
the values of the unknown pixels 
21


<!-- Page 22 / 62 -->

Image Sampling and Quantization  
•
Quantization
•
Quantizes the 
continuous range 
of brightness or 
intensity to K gray 
levels.
•
K = 2n where n is 
known as the 
color capability or 
color depth or bit 
depth.
•
n is the number of 
bits used to 
indicate the color 
of a single pixel.  
22
•
Quantization error is 
defined as the 
difference between 
actual analog value and 
quantized digital value.
•
It is due to rounding or 
truncation.
Continuous 
range of 
brightness
K-1
0
G
Gray levels


<!-- Page 23 / 62 -->

Image Sampling and Quantization  
•
Quantization
•
Image 
quantization = 
discretion in light 
intensity
•
Brightness level = 
gray level in 
monochrome 
image
23
(Source: Sonka, Hlavac and Boyle, 2008)


<!-- Page 24 / 62 -->

Image Sampling and Quantization  
•
Color Depth
•
Maximum number of data a pixel can store
•
Monochrome: p(i,j) = 0, 1, 2, …, K-1
•
Binary: p(i,j) = 0, 1
• 0: black (current off – no light), 1: white (current on –
maximum illumination). 
• Color capability = 1 bit of data
•
Grayscale: p(i,j) = 0, 1, …, 255
• 0: black, 1..254: gray, 255: white
• Color capability = 8 bits of data
24


<!-- Page 25 / 62 -->

Image Sampling and Quantization  
•
Color Depth
•
Color: p(i,j) = [ R(i,j) G(i,j) B(i,j) ]
• RGB/8: R(i,j) = 0..255, G(i,j) = 0..255, B(i,j) = 0..255. 8 bit of 
data per color channel.
25
[ 249 247 247 ] 
[ 0 0 0 ] 
[ 251 5 5 ] 


<!-- Page 26 / 62 -->

Image Sampling and Quantization  
•
Color Depth
•
Indexed Color
• Color capability = 8 bits per pixel, maximum number of 
values = 256. Each value is an index number corresponds to 
explicit color value in the file’s look-up table.
• The look-up table (color look-up table or colormap) is stored 
at the header of the image file. Color look-up table can be a 
hardware device built into an imaging system. 
26


<!-- Page 27 / 62 -->

Image Sampling and Quantization  
•
Color Depth
•
Indexed Color
• A colormap is defined as a list of colors, each indexed by an 
integer pixel value. Each entry in a colormap is called a color 
cell. A color cell represents a color usually defined by a set of 
three numeric values, representing intensities of red, green 
and blue respectively.
• Advantages: save memory/storage space and/or 
transmission time. 
• The finer the sampling (i.e., the larger M and N) and 
quantization (i.e., the larger K), the better the approximation 
of the continuous image function f(x,y) achieved.
• The number of quantization levels (brightness or gray levels) 
should be high enough for human perception of fine shading 
details in the image. 
27


<!-- Page 28 / 62 -->

Image Sampling and Quantization  
•
Color Depth
28
How many gray levels are 
required for human visual 
perception?
K = 32
K = 64
K = 128
A human is able to 
recognize about 60 gray 
levels at most.
A digital image is usually 
quantized to 256 gray levels.
K = 256


<!-- Page 29 / 62 -->

Digital Image Properties
•
Metric and topological properties
•
Histogram
•
Visual perception
29


<!-- Page 30 / 62 -->

Digital Image Properties
•
Metric and Topological Properties
•
A set is a collection of distinct objects.
•
A metric space is a set where a notion of metric (or distance) 
between elements of the set is defined.
•
A topological space is a mathematical structure that allows the 
formal definition of connectivity, convergence and continuity. 
(How parts are interrelated or arranged, and spatial relations 
unaffected by change of shape or size)
30


<!-- Page 31 / 62 -->

Digital Image Properties
•
Connectivity
•
A connected space is a topological space which cannot be 
represented as the disjoint union of two or more nonempty open 
subsets.
31
A
B


<!-- Page 32 / 62 -->

Digital Image Properties
•
Connectivity
•
To provide shape information
•
To establish objects’ components and boundaries
32
Hole
Background
Region


<!-- Page 33 / 62 -->

Digital Image Properties 
•
Connectivity
•
Distance to examine connectivity
33
)
,
max(
:
board
 
Chess
 :
block
City 
)
(
)
(
:
Euclidean
1
2
1
2
8
1
2
1
2
4
2
1
2
2
1
2
y
y
x
x
D
y
y
x
x
D
y
y
x
x
DE











(x1, y1)
(x2, y2)
2
2
2
2
2
2
2
2
1
1
1
1
0
D4
2 2 2 2 2
2
2
2
2 2
2 2 2
2
2
2
1 1 1
1
1
1
1
1
0
D8


<!-- Page 34 / 62 -->

Digital Image Properties 
•
Connectivity
•
Distance to examine connectivity
34
(Source: Sonka, Hlavac and Boyle, 2008)
DE = sqrt( (4-0)^2 + (0-2)^2) = sqrt(20) 
D4 = |4-0| + |0-2| = 6
D8 = max( |4-0| , |0-2|) = 4
(0,2)
(4,0)
•
What is the 
distance between 
(4,0) and (0,2)?


<!-- Page 35 / 62 -->

Digital Image Properties  
•
Typical Connectivity
•
4-neighborhood (or 4-connectivity)
•
8-neighborhood (or 8-connectivity)
35
2 pixels p and q form a region are 4-connected if q is in the set containing the 
4-neighbours of p. D4(p, q) = 1
•
p and q are 
contiguous if there is 
a path between 
them (connected). 
•
A region is a 
connected set (each 
pair of pixels is 
contiguous). 
(Source: Sonka, Hlavac and Boyle, 2008)


<!-- Page 36 / 62 -->

Digital Image Properties  
•
Typical Connectivity
36
(Source: Sonka, Hlavac and Boyle, 2008)
0 – all off, no light, black; background
1 – all on, light, white; object 


<!-- Page 37 / 62 -->

Digital Image Properties  
•
Histogram
•
The brightness histogram H(z) of an image provides the 
frequency of the brightness value z in the image.
•
The histogram of an image with L gray-level is represent by a 1D 
array with L elements.
37


<!-- Page 38 / 62 -->

Digital Image Properties  
•
Histogram
•
Can be achieved by simply counting the number of pixels for 
each gray level.
•
https://www.mathworks.com/help/matlab/ref/matlab.graphics.cha
rt.primitive.histogram.html
38


<!-- Page 39 / 62 -->

Digital Image Properties  
•
Histogram
•
It can detect image with contrast problems, underexposed (too 
dark) and overexposed (too light).
39
Number of pixels
Black
Gray
White
Gray levels
Underexposed
Extended spectrum 


<!-- Page 40 / 62 -->

Digital Image Properties  
•
Histogram
•
More than one images can have the same histogram.
•
It can be used to remove background using thresholding.
•
Invariant to typical image transformation such as rotation.
•
It does not relate to object’s shape information.  
40


<!-- Page 41 / 62 -->

Digital Image Properties  
•
Thresholding
•
Thresholding is the simplest method of image processing.
•
A binary image is created from a grayscale image by marking 
individual pixels in an image as “object” pixels if their value is 
greater than some threshold value (assuming the object is lighter 
than background) and “background” pixel otherwise.   
•
Note that objects in an image are not necessary represented 
using darker shades. 
41


<!-- Page 42 / 62 -->

Digital Image Properties  
•
Thresholding
42
2
2
2
1
1
1
1
1
1
1
1
1
1
1
2
2
2
2
3
3
3
3
3
4
4
4
4
4
4
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
34
10
1
2
7
5
3
4
6
Original image
threshold
White
Number of pixels
Histogram
Binary image
Black
5 6 7
The above is for illustration 
only. The background is 
black and the object is white.


<!-- Page 43 / 62 -->

Digital Image Properties 
•
Visual Perception
43
Scene
Eye
Image
Brain
Perception
Image 
Acquisition
Image 
Interpretation
Does our eye see the tree?
(Source: Gonzalez and Woods, 2010)


<!-- Page 44 / 62 -->

Digital Image Properties 
•
Visual Perception
•
Contrast
• Contrast is the local change in brightness.
• The ratio between average brightness of an object and the 
background.
44
Contrast sensitivity is the ability of our visual system to distinguish 
objects from the background.


<!-- Page 45 / 62 -->

Digital Image Properties 
•
Visual Perception
•
Acuity
• The ability to detect details in an image.
• Acuity defines the resolution ability of human eye (sharpness).
45
Two inner circles of same diameter 
appeared to have different diameters.


<!-- Page 46 / 62 -->

Digital Image Properties 
•
Visual Perception
•
Some visual illusions
46
Parallel diagonal line segments are 
not perceived as parallel.
Rows of black and white squares are 
all parallel.


<!-- Page 47 / 62 -->

Digital Image Properties 
•
Visual Perception
•
Perceptual grouping
• The human visual ability to extract significant image relations 
from lower-level image features without any knowledge of the 
image content, and group them to obtain meaningful higher 
level structure.
47


<!-- Page 48 / 62 -->

Digital Color Images
•
In automated image analysis, color is a powerful 
descriptor that often simplifies object identification and 
extraction from a scene.
•
In image analysis performed by human, human can 
discern thousands of color shades and intensities, 
compared to not more than 60 shades of grey.  
•
Two major areas: full color (image acquired by color TV 
camera or color scanner) and pseudo color (a shade of 
color is assigned to a particular monochrome intensity or 
range of intensities).
48


<!-- Page 49 / 62 -->

Digital Color Images
•
Color Spectrum
•
Sir Issac Newton discovered in 1666 that when a beam of 
sunlight is passed through a glass prism, consists of a 
continuous spectrum of colors ranging from violet at one end to 
red at the other. The color spectrum may be divided into six 
broad regions violet, blue, green, yellow, orange, and red. 
49
Color spectrum seen by passing white light through a prism. (Courtesy of the General Electric Co., 
Lighting Division.) 
Source: Digital Image Processing By Gonzalez and Woods, Pearson. 


<!-- Page 50 / 62 -->

Digital Color Images
•
Color Spectrum
•
When view in full color, no color in the spectrum ends abruptly, but rather each 
color blends smoothly into the next.
•
The colors that human perceives in an object are determined by the nature of the 
light reflected from the object. A body that reflects light that is relatively balanced 
in all visible wavelengths appears white to the observer. 
•
However, a body that favors reflectance in a limited range of the visible spectrum 
exhibits some shades of color. For example, green objects reflect light with 
wavelengths primarily in the 500 to 570 nm range, while absorbing most of the 
energy at other wavelengths.
50
Wavelengths comprising the visible range of the electromagnetic spectrum. (Courtesy of the General 
Electric Co., Lighting Division.) 
Source: Digital Image Processing By Gonzalez and Woods, Pearson. 


<!-- Page 51 / 62 -->

Digital Color Images
•
Color Spectrum
51
Absorption of light by the red, green, and blue cones in the human eye as a function of wavelength.
Source: Digital Image Processing By Gonzalez and Woods, Pearson. 
Color perception in 
human eye are done 
by the 6-7 millions 
cones in human 
eye.  
Three categories: 
red/green/blue light 
sensitive cones


<!-- Page 52 / 62 -->

Digital Color Images
•
Primary and Secondary Colors
•
The primary colors can be added to 
produce the secondary colors of 
light –
•
Magenta = Red + Blue
•
Cyan = Green + Blue
•
Yellow = Red + Green
•
Mixing the three primaries, or a 
secondary with its opposite primary 
color in the right intensities produces 
the white light. 
52
Primary and secondary colors of light and pigments. 
(Courtesy of the General Electric Co., Lighting Division.)
Source: Digital Image Processing By Gonzalez and 
Woods, Pearson. 


<!-- Page 53 / 62 -->

Digital Color Images
•
Color Characteristics
•
Brightness embodies the chromatic notion of intensity.
•
Hue is an attribute associated with the dominant wavelength in a 
mixture of light waves. Thus hue represents the color as 
perceived by an observer; when we call an object red, orange or 
yellow, we are specifying its hue.
•
Saturation refers to relative purity or the amount of white light 
mixed with the hue. The pure spectrum colors are fully saturated. 
Colors such as pink (red and white) are less saturated, with the 
degree of saturation being inversely proportional to the amount 
of white light added.
53


<!-- Page 54 / 62 -->

Digital Color Images
•
Color Characteristics
•
Hue and saturation taken together are called chromaticity, and 
therefore, a color may be characterized by its brightness and 
chromaticity. The amounts of red, green and blue needed to form 
any particular color are called the tristimulus values and are 
denoted, X, Y and Z, respectively. 
•
A color is then specified by its trichromatic coefficients, defined 
as:
• x = X/(X + Y + Z)
• y = Y/(X + Y + Z)
• z = Z/(X + Y + Z)
• x + y + z = 1  
54


<!-- Page 55 / 62 -->

Digital Color Images
•
Chromaticity Diagram
•
It shows color composition as 
a function of x (red) and 
y(green). For any value of x 
and y the corresponding value 
of z (blue) can be obtained by 
x + y + z = 1. 
•
Example, the point marked 
green in Plate IV, has 
approximately 62% green and 
25% red content, and hence 
the composition of blue is 
approximately 13%.
55


<!-- Page 56 / 62 -->

Digital Color Images 
•
Color Models
•
A color model is a specification of a 3D coordinate system and a 
subspace within that system where each color is represented by a 
single point.
•
Hardware oriented models most commonly used in practice are:
• RGB (red, green, blue) model for color monitor and broad class of 
color video cameras.
• CMY (cyan, magenta, yellow) model for color printers; and
• YIQ model, which is the standard for color TV broadcast. In this 
model, Y corresponds to luminance, and I and Q are two chromatic 
components called inphase and quadrature, respectively.
•
Models frequently used for color image manipulation are the HSI (hue, 
saturation, intensity) model and the HSV (hue, saturation, value) model.
•
Color models most often used for image processing are the RGB, the 
CMY, the YIQ and the HSI models.
56
Color model == color space == color system: standardization of color specification


<!-- Page 57 / 62 -->

Digital Color Images
•
RGB Color Models
•
The gray scale extends from black to 
white along the line joining these two 
points, and colors are points on or 
inside the cube, defined by vectors 
extending from the origin.
•
For convenience, the assumption is 
that all color values have been 
normalized so that the cube is a unit 
cube, i.e., all values of R, G, and B 
are assumed to be in the range [0,1].
•
Images in the RGB color model 
consist of three independent image 
planes, one for each primary color. 
Most color cameras used for acquiring 
digital images utilize the RGB format, 
which alone makes this an important 
model in image processing.
57
Points along the main diagonal have grey values from 
black at the origin to white at point (1,1,1).
RGB 
Color 
Cube
Mainly used in color monitors and video cameras


<!-- Page 58 / 62 -->

Digital Color Images 
•
CMY Color Models
58
Mainly used in printing devices


<!-- Page 59 / 62 -->

Digital Color Images
•
YIQ Color Models
59


<!-- Page 60 / 62 -->

Digital Color Images
•
HSI Color Models
•
Hue is a color attribute that describes a pure color (pure yellow, orange 
or red), whereas saturation gives a measure of the degree to which a 
pure color is diluted by white light
•
Two advantages
• The intensity component I, is decoupled from the color information 
of the image. (I == amount of light == grayscale)
• The hue and saturation components are intimately related to the 
way in which human beings perceived color.
•
An ideal tool for developing image processing algorithm based on some 
of the color sensing properties of the human visual system. 
•
Examples of the usefulness of the HSI model range from the design of 
imaging systems for automatically determining the ripeness of fruits and 
vegetables, to systems for matching color samples or inspecting the 
quality of finished color goods.
•
The conversion formulas to go from RGB to HSI and back are 
considerably more complicated than in the preceding models.
60
Based on the way human describes and 
interprets color. Helps in separate color 
and grayscale information in an image. 


<!-- Page 61 / 62 -->

Digital Color Images 
•
HSI Color Models
61
A 24-bit RGB color cube 
HSI components: (a) hue, (b) saturation, and (c) intensity images.
Source: Digital Image Processing By Gonzalez and Woods, Pearson. 


<!-- Page 62 / 62 -->

