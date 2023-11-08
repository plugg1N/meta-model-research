# Meta Model Research Theory Analysis

Research of Meta Model theory. A notebook with verbose analysis and a pdf file with all reasonings.
Progress will be made in the future, as my theory would be approved by more experienced people :)

**DO NOT** review or reference cleanliness of the notebook provided since date `08.11.2023`. `*.ipynb` file is here only because I need
a backup file if *Kaggle* platform fails to save my draft project.

# Update 1

After testing two hypotheses in notebook and reporting the analysis into PDF and DOCX documents, I have received some information about meta-models as a hypothetical idea:


## First hypothesis

Switching from RandomForestClassifier as an "independent judge" from list of models for predictions to "LGBMClassifier" as a judge,
scores haven't really changed. The overfitting of RFC or ETC *(Extra Trees Classifier)* could be the cause of failure of the whole metamodel idea.
Since RFC and ETC were answering with 100% accuracy, Judge had no choice but listen to those models, that proved to be worse on test subset.

> This experiment proves that scores do not really change depending on a model that makes a final verdict (if we choose a strong enough model, ofc.)


## Second hypothesis

The hypothesis was that if I remove two models that overfit on training set completely, we can remove the problem of the first hypothesis. I removed
RFC and ETC as models for evaluations from the `models` list and tried to test LGBMC (*LGBMClassifier*) as an independent judge. Scores from two models
had been boosted significantly. The only thing left to do was to test LGBMC without the metadata to train on.

As we can see in PDF file, LGBMC proved to be better of alone training on raw data than training on the metadata.

> This experiment proves that even overfitting wasn't the problem anyway. Removing models that overfit doesn't make any difference. Independent judge
> still tries to calibrate his (or her, if we want to be politically correct xD) predictions based on decision of other models.
 
This sudden calibration might appear from the fact that models have bigger `feature importance` value than raw data features have. This means
independent judge makes his desicions mostly based on models appended artifcially to dataset.


# Update 2

I've read more articles about metamodel theory. I've came across `voting algorithm` theory. It's **very simple**. We can just collect predictions
from each model and without using any *judges* make our own predictions based on the value that is occuring more frequently within the list of predictions for certain row.
Like, if we have a list of predictions, that looks like this:

```python
[ 1, 0, 1, 1, 1 ]
```

We will choose `1` as our answer, since it is the *mode* (occuring most frequently) within that list.

I've implemented that theory in code in updated notebook (Commit on `08.11.2023`). I've chosen specifically odd amount of models to get predictions from `(5 models)` and concatenated all those
predictions into a DataFrame. Then, by receiving `mode` of each individual row of preds. I received predictions to evaluate on. This algorithm is ever so slightly better than the LGBMC
independent judge one. *This result is not satisfying at all*.
