
# **Synthetic Data Generator**

The Synthetic Data Generator package allows users to generate synthetic datasets that resemble real-world data. The package supports generating continuous, categorical, and time-series features, and even allows users to add noise to simulate real-world imperfections.

This package is ideal for data scientists, researchers, and machine learning engineers who need synthetic data for testing, modeling, or experimentation when real data is unavailable or when data privacy is a concern.

test pypi - Documentation Link: https://test.pypi.org/project/synthetic-data-generator/ 

## **Key Features**
- Generate continuous data following a normal distribution.
- Generate categorical data with customizable categories.
- Generate time-series data with specified start dates, frequencies, and durations.
- Create combined datasets with continuous, categorical, and time-series features.
- Optionally add noise to both continuous and categorical data to simulate real-world variability.

## **Installation**

From TestPyPI, install it using:

```bash
pip install --index-url https://test.pypi.org/simple/ synthetic-data-generator
```

In any other case, install it using:

```bash
pip install --extra-index-url https://test.pypi.org/simple/ synthetic-data-generator
```


## **Usage**

The package is user-friendly and can be used to generate synthetic datasets with just a few lines of code. Below is an example that demonstrates how to generate a dataset with continuous, categorical, and time-series data.

### **Example 1: Basic Usage**

```python
from synthetic_data_generator import SyntheticDataGenerator

# Initialize the generator
generator = SyntheticDataGenerator()

# Generate synthetic data with 2 continuous features, 1 categorical feature, and 1000 samples
df = generator.create_synthetic_dataset(continuous_features=2, categorical_features=1, num_samples=1000)
print(df.head())
```

### **Example 2: Including Time-Series Data**

```python
# Create a dataset with 2 continuous features, 1 categorical feature, and a time-series column
df = generator.create_synthetic_dataset(continuous_features=2, categorical_features=1, num_samples=1000, include_time_series=True, start_date='2023-01-01', freq='D')
print(df.head())
```

### **Example 3: Adding Noise to the Data**

To simulate real-world data, you can add noise to both continuous and categorical features.

```python
# Generate synthetic data with noise
df = generator.create_synthetic_dataset(continuous_features=2, categorical_features=1, num_samples=1000)

# Add noise to the dataset
noisy_df = generator.add_noise(df, continuous_noise_level=0.05, categorical_noise_level=0.1)
print(noisy_df.head())
```

## **API Reference**

### **Class: `SyntheticDataGenerator`**

This is the main class of the package responsible for generating synthetic datasets.

#### **Methods:**

1. **`generate_continuous(num_samples=1000, mean=0, std=1)`**
   - Generates continuous data that follows a normal distribution.
   - **Parameters:**
     - `num_samples`: Number of samples to generate (default is 1000).
     - `mean`: The mean of the normal distribution (default is 0).
     - `std`: The standard deviation of the normal distribution (default is 1).
   - **Returns**: A NumPy array of continuous data.

2. **`generate_categorical(num_samples=1000, categories=None)`**
   - Generates categorical data with user-defined categories.
   - **Parameters:**
     - `num_samples`: Number of samples to generate (default is 1000).
     - `categories`: List of categories (default is `['A', 'B', 'C']`).
   - **Returns**: A NumPy array of categorical data.

3. **`generate_time_series(start_date='2022-01-01', periods=1000, freq='D')`**
   - Generates time-series data based on the specified start date and frequency.
   - **Parameters:**
     - `start_date`: The start date for the time-series data (default is `'2022-01-01'`).
     - `periods`: Number of periods to generate (default is 1000).
     - `freq`: Frequency of the time series (default is `'D'` for daily).
   - **Returns**: A Pandas `DatetimeIndex` object.

4. **`create_synthetic_dataset(continuous_features=1, categorical_features=1, num_samples=1000, include_time_series=False, start_date='2022-01-01', periods=None, freq='D')`**
   - Generates a dataset containing continuous, categorical, and optional time-series features.
   - **Parameters:**
     - `continuous_features`: Number of continuous features to generate (default is 1).
     - `categorical_features`: Number of categorical features to generate (default is 1).
     - `num_samples`: Number of samples to generate (default is 1000).
     - `include_time_series`: Whether to include a time-series column (default is `False`).
     - `start_date`: The start date for the time series (only applicable if `include_time_series=True`).
     - `periods`: Number of periods to generate for the time series (defaults to `num_samples`).
     - `freq`: Frequency of the time series (default is `'D'` for daily).
   - **Returns**: A Pandas `DataFrame` with the generated data.

5. **`add_noise(df, continuous_noise_level=0.01, categorical_noise_level=0.01)`**
   - Adds noise to the continuous and categorical features of the dataset.
   - **Parameters:**
     - `df`: The dataset to which noise will be added.
     - `continuous_noise_level`: The intensity of noise added to continuous features (default is `0.01`).
     - `categorical_noise_level`: The proportion of categorical values to replace with random values (default is `0.01`).
   - **Returns**: A noisy version of the input dataset.

## **Development and Contribution**

If you want to contribute to the development of this package, you can set up the development environment and run tests using `pytest`.

### **Installing Development Dependencies**

To install the development dependencies, use the following command:

```bash
pip install synthetic-data-generator[dev]
```

### **Running Tests**

Tests are written using the `unittest` framework. You can run the tests by executing:

```bash
python -m unittest discover tests
```

## **License**

This project is licensed under the MIT License - see the License file for details.

## **Contributing**

Feel free to submit pull requests or report issues on [GitHub](https://github.com/Gouranga-GH/custom_pypi_sdg.git). Contributions are welcome!

## **Author**

- **Gouranga Jha**
- [post.gourang@gmail.com](mailto:youremail@example.com)
- GitHub: [https://github.com/Gouranga-GH](https://github.com/Gouranga-GH)
