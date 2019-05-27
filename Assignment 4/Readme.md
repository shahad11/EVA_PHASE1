HOW TO START BUILDING A CNN

1) Number of layers:-

  Determining number of layers. even though determining exact number of layers is an iterative process, for a starting we have to consider   some number of layers. 
  
2)Receptive Field:-
  while thinking about number of layers we have to consider receptive field.
  
3) 3x3 Convolution:-

  Appliying a 3x3 convolution on the input image by incorporating the the channels of input image and specifying the output channels.
  
4) Batch Normalization and 5) image normalisation:-
  
  We have to normalise the image aswell as batch inorder to give equal chance for all pixels to be captured.(eg dull image and
  bright image which we discussed)
  
6)Dropout:-

  Dropouts helps us to close the gap between validation accuracy and testing
  accurcy.
  
7)1x1 Convolutions:-
  
  Applying 1x1 convolution inorder to reduce the chanells without losing spacial information for the next layer.
  
8)MaxPooling:-

  Applying max pooling inorder to reduce the computation aswell as overfitting in the data.
  

9)SoftMax

10)Adam vs SGD

11)Learning Rate:- How fast the model will converge to global minima.

12Number of Epochs and when to increase them

13)When to add validation checks

14)Concept of Transition Layers,

15)Position of Transition Layer

16)Position of MaxPooling,

17)When do we introduce DropOut, or when do we know we have some overfitting

18)Kernels and how do we decide the number of kernels?

19)How do we know our network is not going well, comparatively, very early

20)LR schedule and concept behind it

21)Batch Size, and effects of batch size

22)The distance of MaxPooling from Prediction,

23)The distance of Batch Normalization from Prediction,

24)When do we stop convolutions and go ahead with a larger kernel or some other alternative (which we have not yet covered)

  
 
