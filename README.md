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
we add spectral normalization after each convolution layer.
The attention layer has the following network.
![alt text](images/self-attention-gan-network.png)

### Cycle Gan Architectrure and Loss fucntion

Cycle Gan is used for domain transfer. We have two domains A and B (e.g: rainy images 
, no rain images). As shown in figure below, we have two generators; one to tranform image in
domain A to image in domain B. Furthermore; we have two discriminators to compare generated
images to real iamges.

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

We have respectively:

* RealA, fakeB, recA
* RealB, fakeA, recB

![alt text](images/index.png)
![alt text](images/index2.png)
![alt text](images/index11.png)
![alt text](images/index21.png)
![alt text](images/index33.png)


