---
source_pdf: 2025_Chapter 2 - Image Acquisition and Camera Calibration.pdf
exporter: pymupdf_markdown
---



<!-- Page 1 / 75 -->

Dr. NG Hsiao Piau
Ng_h_p@nus.edu.sg


<!-- Page 2 / 75 -->

Lecture 2 
Image Acquisition and Camera Calibration
2


<!-- Page 3 / 75 -->

Topics 
•
Definitions
•
Illumination
•
Camera
•
Camera Calibration
3


<!-- Page 4 / 75 -->

Key takeaways 
•
Image acquisition (illumination + camera + frame grabber)
•
Lighting types: front, back, structured
•
CCD/CMOS sensors use photovoltaic effect
•
Optics: aperture, focal length, magnification
•
Calibration: 3D-to-2D mapping via matrix transforms
4


<!-- Page 5 / 75 -->

1. Definitions
•
Industrial 
manufacturing cell 
with vision cell
•
Task: the vision 
system observes the 
object, determines if 
it is within 
specification, and 
generates command 
signals accordingly.
•
Image acquisition 
system: lights, 
camera and frame 
grabber.
•
Processing 
equipment
•
Output equipment
•
Control action 
5
Computer integrated manufacturing (CIM)
for  statistical 
analysis and 
inventory control


<!-- Page 6 / 75 -->

Image Acquisition
•
The process to transform visual image of a physical 
object and its intrinsic characteristics into a set of 
digitized data which can be used by the processing unit 
of the system.
• Lights (Illumination)
• Camera 
• Frame Grabber
6
Four phases:
1. Illumination
2. Image formation or focusing
3. Image detection or sensing
4. Formatting camera output signal


<!-- Page 7 / 75 -->

Frame Grabber
•
An electronic device that captures individual, digital still 
frames from an analog video signal or a digital video 
stream.
•
In a typical machine/computer vision system, the frame 
grabber also displays, stores or transmits the captured 
video frame in raw or compressed digital form.  
7
Formatting camera output signal


<!-- Page 8 / 75 -->

2. Illumination
•
Refers to the science of the application of lighting.
•
sources of lighting
•
design of lighting systems
•
Aims to produce an effective environment for camera to 
see in the context of machine vision.
8


<!-- Page 9 / 75 -->

Illumination
•
Key parameter, often limiting factor
•
May require 30% of application effort
•
Customized to each application effort
•
Can produce effects beyond human vision (infrared, 
ultraviolet, X-rays, 3D information in a 2D image)
•
Performance of fluorescent lamp varies
•
Regular monitoring
9
The fluorescent lamp output decreases as much as 15% during the first 100 hours 
and then continues to decrease everyday at a slower rate. The fluorescent lamps 
are brightest at 40oC and are sensitive to the applied voltage. 


<!-- Page 10 / 75 -->

Principal kinds of lighting
•
Front lighting: light source and camera on the same side 
relative to object
•
Useful to obtain surface texture, features and for dimensioning
•
Back lighting: object between light source and camera
•
Structured light: illuminating the object with a grid or 
regular stripes
10


<!-- Page 11 / 75 -->

Front Lighting
11
Front lighting employs light reflected from the object. The illumination
source and the camera are both on the same side of the object. It is
useful to obtain surface texture of features as well as dimensioning.


<!-- Page 12 / 75 -->

Back Lighting
•
Create a silhouette of the 
object
•
Often used to locate parts 
moving on a conveyer 
belt
•
Ideal to detect foreign 
material and fracture in 
transparent objects
12
Back lighting is when an 
object is located between the 
light source and the camera. 
Frosted glass


<!-- Page 13 / 75 -->

Back Lighting
15 15 15
15 15 15
15 15
15 15 15
15 15 15
15 15
15 15 15
15 15 15
15 15
15
15
15
15
15
15
15
15
15
15
15 15
10 10
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
1
1
1
Back-lighted object
Image data
13
Produces high contrast images, 
minimizes processing tasks and 
reduces the sensitivity of the system 
to illumination source variation.
Cannot be employed to obtain information 
on surface characteristics, or features not 
visible in silhouette like the presence of 
bolts in blind hole, and objects located on 
top of each other. 


<!-- Page 14 / 75 -->

Structured Light
•
3D information in a 
2D image
•
Lighting angle and 
light structure 
(regular stripes, 
grids) depend on 
the application
14
Structured light is the use of the 
illumination of the object with a special 
pattern or grid. The intersection of the 
object and the projected illumination 
results in a unique pattern depending on 
the shape and dimensions of the object 
A 3-D feature is converted to a 2-D 
image. Vertical and horizontal distances, 
as well as the shape of the surface 
features, can be measured. 


<!-- Page 15 / 75 -->

15
Automated Inspection using Structured Light Scanning: 
http://www.youtube.com/watch?v=lpxQBTrPBEg


<!-- Page 16 / 75 -->

3. Camera
•
A camera is a device used to capture still images 
(photographs) or as sequences of moving images 
(movies or videos).
•
Generally consists of
• Lens system including an opening (aperture) at one 
end for light to enter.
• Image capture for capturing the light at the other end.
16
Image Formation and Focusing
The image of the object is focused on 
the sensing element with a lens. The 
sensor converts the visual image to an 
electrical signal.
Image Detection 
Image detection is done with by the image 
sensor of the camera. The basic concept of 
image sensors is that a separate electrical signal 
is produced for each pixel or area in the sensor 
depending on the amount of light energy falling 
on the device in each pixel area.


<!-- Page 17 / 75 -->

Camera 
•
Most cameras use either CCD or CMOS photosensitive 
elements to capture image, both using photovoltaic 
principles. They capture brightness of a monochromatic 
image.
•
A charge-coupled device (CCD) is a sensor for recording 
images, consisting of an integrated circuit containing an 
array of linked, or coupled, capacitors. 
•
Complementary metal-oxide semiconductor (CMOS) is a 
major class of integrated circuits.
17


<!-- Page 18 / 75 -->

Camera 
•
Photovoltaic principles: The energy of a photon from a 
light source causes an electron to leave its valence band 
and changes to a conduction band. The quantity of 
incoming photons affects macroscopic conductivity. The 
excited electron is a source of electric voltage which 
becomes electric current. The current is directly 
proportional to the amount of incoming energy (photons). 
•
Cameras are equipped with necessary electronics to 
provide digitized images.
•
Color cameras are similar to monochromatic ones and 
contain color filters.
18


<!-- Page 19 / 75 -->

CCD Camera
•
CCD Camera is based on Charge Couple Device 
(CCD) technology.
•
A CCD is an analog shift register consisting of a series 
of closely spaced capacitors.
• It enables analog signals (electric charges) to be 
transported through successive stages (capacitors) 
controlled by a clock signal. 
• It is used to serialize parallel analog signals in arrays 
of photoelectric light sensors.
• For image capturing, there is a photoactive region 
made of silicon and a transmission region which is 
the CCD.
19


<!-- Page 20 / 75 -->

CCD
•
Basics of image capturing operation
• Image is projected onto the capacitor array via the 
photoactive region. Each capacitor will accumulate an 
electric charge proportional to the light intensity at the 
location.
• When the array of capacitor is completely exposed to 
the image (exposure time), a control circuit causes 
each capacitor to transfer its contents to its neighbor.
• The last capacitor in the array moves its charge to a 
charge amplifier which converts the charge into a 
voltage.
• By repeating this process, the control circuit converts 
the entire semiconductor contents of the array to a 
sequence of voltages that are sampled, digitized and 
stored in some form of memory.
20


<!-- Page 21 / 75 -->

CCD
•
Typical sensor size: 8.8 mm x 6.6 mm, almost 200,000 
pixels
CCD sensor inside the camera
. . .
. . .
21


<!-- Page 22 / 75 -->

CCD
•
Two methods to read out the charges that are 
accumulated by the capacitors of the sensor
• Interline transfer
• frame transfer
Interline transfer:
1. Charges are shifted to 
the shielded area.
2. The charges in the 
column are shifted 
down one cell.
3. A row of charge is 
then shifted out. 
. . .
. . .
1
2
Output signal 
(to amplifier)
3
22


<!-- Page 23 / 75 -->

CCD
Frame transfer:
1. All charges are shifted 
down to the shielded 
area.
2. Each row of charge is 
then shifted out. 
2
. . .
. . .
1
Output signal 
(to amplifier)
. . .
23


<!-- Page 24 / 75 -->

•
Other common CCD sensor: 512x256 array of 
photoreceptors
•
A device that detects light by capturing photons.
•
Photoreceptor = photodetector = photosensor
•
Customized arrangement of the receptors possible, e.g. 
similar to human retina
•
Low geometric distortion, price depends on the quality of 
the photoreceptors
•
Pixel transfer rate up to 20 mega pixel per second
•
Voltage signal digitalized (processing) or converted to 
signal (direct to monitor)
•
NTSC color television standard and PAL (Phase 
Alternating Line) are most widely used color encoding 
system.
24
Formatting camera output signal
CCD


<!-- Page 25 / 75 -->

Monochromatic Camera
Charge amplifier – converts the charge into a voltage 
Automatic gain control – changes the gain of the 
camera according to the amount of light in the 
scene. g correction performs non linear 
transformation of the intensity scale.
25


<!-- Page 26 / 75 -->

Monochromatic Camera
26
Gamma correction or encoding of images is 
to compensate for properties of human 
vision – to ensure not too many bits are 
allocated for highlights that human cannot 
see and too few bits for shadow values that 
human are sensitive to.


<!-- Page 27 / 75 -->

Monochromatic Camera
27


<!-- Page 28 / 75 -->

Color Camera
•
Three strategies to capture color images:
• Record three different images in succession by 
employing color filters in front of monochromatic 
camera.
• Color sequential capture – switching colors with a color filter 
wheel.
• Using a color filter array on a single sensor.
• Integral color filter arrays (CFA) – filters of the appropriate 
characteristics of R,G and B are placed on the chip.
• The incoming light is split into several color channels 
using a prism-like device.
• Three-chips color – use optics to split the scene into three 
separate image planes and onto three CCD chips
28


<!-- Page 29 / 75 -->

Color sequential capture 
– switching colors with a color filter wheel
29
https://www.olympus-lifescience.com/es/microscope-
resource/primer/digitalimaging/concepts/threepass/
Olympus Life Science
Digital Imaging in Optical 
Microscopy - Concepts in Digital 
Imaging - Sequential Color Imaging 
Systems | Olympus LS
Disadvantage: Mechanical complexity of the system


<!-- Page 30 / 75 -->

Integral color filter arrays (CFA) 
- filters of the appropriate characteristics of R,G and B 
are placed on the chip
30
https://www.whatdigitalcamera.com/technology_
guides/bayer-filter-work-60461
Bayer filter: What is it and how does it work?
Used in almost all color digital cameras
The property that human eye is most sensitive to 
green, less to red, and least to blue is used by 
the most common color filter for single chip 
camera.
Integral color filter arrays


<!-- Page 31 / 75 -->

Three-chips color 
– use optics to split the scene into three separate image 
planes and onto three CCD chips
31
Disadvantage: using smaller sensors and hence lower image resolution.
https://www.vision-doctor.com/en/area-scan-cameras/three-chip-colour-cameras.html


<!-- Page 32 / 75 -->

CMOS Camera
•
CMOS camera system uses CMOS image sensors or 
CMOS active pixel sensor (APS). CMOS 
(Complementary metal-oxide-semiconductor) is a class 
of integrated circuit.
•
An APS is an image sensor consisting of an integrated 
circuit containing an array of pixel sensors, each pixel 
containing a photodetector and an active amplifer.
•
Most commonly used in mobile phone cameras and web 
cameras.
32


<!-- Page 33 / 75 -->

Smart Camera
•
A smart camera is an integrated machine vision system 
which, in addition to image capture circuitry, includes a 
processor, which can extract information from images 
without need for an external processing unit, and 
interface devices used to make results available to other 
devices.
•
It is an embedded system usually with CMOS image 
sensor.
33


<!-- Page 34 / 75 -->

Aperture and Focal Point
•
Aperture is an opening 
through which light is 
admitted. It controls the 
amount of light that 
passes through the 
camera lens.
•
Focal point is a point 
onto which collimated 
light parallel to the axis 
is focused.
•
Collimated light is light 
whose rays are nearly 
parallel.
34
Focal length is the distance between 
the optical center of a lens and the 
focal point at which parallel rays of 
light converge or appear to converge 
after passing through the lens.


<!-- Page 35 / 75 -->

Focal Length
•
f is a measure of how strongly an 
optical system converges or 
diverges light. 
•
A system with a shorter focal length 
has greater optical power than one 
with a long focal length.
•
From the focal length f, the distance 
Do at which the object is sharp can 
be computed.
•
Example: m=0.05, f=35.7mm, 
Do=750 mm
•
For a lens system with m=0.05, distance 
between object and lens (camera) is 750 
mm, we need a focus length f = 35.7 .
)
1
1(
m
f
Do


35
p = optical power (or 
refractive power) = 1/f


<!-- Page 36 / 75 -->

Magnification
•
m = magnification
• Hi: image size
• Ho: object size
•
m << 1: macroworld
•
typical industrial 
automation systems
•
m >> 1: microscope 
Aperture
Hi
Ho
Object plane
Image plane
Focal point
Focal 
point
Do
Di
o
i
o
i
D
D
H
H
m


36


<!-- Page 37 / 75 -->

Given a 100 x 100 array of photoreceptors to acquire an 
image of size 4 x 4 mm of an object of size 80 x 80 mm.  
What are the magnification, pixel size and pixel size on the 
object? 
Pixel size on array is the distance between sensor elements, and is 
given by dividing the dimension of array by the number of elements in 
the same direction.
mm
8.0
1
20
0.04
image
object
size
 
pixel
object 
on 
 
size
 
pixel
mm
04
.0
100
4
size
 
pixel
20
1
80
4
object
image
ion
magnificat










37


<!-- Page 38 / 75 -->

Field of View
38
The field of view or field of vision (FOV) of a sensor or 
camera is the size of the scene that the sensor can sense 
or the camera can observe.
Examples: FOV = 10 cm x 10 cm; Angular FOV = 50o x 40o
Source: www.microscan.com 


<!-- Page 39 / 75 -->

Depth of Field
•
A camera focuses its lens at a single point but there is a 
zone that stretches in front of and behind this focus point 
that still appears sharp. This zone is known as the depth 
of field. 
39
Depth of field (DoF) is the range of distances in a photograph where objects 
appear sharp and in focus. It is influenced by the size of the aperture.  


<!-- Page 40 / 75 -->

Depth of Field
Aperture (f stop)
Object plane
Image plane
Circle of 
confusion
C
C’
b
a
a’
b’
Depth of field
ion
magnificat
:
)
stop
f(
size
 
aperture
:/
size
 
pixel
:
)1
( /
 
 2
field
 
of
 
depth
2
m
f
m
m
f





Depth of field is the portion 
of a scene that appears 
sharp in image. 
Circle of confusion is an 
optical spot caused by a 
cone of light rays from a 
lens not coming to a perfect 
focus when imaging a point 
source
40


<!-- Page 41 / 75 -->

41
Diagram showing various sizes of Circles of Confusion (CoC). They 
are sized according to the focus (not to scale). Only those CoCs 
projected from inside the Depth of Field are sharp. Our eyes cannot 
perceive them well as they form sharp points. The ones we do see are 
projected from outside the depth of field. When we are able to see the 
CoC it is said to be unsharp.
Source: http://www.photokonnexion.com/?page_id=4373
Depth of Field


<!-- Page 42 / 75 -->

Depth of Field
•
f-stop is the discrete step the f-number is adjusted in a 
camera.
•
f-number is the focal length divided by the effective 
aperture diameter.
•
Standard f-stop scale: f/1, f/1.4, f/2, f/2.8, f/4, f/5.6, f/8, 
f/11, f/16, f/22, f/32, … 
f/4: f-number = 4
200 mm f/4 lens: aperture diameter = 200/4 = 50 mm and 
200 mm/50 mm = 4.
42


<!-- Page 43 / 75 -->

Given f=40 mm and f-stop = 8, what are the diameter of 
aperture opening and f-number? 
•
Diameter of aperture opening (or effective aperture diameter) 
= f/f-stop = 40/8 = 5 mm
•
f-number = f/(effective aperture diameter) = 40 mm/5 mm = 8 
43
The aperture is the opening in the camera lens through which light enters. The size of 
the aperture can be adjusted to control the amount of light that reaches the camera's 
sensor. A larger aperture (smaller f-number, e.g., f/1.8) results in a shallow depth of 
field, where only a small portion of the scene is in focus, and the background appears 
blurred. A smaller aperture (larger f-number, e.g., f/16) creates a deeper depth of field, 
with more of the scene appearing sharp from foreground to background.
Depth of Field


<!-- Page 44 / 75 -->

44
f/8.0
f/5.6
f/2.8
“Smaller F-stop number (Larger apertures) produce a shallower depth of field.”
Source: http://www.cambridgeincolour.com/tutorials/depth-of-field.htm
Image taken on a 200 mm lens
Depth of field is 
‘shallow’ – a 
narrow zone 
appears sharp. 
Depth of field is 
‘deep’ – more 
of the picture 
appears sharp. 


<!-- Page 45 / 75 -->

Depth of Field: Macroworld
•
7.6 x 7.6 mm size 200 x 
200 array sensor
•
f-stop = 16, magnification 
= 1/20
• pixel size = 7.6/200 = 
0.038 mm
• depth of field = 
(2*0.038*16*(1+1/20))*
202 = 511 mm) 
•
In typical industrial 
applications (m << 1), the 
depth of field problem is 
not sufficiently important.
45


<!-- Page 46 / 75 -->

Depth of Field: Optical Microscope
•
3.8 x 3.8 mm sensor array 
•
Pixel size = 3.8/100 = 
0.038 mm
•
If  m = 100 and f-stop=16 
• Depth = 
(2*0.038*16*(1+100))/1
0000 = 12 micrometers
•
In microscopy, the depth is 
limited, 3D vision is hardly 
possible.
46


<!-- Page 47 / 75 -->

47
There are many different types of lenses.
Panasonic super telephoto zoom – an assembly of lens
There is a need to have a relatively simple method to design complex lens system.
- Ray transfer matrix / ray matrix / optical system matrix according to Geometrical Optics. 


<!-- Page 48 / 75 -->

Understanding Focal Length – Nikon USA
48
https://www.nikonusa.com/en/learn-and-explore/a/tips-and-techniques/understanding-focal-
length.html#:~:text=The%20focal%20length%20of%20a,and%20the%20higher%20the%20magnification. 
“Lens focal length tells us the angle of view—how much of the scene will be 
captured—and the magnification—how large individual elements will be. 
The longer the focal length, the narrower the angle of view and the higher the 
magnification. The shorter the focal length, the wider the angle of view and 
the lower the magnification.”
Zoom (variable focal length) vs. Prime Lens (fixed focal length)
FX format is full-frame sensor equivalent in size to a 35 mm frame; DX format 
is a smaller size sensor and hence the field of view is narrower.   
Wide-angle lens: FX – 14-35 mm; DX – 10-24 mm
Standard lens: FX – 50-60 mm; DX – 35 mm
Telephoto lens: FX – 70-200 mm; DX – 55-200 mm
Super Telephoto lens: FX – 300-600 mm; DX – 200-600 mm
Macro lens: FX – 60, 105 and 200 mm; DX – 85 mm


<!-- Page 49 / 75 -->

49
4. Camera Calibration 
• Camera calibration is the process of estimating the 
intrinsic and extrinsic parameters of a camera. 
• This is essential for 3D computer vision tasks such as 
3D reconstruction, augmented reality, and robot vision.


<!-- Page 50 / 75 -->

50
Transformation from Object Space to Image 
Space 
•
Object in world coordinate, image 
in image coordinate
•
Example: image guided robotic 
needle insertion
•
Task: to perform multiple needle 
insertions into organ according to 
perspective projection image of the 
organ
•
The targets in world coordination are 
captured by camera and stored as 
images in image coordinate.
• Assumption: all targets are on the 
same plane.
•
The robot has to insert the needle into 
the target precisely in world 
coordinate.
Camera
Medical robot
Patient
Needle
Computer
Frame Grabber


<!-- Page 51 / 75 -->

51
Calibration: Transformation Between 2D 
Object and 2D Image Coordinates
parameters
tion 
transforma
:
1
:
''
''
:
P
''
''
'
'
cos
sin
sin
cos
:)
R(
'
'
:)
T(
projection
 e
perspectiv
:
P 
rotation,
:
R
 
n,
translatio
:
T
PRT
:
object
   
,
:
image
23
22
21
13
12
11
ij
y
x
a
Y
X
a
a
a
a
a
a
y
x
T
y
x
Y
X
Y
X
Y
X
Y
X
v
v
Y
X
w
Y
X
y
x
Y
X
y
x























































































Calibration is the process of 
identifying the transformation 
parameters 
w
R
Camera
Work plane
Checkerboard 
for camera 
calibration


<!-- Page 52 / 75 -->

52
Calibration
2
23
22
21
13
12
11
2
2
2
2
1
1
1
1
2
2
1
1
23
22
21
13
12
11
23
22
21
13
12
11
error 
 
minimal
 
 the
o
solution t
 
 the
is
.4
1
0
0
0
0
0
0
1
1
0
0
0
0
0
0
1
1
0
0
0
0
0
0
1
3.
locations.
 
identified
 
 
 targeting
is
robot 
 
medical
  
The
2.
1
0
0
0
0
0
0
1
1
.1
Xa
x
x
X
X)
(X
a
T
1
T



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





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







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





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




























a
a
a
a
a
a
Y
X
Y
X
Y
X
Y
X
Y
X
Y
X
y
x
y
x
y
x
N
a
a
a
a
a
a
Y
X
Y
X
Y
X
a
a
a
a
a
a
y
x
N
N
N
N
N
N


Least squares solution 
or least square 
approximation
a
X (object)
x (image)
Identify N image points that corresponds 
to N locations on the object space. 
Identify N image points that corresponds to N locations on the object space. 


<!-- Page 53 / 75 -->

53
Least Squares Approximation
•
Suppose a system ax = b has N 
equations, N > 1, in only one unknown. 
(Equation 1.1)
•
One possibility of solving this 
inconsistent equation is to determine x 
from a part of the system, and ignore 
the rest.
•
A more reasonable method is to 
determine x that minimizes the 
average error in the N equations.
•
Sum of squares is a popular method to 
define average errors (Equation 1.2)
•
If there is an exact solution, minimum 
E=0.
•
If b is not proportional to a, the function 
E2 is a parabola with its minimum at 
the point defined by Equation 1.3.
•
Solving for x, Equation 1.4 is the least 
squares solution of the system


)
4.1(
4
3
2
4
3
2
)
3.1(
0
4
)
4
(
3
)
3
(
2
)
2
(
2
)
2.1(
)
4
(
)
3
(
)
2
(
)1.1(
4
3
2
4
3
2
2
2
2
3
2
1
3
2
1
2
2
3
2
2
2
1
2
3
2
1




































b
b
b
x
b
x
b
x
b
x
dx
dE
b
x
b
x
b
x
E
b
x
b
x
b
x
a


<!-- Page 54 / 75 -->

54
Least Squares Approximation
•
General formula: given any a
not equal to 0 and any b, the 
error E is the length of the 
vector ax-b (Equation 1.5)
•
The parabola (Equation 1.6) 
has a minimum at the point 
defined by Equation 1.7.
•
The least squares solution to 
ax=b can be determined using 
Equation 1.8.
)
8.1(
)
7.1(
0
2
2
)
6.1(
2
)
(
)
(
)
5.1(
]
)
(
)
[(
2
2
2
2
1
2
2
1
1
a
a
b
a
b
a
a
a
b
a
a
a
b
b
b
a
a
a
b
a
b
a
b
a
T
T
T
T
T
T
T
T
T
T
n
N
x
x
x
dx
dE
x
x
x
x
E
b
x
a
b
x
a
x
E






















<!-- Page 55 / 75 -->

55
Least Squares Approximation
•
The least squares solution is 
given by Equation 1.9.
•
If the matrix ATA is invertible, 
Equation 1.10 is the unique 
least squares solution.
)
10
.1(
)
9.1(
b
A
A)
(A
x
b
A
Ax
A
T
1
T
T
T





<!-- Page 56 / 75 -->

56
Least Squares Approximation
•
Suppose we do a series of experiments, and expect the 
output y to be approximated by a linear function of t, 
y=C+Dt.
•
Example, measure the strain y of a linear elastic material 
subjected to a load t. If there is no error, only two 
measurement of (y,t) are sufficient. But there will be 
experimental errors, a series of more than two sets of 
(y,t) measured from the experiments are unlikely to fall 
on a straight line. We need to “average” all the 
experiments to determine the optimal line.


<!-- Page 57 / 75 -->

57
Least Squares Approximation



























































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



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
















i
i
i
i
i
i
N
N
N
N
N
N
y
t
y
t
t
t
N
D
C
D
C
D
C
E
t
D
C
y
E
Dt
C
y
Dt
C
y
Ax
b
E
D
C
D
C
t
t
t
y
y
y
Dt
C
y
Dt
C
y
Dt
C
y
1
2
1
2
2
2
2
1
2
2
2
1
2
1
2
2
1
1
)
(
.
 
of
solution 
 
squares
least 
 
 the
is
 
minimizes
 which 
 
line
straight 
 
The
).
0
(
 
 to
possible
 
as
 
close
 
as
 
is
 
 that 
so
 
 
choose
 
We
)
(
)
(
minimize
 
 to
 
and
 
 
choose
 
 want to
 We
errors
 
 the
of
 
squares
 
 the
of
 
sum
 
the
minimizes
 that 
one
 
 the
is
 
sense
 
squares
least 
 
in the
solution 
best 
 
The
1
1
1
.
results,
 
al
experiment
 
 the
From
b
A
A
A
b
A
A
A
b
A
Ax
A
b
Ax
b
Ax
p
x
Ax
b
T
T
T
T
T
T







<!-- Page 58 / 75 -->

58
•
In practice, the assumption in the example of image 
guided medical robot that all target points are on a single 
horizontal work plane may not hold.
Camera
Work plane
Body cavity
A typical 2D image from a single 
camera does not have sufficient 
information to recover the 3D 
information of the object.


<!-- Page 59 / 75 -->

59
Homogeneous Coordinates
•
A homogeneous vector 
corresponds to a straight 
line through the origin.
0
     
,

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













k
k
kz
ky
kx
z
y
x
h
O
Scale factor
Cartesian 
coordinate
Homogeneous 
coordinate


<!-- Page 60 / 75 -->

60
Advantages of Homogeneous Coordinates
•
Translation and perspective transformation can be 
expressed in matrix form:
•
Unified matrix representation: v’ = T v
•
v: column vector containing the coordinate
•
T: 4x4 Homogeneous Transformation Matrix (HTM)
•
Consecutive geometric transformation can be expressed 
as series of matrices with matrix multiplication


<!-- Page 61 / 75 -->

61
Image and Object Points in Homogeneous 
Coordinates
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
































k
kz
ky
kx
z
y
x
k
ky
kx
y
x
o
o
o
o
o
o
o
o
i
i
i
i
i
i
X
X
u
u

:
point
object 
ˆ
:
point
 
image
^
To convert from n x 1 vector 
in homogeneous coordinates 
to coordinate of dimension n-
1, we have to divide by the 
nth element and then delete 
the nth component. 


<!-- Page 62 / 75 -->

62
Translation in Homogeneous Coordinates
































z
y
x
t
t
t
z
y
x
z
y
x
new
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


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



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


1
1
0
0
0
1
0
0
0
1
0
0
0
1
1
new
z
y
x
t
t
t
z
y
x
z
y
x
In homogeneous coordinates:
fake coordinate
Translation as invertible matrix:
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







1
0
0
0
1
0
0
0
1
0
0
0
1
1
z
y
x
t
t
t
T
Using unified matrix representation


<!-- Page 63 / 75 -->

63
Scaling in Homogeneous Coordinates
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



1
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
z
y
x
S
S
S
S
Scaling by factors Sx, Sy and 
Sz along the x, y, and z axes.


<!-- Page 64 / 75 -->

64
Rotation in Homogeneous Coordinates
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




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




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




1
0
0
0
0
cos
0
sin
0
0
1
0
0
sin
0
cos
1
0
0
0
0
cos
sin
0
0
sin
cos
0
0
0
0
1
1
0
0
0
0
1
0
0
0
0
cos
sin
0
0
sin
cos
,
,
,















y
x
z
R
R
R
Rotation of a point about each of 
the coordinate axes. Angles are 
measured clockwise. 
Non-standard orientation of coordinate 
system:
Common in 2D computer graphics with 
the origin at the top left corner and 
the y-axis down the screen.
Angles are clockwise positive.
Computer vision and computer graphics 
are closely related.
X
  1       0         0
R ( )
   0    cosθ   -sinθ
  0    sinθ     cosθ 











Y
 cosθ     0      sinθ
R  ( ) 
    0        1        0
  -sinθ     0      cosθ











Z
 cosθ     -sinθ       0
R ( ) 
  sinθ       cosθ       0
  0            0           1











zAo
yA1
,zA1


yAo
xA1
xA0
Standard right-hand Cartesian 
coordinate system in mathematics:
x-axis to the right and y-axis up the 
screen. 


<!-- Page 65 / 75 -->

65
Composite Transformation
•
With homogeneous coordinates, a 
sequence of transformations: 
translation T, scaling S, followed by 
rotation about z axis can be 
represented in matrix equations.
•
P’ is the transformed point 
corresponding to the point P.
•
The order of application is important.
•
Many transformations have inverse 
matrices that can be used to perform 
the opposite transformation.  
ST
R
A
θ
z,

AP
P 
'


<!-- Page 66 / 75 -->

66
Perspective Projection
•
Projection from 3D points onto a 
plane
Z
f
Y
f
Z
Y
f
y
Z
f
X
f
Z
X
f
x
f
Z











:
iangles
similar tr
The inverse perspective 
transformation from a 
point in plane to 3D 
space corresponds to a 
line, i.e. to an
homogeneous vector. 
Perspective transformation (image transformation) projects 3D points onto a plane.


<!-- Page 67 / 75 -->

67
Perspective Projection in Matrix Form
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

















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





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


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





Z
f
fZ
Z
f
fY
Z
f
fX
z
y
x
k
f
kZ
kZ
kY
kX
k
kZ
kY
kX
f
c
Pw
c
w
,
c
P
h
h
h
h
point
 
image
 
 the
of
 s
coordinate
 
Cartesian
1
1
0
0
0
1
0
0
0
0
1
0
0
0
0
1
vely
  respecti
workspace
and  
  
image
for 
 s
coordinate
 s
homogeneou
:
 matrix
projection
 e
perspectiv
 :
 can be recovered from 
 by dividing the first three elements of 
 by the fourth element.  
1
(4)

h
h
h
h
c
c
c
c
c c


<!-- Page 68 / 75 -->

68
Perspective Projection in Matrix Form
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






1
1
0
0
0
1
0
0
0
0
1
0
0
0
0
1
D
-
3 
into
 
point back
 
image
 
 maps
ation
 transform
e
perspectiv
 
Inverse
1
1
f
P
c
P
w
h
h
Inverse perspective 
transformation problem: 
Given the coordinates of a 
point in image plane, we 
cannot determine the 
corresponding coordinates 
in 3D scene. 
Mapping a 3D scene into a 
2D image plane is a many-
to-one transformation.


<!-- Page 69 / 75 -->

69
Homogeneous Coordinates
•
To represent 
rotation, translation, 
scaling and 
perspective 
transformation in a 
similar way, using 
matrices
•
Composed 
operations can be 
realized using matrix 
multiplication.
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


1
0
0
0
3
33
32
31
2
23
22
21
1
13
12
11
t
R
R
R
t
R
R
R
t
R
R
R
Perspective Projection: -1/f
3x3 rotation matrix
3x1 
translation 
vector
1x3 perspective 
projection vector
1x1 scaling 
(stretching) 
matrix


<!-- Page 70 / 75 -->

World 
coordinate 
system
Camera coordinate system
Offset of the 
centre of image 
plane with 
respect to 
gimbal centre 
Offset of the 
centre of gimbal 
centre from 
original of world 
coordinate 
system 
70
Camera Model
In practice, the camera and 
world camera systems are 
not coincident.
A camera mounted on 
gimbal can pan through an 
angle between x and X 
axes and tilt through an 
angle between z and Z 
axes.
w: a point in 3D
c: image point 


<!-- Page 71 / 75 -->

71
To develop a camera model
1.
A translation from the origin of the world coordinates to the 
gimbal centre
2.
A rotation about z-axis by an angle θ
- Pan angle is measured between the x and X axes.
3.
A rotation about x-axis by an angle α
- Tilt angle is measured between the z and Z axes.
4.
A translation from the gimbal centre to the origin of the camera 
coordinate frame.
5.
A perspective transform from the image point to the world point.
Camera 
coordinates
World 
coordinates
h
z
x
h
w
T
R
R
PT
c
)
(
)
(
)
(
)
(
0
w
r



Transformations
The initial orientation of the camera has the x-y-z axes parallel to X-Y-Z axes 
(the camera is pointing upward initially).


<!-- Page 72 / 75 -->

72
Camera Calibration of Linear Model
•
In homogeneous coordinates, 
the projection of a scene point
or object point in world 
coordinate X to an image point 
u is given by a simple linear 
mapping. (Equation 4.1). M is 
the camera projection matrix.
•
If the scale factor = 1 in the 
homogeneous coordinates, we 
have Equation 4.2. 
)
2.4
(
1
1
)1.4
(
1
44
43
42
41
34
33
32
31
24
23
22
21
14
13
12
11
44
43
42
41
34
33
32
31
24
23
22
21
14
13
12
11
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


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



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


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


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



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




Z
Y
X
a
a
a
a
a
a
a
a
a
a
a
a
a
a
a
a
z
y
x
Z
Y
X
a
a
a
a
a
a
a
a
a
a
a
a
a
a
a
a
k
kz
ky
kx
MX
u


<!-- Page 73 / 75 -->

73
Camera Calibration of Linear Model
•
Ignoring the term of z 
since z=0 on the 
image plane (Equation 
4.3). 
•
There are 11 free 
parameters in M. 


<!-- Page 74 / 75 -->

74
Camera Calibration of Linear Model
1.
Measure N points in workspace and record the 
corresponding points in the image
2.
Identify the 11 parameters α using the least square 
solution method
3.
Improve the calibration using a look up table or a 
neural network


<!-- Page 75 / 75 -->

