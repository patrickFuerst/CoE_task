# CoE_task
Reproducing results of the paper: TUD-MMC at MediaEval 2016: Context of Experience task


Dataset can be found [here](https://www.dropbox.com/sh/j7nunecnzfjrp2r/AAC1BAf5JEv-rGUW9h02L2X2a?dl=0).
The dataset is described in the paper found within the dataset folder. 


## Experimental Setup 

As mentioned in the paper _Right Inflight? A Dataset for Exploring the Automatic Prediction of Movies Suitable for a Watching Situation_ (contained in the data set folder) the data is labled using crowdworkers, which participated in a study decide if a movie is good or bad to be shown on a plane. 

Since this is a snapshot of the measured data we have repeatable and controlled environment. 

Using the multimodal dataset, the experiment consists of using ensemble classifiers to 'boost' them into a strong learner. The process can be seperated into three stages: classifier selection, feature selection and classifier stacking.

As performance measures they use 3 different one. Precision and Recall and F1-Score. 


## Weka Description

We implemented the ML pipeline to verifiy the results of Table 1 in Weka as mentioned in the paper. 
The data is exported within the jupyter notebook with the needed features as a csv file. This makes it easier to load it in Weka without processing it much. See files in `data` folder with ending `_exported.csv`. 

The different combination of modalities are implemented in single weka files found in this directory. 


### Weka Results: 

As there is no more information on how the data is preprocessed and which parameters are used for the PART algorithms we needed to make some assumptions. 

_Data:_

For the `user rating` data we didn't need to make any preprocessing. 
For the `meta` data we crated dummy variable for the columns `country`, `genre` and `language`. This gave better results with the PART algorithm.  	

For the `visual features` we have the same problem as within the jupyter implementation. As there is now information what the actual visual descriptors are we can not differenciate. So we just to the same as in the jupyter notebook and use all.

_PART Parameters:_
The PART algorithm has some parameter we can tune to get better results. We tried some changes by hand to get the best results. 

#### User Rating: 
This is the best we got for user rating data: 

```
=== Detailed Accuracy By Class ===

                 Precision  Recall   F-Measure  Class
                 0.316      0.140    0.194      0
                 0.513      0.750    0.609      1
Weighted Avg.    0.424      0.474    0.421      

=== Confusion Matrix ===

  a  b   <-- classified as
  6 37 |  a = 0
 13 39 |  b = 1
```

#### Meta data: 
This is the best we got for just the meta data: 

```
=== Detailed Accuracy By Class ===

                 Precision  Recall   F-Measure  Class
                 0.535      0.535    0.535      0
                 0.615      0.615    0.615      1
Weighted Avg.    0.579      0.579    0.579      

=== Confusion Matrix ===

  a  b   <-- classified as
 23 20 |  a = 0
 20 32 |  b = 1
```

#### Visual data: 
This is the best we got for just the visual
 data: 

```

=== Detailed Accuracy By Class ===

                 Precision  Recall   F-Measure  Class
                 0.726      0.616    0.667      0
                 0.718      0.808    0.760      1
Weighted Avg.    0.722      0.721    0.718      

=== Confusion Matrix ===

  a  b   <-- classified as
 53 33 |  a = 0
 20 84 |  b = 1
 ```

#### Meta data + User rating: 
This is the best we got for meta and user rating data: 

```
=== Detailed Accuracy By Class ===

                 Precision  Recall   F-Measure  Class
                 0.500      0.535    0.517      0
                 0.565      0.531    0.547      1
Weighted Avg.    0.535      0.533    0.533      

=== Confusion Matrix ===

  a  b   <-- classified as
 23 20 |  a = 0
 23 26 |  b = 1

 ```
#### Meta data + visual: 
This is the best we got for meta and visual data:

```

=== Detailed Accuracy By Class ===

                 Precision  Recall   F-Measure  Class
                 0.490      0.581    0.532      0
                 0.561      0.469    0.511      1
Weighted Avg.    0.528      0.522    0.521      

=== Confusion Matrix ===

  a  b   <-- classified as
 25 18 |  a = 0
 26 23 |  b = 1
 ``` 


