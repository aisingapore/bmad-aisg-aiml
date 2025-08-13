# AI/ML Development Guidelines

## Overview

This document establishes coding standards, architectural patterns, and development practices for AI/ML engineering projects. These guidelines ensure consistency, reproducibility, and maintainability across all machine learning development stories.

## Python Standards

### Naming Conventions

**Modules and Packages:**
- Use lowercase with underscores: `data_preprocessing.py`, `model_training.py`
- Descriptive names that indicate purpose: `feature_engineering.py` not `fe.py`

**Classes:**
- PascalCase for classes: `ModelTrainer`, `DataPipeline`, `FeatureExtractor`
- Suffix with type when appropriate: `*Pipeline`, `*Transformer`, `*Model`

**Functions and Variables:**
- snake_case for functions: `train_model()`, `evaluate_performance()`
- snake_case for variables: `learning_rate`, `batch_size`, `model_config`
- Descriptive names: `cross_val_score` not `cvs`

**Constants:**
- UPPER_SNAKE_CASE: `MAX_EPOCHS`, `DEFAULT_BATCH_SIZE`, `MODEL_VERSION`

### Code Organization

```python
# Standard import order
import os
import sys
from pathlib import Path

import numpy as np
import pandas as pd
import torch
from sklearn.model_selection import train_test_split

from src.models import CustomModel
from src.utils import load_config
```

### Type Hints and Documentation

```python
from typing import Tuple, Dict, List, Optional
import pandas as pd
import numpy as np

def preprocess_data(
    df: pd.DataFrame,
    target_column: str,
    test_size: float = 0.2,
    random_state: Optional[int] = 42
) -> Tuple[np.ndarray, np.ndarray, np.ndarray, np.ndarray]:
    """
    Preprocess data for model training.
    
    Args:
        df: Input dataframe
        target_column: Name of target column
        test_size: Proportion of data for testing
        random_state: Random seed for reproducibility
        
    Returns:
        Tuple of (X_train, X_test, y_train, y_test)
    """
    X = df.drop(columns=[target_column])
    y = df[target_column]
    return train_test_split(X, y, test_size=test_size, random_state=random_state)
```

## ML Architecture Patterns

### Project Structure

```
ml-project/
├── configs/
│   ├── model_config.yaml
│   └── training_config.yaml
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
├── models/
│   ├── checkpoints/
│   └── production/
├── notebooks/
│   ├── 01_eda.ipynb
│   └── 02_modeling.ipynb
├── src/
│   ├── __init__.py
│   ├── data/
│   │   ├── __init__.py
│   │   ├── loader.py
│   │   └── preprocessor.py
│   ├── features/
│   │   ├── __init__.py
│   │   └── engineering.py
│   ├── models/
│   │   ├── __init__.py
│   │   ├── base.py
│   │   └── custom_model.py
│   ├── training/
│   │   ├── __init__.py
│   │   ├── trainer.py
│   │   └── evaluator.py
│   └── serving/
│       ├── __init__.py
│       └── predictor.py
├── tests/
│   ├── test_data.py
│   ├── test_models.py
│   └── test_features.py
├── scripts/
│   ├── train.py
│   └── evaluate.py
├── requirements.txt
├── setup.py
└── README.md
```

### Data Pipeline Pattern

```python
from abc import ABC, abstractmethod
import pandas as pd

class DataPipeline(ABC):
    """Abstract base class for data pipelines."""
    
    @abstractmethod
    def load(self) -> pd.DataFrame:
        """Load raw data."""
        pass
    
    @abstractmethod
    def clean(self, df: pd.DataFrame) -> pd.DataFrame:
        """Clean data."""
        pass
    
    @abstractmethod
    def transform(self, df: pd.DataFrame) -> pd.DataFrame:
        """Transform features."""
        pass
    
    def run(self) -> pd.DataFrame:
        """Execute complete pipeline."""
        df = self.load()
        df = self.clean(df)
        df = self.transform(df)
        return df

class CustomDataPipeline(DataPipeline):
    """Implementation of data pipeline for specific use case."""
    
    def load(self) -> pd.DataFrame:
        return pd.read_csv("data/raw/dataset.csv")
    
    def clean(self, df: pd.DataFrame) -> pd.DataFrame:
        # Remove nulls, outliers, etc.
        return df.dropna()
    
    def transform(self, df: pd.DataFrame) -> pd.DataFrame:
        # Feature engineering
        return df
```

### Model Training Pattern

```python
import mlflow
from typing import Dict, Any
import joblib

class ModelTrainer:
    """Handles model training with experiment tracking."""
    
    def __init__(self, model_config: Dict[str, Any]):
        self.model_config = model_config
        self.model = None
        
    def train(self, X_train, y_train, X_val, y_val):
        """Train model with MLflow tracking."""
        with mlflow.start_run():
            # Log parameters
            mlflow.log_params(self.model_config)
            
            # Train model
            self.model = self._create_model()
            self.model.fit(X_train, y_train)
            
            # Evaluate
            train_score = self.model.score(X_train, y_train)
            val_score = self.model.score(X_val, y_val)
            
            # Log metrics
            mlflow.log_metrics({
                "train_score": train_score,
                "val_score": val_score
            })
            
            # Save model
            mlflow.sklearn.log_model(self.model, "model")
            
        return self.model
    
    def _create_model(self):
        """Create model instance based on config."""
        # Model creation logic
        pass
```

## MLOps Standards

### Reproducibility Requirements

```python
# Always set random seeds
import random
import numpy as np
import torch

def set_seeds(seed: int = 42):
    """Set seeds for reproducibility."""
    random.seed(seed)
    np.random.seed(seed)
    torch.manual_seed(seed)
    if torch.cuda.is_available():
        torch.cuda.manual_seed(seed)
        torch.cuda.manual_seed_all(seed)
```

### Configuration Management

```yaml
# config.yaml
model:
  name: "xgboost"
  version: "1.0.0"
  parameters:
    n_estimators: 100
    max_depth: 5
    learning_rate: 0.1
    
training:
  batch_size: 32
  epochs: 100
  early_stopping_rounds: 10
  validation_split: 0.2
  
data:
  input_path: "data/processed/features.parquet"
  target_column: "target"
  feature_columns: ["feature1", "feature2", "feature3"]
```

### Pipeline Automation

```python
# CI/CD Pipeline Script
from pathlib import Path
import yaml
import mlflow

class MLPipeline:
    """Automated ML pipeline for training and deployment."""
    
    def __init__(self, config_path: str):
        with open(config_path, 'r') as f:
            self.config = yaml.safe_load(f)
    
    def run(self):
        """Execute complete ML pipeline."""
        # Data preparation
        data = self.prepare_data()
        
        # Model training
        model = self.train_model(data)
        
        # Model validation
        metrics = self.validate_model(model, data)
        
        # Deployment decision
        if self.should_deploy(metrics):
            self.deploy_model(model)
            
    def prepare_data(self):
        """Data preparation stage."""
        pass
        
    def train_model(self, data):
        """Model training stage."""
        pass
        
    def validate_model(self, model, data):
        """Model validation stage."""
        pass
        
    def should_deploy(self, metrics):
        """Deployment decision logic."""
        return metrics['accuracy'] > self.config['deployment']['min_accuracy']
        
    def deploy_model(self, model):
        """Model deployment stage."""
        pass
```

## Model Serving

### REST API Pattern

```python
from fastapi import FastAPI, HTTPException
from pydantic import BaseModel
import joblib
import numpy as np

app = FastAPI(title="ML Model API", version="1.0.0")

# Load model at startup
model = joblib.load("models/production/model.pkl")

class PredictionRequest(BaseModel):
    features: List[float]
    
class PredictionResponse(BaseModel):
    prediction: float
    confidence: float

@app.post("/predict", response_model=PredictionResponse)
async def predict(request: PredictionRequest):
    """Generate prediction from model."""
    try:
        # Prepare input
        X = np.array(request.features).reshape(1, -1)
        
        # Generate prediction
        prediction = model.predict(X)[0]
        confidence = model.predict_proba(X).max()
        
        return PredictionResponse(
            prediction=prediction,
            confidence=confidence
        )
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))

@app.get("/health")
async def health():
    """Health check endpoint."""
    return {"status": "healthy"}
```

### Batch Processing Pattern

```python
import pandas as pd
from typing import List
import asyncio

class BatchPredictor:
    """Handle batch predictions efficiently."""
    
    def __init__(self, model, batch_size: int = 100):
        self.model = model
        self.batch_size = batch_size
    
    async def predict_batch(self, data: pd.DataFrame) -> List[float]:
        """Process predictions in batches."""
        predictions = []
        
        for i in range(0, len(data), self.batch_size):
            batch = data.iloc[i:i+self.batch_size]
            batch_predictions = await self._predict_async(batch)
            predictions.extend(batch_predictions)
            
        return predictions
    
    async def _predict_async(self, batch: pd.DataFrame) -> List[float]:
        """Async prediction for a single batch."""
        # Simulate async operation
        await asyncio.sleep(0.01)
        return self.model.predict(batch).tolist()
```

## Testing Standards

### Unit Testing

```python
import pytest
import numpy as np
from src.features.engineering import FeatureEngineer

class TestFeatureEngineering:
    """Test feature engineering functions."""
    
    @pytest.fixture
    def sample_data(self):
        """Create sample data for testing."""
        return pd.DataFrame({
            'feature1': [1, 2, 3, 4, 5],
            'feature2': [10, 20, 30, 40, 50],
            'target': [0, 1, 0, 1, 0]
        })
    
    def test_feature_scaling(self, sample_data):
        """Test feature scaling."""
        engineer = FeatureEngineer()
        scaled_data = engineer.scale_features(sample_data)
        
        assert scaled_data['feature1'].mean() == pytest.approx(0, abs=1e-10)
        assert scaled_data['feature1'].std() == pytest.approx(1, abs=1e-10)
    
    def test_feature_creation(self, sample_data):
        """Test new feature creation."""
        engineer = FeatureEngineer()
        enhanced_data = engineer.create_features(sample_data)
        
        assert 'feature1_squared' in enhanced_data.columns
        assert len(enhanced_data) == len(sample_data)
```

### Integration Testing

```python
import pytest
from fastapi.testclient import TestClient
from src.serving.api import app

class TestModelAPI:
    """Test model serving API."""
    
    @pytest.fixture
    def client(self):
        """Create test client."""
        return TestClient(app)
    
    def test_prediction_endpoint(self, client):
        """Test prediction endpoint."""
        response = client.post(
            "/predict",
            json={"features": [1.0, 2.0, 3.0]}
        )
        assert response.status_code == 200
        assert "prediction" in response.json()
        assert "confidence" in response.json()
    
    def test_health_endpoint(self, client):
        """Test health check endpoint."""
        response = client.get("/health")
        assert response.status_code == 200
        assert response.json()["status"] == "healthy"
```

### Model Testing

```python
import numpy as np
from sklearn.metrics import accuracy_score, precision_score, recall_score

class ModelValidator:
    """Validate model performance."""
    
    def __init__(self, model, X_test, y_test):
        self.model = model
        self.X_test = X_test
        self.y_test = y_test
    
    def validate_performance(self, min_accuracy: float = 0.8):
        """Validate model meets performance criteria."""
        predictions = self.model.predict(self.X_test)
        
        metrics = {
            'accuracy': accuracy_score(self.y_test, predictions),
            'precision': precision_score(self.y_test, predictions, average='weighted'),
            'recall': recall_score(self.y_test, predictions, average='weighted')
        }
        
        assert metrics['accuracy'] >= min_accuracy, f"Accuracy {metrics['accuracy']} below threshold"
        return metrics
    
    def test_edge_cases(self):
        """Test model on edge cases."""
        # Test with all zeros
        zeros = np.zeros((1, self.X_test.shape[1]))
        prediction = self.model.predict(zeros)
        assert prediction is not None
        
        # Test with very large values
        large_values = np.ones((1, self.X_test.shape[1])) * 1e6
        prediction = self.model.predict(large_values)
        assert prediction is not None
```

## Monitoring and Logging

### Model Monitoring

```python
from prometheus_client import Counter, Histogram, Gauge
import time

# Metrics
prediction_counter = Counter('model_predictions_total', 'Total predictions')
prediction_latency = Histogram('model_prediction_duration_seconds', 'Prediction latency')
model_accuracy = Gauge('model_accuracy', 'Current model accuracy')

class ModelMonitor:
    """Monitor model performance in production."""
    
    def track_prediction(self, func):
        """Decorator to track predictions."""
        def wrapper(*args, **kwargs):
            start_time = time.time()
            
            try:
                result = func(*args, **kwargs)
                prediction_counter.inc()
                return result
            finally:
                prediction_latency.observe(time.time() - start_time)
                
        return wrapper
    
    def update_accuracy(self, accuracy: float):
        """Update accuracy metric."""
        model_accuracy.set(accuracy)
```

### Structured Logging

```python
import logging
import json
from datetime import datetime

class StructuredLogger:
    """Structured logging for ML systems."""
    
    def __init__(self, name: str):
        self.logger = logging.getLogger(name)
        handler = logging.StreamHandler()
        handler.setFormatter(self.JsonFormatter())
        self.logger.addHandler(handler)
        self.logger.setLevel(logging.INFO)
    
    class JsonFormatter(logging.Formatter):
        """Format logs as JSON."""
        
        def format(self, record):
            log_obj = {
                'timestamp': datetime.utcnow().isoformat(),
                'level': record.levelname,
                'message': record.getMessage(),
                'module': record.module,
                'function': record.funcName,
                'line': record.lineno
            }
            return json.dumps(log_obj)
    
    def log_prediction(self, input_data, prediction, confidence):
        """Log prediction details."""
        self.logger.info("Prediction made", extra={
            'input_shape': str(input_data.shape),
            'prediction': prediction,
            'confidence': confidence
        })
```

## Security and Ethics

### Data Privacy

```python
import hashlib
from typing import Any

class DataPrivacy:
    """Handle data privacy requirements."""
    
    @staticmethod
    def anonymize_pii(data: pd.DataFrame, pii_columns: List[str]) -> pd.DataFrame:
        """Anonymize personally identifiable information."""
        data_copy = data.copy()
        
        for col in pii_columns:
            if col in data_copy.columns:
                data_copy[col] = data_copy[col].apply(
                    lambda x: hashlib.sha256(str(x).encode()).hexdigest()[:8]
                )
        
        return data_copy
    
    @staticmethod
    def remove_sensitive_features(data: pd.DataFrame, 
                                 sensitive_columns: List[str]) -> pd.DataFrame:
        """Remove sensitive features from dataset."""
        return data.drop(columns=sensitive_columns, errors='ignore')
```

### Bias Detection

```python
from fairlearn.metrics import MetricFrame
from sklearn.metrics import accuracy_score

class BiasDetector:
    """Detect and measure bias in model predictions."""
    
    def __init__(self, model):
        self.model = model
    
    def check_demographic_parity(self, X_test, y_test, sensitive_features):
        """Check for demographic parity."""
        predictions = self.model.predict(X_test)
        
        metric_frame = MetricFrame(
            metrics=accuracy_score,
            y_true=y_test,
            y_pred=predictions,
            sensitive_features=sensitive_features
        )
        
        disparity = metric_frame.difference()
        
        if disparity > 0.1:  # Threshold for acceptable disparity
            raise Warning(f"High disparity detected: {disparity}")
            
        return metric_frame
```

### Model Security

```python
import numpy as np

class AdversarialDefense:
    """Defend against adversarial attacks."""
    
    @staticmethod
    def input_validation(input_data: np.ndarray) -> bool:
        """Validate input is within expected bounds."""
        # Check for NaN or Inf
        if np.any(np.isnan(input_data)) or np.any(np.isinf(input_data)):
            return False
            
        # Check value ranges
        if np.any(np.abs(input_data) > 1e6):  # Adjust threshold as needed
            return False
            
        return True
    
    @staticmethod
    def add_noise_defense(predictions: np.ndarray, epsilon: float = 0.01):
        """Add noise to predictions for differential privacy."""
        noise = np.random.laplace(0, epsilon, predictions.shape)
        return predictions + noise
```

## Performance Optimization

### Memory Management

```python
import gc
import psutil

class MemoryManager:
    """Manage memory usage in ML pipelines."""
    
    @staticmethod
    def optimize_dataframe(df: pd.DataFrame) -> pd.DataFrame:
        """Optimize dataframe memory usage."""
        for col in df.columns:
            col_type = df[col].dtype
            
            if col_type != 'object':
                c_min = df[col].min()
                c_max = df[col].max()
                
                if str(col_type)[:3] == 'int':
                    if c_min > np.iinfo(np.int8).min and c_max < np.iinfo(np.int8).max:
                        df[col] = df[col].astype(np.int8)
                    elif c_min > np.iinfo(np.int16).min and c_max < np.iinfo(np.int16).max:
                        df[col] = df[col].astype(np.int16)
                    elif c_min > np.iinfo(np.int32).min and c_max < np.iinfo(np.int32).max:
                        df[col] = df[col].astype(np.int32)
                else:
                    if c_min > np.finfo(np.float16).min and c_max < np.finfo(np.float16).max:
                        df[col] = df[col].astype(np.float16)
                    elif c_min > np.finfo(np.float32).min and c_max < np.finfo(np.float32).max:
                        df[col] = df[col].astype(np.float32)
        
        return df
    
    @staticmethod
    def clear_memory():
        """Clear memory and run garbage collection."""
        gc.collect()
        
    @staticmethod
    def get_memory_usage():
        """Get current memory usage."""
        process = psutil.Process()
        return process.memory_info().rss / 1024 / 1024  # MB
```

### Computation Optimization

```python
import numba
from joblib import Parallel, delayed

class ComputeOptimizer:
    """Optimize computational performance."""
    
    @staticmethod
    @numba.jit(nopython=True)
    def fast_distance_calculation(x1: np.ndarray, x2: np.ndarray) -> float:
        """JIT-compiled distance calculation."""
        return np.sqrt(np.sum((x1 - x2) ** 2))
    
    @staticmethod
    def parallel_processing(func, items, n_jobs=-1):
        """Process items in parallel."""
        results = Parallel(n_jobs=n_jobs)(
            delayed(func)(item) for item in items
        )
        return results
```

## Development Workflow

### Story Implementation Process

1. **Understand Requirements:**
   - Review acceptance criteria
   - Identify data requirements
   - Define success metrics

2. **Design Solution:**
   - Select appropriate algorithms
   - Design data pipeline
   - Plan experiments

3. **Implement:**
   - Write clean, documented code
   - Follow established patterns
   - Implement tests

4. **Validate:**
   - Run unit and integration tests
   - Validate model performance
   - Check for bias and fairness

5. **Deploy:**
   - Package model for deployment
   - Set up monitoring
   - Document deployment process

### Code Review Checklist

- [ ] Code follows Python style guidelines
- [ ] All functions have type hints and docstrings
- [ ] Unit tests cover critical functionality
- [ ] Model performance meets requirements
- [ ] No sensitive data exposed
- [ ] Reproducibility ensured (seeds, versions)
- [ ] Memory and compute optimized
- [ ] Monitoring and logging implemented
- [ ] Documentation updated

## Performance Requirements

### Model Performance

- **Training Time**: Reasonable for dataset size
- **Inference Latency**: <100ms for real-time, <1s for batch
- **Memory Usage**: Within deployment environment limits
- **Accuracy**: Meets business requirements

### System Performance

- **API Response Time**: p99 < 500ms
- **Throughput**: Handle expected load + 50%
- **Availability**: 99.9% uptime
- **Data Processing**: Linear scaling with data size

These guidelines ensure consistent, high-quality ML engineering that meets production requirements and maintains code quality across all implementation stories.