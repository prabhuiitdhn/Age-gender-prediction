In this project, I'm using adience dataset.

* The Adience dataset [35] consists of 26,580 images of faces. A total of 2,284 subjects (people)were captured in this dataset. The dataset was then split into two gender classes (male and female)along with eight age groups; specifically: 0-2, 4-6, 8-13, 15-20, 25-32, 38-43, 48-53, and 60+. The goal of the Adience dataset is to correctly predict both the age and the gender of a given person in a photo

* In this project, I've create two saparate CNN model for predicting the ages and gender and it's only for robustness

For the age model, we’ll report “one-off” accuracy. One-off accuracy measures whether the ground-truth class label matches the predicted class label or if the groundtruth label exists in the two adjacent bins. For example, suppose our age model predicted the age bracket 15−20; however, the ground-truth label is 25−32 – according to the one-off evaluation metric, this value is still correct because 15−20 exists in the set f15−20;25−32;38−48g.

Note that one-off accuracy is not the same thing as rank-2 accuracy. 

For example, if our model was presented with an image containing a person of age 48−53 (i.e., the ground-truth label) and our model predicted:

• 4−6 with probability 63.7%

• 48−53 with probability 36.3%

Then we would consider this an incorrect classification since the first predicted label (4− 6) is not adjacent to the 48−53 bin. If instead our model predicted:

• 38−43 with probability 63.7%

• 48−53 with probably 36.3%

Then this would be a correct one-off prediction since the 38− 43 bin is directly adjacent to the 48− 53 bin.

The configuration of file as follows:

-age_gender_config.py will beused to when we're training our CNNs

-age_gender_deploy-will be used for deploying after training parts will complete

Checkpoint directory will store all model checkpoint during training So age subdirectory will contain all checkpoints related to the age CNN while the gender subdirectory will store all checkpoints related to the gender CNN.

The build_dataset.py script will be responsible for creating our .lst and .rec files for both the age and gender splits. Once have created our datasets, we can use train.py to train our CNNs. To evaluate the performance of our networks on the testing set, we’l use test_accuracy.py. We’ll then be able to visualize predictions from within the Adience dataset using vis_classification.py. Anytime we want to classify an image outside of Adience, we’ll use test_prediction.py.

