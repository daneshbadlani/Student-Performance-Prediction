# Final Project

* Danesh Badlani
* Sam Bluestone
* Leslie Le
* Joe Salerno


## Dataset and Study

A study on statistics taken from Portuguese school children. Given the children's performance in two core classes, Mathematics and Portuguese, the machine attempted to predict the children's performance in secondary school, which will help improve the quality of education and enhance school resource management.

The dataset contains eduactional statistics of 395 students with 33 features, 16 of these being non-numerical data. Although of these 16, depending on how you transform the data, at least 11 features can be defined as binary features. Also, there are no missing features within this dataset.

Consult raw-data/student.md for all of the descriptions and names of the features within the dataset and how these features are being defined - binary, nominal, or numeric. 


## Feature Transformation

We used the last three columns to create a scores column, which is the target variable. These last three columns - G1, G2, and G3 - represent the student's first period score, second period score, and final score, respectively. We decided to compile these scores together by averaging the three scores and assigning those values according to the letter grades mentioned in the paper. We ended up mapping these ordinal values into integers. 

We also decided to binarize the following features:
* school
* sex
* address
* famsize
* Pstatus
* schoolsup
* famsup
* activities
* paid 
* internet
* nursery
* higher
* romantic

The reason we decided to binarize these features was to allow for easy processing since these features contained two values each. For example, 'male' were assigned 1 while 'female' were replaced by 0 in the sex feature. Moreover, all the features that contained 'yes' and 'no' were replaced by 1 and 0 respectively.

We decided against using a one-hot-encoding vector for these features because doing so may increase the processing time and the complexity of finding the correlations between features (due to all the new columns that will be created).


## Feature Selection

We used a **RandomForest feature** selector to determine which features were the most important towards determining the value of the target feature. According to the graph generated by the random forest, the top five features that was the most important to determining the target feature the most were 'absences', 'freetime', 'Fedu', 'goout', and 'health'.

The **heatmap correlation graph** is a large graph that shows the correlations between all the features against each other. Rather than comparing the number of features that can be found on the dataset, the heatmap compares a larger number of features due to the one-hot-encoding vector of the categorical features: Mjob,  Fjob, reason, and guardian. It is difficult to see individual values of the generated heatmap, but the top five features, according the heatmap, that are most correlated to the target feature are the mother's job type ('Mjob'): 'other' and 'services', 'Medu', 'romantic', 'Fedu', and 'health'.

According to the two feature selection algorithms, the aggreed on features that coorelate the most or the most important features to the target features are 'Fedu' and 'health'. We believe that we should not use many of the binary features or categorical features due to the features' low variances (the features do not provide assitance in predicting a correct model or the feature does not provide enough information).

## Feature Extraction

For the **Principal Component Analysis**, it is recommended that one hot encoded binary features should not be used in this algorithm. Due to this, we used only the continuous features in the PCA. We tested two separate classifiers, one being regular PCA and the other being KPCA (Kernel). The result we got from them differed drastically because it appears that our dataset is not linear. For PCA, our output consisted of a bar graph and a scatterplot, the scatterplot providing us with more information of the two by revealing that our dataset is not linearly separable. This is everso evident because the classes show no separation whatsoever, with all the points from the classes scattered on top of eachother with no possibility for decision regions. For KPCA, we got more promising results because KPCA excels on non-linear dimensionality reduction. The graph produced shows the classes are well separated with the use of kernels, demonstrating that we have a suitable dataset for non-linear classifiers. Thus, the use of both methods of PCA has given us a lead on what classifier might perform best on the given dataset because it is not linear. So, we are inclined to believe that classifiers such as SVM might work best for our model of the dataset although, this will not stop us from exploring many potential models.

The **Linear Discriminant Analysis** [TBD].
