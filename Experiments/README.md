## FILES 
Different experiments have been done to compare the performance of both networks.
Each directory contains:
- Dataset: the dataset used to train and test the network
- Train Results: files obtained from training:
  - .pth files: containing the last version of the networks
  - loss_log.txt
  - train_opt.txt

## EXPERIMENTS
### Experiment 1 - Pix2Pix
Pix2Pix model for colorization requires only the colored version of the images, since the code computes its black and white version before starting training the network. Therefore, we used 90% of our colored dataset, more concretely, 360 images. [Note that the network has been trained with 720 pictures]. 
We first trained it using a batch size equal to 32. 

### Experiment 2 - Pix2Pix
For comparison purposes, Pix2Pix has been also trained with a reduced batch size; because the cluster did not allow us to train CycleGAN model using a batch size larger than 1. The dataset used is the same one as in experiment 1. 

### Experiment 3 - CycleGAN
CycleGAN model learns the mapping between two distribution for an unpaired dataset. Hence, we divided our dataset so that the black and white and colored versions didn’t correspond. Which reduced our training dataset to 360 images (180 black and white and 180 colored images). 
As it has been stated in Experiment 2, all experiments involving CycleGAN require a batch size equal to 1. 

### Experiment 4 - CycleGAN
Since Experiment 3 took advantage of only 45% of the dataset, another experiment has been done to include more data. In this case, the 90% of the whole dataset has been inputted for the training. Even if the model has been trained with both versions of the same images, the model does not treat the data as so. 
