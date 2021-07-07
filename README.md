# LP-2-shared-task

This repository contains our implementation of an Authorship Verification model for PAN at CLEF 2021 open-set shared task. It is structured in the following way:

- our_model.py contains the command line interface for training and testing the model.
- training.py contains model training and the automatic selection of best models, including the best hyperparameters.
- vectorizers.py contains all vectorizer features.
- scalar_features.py contains all scalar features.

## Installing and running

You need to install the pip packages used for the project. To do so run the following command (using pip):
`pip install -r requirements.txt`

To run the application you should run our_model.py. It accepts a number of CLI parameters, to see those run:
`python our_model.py -h`

## Model training and caching

It is pretty straight forward to train the model. To see the accepted format check https://pan.webis.de/clef21/pan21-web/author-identification.html#data
Since the training takes a long time we have included an option to cache intermediate results. In order to use that pass a cache directory as an argument.
Each vectorizer that has to be trained will be cached. Additionally, all used feature transformations of training data will be saved separately, allowing an efficient way to swap, remove and add new features. Remember to remove `transformed.pickle` if you want to modify features.
Furthermore, if you modify the function of the features without changing their names, remember to remove the cache files that contain their names.
