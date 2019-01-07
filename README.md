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
