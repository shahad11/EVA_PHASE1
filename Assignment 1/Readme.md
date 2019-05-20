Assignment 1B
Question 1. What are Channels and Kernels (according to EVA)?

Answer: In limited words, in a Convolutional Neural Network, kernels are feature extractors, while channels are similar feature bags.

For detailed understanding let's take the example of making a movie. For simplicity lets take an example of short 2 minutes movie consisting only of a single person. Let's watch a movie now.

Movie: The Scarecrow

Isn't that good? Now ask yourself a question, even to create such a simple movie how many people do you think have come together? Ok, Let's watch behind the scenes of this movie.

Behind the scenes of the Movie

Do you see that? Almost 8 people. Actor, CameraMan, Director, Technicians, Crew Boys, Makeup Man etc. They are the people on the set. What about people behind post production? The Sound engineer, Producer, Editor etc. What about camera, audio gears and editing software used? You understand now what goes behind making a simple and short movie like that.

Now think of kernels/feature extractors as your questions on making of a movie such as 'Who is the director?', 'What were the camera gears used?'.

Then, Channels/Similar feature bags shall represent the answers you receive such as 'The director of this movie is Jacob Owens', 'Camera gears used for this movie are Canon 6D Mark II, Lexar SD Memory Card, Canon 24-105mm lens, Mic pro +, G-Raid 8TB Hard drive and Think Tank Camera Bags'.

Thats what happens inside our Convolutional Neural Networks. Consider the complete movie making process as our whole network.

    During initial layers of network our kernels try to extract just the fundamental layers of an image i.e. Edges or gradients or might well be textures. The kernel matrix constitutes of well defined numbers (refined with back propagation) which when applied on a small same sized patch of image starts collecting the required patterns as channels. You can compare this step to peoples and gears required for making a movie.
    Next, layer of kernels tries to extract channels of patterns out of it and creates a new bag of features containing patterns. Compare this to bringing people and items together in a studio/set and having a jamming session between them about the movie making process.
    Next, layers of kernels extracts channels of parts of objects out of them. Compare this to individual people working with their gears such as story-writer writing a story, camera man shooting with camera etc.
    Next, layers kernel extracts the channels of objects from the image. Compare this to different scenes shot every day or hour.

And so on. Ok, Now come out of 'movie-making-process' simile and observe the image below.

image

Observe the channels at every layer containing the similar patterns I just explained (textures -> parts of face -> face). I believe this makes everything clear. I leave you with the animation below, which summarizes the roles of kernels and channels. The 3x3 (with a depth of 3) matrix that hovers around a coloured image of size 5x5 (with a depth of 3) is a kernel and the grey colored 3x3 matrices (with a depth of 1) are their respective channels.

Convolution
Question 2. Why should we only (well mostly) use 3x3 Kernels?

Answer: Consider we are answering this during the initial days of computer vision technology. We are trying to find out which square sized kernel should be accepted as a fundamental kernel for extracting useful features of an image. Let's begin with applying a kernel on an image.

    1x1 : it's just an identity mapping. It extracts no information from the neighbouring pixels.

    2x2 : When extracting features such as detecting an edge/gradient or blur the image we don't get good results using this. The reason behind is the lack of a central element and symmetry around target pixel. A 2x2 kernel doesn't know which pixel's local features we want to extract, so basically it just extracts something without knowing the purpose. For extracting a gradient we need to have a matrix in form of discrete differentiation, or while gaussian blurring we need to have a discrete symmetrical distribution in the kernel, both of which is not possible with 2x2 kernel, thus resulting in distortions in output layers.

    Figure 1

    3x3 : This works great as feature extractor as it aligns perfect with every target pixel and also has a symmetry around it. It extracts the local information around each pixels and that also efficiently using just 9 parameters.

    Figure 2

    4x4 : Again it has same issues as 2x2 kernel. This is a general problem of every even sized kernels.

    5x5 : Even though it has every good properties of 3x3, it's not that computationally efficient because of 25 parameters and limited while extracting local features due to large area cover. This trend continues for every higher odd sized kernels.

We stop our search here and declare 3x3 as the best choice for feature extractor and optimise our hardware for this matrix multiplication.
Question 3. How many times do we need to perform 3x3 convolution operation to reach 1x1 from 199x199 (show calculations)?

Answer: Each 3x3 convolution operation decreases the spatial dimensions of the image by 2. Thus in short we would require 199/2 = 99 (quotient) convolution operation to reach 1x1 sized image.

Complete calculation of every 99 steps is provided below:

    199x199 | Conv 3x3 | 197x197

    197x197 | Conv 3x3 | 195x195

    195x195 | Conv 3x3 | 193x193

    193x193 | Conv 3x3 | 191x191

    191x191 | Conv 3x3 | 189x189

    189x189 | Conv 3x3 | 187x187

    187x187 | Conv 3x3 | 185x185

    185x185 | Conv 3x3 | 183x183

    183x183 | Conv 3x3 | 181x181

    181x181 | Conv 3x3 | 179x179

    179x179 | Conv 3x3 | 177x177

    177x177 | Conv 3x3 | 175x175

    175x175 | Conv 3x3 | 173x173

    173x173 | Conv 3x3 | 171x171

    171x171 | Conv 3x3 | 169x169

    169x169 | Conv 3x3 | 167x167

    167x167 | Conv 3x3 | 165x165

    165x165 | Conv 3x3 | 163x163

    163x163 | Conv 3x3 | 161x161

    161x161 | Conv 3x3 | 159x159

    159x159 | Conv 3x3 | 157x157

    157x157 | Conv 3x3 | 155x155

    155x155 | Conv 3x3 | 153x153

    153x153 | Conv 3x3 | 151x151

    151x151 | Conv 3x3 | 149x149

    149x149 | Conv 3x3 | 147x147

    147x147 | Conv 3x3 | 145x145

    145x145 | Conv 3x3 | 143x143

    143x143 | Conv 3x3 | 141x141

    141x141 | Conv 3x3 | 139x139

    139x139 | Conv 3x3 | 137x137

    137x137 | Conv 3x3 | 135x135

    135x135 | Conv 3x3 | 133x133

    133x133 | Conv 3x3 | 131x131

    131x131 | Conv 3x3 | 129x129

    129x129 | Conv 3x3 | 127x127

    127x127 | Conv 3x3 | 125x125

    125x125 | Conv 3x3 | 123x123

    123x123 | Conv 3x3 | 121x121

    121x121 | Conv 3x3 | 119x119

    119x119 | Conv 3x3 | 117x117

    117x117 | Conv 3x3 | 115x115

    115x115 | Conv 3x3 | 113x113

    113x113 | Conv 3x3 | 111x111

    111x111 | Conv 3x3 | 109x109

    109x109 | Conv 3x3 | 107x107

    107x107 | Conv 3x3 | 105x105

    105x105 | Conv 3x3 | 103x103

    103x103 | Conv 3x3 | 101x101

    101x101 | Conv 3x3 | 99x99

    99x99 | Conv 3x3 | 97x97

    97x97 | Conv 3x3 | 95x95

    95x95 | Conv 3x3 | 93x93

    93x93 | Conv 3x3 | 91x91

    91x91 | Conv 3x3 | 89x89

    89x89 | Conv 3x3 | 87x87

    87x87 | Conv 3x3 | 85x85

    85x85 | Conv 3x3 | 83x83

    83x83 | Conv 3x3 | 81x81

    81x81 | Conv 3x3 | 79x79

    79x79 | Conv 3x3 | 77x77

    77x77 | Conv 3x3 | 75x75

    75x75 | Conv 3x3 | 73x73

    73x73 | Conv 3x3 | 71x71

    71x71 | Conv 3x3 | 69x69

    69x69 | Conv 3x3 | 67x67

    67x67 | Conv 3x3 | 65x65

    65x65 | Conv 3x3 | 63x63

    63x63 | Conv 3x3 | 61x61

    61x61 | Conv 3x3 | 59x59

    59x59 | Conv 3x3 | 57x57

    57x57 | Conv 3x3 | 55x55

    55x55 | Conv 3x3 | 53x53

    53x53 | Conv 3x3 | 51x51

    51x51 | Conv 3x3 | 49x49

    49x49 | Conv 3x3 | 47x47

    47x47 | Conv 3x3 | 45x45

    45x45 | Conv 3x3 | 43x43

    43x43 | Conv 3x3 | 41x41

    41x41 | Conv 3x3 | 39x39

    39x39 | Conv 3x3 | 37x37

    37x37 | Conv 3x3 | 35x35

    35x35 | Conv 3x3 | 33x33

    33x33 | Conv 3x3 | 31x31

    31x31 | Conv 3x3 | 29x29

    29x29 | Conv 3x3 | 27x27

    27x27 | Conv 3x3 | 25x25

    25x25 | Conv 3x3 | 23x23

    23x23 | Conv 3x3 | 21x21

    21x21 | Conv 3x3 | 19x19

    19x19 | Conv 3x3 | 17x17

    17x17 | Conv 3x3 | 15x15

    15x15 | Conv 3x3 | 13x13

    13x13 | Conv 3x3 | 11x11

    11x11 | Conv 3x3 | 9x9

    9x9 | Conv 3x3 | 7x7

    7x7 | Conv 3x3 | 5x5

    5x5 | Conv 3x3 | 3x3

    3x3 | Conv 3x3 | 1x1
