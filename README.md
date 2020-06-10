# Comparison of Pix2Pix and CycleGAN’s performances for illustration colorization
```
Authors:
Maria Alba Sendra 
Berta Benet Cugat 
Maria Elena Budan
```

# Comparison of Pix2Pix and CycleGAN’s performances for illustration colorization
## 1. Introduction
Image to image translation in Deep Learning is the task of automatically translating images from one domain to another, given two collections of images from each type to develop the training and testing operations. Some examples would be transforming paintings into real photos, changing the season of a picture from, for instance, summer to winter, or transforming a drawing into a real object. For this project, we will develop the task of colorization: transforming old images from black and white to color domain.

We aim to compare the two main architectures that are used to perform these tasks, both provided by Jun-Yan Zhu and Teasung Park, called Pix2Pix [[1](https://arxiv.org/pdf/1611.07004.pdf)] and CycleGan [[2](https://arxiv.org/pdf/1703.10593.pdf)]. We will begin with a brief definition of the dataset we will be working with [[3](https://www.kaggle.com/elibooklover/victorian400)] and, in the third section of this Report, we will provide a detailed explanation of how these two architectures work separately, referring to all the elements that constitute them as well as what are the aspects that differ from one another. Moreover, we will introduce a brief explanation of the GAN architecture, the main idea from where these two architectures diverge. We would like to remark that both architectures are application-specific, meaning that they present simple structures and hence can be applied to many different problems.

Regarding on how each architecture fits our dataset, in section 4 we will provide the different experiments we have developed with each architecture, considering different values for the parameters as, for instance, the batch size or, on the other hand, how we have distributed the datasets to elaborate the training and testing tasks.

We will finally present the results, commenting on the training losses and times, as well as which one converges quickly. In the last section we will give some conclusions on how the two architectures have performed in general and if the results match with the hypothesis we presented on the proposal of this final project.

## 2. Dataset
The dataset that we have chosen for this project is a set of 400 illustrations in black and white from the Victorian era [[3](https://www.kaggle.com/elibooklover/victorian400)] together with a set of colorful images also from the 19th century. Our architectures need a dataset that is composed by these two domains to train their networks in an optimal way, so this dataset will be useful.
We want to remark that the generator in CycleGAN involves a series of down sampling / up sampling operations that require image sizes to be multiple of 4. Hence, we have chosen this dataset also because it presents a resized version of the illustrations of 256x256, which will fit the model. Moreover, since this architecture is quite memory-intensive and needs to be loaded on one GPU, we are not able to work with large images. Hence, this smaller version, which still presents higher resolution, will also be useful. 

## 3. Architecture
To understand well how Pix2Pix and cycleGAN work, we need to understand well Generative Adversarial Networks. All this information can be found in the original papers [[1](https://arxiv.org/pdf/1611.07004.pdf)] and [[2](https://arxiv.org/pdf/1703.10593.pdf)].

## 4. Experiments
The experiments performed can be found inside the folder [experiments](https://github.com/marilenabudan/Colorization_Pix2Pix_CycleGAN/tree/master/Experiments) where you will find a [ReadMe](https://github.com/marilenabudan/Colorization_Pix2Pix_CycleGAN/blob/master/Experiments/README.md) inside that explains what each experiment consists of.

## 5. Results
After analyzing the different experiments we can conclude that the one that performs better is the second one: Pix2Pix with batch size = 1. This makes sense since Pix2Pix is a paired model (which tends to learn better) and because we have a small dataset it is prefered to use a small batch size. Notice that the results of the first experiment present red artifacts, which has been corrected in the second one. 

However, we may take into account the cycleGAN in experiment 3 has still quite good results given that it performs unpaired learning and has been trained with half of the training dataset (45%). We could conclude with the idea that, even though the experiments do not show a realistic colorization compared with the Ground truth, they still pass as realistic colorized illustrations.


