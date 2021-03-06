# Repo name: rf-incremental-learning

```
Last updated on: 22Dec16
```
Incremental learning for random forest algorithm. It learns at every run instead of rebuilding. Detailed flow of this process is explained [here](https://github.com/kartheekpnsn/rf-incremental-learning/blob/master/Incremental.pptx) and [here](https://github.com/kartheekpnsn/rf-incremental-learning/blob/master/read-me.txt)

Run using:
```
Rscript 0-run-this.R
```

Once you are done running. Check logs in the 'logs' folder to assess the performance.

In Summary:
```
Incremental Learning
--------------------
Two stages:
1) Initial Run
2) Incremental Run

Stage:1
-------
- Take the labelled data (call it Data), divide it into train and validation sets (75-25 split)
- Use the train data to build the model
- Print the performance of the model on the validation set
- Apply the model on the new-unseen test set.
- Save the model object as List [[obj_1, obj_2]]
- Save the trees to take object as List [[trees for obj_1, trees for obj_2]]
- Save the validation set for next stage
- Sit back and wait for the feedback

Stage:2
-------
- Start the iterations[iter = 1 to n]
- Assumption is that the feedback is arrived for the new-unseen test set.
- Read in the Model list object
- Read in the validation set object (This is now called Data).
- Read in the feedback data (This is called Feedback).
- Make the Feedback data into a split of training and testing (90 - 10 split)
- Assume that the feedback training data is 60% of the data, take out the remaining 40% from the Data. This becomes the training data
- Train a model on this data.
- Validate this model on the feedback testing set
- Validate the Model list on the feedback testing set
- Then, take top x % of trees from the new model. Drop x % of trees from the old model
- Print the overall performance of this combined two models on feedback testing set.
- Apply the model on the new-unseen test set
- Save the model object as List [[obj_1, obj_2, .... obj_iter]]
- Save the trees to take object as List [[trees for obj_1, trees for obj_2, ... trees for obj_iter]]
- Save the validation set for next stage
- Repeat the iterations whenever there is a feedback.
```
