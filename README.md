# Progressively-trained local-enhanced CycleGAN in PyTorch

This repo is for submitting the final project codes and results of EECS 598 Deep Learning course at University of Michigan, Ann Arbor.

It is forked and adapted from the repo Jun-yan Zhu et al. created for their work on CycleGAN in Pytorch. (https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix.git) 

To carry out our experiments on the original CycleGAN codes, we mainly modified the "ResnetGenerator" class in "models/networks.py" to add progressive training and local enhancement. We also added a "load_partial_networks" function in the "models/base_model.py" and some other modifications for the option setting scripts in "options/". 

Extra to the report, we further experimented with a large model with progressive training local enhancement, which has a model architecture and size similar to the large baseline model mentioned in the report.

## To run the code: 
### 1. Clone this repo
```bash
git clone https://github.com/QiruiZhang/pytorch-PG-LE-CycleGAN.git
```

### 2. Download the Cityscapes Dataset
```bash
./bash ./datasets/download_cyclegan_dataset.sh Cityscapes
```

### 3. Run training scripts (Optional)
As pretrained models are already stored in "checkpoints/city_XX_9layer_XX/", it is not suggested to train again, which will overwrite the pretrained models.
- Train the G1 part of the medium-sized model 
```bash
./run_2x_9layer_city_medium.sh
```
- Train the complete the medium-sized model with pre-trained G1
```bash
./run_LE_9layer_city_medium.sh
```

- Train the G1 part of the large model 
```bash
./run_2x_9layer_city_large.sh
```
- Train the complete large model with pre-trained G1
```bash
./run_LE_9layer_city_large.sh
```
The trained models are in "checkpoints/city_XX_9layer_XX/".

### 4. Run testing scripts
- Test the G1 part of the medium-sized model 
```bash
./test_2x_9layer_city_medium.sh
```
- Test the complete the medium-sized model with pre-trained G1
```bash
./test_LE_9layer_city_medium.sh
```

- Test the G1 part of the large model 
```bash
./test_2x_9layer_city_large.sh
```
- Test the complete large model with pre-trained G1
```bash
./test_LE_9layer_city_large.sh
```
The testing results are in "results/city_XX_9layer_XX/test_latest/images/".
