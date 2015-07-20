# 深度学习的基础介绍（Part 1）

## 早期深度学习算法－感知器

早期的有监管的训练算法之一就是感知器，一种基础的神经网络结构单元。假设平面上有n个点，标记为0或1。现在加上一个新的点，如何猜测它是0还是1呢？一个方法是看最邻近的点是什么标签，但是另一个更好的方法是找出一个可以分离有标记的数据的线，这个线被称为分离器。

![](http://mmbiz.qpic.cn/mmbiz/ghbI8QDvgWt7xv50pXZZIrywFbg43PRkdL2FmvOTh0icqz9IOth3xsCZM9xc3EcBEwsUbje026ZTib4uWx78TOuQ/640?wx_fmt=png&tp=webp&wxfrom=5)


每个输入数据都可以用向量X＝（X_1，X_2）来表示，线的上面是1，线的下面是0。如果用数学公式来表示的话，结合权重向量W和偏移量向量B来表示这个函数：

![](http://mmbiz.qpic.cn/mmbiz/ghbI8QDvgWt7xv50pXZZIrywFbg43PRkynXbD1BA3dIsAEX1bSpfnwFeknCSk7iaKtPc7RktlsKibozYDxhoPicjw/640?wx_fmt=png&tp=webp&wxfrom=5)

这个函数的结果会被输入一个激活函数来产生标签，在上述例子中，激活函数可以用临界值来表示，例如大于某值为1:

![](http://mmbiz.qpic.cn/mmbiz/ghbI8QDvgWt7xv50pXZZIrywFbg43PRkWEic5ZfghrQBm1d85G7dKIV7RdibH5gExmceszpLWTib5yQYIF4icgMvJg/640?wx_fmt=png&tp=webp&wxfrom=5)


## 训练感知器

训练感知器的过程包括采用多批样本数据并之一计算输出结果。每次结果产生后权重W都会被调整以使输出误差最小。在此我们定义误差为结果期望值和实际值之间的差，均方误差也常用，虽然定义不同，但是基本的训练原则是一样的。

## 单一感知器的缺点

单一感知器法的缺点是只能学习线性可分函数。但是有些函数不能用线性分离器分开，例如下图XOR。为了解决这个问题，我们需要多层感知器，即前馈神经网络。我们会结合一系列感知器来建立一个更强大的机器学习机制。

![](http://mmbiz.qpic.cn/mmbiz/ghbI8QDvgWt7xv50pXZZIrywFbg43PRk6YxyDVEXBhxhw1cPPqibo5RLwu7FAUjGnS8lXDNibWxB1YzjAFXEr2OQ/640?wx_fmt=png&tp=webp&wxfrom=5)

## 深度学习的前馈神经网络

神经网络是由感知器以不同方式连接并且以不同激活函数运行的。下面我们来看一下前馈神经网络的特性。

![](http://mmbiz.qpic.cn/mmbiz/ghbI8QDvgWt7xv50pXZZIrywFbg43PRk0kRADkWswWxMHFZcIwDhDztbRKa5z8qu0u4r4VZbRichoVoSgzQSQAw/640?wx_fmt=png&tp=webp&wxfrom=5)

- 有一个输入数据层，一个输出数据层，以及一个或多个隐藏层。上图表示了一个由三个单元输入层，四个单元隐藏层以及两个单元的输出层构成的神经网络。
- 每个单元就是一个单一感知器。
- 输入层单元是隐藏层的输入端，隐藏层又是输出层的输入端。
- 每两个单元之间的连接有一个权重。
- T层的单元通常与T－1层的每个单元连接，如果不连接的话即设置权重位0。
- 在处理输入层数据时，将输入向量‘夹入’输入层，设置向量值为输入单元的‘输出’。在上述例子中，由于输入层有三个单元，网络可以处理三维的输入向量。假设输入层单元为［7，1，2］，即设置第一个输入单元的输出为7，中间单元为1，最后一个单元为2。这些数据会被加权总和传送函数传播到隐藏层单元，然后再计算输出（激活函数）。
- 输出层用同样的方法计算输出，输出层的计算结果就是整个神经网络的计算结果。

## 超越线性

如果感应器只能使用线性激活函数的话会怎么样呢？那么网络的最终结果仍会是输入的线性组合，但是权重会通过网络计算结果不断被调整。换句话说，线性函数的结合仍然是线性函数。如果把神经网络限制为线性激活函数，那么无论有多少层，前馈神经网络不会比感应器显示更多优势。因此大多数神经网络使用非线性激活函数，例如逻辑函数，双曲正切函数等等。

## 大型神经网络的问题

神经网络可能有多个隐藏层，在这样的情况下隐藏层在前一层的基础上建立新的结果。多个隐藏层可以使深度学习更有效，但是也会带来一些问题。其中最主要的两个问题就是1）消失的梯度和 2）过度训练。本篇文章的第二部分就会进一步探讨这些问题以及如何解决。