# Meta Model Research Theory Analysis

Research of Meta Model theory. A notebook with verbose analysis and a pdf file with all reasonings.
Progress will be made in the future, as my theory would be approved by more experienced people :)

**DO NOT** review or reference cleanliness of the notebook provided since date `08.11.2023`. *.ipynb file is here only because I need
a backup file if *Kaggle* platform fails to save my draft project.

# Update 1

After testing two hypotheses in notebook and reporting the analysis into PDF document, we have received some information about meta-models as a hypothetical idea:

## First hypothesis

Switching from RandomForestClassifier as an "independent judge" from list of models for predictions to "LGBMClassifier" as a judge,
scores haven't really changed. The overfitting of RFC or ETC *(Extra Trees Classifier)* could be the cause of failure of the whole metemodel idea.
Since RFC and ETC were answering with 100% accuracy, Judge had no choice but listen to those models, that proved to be worse on test subset.

> This experiment proves that scores do not really change depending on a model that makes a final verdict (if we chose a strong enough model, ofc.)

## Second hypothesis

Removing two 
