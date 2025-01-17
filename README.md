# Fake News Detection and Classification

## Steps to training the model:

1. **Download the dataset**:

Download the dataset at https://github.com/several27/FakeNewsCorpus and follow the provided steps to extract the archive. The resulting dataset is a CSV file containing multiple fields, such as: `id`, `content`, `type`, `title`, `url`.

For this project, the primary fields of interest are: 
- `content`: contains the news article text content
- `type`: represents the category of the news article (reliable, fake, satire, conspiracy etc.)


2. **Insert data into MongoDB**:

To read the csv file and insert the data into a MongoDB database:

`python3 database/read_csv.py`


3. **Split data into training and testing data**:

To split the data into training and testing data:

`python3 database/split_train_test.py`


4. **Train the TFIDF model**:

To train the TFIDF model:

`python3 machine_learning/train_tfidf.py`


5. **Train a classification model**:

To train a classification model:

`python3 machine_learning/train_model.py <model_name>`

where `<model_name>` can be one of: SGD, SVC, NB, PAC


6. **Test model accuracy**:

To test the model accuracy and plot the confusion matrix:

`python3 machine_learning/test_accuracy.py <model_name>`

where `<model_name>` can be one of: SGD, SVC, NB, PAC


## Steps to running the app:

`python3 server.py`

This runs a Flask server that exposes an API with the route `POST /predict`. 
To get a prediction, send a POST request to `http://localhost:5000/predict` with a JSON encoded body:

`
{
    "text": "<news article text content>"
}
`

