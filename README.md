# DVC

## General description

DVC enables you to version data. It has many more features like ML pipelines, some of them are overlapping with MLflow features.  
DVC has very powerful cache system that skips pipeline steps that have been run before and don't have to be rerun.  
DVC studio is similar to MLflow ui but it's paid up to 5 collaborants and have more limitations. Nevertheless it allows you to compare model metrics, data as well as source code.  

## Few helpful commands examples

Add google drive as default (-d) remote server to store data:

```console
dvc remote add -d myremote gdrive://0AIac4JZqHhKmUk9PDA
```

```console
dvc run -n featurize  \
    -p featurize.max_features,featurize.ngrams \
    -d src/featurization.py -d data/data.xml \
    -o data/features \
    python src/featurization.py data/prepared data/features
```

[How to use DVC with MLflow](https://www.sicara.fr/blog-technique/dvc-pipeline-runs-mlflow)

## DVCLive

Library for logging machine learning parameters, metrics and other metadata in simple file formats, which is fully compatible with DVC.  

Log:

- scalar

```python
live.log_param("num_classes", 10)
```

- image

```python
img = np.ones((500, 500, 3), np.uint8)
live.log_image("image.png", img)
```

- plot

```python
y_true = [0, 0, 1, 1]
y_pred = [0.2, 0.5, 0.3, 0.8]
live.log_plot("roc", y_true, y_score)
```
