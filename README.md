# MLOps project - Hand Gesture Recognition
<!-- ============================== -->

Katrine Bay s183910

Rasmus Bryld s183898

Asger Schultz s183912

Eper Stinner s222955


## Main goal of the project

The objective of this project is to develop a Deep Learning model capable of transcribing static hand gestures in American Sign Language (ASL) into the corresponding English alphabet letters. Additionally, if feasible, the network will be enhanced to classify dynamic hand movement sequences to translate signs representing words. The potential for converting the images to 3D hand landmarks using MediaPipe, to make classification easy and scalable, will also be explored.

## Frameworks expected to be implemented

- Which: We expect to use PyTorch for developing the model, possibly with Lighting on top. Potentially, the framework MediaPipe will be applied to reduce images to hand landmarks.
<!-- - How: We intend to utilise a pretrained model from the Transformer framework, as we will focus on creating a well organised, reproducable, scalable and xx project repository. -->
- How: We intend to first develop a rather simple CNN, as we will focus on creating a well organised, reproducable and scalable project repository. To improve, we will make use of pretrained models from the Pytorch Image Models framework.

## Data

The data set which will be used in this project is the [Sign Language MNIST](https://www.kaggle.com/datasets/datamunge/sign-language-mnist) data set on Kaggle licensed under [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/). The data set contains 24 classes of images representing the letters of ASL (excluding J and Z as these require motion). The training data (27,455 cases) and test data (7,172 cases) which represent a single 28x28 pixel image with grayscale values between 0-255. Each training and test case represents a label (0-25) as a one-to-one map for each alphabetic letter A-Z (and no cases for 9=J or 25=Z because of gesture motions).[source](https://www.kaggle.com/datasets/datamunge/sign-language-mnist).

If we consider it a viable option, will also look for a data set with 3D hand landmarks coordinates and matching hand gestures. If no data sets are available, we can create our own, or attempt to convert existing images from the data set to hand landmarks using MediaPipe.

## Deep learning models
Due to the time limitations on the project, we make use of pre-trained models and do transfer learning. The Deep Learning model used for image classification will be a pre-trained ResNet50 model, imported using PyTorch. If we manage to work with hand landmarks instead of images with the help of 'MediaPipe Hand', it will likely be possible to get good performance with a low complexity model like a Random Forest (RF), considering the low dimensionality of the data (21 landmarks x 3 coordinates).



Project Organization
------------

    ├── LICENSE
    ├── Makefile           <- Download data with `make data`, train model with `make train`, and evaluate with `make predict`.
    ├── README.md
    ├── data
    │   ├── external       <- Data from third party sources.
    │   ├── interim        <- Intermediate data that has been transformed.
    │   ├── processed      <- The final, canonical data sets for modeling.
    │   └── raw            <- The original, immutable data dump.
    │
    ├── docs
    │
    ├── models             <- Trained and serialized models, model predictions, or model summaries
    │
    ├── notebooks          <- Jupyter notebooks. Naming convention is a number (for ordering),
    │                         the creator's initials, and a short `-` delimited description, e.g.
    │                         `1.0-jqp-initial-data-exploration`.
    │
    ├── references         <- Data dictionaries, manuals, and all other explanatory materials.
    │
    ├── reports            <- Generated analysis as HTML, PDF, LaTeX, etc.
    │   └── figures        <- Generated graphics and figures to be used in reporting
    │
    ├── requirements.txt
    │
    ├── setup.py           <- Make project pip installable (pip install -e .) so `src` can be imported.
    ├── src
    │   ├── __init__.py
    │   │
    │   ├── data
    │   │   └── make_dataset.py
    │   │
    │   ├── features
    │   │   └── build_features.py
    │   │
    │   ├── models
    │   │   │
    │   │   ├── predict_model.py
    │   │   └── train_model.py
    │   │
    │   └── visualization
    │       └── visualize.py
    │
    └── tox.ini


--------

<p><small>Project based on the <a target="_blank" href="https://drivendata.github.io/cookiecutter-data-science/">cookiecutter data science project template</a>. #cookiecutterdatascience</small></p>

## Overall project checklist

### Week 1

* [x] Create a git repository
* [x] Make sure that all team members have write access to the github repository
* [x] Create a dedicated environment for you project to keep track of your packages
* [x] Create the initial file structure using cookiecutter
* [ ] Fill out the `make_dataset.py` file such that it downloads whatever data you need and
* [x] Add a model file and a training script and get that running
* [x] Remember to fill out the `requirements.txt` file with whatever dependencies that you are using
* [x] Remember to comply with good coding practices (`pep8`) while doing the project
* [x] Do a bit of code typing and remember to document essential parts of your code
* [x] Setup version control for your data or part of your data
* [x] Construct one or multiple docker files for your code
* [x] Build the docker files locally and make sure they work as intended
* [x] Write one or multiple configurations files for your experiments
* [x] Used Hydra to load the configurations and manage your hyperparameters
* [x] When you have something that works somewhat, remember at some point to to some profiling and see if
      you can optimize your code
* [x] Use Weights & Biases to log training progress and other important metrics/artifacts in your code. Additionally,
      consider running a hyperparameter optimization sweep.
* [ ] Use Pytorch-lightning (if applicable) to reduce the amount of boilerplate in your code

### Week 2

* [x] Write unit tests related to the data part of your code
* [x] Write unit tests related to model construction and or model training
* [x] Calculate the coverage.
* [x] Get some continuous integration running on the github repository
* [x] Create a data storage in GCP Bucket for you data and preferable link this with your data version control setup
* [x] Create a trigger workflow for automatically building your docker images
* [x] Get your model training in GCP using either the Engine or Vertex AI
* [x] Create a FastAPI application that can do inference using your model
* [ ] If applicable, consider deploying the model locally using torchserve
* [ ] Deploy your model in GCP using either Functions or Run as the backend

### Week 3

* [x] Check how robust your model is towards data drifting
* [ ] Setup monitoring for the system telemetry of your deployed model
* [ ] Setup monitoring for the performance of your deployed model
* [ ] If applicable, play around with distributed data loading
* [ ] If applicable, play around with distributed model training
* [ ] Play around with quantization, compilation and pruning for you trained models to increase inference speed

### Additional

* [ ] Revisit your initial project description. Did the project turn out as you wanted?
* [ ] Make sure all group members have a understanding about all parts of the project
* [x] Uploaded all your code to github
