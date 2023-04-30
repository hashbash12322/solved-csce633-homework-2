Download Link: https://assignmentchef.com/product/solved-csce633-homework-2
<br>
<h1>Question 1: Decision Tree</h1>

<ul>

 <li>Suppose we have 80 observations representing in the following tabulated data with binaryfeatures, such as temperature, humidity, and sky condition, and we observe the occurrence of the rainy day, denoted by total rainy days per total observations (#Rainy/#Observations) for each combination of features. Using this data, we want to grow a decision tree which maximizes information gain, to predict the future occurrence rainy days. Please provide (i) the intermediate computations, (ii) the predictor variable/feature that you select for the split in each node of the tree based on information gain criteria, and (iii) draw the resulting decision tree.</li>

 <li>In training decision trees, the ultimate goal is to minimize the classification error. However,the classifaction error is not a smooth function; thus, several surrogate loss functions have been proposed. Two of the most common loss functions are the Gini index and Cross-entropy. Prove that, for any discrete probability distribution p with K classes, the value of the Gini index is less than or equal to the corresponding value of the entropy. This implies that the Gini index is a better approximation of the misclassification error.</li>

</ul>

<em>Definitions: </em>For a K-valued discrete random variable with probability mass function <em>p<sub>i</sub></em>, <em>i </em>=

1<em>,…,K </em>the Gini index is defined as: ) and the entropy is defined as.

<ul>

 <li><strong>Classifying benign vs malignant tumors: </strong>We would like to classify if a tumor is benign or malign based on its attributes. We use data from the Breast Cancer Wisconsin Data Set of the UCI Machine Learning Repository: https://archive.ics.uci.edu/ml/datasets/ breast+cancer+wisconsin+(original).</li>

</ul>

Inside “Homework 2” folder on Piazza you can find one file containing the data (named “hw2 question1.csv”) for our experiments. The rows of these files refer to the data samples, while the columns denote the features (columns 1-9) and the outcome variable (column 10), as described bellow:

<ol>

 <li>Clump Thickness: discrete values {1<em>,</em>10}</li>

 <li>Uniformity of Cell Size: discrete values {1<em>,</em>10}</li>

 <li>Uniformity of Cell Shape: discrete values {1<em>,</em>10}</li>

 <li>Marginal Adhesion: discrete values {1<em>,</em>10}</li>

 <li>Single Epithelial Cell Size: discrete values {1<em>,</em>10}</li>

 <li>Bare Nuclei: discrete values {1<em>,</em>10}</li>

 <li>Bland Chromatin: discrete values {1<em>,</em>10}</li>

 <li>Normal Nucleoli: discrete values {1<em>,</em>10}</li>

 <li>Mitoses: discrete values {1<em>,</em>10}</li>

 <li>Class: 2 for benign, 4 for malignant (this is the <strong>outcome </strong>variable)</li>

</ol>

<ul>

 <li>Compute the number of samples belonging to the benign and the number of samplesbelonging to the malignant case. What do you observe? Are the two classes equally represented in the data? Separate the data into a train (2/3 of the data) and a test (1/3 of the data) set. Make sure that both classes are represented with the same proportion in both sets.</li>

 <li><em>Implement </em>two decision trees using the training samples. The splitting criterion for the first one should be the entropy, while for the second one should be the gini index. Plot the accuracy on the train and test data while the number of nodes in the tree increases for both splitting criteria. Do you observe any differences in practice?</li>

</ul>

(c.ii) <strong>Bonus: </strong><em>Implement </em>pre-pruning using a lower threshold on the values of the splitting criterion for each branch. Experiment with different thresholds and report results both in the train and test set.

<h1>Question 2: Kernel Ridge Regression</h1>

In this problem, we will derive kernel ridge regression, a nonlinear extension of linear ridge regression. Given a set of training data {(<strong>x<sub>1</sub></strong><em>,y</em><sub>1</sub>)<em>,…,</em>(<strong>x<sub>N</sub></strong><em>,y<sub>N</sub></em>)} where <strong>x<sub>n </sub></strong>∈ R<em><sup>D</sup></em>, linear ridge regression learns the weight vector <em>w </em>(assuming the bias term is absorbed into <em>w</em>) by optimizing the following objective function:

<em>J</em>(<strong>w</strong>) = (<strong>y </strong>−<strong>Xw</strong>)<em><sup>T </sup></em>(<strong>y </strong>−<strong>Xw</strong>)


where <em>λ </em>is the regularization coefficient.

Assume that we apply a nonlinear feature mapping to each sample <strong>x<sub>n </sub></strong>→ <strong>Φ</strong><em><sub>i </sub></em>= <em>φ</em>(<strong>x<sub>n</sub></strong>) ∈ R<em><sup>T </sup></em>, where. Define Φ ∈R<em><sup>N</sup></em><sup>×<em>T </em></sup>as a matrix containing all <strong>Φ</strong><em><sub>n</sub></em>.

(a) Express the above criterion function in terms of the non-linear transform <em>φ </em>and show that the weights <strong>w</strong><sup>∗ </sup>that minimize the criterion function can be written as

<strong>w</strong>∗ = <strong>Φ</strong><em>T </em>(<strong>ΦΦ</strong><em>T </em>+ <em>λ</em><em>I</em><em>N</em>)−1<strong>y</strong>

where <strong>y </strong>= [<em>y</em><sub>1</sub><em>,…,y<sub>N</sub></em>]<em><sup>T </sup></em>and <strong>X </strong>

<em>Hint: </em>You may use the following identity for matrices. For any matrix <em>P </em>∈R<em><sup>p</sup></em><sup>×<em>p</em></sup>, <em>B </em>∈R<em><sup>q</sup></em><sup>×<em>p</em></sup>,

<em>R </em>∈R<em><sup>q</sup></em><sup>×<em>q </em></sup>and assume the matrix inversion is valid, we have

(<strong>P</strong>−1 + <strong>B</strong><em>T </em><strong>R</strong>−1<strong>B</strong>)−1<strong>B</strong><em>T </em><strong>R</strong>−1 = <strong>PB</strong><em>T </em>(<strong>BPB</strong><em>T </em>+ <strong>R</strong>)−1

<ul>

 <li>Given a testing sample <em>φ</em>(<strong>x</strong>), show that the prediction <em>y </em>= <strong>w</strong><sup>∗<em>T </em></sup><em>φ</em>(<strong>x</strong>) can be written as:</li>

</ul>

<em>y </em>= <em>y<sup>T </sup></em>(<em>K </em>+ <em>λ</em><em>I<sub>N</sub></em>)<sup>−1</sup><em>κ</em>(<strong>x</strong>)

where <strong>K </strong>∈R<em><sup>N</sup></em><sup>×<em>N </em></sup>is a kernel matrix defined as is a vector with n<em><sup>th </sup></em>element (<em>κ</em>(<strong>x</strong>))<em><sub>n </sub></em>= <em>φ<sup>T </sup></em>(<strong>x<sub>n</sub></strong>)<em>φ</em>(<strong>x</strong>). Now you can see that <em>y </em>only depends on the dot product (or kernel value) of <strong>Φ</strong><em><sub>i</sub></em>.

<ul>

 <li><strong>Bonus: </strong>Compare the computational complexity between linear ridge regression and kernel ridge regression.</li>

</ul>

<h1>Question 3: Support Vector Machines</h1>

We will use the Phishing Websites Data Set from UCI’s machine learning data repository: https://archive.ics.uci.edu/ml/datasets/Phishing+Websites. The dataset is for a binary classification problem to detect phishing websites.

Inside “Homework 2” folder on Piazza you can find a file containing the data (named “hw2 question3.csv”) for our experiments. The rows of these files refer to the data samples, while the columns denote the features (columns 1-30) and the binary outcome variable (column 31).

<ul>

 <li><strong>Data pre-processing: </strong>All the features in the datasets are categorical. You need to preprocess the training and test data to make features with multiple values to features taking values only zero or one. If a feature <em>f<sub>i </sub></em>have value {−1<em>,</em>0<em>,</em>1}, we create three new features <em>f<sub>i,</sub></em><sub>−1</sub>, <em>f<sub>i,</sub></em><sub>0</sub>, and <em>f<sub>i,</sub></em><sub>1</sub>. Only one of them can have value 1 and <em>f<sub>i,x </sub></em>= 1 if and only if <em>f<sub>i </sub></em>= <em>x</em>. For example, we transform the original feature with value 1 into [0<em>,</em>0<em>,</em>1]. In the given dataset, the features 2, 7, 8, 14, 15, 16, 26, 29 (index starting from 1) take three different values {−1<em>,</em>0<em>,</em>1}. You need to transform each above feature into three 0/1 features. For all the following experiments randomly separate the data into train (2/3) and test (1/3) set.</li>

</ul>

<strong>Use linear SVM in LIBSVM: </strong>LIBSVM is widely used toolbox for SVM and has Matlab interface. Download LIBSVM from https://www.csie.ntu.edu.tw/~cjlin/libsvm/ and install it according to the README file provided with the download. Experiment with different values of