
# PyTorch Challenge by Facebook (as part of a Udacity course)
pytorch-challenge
This repo summarizes the last challenge in the a scholarhip from Facebook to learn of PyTorch and implementing CNNs and RNNs as part of a udacity course.
The challenge was to create an image classifier that predicts which flower is present in an image out of 102 flower classes.

## Classifer Summary
The classifier was created by transer-learning, based on the [Inception-v3](https://arxiv.org/abs/1512.00567) network.
The current version of the model was created on 2018-12-29.
This version reached a 98.289% accuracy on the validation data, and a 98.168% accuracy on the testing data.

## Repo Contents
`flower_data.zip` The datasets that were used for training, validation, and testing are bundled in the file 'flower_data.zip'. [Dataset Source](http://www.robots.ox.ac.uk/~vgg/data/flowers/102/).
The zip file must be unzipped in order to recreate the model's training and testing.
Datasets were originally obtained from the [deep-learning-flower-identifier](https://github.com/GabrielePicco/deep-learning-flower-identifier) repo.
The zip file also contains a directory named 'google'.  I did not generate this dataset, but it is my understanding that it is made up of the top 10 google image search results for each of the flower classes.
As such, this dataset may be incorrectly labelled to a large degree.  The accuracy for this dataset is 63.664%.
`cat_to_name.json` is a dictionary of the flower labels that correspond to numbered classes within 'flower_data.zip'
`2018-12-29-model-incept-v3-AL.pt` is the whole trained model saved.
`checkpoint.tar` contains the `state_dict` of the model, and can be loaded if the model architecture is recreated identically.
`batch-size-calibration` contains an Excel file with summary statistics and plot of different batch sizes used during training, and their timing, in order to pick the optimal batch size.

## Unique Cells for Compatability
The classifier was originally created using the Google Colab framework and had to be adjusted to the package versions used by the Udacity Virtual Machine, so the first cells are meant to load the correct package versions for the proper operation of the classifer both frameworks.
Additionally, Google Colab session last for 12 hours at a time. To maintain the progress state, Google Colab had to be linked to Google Drive for cloud storage, and so some of the first few cells exist for this purpose.

## Future Optimizations
In future efforts to train an image classifer I'd like to implement some of methods that I didn't get a chance to try out:
- Further augment the training data using the [Augmentor](https://github.com/mdbloice/Augmentor) library.
- [Must Know Tips/Tricks in Deep Neural Networks by Xiu-Shen Wei](http://lamda.nju.edu.cn/weixs/project/CNNTricks/CNNTricks.html). Specifically, sections 6, 7, and 8 on Regularizations and Ensembles.
- Section 4 of the above linke describes the use of ReLU activation function variants, that include Leaky ReLU, PReLU, RReLU.
- There is a mention of PCA whitening and Fancy PCA methods that may prove benficial.
- Use an entirely different pre-trained model: ResNet, DenseNet
