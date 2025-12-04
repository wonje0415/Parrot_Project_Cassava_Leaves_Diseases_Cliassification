# Parrot_Project_Cassava_Leaves_Diseases_Cliassification

## Goal

- Using MobileNetV2 as backbone, fine-tune it to classify Cassava Leaf Disease Classification dataset.

## Constraint

- GPU : 1 NVIDIA T4 (by using Colab)
    - Therefore, we conducted only one epoch for fine-tuning.
- Storage limitation : 100MB (by using Colab)
- Data augmentation should be carefully applied because the color of the image is a very important feature to identify the illness of leaves.
- We can not use encoder type model, such as ViT.

## Duration

- 2024.01.11 ~ 2024.01.26

## Members

- DongHwi Seo
- Wonje Jang
- Hyorim Kim
- Heewon Jung

## Details

- Caution to augment data
    - The features which are used to identify the illness should not be damaged.
        - ColorJitter, RandomGrayScale, CenterCrop, etc should not be used.
- MobileNetV2 was a backbone, and an additional Linear Projection was used as classifier.
- Adam optimizer was used.
    - learning rate : 0.00005

## My Contribution

1. Checking data bias
2. Code design
3. Comparing data augmentation results
4. Fine-tuning

## Results

<img width="1213" height="217" alt="image" src="https://github.com/user-attachments/assets/060f5c99-2bc6-44cb-9bd4-545d2e40aa55" />


## What I Learned

1. Data augmentation should be applied according to the features of the data.
    - Without considering the features of data, data augmentation rather decrease the model’s performance.
    - There are two options for data augmentation: Offline(with Concat) and Online(without Concat)
        - Offline: Two datasets are used for training — one original and one augmented.
        - Online: A single dataset is used for training, with data augmentation applied randomly.
2. A linear projection layer can be used to make classifier.
3. In fine-tuning, lower learning rate can be more useful than high learning rate.
    - Because, lower learning rate can preserve the representation of the backbone model.
    - Especially, when the size of dataset is small, lower learning rate may be better.
