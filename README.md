# Cycle Gan Experiments

## Network Architecture

### Generator 
![alt text](images/network.png)
![alt text](images/components.png)

### Discriminator
![alt text](images/disc__.png)
![alt text](images/parts_disc.png)

### Attention Layer

We use the attention layer proposed in [Self-Attention Generative Adversarial Networks](https://arxiv.org/pdf/1805.08318.pdf);
we add [spectral normalization](https://arxiv.org/pdf/1802.05957.pdf) after each convolution layer.
The attention layer has the following network.
![alt text](images/self-attention-gan-network.png)

### Cycle Gan Architectrure and Loss fucntion

Cycle Gan is used for domain transfer. We have two domains A and B (e.g: rainy images 
, no rain images). As shown in figure below, we have two generators; one to transform image in
domain A to image in domain B. Furthermore; we have two discriminators to compare generated
images to real images.

![alt text](images/cycle_gan.png)

### Loss functions


Label for real images is 1.0 and 0.0 for fake images.
The two discriminators are trained using the following loss function; 
where MSE = mean square error.

<img src="https://latex.codecogs.com/svg.latex?\Large&space;LossDiscriminator_B={0.5*MSE(FakeB, 0.0) + 0.5*MSE(RealB, 1.0)}" title="equation1" />
<img src="https://latex.codecogs.com/svg.latex?\Large&space;LossDiscriminator_A={0.5*MSE(FakeA, 0.0) + 0.5*MSE(RealA, 1.0)}" title="equation2" />

--------
<img src="https://latex.codecogs.com/svg.latex?\Large&space;LossGenerator_A_2_B={10*MSE(RecB, RealB) + Discriminator_B(FakeB, 1.0)}" title="equation3" />
<img src="https://latex.codecogs.com/svg.latex?\Large&space;LossGenerator_B_2_A={10*MSE(RecA, RealA) + Discriminator_B(FakeB, 1.0)}" title="equation4" />

---
We train the network using the Adam optimizer with learning rate = 0.0002;
batch_size =1 and  image_size = 512x512


# Rainy to clear images:

Example of output images during training:
We use synthetic rainy images in our example;
we can find  real world rainy image in the following [link](https://drive.google.com/file/d/1Vh3T6XZ-2337vTwrnS7kvGTTiBronyqr/view?usp=sharing). 

We have respectively:

* RealA, fakeB, recA
* RealB, fakeA, recB
* Gaussian noise, RealA-fakeB, fakeA-RealB

![alt text](images/index.png)
![alt text](images/index2.png)
![alt text](images/index11.png)
![alt text](images/index21.png)
![alt text](images/index33.png)

# Gaussian denoising:

Example of output images during training:


We have respectively:

* RealA, fakeB, recA
* RealB, fakeA, recB

![alt text](images/gaussian_noise2.png)
![alt text](images/gaussian_noise3.png)
![alt text](images/Gaussian_noise1.png)


# Hazy to clear images:

We have respectively:

* RealA, fakeB, recA
* RealB, fakeA, recB

![alt text](images/haze.png)
![alt text](images/haze2.png)
![alt text](images/haze22.png)


# Underwater to clear images:

![alt text](images/under22.png)
![alt text](images/under223.png)
![alt text](images/under2222.png)
![alt text](images/underwater.png)
![alt text](images/underwater33.png)

# Face Sketch to images:

![alt text](images/sketch11.png)
![alt text](images/sketch24.png)
![alt text](images/sketch33.png)
![alt text](images/sketch45.png)
![alt text](images/sketch46.png)
![alt text](images/sketch345.png)


# Other approach

## Architecture
![alt text](images/network_22.png)

## Denoisng: Darmstadt Noise Dataset

### With data L2 loss similar to discriminator loss in importance

Real A, Fake B, Real B, fake A:

![alt text](images/dnd.png)


### With data L2 loss higher importance than discriminator loss
![alt text](images/dnd2.png)


## Dehazing

### With data L2 loss similar to discriminator loss in importance

Real A, Fake B, Real B, fake A:

![alt text](images/dehaze.png)


