# Project Title

Panorama Detection

## Description

In this project, I will detect objects in a panoramic image into 5 categories: desert, mountains, sea, sunset and tree (multilabel case) using a pretrained model "MobileNetV2".

## Instalation 

```
conda install pytorch==1.6.0 torchvision==0.7.0 torchtext==0.7.0 cpuonly -c pytorch
```

## Step 1 Dataset & Dataloader 

Here I use a custom dataset called multilabeldataset with a batch size of 64. The transformations performed are: rotation, crop (224 x 224) and horizontal flip.

## Step 2 Arsitektur & Config

I'm using the pretrained model "MobileNetV2" along with the architecture and weights from ImageNet. But here I change fully connected according to my problem, namely 5 categories. I also made freeze and unfreeze methods which I will explain during the training phase. And finally I save the configuration I need such as: output size, batch size and crop size.

## Step 3 Training 

During the training I divided it into two phase, namely: adaptation and fine tuning.

### Phase 1 Adaptation (lr standard + small patience)

In this phase I freeze all layers except 5 neurons behind because that's the target of my case. I give a standard learning rate 0.001 and early stop patience 2. I do this phase to make sure the 5 neurons are well trained.

gambar 

### Phase 2 Fine Tuning (lr small + great patience)

In this phase I unfreeze all layers. I give a learning rate 1e-05 and early stop patience 6. I do this so that the model can learn more and not damage the pretrained model.

gambar 

## Finaly Sanity Check 

What's amazing about the results is that the model even manages to correctly predict data that is labeled incorrectly.

gambar 

# Conclusion 
After running a long training process and paying off with the results. We have successfully built a model that can detect objects in a panoramic image. Amazingly the model managed to correctly predict the data even though the label was wrong (generalization).

Thank you for reading :)
