# Flight Delay Prediction

## Overview

This project focuses on predicting flight delays using historical flight data. The model is built with a machine learning approach to forecast delays for future flights based on various factors, such as departure and arrival cities, scheduled departure time, and flight distance.

## Table of Contents

- [Project Structure](https://github.com/myselfRaifMondal/Flight-Prediction/edit/main/README.md#project-structure)
- [Data Preprocessing](https://github.com/myselfRaifMondal/Flight-Prediction/edit/main/README.md#data-preprocessing)
- [Model Training](https://github.com/myselfRaifMondal/Flight-Prediction/edit/main/README.md#model-training)
- [Prediction](https://github.com/myselfRaifMondal/Flight-Prediction/edit/main/README.md#prediction)
- [Usage](https://github.com/myselfRaifMondal/Flight-Prediction/edit/main/README.md#usage)
- [Results](https://github.com/myselfRaifMondal/Flight-Prediction/edit/main/README.md#results)
- [Future Work](https://github.com/myselfRaifMondal/Flight-Prediction/edit/main/README.md#future-work)
- [Contributing](https://github.com/myselfRaifMondal/Flight-Prediction/edit/main/README.md#contributing)
- [License](https://github.com/myselfRaifMondal/Flight-Prediction/edit/main/README.md#license)

## Project Structure

The repository is organized as follows:
```
├── data
│   ├── flight_data_1000.csv        # Original dataset
├── models
│   └── flight_delay_model.h5  # Trained machine learning model
├── notebooks
│   └── main.ipynb          # Jupyter notebook containing the full analysis
├── README.md               # Project overview and instructions
└── requirements.txt        # List of dependencies
```
## Data Preprocessing

The preprocessing step involves the following tasks:

**Dummy Variables**: Convert categorical variables like ORIGIN_CITY_NAME and DEST_CITY_NAME into dummy/indicator variables.

**Feature Scaling**: Use MinMaxScaler to scale the numerical features, ensuring that all inputs to the model are on a similar scale.
The preprocessed data is saved for use in model training and prediction tasks.

## Model Training

The model is trained using a sequence of past flight data. The key steps include:

**Sequence Preparation**: Prepare sequences of a specified length (seq_length = 30) from the historical flight data.
**Model Architecture**: A neural network is trained on the sequences to predict future delays. The architecture and hyperparameters are optimized for this specific task.

## Prediction

The model is capable of predicting delays for both test data and specific future flights. For instance, given a flight from Houston to New York with a scheduled departure time and distance, the model predicts the expected delay.

### Example
Here’s how you can use the model to predict delays for a new flight:
```
from src.predict import predict_delay

ft_data = {
    'DEP_DELAY': 0,
    'ORIGIN_CITY_NAME': 'Houston',
    'DEST_CITY_NAME': "New York",
    'CRS_DEP_TIME': 1230,
    'DISTANCE': 454
}

predicted_delay = predict_delay(ft_data)
print(f"Predicted delay: {predicted_delay:.2f} minutes")
```
## Usage

To use this project, follow these steps:

1. Clone the repository:
```
git clone https://github.com/yourusername/Flight-Prediction.git
cd Flight-Prediction
```
2. Install the dependencies:
```
pip install -r requirements.txt
```
3. Run the Jupyter notebook:
Open notebooks/main.ipynb to explore the data preprocessing, model training, and prediction process.
4. Make predictions:
Use the provided scripts to preprocess new data, train the model, or make predictions.

## Results

The model has shown promising results with a mean absolute error of X minutes on the test dataset. Future improvements could include refining the model architecture or incorporating additional features to enhance predictive accuracy.

## Future Work

**Model Tuning**: Explore different model architectures and hyperparameters to further improve performance.
**Additional Features**: Incorporate weather data and real-time updates to refine predictions.
**Deployment**: Consider deploying the model as a web service for real-time delay predictions.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request if you have suggestions or improvements.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
