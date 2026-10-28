# Practical Machine Learning: Course Project

Predicting how well six people performed a dumbbell biceps curl (the `classe`
variable, A to E) from accelerometer, gyroscope and magnetometer readings on
the belt, arm, forearm and dumbbell.

## Files

- [`index.Rmd`](index.Rmd) is the R Markdown source of the analysis.
- [`index.html`](index.html) is the compiled report. GitHub shows HTML files as
  source code, so read it on the live page below or download it and open it in
  a browser.

**Live report:** <https://syed-suhaan.github.io/pml-course-project/>

## Approach

1. Drop the 100 window-summary columns that are empty on almost every row and
   on all test rows, and the 7 bookkeeping columns (row number, name,
   timestamps, window ids) that leak the label. 52 sensor predictors remain.
2. Hold out 25% of the rows as a validation set.
3. Compare a classification tree and a random forest with 5-fold
   cross-validation on the other 75%, tuning `mtry` for the forest.
4. Estimate the out-of-sample error of the chosen forest on the validation set.
5. Check how the model does on a person it has never seen (leave one
   participant out).
6. Predict the 20 test cases.

## Rebuilding

The report downloads the data into `data/` on first run.

```r
install.packages(c("caret", "randomForest", "e1071", "rmarkdown"))
rmarkdown::render("index.Rmd")
```

## Data

Velloso, E., Bulling, A., Gellersen, H., Ugulino, W. and Fuks, H. (2013).
*Qualitative Activity Recognition of Weight Lifting Exercises.* Proceedings of
the 4th International Conference in Cooperation with SIGCHI (Augmented
Human '13). Stuttgart, Germany: ACM SIGCHI.
[Weight Lifting Exercise Dataset](http://web.archive.org/web/20161224072740/http:/groupware.les.inf.puc-rio.br/har).
