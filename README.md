# End-to-end Machine Learning Project with MLflow

<div align="center">

![MLflow](https://img.shields.io/badge/MLflow-Experiment%20Tracking-blue)
![Python](https://img.shields.io/badge/python-3.8+-green)
![License](https://img.shields.io/badge/license-MIT-green)
![Docker](https://img.shields.io/badge/docker-containerized-blue)
![AWS](https://img.shields.io/badge/AWS-EC2-orange)

A comprehensive end-to-end wine quality prediction system built with modern ML operations and cloud deployment practices.

[Features](#features) • [Tech Stack](#tech-stack) • [Quick Start](#quick-start) • [Architecture](#architecture) • [Contributing](#contributing)

</div>

---

## Overview

This project demonstrates a production-grade machine learning pipeline for wine quality prediction. It showcases best practices in ML engineering, including modular code architecture, experiment tracking, containerization, and cloud deployment.

**Key Achievement**: End-to-end wine quality prediction system deployed on AWS EC2 with real-time inference capabilities.

## Features

✨ **Core Features**
- **Modular Data Pipelines**: YAML-based configuration for data ingestion, validation, transformation, and training
- **Experiment Tracking**: MLflow integration for comprehensive experiment monitoring and model comparison
- **Containerization**: Docker support for consistent development and production environments
- **CI/CD Pipeline**: GitHub Actions automated testing and deployment workflows
- **Cloud Deployment**: Integrated AWS EC2 deployment for scalable predictions
- **Real-time API**: Flask-based REST API for model inference
- **Scikit-learn & ElasticNet**: Robust machine learning models for quality prediction

## Tech Stack

### Core Technologies
| Component | Technology |
|-----------|------------|
| **ML Framework** | Scikit-learn, ElasticNet |
| **Backend** | Flask |
| **Database** | MongoDB, SQL |
| **Experiment Tracking** | MLflow |
| **Containerization** | Docker |
| **CI/CD** | GitHub Actions |
| **Cloud Platform** | AWS EC2 |
| **Version Control** | Git/GitHub |

### Languages
- Python 3.8+
- HTML, CSS, JavaScript (Frontend)
- YAML (Configuration)

## Project Structure

```
End-to-end-Machine-Learning-Project-with-MLflow/
├── src/
│   └── mlProject/              # Main project package
│       ├── components/         # ML pipeline components
│       ├── configuration/      # Config management
│       ├── entity/            # Data entities
│       ├── logging/           # Logging setup
│       ├── pipeline/          # ML pipelines
│       └── utils/             # Utility functions
├── config/                     # Configuration files (YAML)
│   ├── config.yaml            # Main configuration
│   └── params.yaml            # Model parameters
├── research/                   # Jupyter notebooks (research & exploration)
├── templates/                  # HTML templates
│   ├── index.html            # Home page
│   └── results.html          # Results page
├── static/                     # Static assets (CSS, JS)
├── tests/                      # Unit tests
├── app.py                      # Flask application entry point
├── main.py                     # Main execution script
├── Dockerfile                  # Container configuration
├── requirements.txt            # Python dependencies
├── setup.py                    # Package setup
├── schema.yaml                 # Data schema definition
└── params.yaml                 # Model hyperparameters
```

## Installation

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Docker (optional, for containerization)
- AWS Account (optional, for cloud deployment)

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone https://github.com/MadanAyyanavara/End-to-end-Machine-Learning-Project-with-MLflow.git
   cd End-to-end-Machine-Learning-Project-with-MLflow
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## Quick Start

### Running the ML Pipeline

1. **Configure parameters** (edit `config/params.yaml`)

2. **Execute the pipeline**
   ```bash
   python main.py
   ```

3. **View experiments in MLflow**
   ```bash
   mlflow ui
   ```
   Navigate to `http://localhost:5000` to view experiment tracking dashboard.

### Running the Flask Application

1. **Start the Flask server**
   ```bash
   python app.py
   ```

2. **Access the web interface**
   - Open `http://localhost:5000` in your browser
   - Enter wine attributes and get quality predictions

### Docker Deployment

1. **Build Docker image**
   ```bash
   docker build -t wine-quality-prediction .
   ```

2. **Run container**
   ```bash
   docker run -p 5000:5000 wine-quality-prediction
   ```

## Architecture

### Pipeline Flow

```
Raw Data → Ingestion → Validation → Transformation → Model Training → Evaluation → Deployment
```

### Components

#### 1. **Data Ingestion**
- Loads wine quality dataset
- Handles data source abstraction

#### 2. **Data Validation**
- Schema validation against `schema.yaml`
- Data quality checks
- Missing value detection

#### 3. **Data Transformation**
- Feature engineering
- Data scaling and normalization
- Train-test split

#### 4. **Model Training**
- ElasticNet model training
- Hyperparameter optimization
- MLflow experiment tracking

#### 5. **Model Evaluation**
- Performance metrics (MAE, MSE, R²)
- Cross-validation
- Model comparison

#### 6. **Deployment**
- Flask API for predictions
- Docker containerization
- AWS EC2 deployment

## Configuration

### params.yaml
Define model hyperparameters:
```yaml
model:
  alpha: 0.1
  l1_ratio: 0.5
  random_state: 42
```

### config.yaml
Configure data paths and pipeline settings:
```yaml
data:
  raw_data_path: data/raw/
  processed_data_path: data/processed/
```

## ML Pipeline Details

### Experiment Tracking with MLflow

All experiments are tracked automatically with:
- Model parameters
- Performance metrics
- Artifact storage
- Model versioning

### Model Performance

The ElasticNet model provides:
- Regularized linear regression
- Feature importance analysis
- Cross-validated metrics

## API Endpoints

### Predict Wine Quality

**POST** `/predict`

Request body:
```json
{
  "features": [7.4, 0.7, 0.0, 1.9, 0.076, 11.0, 34.0, 0.9971, 3.51, 0.56, 9.4]
}
```

Response:
```json
{
  "prediction": 5.2,
  "timestamp": "2024-02-05T16:00:00",
  "model_version": "v1.0"
}
```

## AWS Deployment

### Steps

1. **Create EC2 instance** with appropriate security groups
2. **Configure environment variables** for AWS credentials
3. **Deploy using GitHub Actions** CI/CD pipeline
4. **Access API** via EC2 public IP address

## Development Workflow

### Making Changes

1. Create a feature branch
   ```bash
   git checkout -b feature/your-feature
   ```

2. Make changes and test
   ```bash
   pytest tests/
   ```

3. Commit and push
   ```bash
   git commit -m "Add feature description"
   git push origin feature/your-feature
   ```

4. Create Pull Request on GitHub

## Testing

Run unit tests:
```bash
pytest tests/ -v
```

With coverage:
```bash
pytest tests/ --cov=src/
```

## Performance Metrics

### Model Evaluation Metrics
- **Mean Absolute Error (MAE)**: Measures average prediction error
- **Mean Squared Error (MSE)**: Penalizes larger errors
- **R² Score**: Measures model fit quality

## Best Practices Implemented

✅ **Code Organization**
- Modular architecture
- Separation of concerns
- Configuration-driven pipeline

✅ **ML Operations**
- Experiment tracking
- Model versioning
- Reproducible pipelines

✅ **DevOps**
- Containerization (Docker)
- CI/CD automation (GitHub Actions)
- Cloud deployment (AWS)

✅ **Code Quality**
- Version control (Git)
- Documentation
- Logging and monitoring

## Troubleshooting

### Common Issues

**Issue**: `ModuleNotFoundError` when running `main.py`
- **Solution**: Ensure virtual environment is activated and dependencies are installed

**Issue**: MLflow UI not accessible
- **Solution**: Check if port 5000 is available and MLflow server is running

**Issue**: Docker build fails
- **Solution**: Verify Dockerfile syntax and all dependencies are in requirements.txt

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/improvement`)
3. Commit changes (`git commit -m 'Add improvement'`)
4. Push to branch (`git push origin feature/improvement`)
5. Open a Pull Request

### Guidelines
- Follow PEP 8 coding standards
- Add tests for new features
- Update documentation
- Write clear commit messages

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Madan Ayyanavara**
- GitHub: [@MadanAyyanavara](https://github.com/MadanAyyanavara)
- LinkedIn: [Profile](#)

## Acknowledgments

- Scikit-learn and ElasticNet for robust ML models
- MLflow for comprehensive experiment tracking
- Flask for lightweight web framework
- AWS for scalable cloud infrastructure
- GitHub for version control and CI/CD

## Support

For questions or issues:
- Open an [Issue](https://github.com/MadanAyyanavara/End-to-end-Machine-Learning-Project-with-MLflow/issues)
- Check [Discussions](https://github.com/MadanAyyanavara/End-to-end-Machine-Learning-Project-with-MLflow/discussions)
- Review existing [Documentation](#)

---

<div align="center">

**[↑ Back to top](#end-to-end-machine-learning-project-with-mlflow)**



</div>
