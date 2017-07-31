## S<font size="4">U</font>B<font size="4">I</font>C: A supervised, structured binary code for image search
![subic](subic.png)

**Tensorflow implementation of our paper**  

#### To train: 
You need to provide a *path_file* with paths for all training images along with their label ids. 

To trained from a pre-trained base-CNN and fine-tuning only the new layers, as we do in the paper, run: 
`ipython train_subic --m 8 --k 256 --nclass 1000 --img_path path_file --pretrained trained_model --skip_last 2 --finetune 2`

Or for a full training run:  
`ipython train_subic --m 8 --k 256 --nclass #classes --img_path path_file`

Check the arguments in *train_subic.py* to try different parameters and settings. 

The *path_file* should look like,  
```
path/to/imagenet/images/000001.jpg 0
path/to/imagenet/images/000001.jpg 0
```

subic.npy is our trained model download it from [here](https://drive.google.com/drive/folders/0Bz7VLuL7oLuvZmczV3gxSjVlTlk?usp=sharing). It has 8 layers, the first 7 layers are of VGG_M_128 and the weights are from [link](http://www.robots.ox.ac.uk/~vgg/software/deep_eval/releases/bvlc/VGG_CNN_M_128.caffemodel).

#### To test:

For a quick test we provide VGG\_M\_128 features for pascalvoc images with labels, download from [here](https://drive.google.com/drive/folders/0Bz7VLuL7oLuvZmczV3gxSjVlTlk?usp=sharing). Then, add the paths of the downloaded file in *test_subic.py* and run:  
`ipython test_subic subic.npy VGG_M_128 --m 8 --k 256 --testset pascalvoc_features`



To test with settings we used in the paper, you need to put the path file(s) for images and labels in *test_subic.py* corresponding to their datasets.   
Otherwise, directly run as:   
`ipython test_subic subic.npy VGG_M_128 --m 8 --k 256 --testset mydata --nclass #classes --split split_size --N dataset_size  --img_path path_file`



