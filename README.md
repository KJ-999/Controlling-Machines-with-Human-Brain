# Controlling-Machines-with-Human-Brain

This repository provides code for the Brain Computer Interface Channel Whitening [(BCICW)](https://www.mdpi.com/1424-8220/22/16/6042) proposed in the paper: [Whitening Technique Based on Gram–Schmidt Orthogonalization for Motor Imagery Classification of Brain–Computer Interface Applications](https://www.mdpi.com/1424-8220/22/16/6042)

Authors: Hojong Choi, Junghun Park, Yeon-Mo Yang

Department of Electronic Engineering, Gachon University, Seongnam 13306, Korea
School of Electronic Engineering, Kumoh National Institute of Technology, Gumi 39177, Korea

#

In BCI research, our aim is clear: enhance algorithmic consistency across subjects by addressing the variance in brain signals. Our solution, "**Whitening Transform**" or [BCICW](https://www.mdpi.com/1424-8220/22/16/6042), precedes **Eigen Face Analysis (EFA)** and **Linear Discriminant Analysis (LDA)** using EEG data from channels C3, Cz, C5, and trials from nine subjects, helps uniform classification.

<p align="center">
The components of the BCICW model
</p>
<p align="center">
<img src="https://raw.githubusercontent.com/KJ-999/Controlling-Machines-with-Human-Brain/main/Assets/Workflow_BCI.webp?token=GHSAT0AAAAAACOLUMH7RMFHSR7Q5HDTYFDWZOSJHQA" alt="The components of the proposed BCICW model" width="400"/>
</p>

## About [BCICW](https://www.mdpi.com/1424-8220/22/16/6042) : 
* Whitening Technique [(BCICW)](https://www.mdpi.com/1424-8220/22/16/6042) is a preprocessing step where we use Gram–Schmidt Orthogonalization to de-correlate the mixed signal data i.e. to minimize the variance in accuracy among subjects. 
* [Whitening Transform](https://www.mdpi.com/1424-8220/22/16/6042) is aimed to provide a unit variance and a minimum covariance for the given random data due to which it minimizes the dependency between experimental participants or subjects which is an essential key factor to solve classification problems.

<p align="center">
<img src="https://github.com/KJ-999/Controlling-Machines-with-Human-Brain/blob/main/Assets/Whitening.png" alt="Covariance matrix for Whitening Transform" width="700"/>
</p>

* We tried to minimize channel dependence among the measured data in electrodes by maximizing the diagonal terms to unity and minimizing the off-diagonal terms, i.e., whitening the data.
* Because of whitening in channel direction, the independent eigenface for each class is unique and distinguishable. In addition, the Euclidean distance between the coefficients of left and right classes has been increased. Those contributions result in improved accuracy and a reduced variance.

##
The [Automated_BCICW_EFA_LDA.py](https://github.com/KJ-999/Controlling-Machines-with-Human-Brain/blob/main/Automated_BCICW_EFA_LDA.ipynb) loads the data using pickle and apply two approaches : 
1. In first approach we applied **EFA** & **LDA** **without** applying the [Whitening Technique](https://www.mdpi.com/1424-8220/22/16/6042) on each subject. Calculated the accuracy for each subject and variance in accuracy among subjects to compare with the second approach.
2. Next we applied **EFA & LDA with** [Whitening Technique](https://www.mdpi.com/1424-8220/22/16/6042) on each subject and again calculated accuracy and variance in accuracy among subjects.

<p align="center">
The accuracies for 9 subjects are : 
</p>
<p align="center">
<img src="https://github.com/KJ-999/Controlling-Machines-with-Human-Brain/blob/main/Assets/Accuracies.png" alt="The accuracies for 9 subjects are : " width="600"/>
</p>

* We can clearly observe that accuracy has been improved and variance has been reduced drastically.
* After whitening the mean of accuracy improved by almost **35%** and variance reduced to **50%** of original variance.

## Development environment
Models were trained and tested by a single GPU, using Python 3.10.8 [Anaconda 3](https://www.anaconda.com/products/distribution) was used on [Windows 11](https://www.microsoft.com/en-hk/software-download/windows11).
The following packages are required:
* pickle
* pandas
* mpl_toolkits.mplot3d
* matplotlib 3.5
* NumPy 1.20
* scikit-learn 1.0

## Dataset 
The [BCI Competition IV-2a](https://www.bbci.de/competition/iv/#dataset2a) dataset needs to be downloaded and the data path placed at 'train_df' variable in [*Automated_BCICW_EFA_LDA.py*](https://github.com/KJ-999/Controlling-Machines-with-Human-Brain/blob/main/Automated_BCICW_EFA_LDA.ipynb) file. The dataset can be downloaded from [here](https://www.kaggle.com/competitions/ucsd-neural-data-challenge/data).


