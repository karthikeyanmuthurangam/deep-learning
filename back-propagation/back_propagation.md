#### 0 - Read Input and Output



| x                                                            | wh   | bh   | hl_input | hl_activations | wout | bout | output | Y                                                       | E    |
| ------------------------------------------------------------ | ---- | ---- | -------- | -------------- | ---- | ---- | ------ | ------------------------------------------------------- | ---- |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ |      |      |          |                |      |      |        | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ |      |



#### 1 - Initialize weights and biases with Random values

| x                                                            | wh                                                           | bh                                                           | hl_input | hl_activations | wout                                                         | bout                                             | output | Y                                                       | E    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------- | -------------- | ------------------------------------------------------------ | ------------------------------------------------ | ------ | ------------------------------------------------------- | ---- |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03 & 0.56 & 0.46 \\0.67 & 0.34 & 0.76 \\0.47 & 0.87 & 0.56\\0.32 & 0.45 & 0.71\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ |          |                | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ |        | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ |      |



#### 2 - Calculate Hidden Layer input



###### hidden_layer_input= matrix_dot_product(X,wh) + bh

| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations | wout                                                         | bout                                             | output | Y                                                       | E    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------- | ------------------------------------------------------------ | ------------------------------------------------ | ------ | ------------------------------------------------------- | ---- |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03 & 0.56 & 0.46 \\0.67 & 0.34 & 0.76 \\0.47 & 0.87 & 0.56\\0.32 & 0.45 & 0.71\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ |                | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ |        | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ |      |

#### 3 - Perform Non-Linear Operation on Hidden Linear Input



###### hiddenlayer_activations = sigmoid(hidden_layer_input)

| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations                                               | wout                                                         | bout                                             | output | Y                                                       | E    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | ------ | ------------------------------------------------------- | ---- |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03 & 0.56 & 0.46 \\0.67 & 0.34 & 0.76 \\0.47 & 0.87 & 0.56\\0.32 & 0.45 & 0.71\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ | $$\left[\begin{matrix} 0.81 & 0.86 & 0.84 \\0.86 & 0.91 & 0.91 \\0.88 & 0.76 & 0.89\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ |        | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ |      |

#### 4 - Peform Linear and Non Linear transformation of hidden layers activation at output layer



###### output_layer_input = matrix_dot_product (hiddenlayer_activations * wout ) + bout
###### output = sigmoid(output_layer_input)

| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations                                               | wout                                                         | bout                                             | output                                                       | Y                                                       | E    |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------- | ---- |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03 & 0.56 & 0.46 \\0.67 & 0.34 & 0.76 \\0.47 & 0.87 & 0.56\\0.32 & 0.45 & 0.71\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ | $$\left[\begin{matrix} 0.81 & 0.86 & 0.84 \\0.86 & 0.91 & 0.91 \\0.88 & 0.76 & 0.89\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.92 \\ 0.93\\ 0.92\\\end{matrix}\right]$$ | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ |      |



#### 5 - Calculate gradient of error at output layer

###### E = y-output



| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations                                               | wout                                                         | bout                                             | output                                                       | Y                                                       | E                                                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------- | ------------------------------------------------------------ |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03 & 0.56 & 0.46 \\0.67 & 0.34 & 0.76 \\0.47 & 0.87 & 0.56\\0.32 & 0.45 & 0.71\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ | $$\left[\begin{matrix} 0.81 & 0.86 & 0.84 \\0.86 & 0.91 & 0.91 \\0.88 & 0.76 & 0.89\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.92 \\ 0.93\\ 0.92\\\end{matrix}\right]$$ | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.078 \\ 0.070\\ -0.921\\\end{matrix}\right]$$ |



#### 6 - Compute slope at output and hidden layer

###### Slope_output_layer= derivatives_sigmoid(output)
###### Slope_hidden_layer = derivatives_sigmoid(hiddenlayer_activations)



| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations                                               | wout                                                         | bout                                             | output                                                       | Y                                                       | E                                                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------- | ------------------------------------------------------------ |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03 & 0.56 & 0.46 \\0.67 & 0.34 & 0.76 \\0.47 & 0.87 & 0.56\\0.32 & 0.45 & 0.71\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ | $$\left[\begin{matrix} 0.81 & 0.86 & 0.84 \\0.86 & 0.91 & 0.91 \\0.88 & 0.76 & 0.89\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.92 \\ 0.93\\ 0.92\\\end{matrix}\right]$$ | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.078 \\ 0.070\\ -0.921\\\end{matrix}\right]$$ |

##### Slope Hidden Layer

$$\left[\begin{matrix}0.151 & 0.120 & 0.134 \\0.121 & 0.085 & 0.078 \\0.107 & 0.180 & 0.096\end{matrix}\right]$$

##### Slope

$$\left[\begin{matrix}0.0718 \\0.0653 \\0.0719\end{matrix}\right]$$



#### 7 - Compute delta at output layer

###### *d_output = E \* slope_output_layer*lr



| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations                                               | wout                                                         | bout                                             | output                                                       | Y                                                       | E                                                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------- | ------------------------------------------------------------ |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03 & 0.56 & 0.46 \\0.67 & 0.34 & 0.76 \\0.47 & 0.87 & 0.56\\0.32 & 0.45 & 0.71\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ | $$\left[\begin{matrix} 0.81 & 0.86 & 0.84 \\0.86 & 0.91 & 0.91 \\0.88 & 0.76 & 0.89\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.92 \\ 0.93\\ 0.92\\\end{matrix}\right]$$ | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.078 \\ 0.070\\ -0.921\\\end{matrix}\right]$$ |

##### Slope Hidden Layer

$$\left[\begin{matrix}0.151 & 0.120 & 0.134 \\0.121 & 0.085 & 0.078 \\0.107 & 0.180 & 0.096\end{matrix}\right]$$

##### Slope

$$\left[\begin{matrix}0.0718 \\0.0653 \\0.0719\end{matrix}\right]$$

##### Delta Output

$$\left[\begin{matrix}0.0056 \\0.0046 \\-0.0663\end{matrix}\right]$$



#### 8 - Calculate Error at hidden layer



###### Error_at_hidden_layer = matrix_dot_product(d_output, wout.Transpose)



| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations                                               | wout                                                         | bout                                             | output                                                       | Y                                                       | E                                                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------- | ------------------------------------------------------------ |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03 & 0.56 & 0.46 \\0.67 & 0.34 & 0.76 \\0.47 & 0.87 & 0.56\\0.32 & 0.45 & 0.71\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ | $$\left[\begin{matrix} 0.81 & 0.86 & 0.84 \\0.86 & 0.91 & 0.91 \\0.88 & 0.76 & 0.89\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.92 \\ 0.93\\ 0.92\\\end{matrix}\right]$$ | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.078 \\ 0.070\\ -0.921\\\end{matrix}\right]$$ |

##### Slope Hidden Layer

$$\left[\begin{matrix}0.151 & 0.120 & 0.134 \\0.121 & 0.085 & 0.078 \\0.107 & 0.180 & 0.096\end{matrix}\right]$$

##### Slope

$$\left[\begin{matrix}0.0718 \\0.0653 \\0.0719\end{matrix}\right]$$

##### Delta Output

$$\left[\begin{matrix}0.0056 \\0.0046 \\-0.0663\end{matrix}\right]$$

##### Error at Hidden Layer

$$\left[\begin{matrix}0.0031 & 0.0042 & 0.0037\\0.0026 & 0.0035 & 0.0031 \\-0.0371 & -0.0504 & -0.0445\end{matrix}\right]$$



#### 9 -  Compute delta at hidden layer

###### d_hiddenlayer = Error_at_hidden_layer \* slope_hidden_layer



| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations                                               | wout                                                         | bout                                             | output                                                       | Y                                                       | E                                                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------- | ------------------------------------------------------------ |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03 & 0.56 & 0.46 \\0.67 & 0.34 & 0.76 \\0.47 & 0.87 & 0.56\\0.32 & 0.45 & 0.71\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ | $$\left[\begin{matrix} 0.81 & 0.86 & 0.84 \\0.86 & 0.91 & 0.91 \\0.88 & 0.76 & 0.89\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.92 \\ 0.93\\ 0.92\\\end{matrix}\right]$$ | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.078 \\ 0.070\\ -0.921\\\end{matrix}\right]$$ |

##### Slope Hidden Layer

$$\left[\begin{matrix}0.151 & 0.120 & 0.134 \\0.121 & 0.085 & 0.078 \\0.107 & 0.180 & 0.096\end{matrix}\right]$$

##### Slope

$$\left[\begin{matrix}0.0718 \\0.0653 \\0.0719\end{matrix}\right]$$

##### Delta Output

$$\left[\begin{matrix}0.0056 \\0.0046 \\-0.0663\end{matrix}\right]$$

##### Error at Hidden Layer

$$\left[\begin{matrix}0.0031 & 0.0042 & 0.0037\\0.0026 & 0.0035 & 0.0031 \\-0.0371 & -0.0504 & -0.0445\end{matrix}\right]$$

##### Delta Hidden Layer

$$\left[\begin{matrix}0.00047 & 0.00051 & 0.00050\\0.00031 & 0.00030 & 0.00024 \\-0.00400 & -0.00911 & -0.00429\end{matrix}\right]$$



#### 10 - Update weight at both output and hidden layer



###### wout = wout + matrix_dot_product(hiddenlayer_activations.Transpose, d_output)*learning_rate
###### wh =  wh+ matrix_dot_product(X.Transpose,d_hiddenlayer)*learning_rate



| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations                                               | wout                                                         | bout                                             | output                                                       | Y                                                       | E                                                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------- | ------------------------------------------------------------ |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03008 & 0.56008 & 0.46007 \\0.66960 & 0.33909 & 0.75957 \\0.47007 & 0.87008 & 0.56007\\0.31963 & 0.44912 & 0.70960\end{matrix}\right]$$ | $$\left[\begin{matrix}0.98 & 0.38 & 0.64 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ | $$\left[\begin{matrix} 0.81 & 0.86 & 0.84 \\0.86 & 0.91 & 0.91 \\0.88 & 0.76 & 0.89\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.8\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.92 \\ 0.93\\ 0.92\\\end{matrix}\right]$$ | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.078 \\ 0.070\\ -0.921\\\end{matrix}\right]$$ |

##### Slope Hidden Layer

$$\left[\begin{matrix}0.151 & 0.120 & 0.134 \\0.121 & 0.085 & 0.078 \\0.107 & 0.180 & 0.096\end{matrix}\right]$$

##### Slope

$$\left[\begin{matrix}0.0718 \\0.0653 \\0.0719\end{matrix}\right]$$

##### Delta Output

$$\left[\begin{matrix}0.0056 \\0.0046 \\-0.0663\end{matrix}\right]$$

##### Error at Hidden Layer

$$\left[\begin{matrix}0.0031 & 0.0042 & 0.0037\\0.0026 & 0.0035 & 0.0031 \\-0.0371 & -0.0504 & -0.0445\end{matrix}\right]$$

##### Delta Hidden Layer

$$\left[\begin{matrix}0.00047 & 0.00051 & 0.00050\\0.00031 & 0.00030 & 0.00024 \\-0.00400 & -0.00911 & -0.00429\end{matrix}\right]$$

**Learning Rate**	- 0.1



#### 11 - Update biases at both input and hidden layer



###### bh = bh + sum(d_hiddenlayer, axis=0) \* learning_rate

###### bout = bout + sum(d_output, axis=0)\*learning_rate



| x                                                            | wh                                                           | bh                                                           | hl_input                                                     | hl_activations                                               | wout                                                         | bout                                                 | output                                                       | Y                                                       | E                                                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ---------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------- | ------------------------------------------------------------ |
| $$\left[\begin{matrix}1 & 0 & 1 & 0 \\1 & 0 & 1 & 1 \\0 & 1 & 0 & 1 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.03008 & 0.56008 & 0.46007 \\0.66960 & 0.33909 & 0.75957 \\0.47007 & 0.87008 & 0.56007\\0.31963 & 0.44912 & 0.70960\end{matrix}\right]$$ | $$\left[\begin{matrix}0.97968 & 0.37917 & 0.63965 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}1.48 & 1.81 & 1.66 \\1.8 & 2.26 & 2.37 \\1.97 & 1.17 & 2.11\\\end{matrix}\right]$$ | $$\left[\begin{matrix} 0.81 & 0.86 & 0.84 \\0.86 & 0.91 & 0.91 \\0.88 & 0.76 & 0.89\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.56 \\ 0.76\\ 0.67 \\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.79438\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.92 \\ 0.93\\ 0.92\\\end{matrix}\right]$$ | $$\left[\begin{matrix}1 \\ 1\\ 0\\\end{matrix}\right]$$ | $$\left[\begin{matrix}0.078 \\ 0.070\\ -0.921\\\end{matrix}\right]$$ |

##### Slope Hidden Layer

$$\left[\begin{matrix}0.151 & 0.120 & 0.134 \\0.121 & 0.085 & 0.078 \\0.107 & 0.180 & 0.096\end{matrix}\right]$$

##### Slope

$$\left[\begin{matrix}0.0718 \\0.0653 \\0.0719\end{matrix}\right]$$

##### Delta Output

$$\left[\begin{matrix}0.0056 \\0.0046 \\-0.0663\end{matrix}\right]$$

##### Error at Hidden Layer

$$\left[\begin{matrix}0.0031 & 0.0042 & 0.0037\\0.0026 & 0.0035 & 0.0031 \\-0.0371 & -0.0504 & -0.0445\end{matrix}\right]$$

##### Delta Hidden Layer

$$\left[\begin{matrix}0.00047 & 0.00051 & 0.00050\\0.00031 & 0.00030 & 0.00024 \\-0.00400 & -0.00911 & -0.00429\end{matrix}\right]$$

**Learning Rate**	- 0.1

