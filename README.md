# CoE_task
Reproducing results of the paper: TUD-MMC at MediaEval 2016: Context of Experience task


Dataset can be found [here](https://www.dropbox.com/sh/j7nunecnzfjrp2r/AAC1BAf5JEv-rGUW9h02L2X2a?dl=0).
The dataset is described in the paper found within the dataset folder. 


## Experimental Setup 

As mentioned in the paper _Right Inflight? A Dataset for Exploring the Automatic Prediction of Movies Suitable for a Watching Situation_ (contained in the data set folder) the data is labled using crowdworkers, which participated in a study decide if a movie is good or bad to be shown on a plane. 

Since this is a snapshot of the measured data we have repeatable and controlled environment. 

Using the multimodal dataset, the experiment consists of using ensemble classifiers to 'boost' them into a strong learner. The process can be seperated into three stages: classifier selection, feature selection and classifier stacking.

As performance measures they use 3 different one. Precision and Recall and F1-Score. 
