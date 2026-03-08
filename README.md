# Comp 590 Assignment 1: Video Compression Optimization

## Spatial Encoding
When observing the code and the specific video we're attempting to encode(bourne.mp4), it immediately seemed to me that the primary downfall of the encoder's implementation was not making use of all the spatial context each pixel has access to. 

## Implementation
The spacial encoder implemented here encodes a pixel either using the pixel to it's immediate left in the current frame being encoded, or if it exists in the first column of the frame, it's corresponding pixel in the previous frame is used. The predicted value of a pixel is simply the difference between it's greyscale value and the greyscale value of the pixel used to predict it. This makes it very easy to encode large areas with very similar color characteristics, like the white wall in the video as pixels which are identical will simply be stored as 0. Decoding is also quite simple as all we need to do is use the previously decoded predictor pixel and add our decoded residual value to it giving us the fully decoded value for the pixel we want.

## Result
This simple change increased our total compression efficiency by a more than double.

Without Spatial Encoding
![Old Result](./data/Old%20Result.png)

With Spatial Encoding
![New Result](./data/New%20Result.png)