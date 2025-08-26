# House Price Prediction API

## Overview
This project implements a RESTful API using FastAPI for house price prediction and item management. It combines machine learning capabilities with CRUD operations, using SQLAlchemy for database management and a pre-trained linear regression model for predictions.

## Project Structure
```
.
├── app_3.py              # Main application file
├── linear_regression.joblib    # Trained model
├── selected_features.csv       # Feature list for predictions
├── requirements.txt           # Project dependencies
└── .env                      # Environment variables
```

## Features
- House price prediction using machine learning
- CRUD operations for items management
- Database integration with SQLAlchemy
- Pagination and search functionality
- Health check endpoint
- Automatic API documentation

## Technical Stack
- **Framework:** FastAPI
- **Database:** SQLAlchemy
- **ML Model:** Scikit-learn (Linear Regression)
- **Data Processing:** Pandas
- **File Handling:** Python IO
- **Time Management:** pytz

## API Endpoints

### Health Check
```http
GET /health
```
Verifies API health status

### Items Management

#### Create Item
```http
POST /items/
```
Creates a new item with name and description

#### Read Item
```http
GET /items/{item_id}
```
Retrieves a specific item by ID

#### Update Item
```http
PUT /items/{item_id}
```
Updates an existing item

#### Delete Item
```http
DELETE /items/{item_id}
```
Removes an item by ID

#### List Items
```http
GET /items/?skip=0&limit=10
```
Lists items with pagination support

#### Search Items
```http
GET /items/search/{query}
```
Searches items by name

### Predictions
```http
POST /predict
```
Accepts CSV file for house price predictions

## Data Models

### Item
```python
{
    "id": int,
    "name": str,
    "description": str (optional)
}
```

## Setup Instructions

1. Clone the repository
2. Create a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Mac/Linux
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Set up environment variables:
```bash
export SQLALCHEMY_DATABASE_URL="your_database_url"
```

5. Run the application:
```bash
uvicorn app_3:app --reload
```

## Making Predictions

1. Prepare a CSV file with the required features (see selected_features.csv)
2. Send a POST request to `/predict` with the CSV file
3. Receive predictions in JSON format
4. Results are automatically stored in the predictions table

## Database Schema

### Items Table
- id (Primary Key)
- name
- description

### Predictions Table
- file_name
- prediction
- created_at

## Error Handling
- 404: Resource not found
- 400: Bad request
- 500: Internal server error

## Development

### Running Tests
```bash
pytest tests/
```

### Code Style
Follow PEP 8 guidelines for Python code style

## Environment Variables
Required environment variables:
- `SQLALCHEMY_DATABASE_URL`: Database connection string

## API Documentation
Once running, access the automatic API documentation at:
- Swagger UI: `http://localhost:8000/docs`
- ReDoc: `http://localhost:8000/redoc`

## Contributing
1. Fork the repository
2. Create a feature branch
3. Commit changes
4. Push to the branch
5. Create a Pull Request

## Authors
Carlos Sánchez

---

For more information or support, please open an issue in the repository.