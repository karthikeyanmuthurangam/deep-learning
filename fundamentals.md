Name : **Karthikeyan Muthurangam**

Batch : **02**

### Convolution

Convolution is a process of extracting features from an input image. It is performed on the input data with the use of a **filter or kernel** to produce a **feature map**.

Convolution operation is done by sliding the filter over the input. At every location, a matrix multiplication is performed and sums the result onto the feature map.

Applying multiple kernels over the same input image creates multiple feature maps for the same image. This set of feature maps is called the convolution layer. 

###### Convolution of 5x5 image with 3x3 filter![Convolution](https://cdn-images-1.medium.com/max/1600/1*VVvdh-BUKFh2pwDD0kPeRA@2x.gif "Convolution of 5x5 image with 3x3 filter")

Applying a kernel of size 3x3 on an input image of size 5x5 pixels means placing the 3x3 matrix over the 5x5 image starting from pixel (0,0) and sliding the 3x3 matrix on each pixel of the image results in creating a 3x3 matrix called the feature map.

### Filters/Kernels

In Image Processing, **kernel or filter** is used to *detect useful features* from an image. Applying multiple filters on an input image helps extract more features about an image.  

Smaller size kernels are more efficient and usually odd value such as 1x1, 3x3, 5x5 are used. 

More kernels can be used to extract more features from an input image. The size of the filter and the number of filters determine the quality of the features derived and the performance of a neural network. 

Bigger the size of the filter and the number of filters, bigger the number of parameters that needs to be derived by neural networks

##### Sample Kernels

###### Blur

![Blur Kernel](http://aishack.in/static/img/tut/conv-simple-blur.jpg "Blur Kernel")



###### Edge Detection

![Edge Detection](http://aishack.in/static/img/tut/conv-edge-detection.jpg "Edge Detection")



###### Line Detection

![Line Detection](http://aishack.in/static/img/tut/conv-line-detection.jpg "Line Detection")

### Epochs

One Epoch is when an *entire dataset is passed forward and backward through the neural network only once* 

Neural Network cannot pass through entire dataset in a single iteration because it needs large amount of memory. So, entire dataset is divided into number of batches.

For example: If we divide a dataset of 2000 training examples into 500 batches, then 4 iterations will complete 1 epoch

One Epoch can lead to underfitting because of the limited dataset. To optimize the learning and the graph, iterative process like *Gradient Descent* is used requiring multiple epochs.

### 1x1 Convolution

1x1 convolutions are actually used to adapt depths, by merging them, without changing the spatial information

 This type of convolution when we need to transform a volume depth into another (called squeezing or expanding) without losing spatial information

![1x1 Convolution](https://cdn-images-1.medium.com/max/1600/1*HM4R0z0dpOtHhwIByaoBZQ.png "1x1 Convolution")

Let’s see the impact of 1x1 convolution on Input image sizeof 28x28x1

###### Case 1

| Convolution Layer | Filter              | Input    | Output   | Parameter                |
| ----------------- | ------------------- | -------- | -------- | ------------------------ |
| Layer 1           | 32 filters of 3x3   | 28x28x1  | 26x26x32 | 320 = (3x3x1+1)x32       |
| Layer 2           | 10 filters of 26x26 | 26x26x32 | 1x1x10   | 216330 = (26x26x32+1)*10 |

Total #. of parmeters : **216650**

###### Case 2

| Convolution Layer | Filter              | Input    | Output   | Parameter               |
| ----------------- | ------------------- | -------- | -------- | ----------------------- |
| Layer 1           | 32 filters of 3x3   | 28x28x1  | 26x26x32 | 320 = (3x3x1+1)x32      |
| Layer 2           | 10 filters of 1x1   | 26x26x32 | 26x26x10 | 330 = (1x1x32+1)x10     |
| Layer 3           | 10 filters of 26x26 | 26x26x10 | 26x26x10 | 67610 = (26x26x10+1)x10 |

Total #. of parameters : **68260**

###### Observation

Introducing 1x1 convolution in the Convolution Layer has  significantly reduces the no. of parameters (216650 in Case 1 vs 68260 in Case 2)

### 3x3 convolution

3x3 convolution is the optimal size of the filter that has proven accuracy. In convolution layer, 3x3 filter reduces the the output matrix by 2x2

 A 5x5 filter is equivalent to two layers of 3x3 filters.

 ###### Average (blur, smooth) 3x3 convolution kernel

$$
A= \left[\begin{matrix}
    1 & 1 & 1 \\
    1 & 1 & 1 \\
    1 & 1 & 1 \\
    \end{matrix}
    \right]
$$

###### Sharpen 3x3 convolution kernel

$$
S=\left[\begin{matrix}
    0 & -1 & 0 \\
    -1 & 5 & -1 \\
    0 & -1 & 0 \\
    \end{matrix}
    \right]
$$

######Edge detection 3x3 convolution kernels

$$
E=
    \left[\begin{matrix}
    0 & -1 & 0 \\
    -1 & 4 & -1 \\
    0 & -1 & 0 \\
    \end{matrix}
    \right]

    E_H=
    \left[\begin{matrix}
    0 & 0 & 0 \\
    -1 & 2 & -1 \\
    0 & 0 & 0 \\
    \end{matrix}
    \right]

    E_V=
    \left[\begin{matrix}
    0 & -1 & 0 \\
    0 & 2 & 0 \\
    0 & -1 & 0 \\
    \end{matrix}
    \right]
$$

### Feature Maps

A Feature map is a convoluted result of applying a kernel to an input image.  The size of the feature map is determined by its filter size.

The first layer feature maps retain most of the information present in the image. As we go deeper into the network, the feature maps look less like the original image and more like an abstract representation of it. 

Choice of the Kernel decides the Feature Maps in every layer of the Convolution Neural Network (CNN)

![Feature Maps](http://www.superdatascience.com/wp-content/uploads/2018/08/Convolutional_Neural_Networks_CNN_Step1_Img4.png "Feature Maps")

### Feature Engineering

Feature Engineering is the process of identifying the features for the given dataset based on the requirement. 

A machine learning model is as good as its feature set. Simple models with right features perform much better than the complex models built on incorrect features. 

The number of features is an important criterion in feature engineering because with less features, models may not be able to perform the task and with too many features, models will be expensive to train

### Activation Function

Activation function decides whether a neuron should be activated or not based on the information received.

Different activation functions

1. Sigmoid
2. Hyperbolic Tangent Activation Function(tanh)
3. Rectified Linear Unit Activation Function (ReLU)
4. Leaky ReLU
5. ELU(Exponential Linear Units)

![Activation Functions](https://cdn-images-1.medium.com/max/1600/1*ZafDv3VUm60Eh10OeJu1vw.png "Activation Functions")

### Receptive Field

Receptive field is an area in the image whose stimulation leads to activation of a certain neuron in our brain. Each neuron responds to only few stimuli not all the stimuli. 

Neurons on the Convolution Layer are built to mimic the Visual Cortex area where every neuron is connected to only those neurons in its local receptive field or directly to pixels images in the local receptive field.   

In Convolution Layer of Convolutional Neural Network (CNN), receptive field is called the size of the kernel.

### Math Jax

###### Matrix 


$$
E=
    \left[\begin{matrix}
    0 & -1 & 0 \\
    -1 & 4 & -1 \\
    0 & -1 & 0 \\
    \end{matrix}
    \right]
$$

###### Fractions

$\frac{(n^2+n)}{6}$

###### Formulas

$\sum_{i=0}^n i^2 = \frac{(n^2+n)}{6}$

###### Greek letters

$$\alpha\beta\omega\Gamma\Delta$$ 

###### Superscripts and Subscripts

$(a+b)^2=a^2+b^2+2ab$

###### Radical signs

$\sqrt[3]{\frac xy}$

###### Special functions

$\lim_{z\to 0}$

