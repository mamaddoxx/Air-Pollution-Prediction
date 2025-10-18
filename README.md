# 🌫️ Air Pollution Prediction using Deep Learning

A comprehensive deep learning project that predicts PM2.5 air pollution levels in Beijing using CNN-LSTM neural networks. This project implements a sophisticated time series prediction model based on the research paper "Air pollution prediction in smart city, deep learning approach."

## 📊 Project Overview

This project analyzes air quality data from 12 monitoring stations across Beijing and builds a predictive model to forecast PM2.5 concentrations. The model uses a hybrid CNN-LSTM architecture that captures both spatial and temporal patterns in air pollution data.

## 🎯 Key Features

- **Multi-station Analysis**: Data from 12 Beijing air quality monitoring stations
- **Advanced Preprocessing**: Time-aware interpolation and wind direction encoding
- **Hybrid CNN-LSTM Model**: Combines Convolutional and LSTM layers for optimal performance
- **Comprehensive Evaluation**: MAE, RMSE, and R² metrics with visualization
- **Feature Engineering**: Spatial correlation analysis and meteorological feature integration

## 📈 Model Performance

| Model Configuration | MAE | RMSE | R² |
|-------------------|-----|------|-----|
| 24-hour lookback | ~6.74 | ~12.92 | ~0.989 |
| 168-hour lookback | ~9.03 | ~16.63 | ~0.979 |

## 🗂️ Project Structure

```
Air-Pollution-Prediction/
├── 📓 Air-Pollution Prediction in Benjing.ipynb  # Main analysis notebook
├── 📄 Air_pollution_prediction_in_smart_city,_deep_learning_approach.pdf  # Research paper
├── 📁 dataset/                                    # Raw data files
│   ├── PRSA_Data_Aotizhongxin_20130301-20170228.csv
│   ├── PRSA_Data_Changping_20130301-20170228.csv
│   └── ... (10 more station files)
├── 📁 data/processed/                             # Processed features
│   └── Aotizhongxin_features.xlsx
├── 📁 outputs/models/                             # Trained models and results
│   ├── cnn_lstm_lb24_bs32.keras                  # 24h lookback model
│   ├── cnn_lstm_lb168_bs32.keras                 # 168h lookback model
│   ├── metrics_lb24_bs32.json                     # Performance metrics
│   ├── metrics_lb168_bs32.json                    # Performance metrics
│   ├── Lag1-Day.png                              # Prediction visualization
│   └── Lag7-Day.png                              # Prediction visualization
└── 📄 README.md                                   # This file
```

## 🚀 Quick Start

### Prerequisites

```bash
pip install pandas numpy matplotlib scikit-learn tensorflow
```

### Running the Analysis

1. **Open the Jupyter Notebook**:
   ```bash
   jupyter notebook "Air-Pollution Prediction in Benjing.ipynb"
   ```

2. **Run All Cells**: Execute the notebook cells sequentially to:
   - Load and preprocess the data
   - Perform exploratory data analysis
   - Train the CNN-LSTM models
   - Evaluate model performance
   - Generate prediction visualizations

## 🔬 Technical Details

### Data Preprocessing
- **Missing Value Handling**: Time-aware linear interpolation per station
- **Wind Direction Encoding**: 16-point compass converted to azimuth degrees
- **Normalization**: Min-Max scaling to [0,1] range
- **Feature Engineering**: Spatial correlation analysis across stations

### Model Architecture
```
Input Layer → Conv1D(64) → BatchNorm → Conv1D(64) → BatchNorm → 
Conv1D(32) → MaxPool1D(3) → LSTM(100) → Dropout(0.1) → 
LSTM(50) → Dropout(0.1) → Dense(1)
```

### Training Configuration
- **Optimizer**: Adam (lr=1e-3, decay=1e-4)
- **Loss Function**: Mean Squared Error
- **Callbacks**: EarlyStopping, ModelCheckpoint
- **Train/Test Split**: 80%/20% chronological split

## 📊 Dataset Information

**Source**: UCI Beijing Multi-Site Air-Quality Dataset
**Period**: March 2013 - February 2017
**Frequency**: Hourly measurements
**Stations**: 12 monitoring stations across Beijing
**Features**: PM2.5, PM10, SO2, NO2, CO, O3, Temperature, Pressure, Dew Point, Rain, Wind Direction, Wind Speed

## 🎨 Visualizations

The project includes comprehensive visualizations:
- **Missing Data Heatmaps**: Station-wise data completeness analysis
- **Correlation Matrices**: Feature and spatial correlation analysis
- **Prediction Plots**: Time series comparison of predictions vs actual values
- **Data Quality Analysis**: Temporal patterns in data availability

## 🔧 Model Files

- **`cnn_lstm_lb24_bs32.keras`**: Model trained with 24-hour lookback window
- **`cnn_lstm_lb168_bs32.keras`**: Model trained with 168-hour (7-day) lookback window
- **`metrics_lb24_bs32.json`**: Performance metrics for 24h model
- **`metrics_lb168_bs32.json`**: Performance metrics for 168h model

## 📚 Research Background

This project is based on the research paper "Air pollution prediction in smart city, deep learning approach" and implements the CNN-LSTM architecture described in the paper for predicting PM2.5 concentrations in Beijing.

## 🤝 Contributing

Contributions are welcome! Please feel free to:
- Report bugs or issues
- Suggest improvements to the model architecture
- Add new visualization features
- Improve data preprocessing techniques

## 📄 License

This project is open source and available under the MIT License.

## 👨‍💻 Author

**Mohammad** - Air Pollution Prediction Project

## 🙏 Acknowledgments

- UCI Machine Learning Repository for the Beijing Air Quality dataset
- The authors of "Air pollution prediction in smart city, deep learning approach"
- TensorFlow and Keras communities for excellent deep learning frameworks

---

**Note**: This project demonstrates the application of deep learning techniques to environmental monitoring and air quality prediction, contributing to smart city initiatives and public health awareness.
