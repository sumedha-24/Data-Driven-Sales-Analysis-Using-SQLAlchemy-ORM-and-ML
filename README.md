# Data-Driven-Sales-Analysis-Using-SQLAlchemy-ORM-and-ML

A containerized project built using SQLAlchemy, Flask, and Docker for sales data analysis and gross income prediction in a supermarket setting.

## Overview

This project uses SQLAlchemy ORM to interact with a relational database of supermarket sales. It supports:
- Exploratory data analysis with visualizations (via Matplotlib)
- A Flask API for gross income prediction
- Dockerized deployment of the full pipeline

## Technologies Used

### **SQLAlchemy ORM**
- Object-Relational Mapping for database interactions
- Simplifies querying using Python objects

### **Matplotlib**
- Used for static and interactive data visualizations

### **Flask**
- Lightweight Python web framework
- Hosts a prediction API and web interface

### **Docker**
- Containerization of the app, MySQL DB, and Jupyter Notebook
- Ensures consistency and scalability

## Docker Implementation

**Project Includes:**
- `sales.ipynb`: SQLAlchemy-based notebook for EDA
- `Dockerfile`: App container configuration
- `docker-compose.yaml`: Service orchestration

### Dockerfile Highlights:
- Python 3.11.7 image
- Installs dependencies (e.g., `sqlalchemy`, `mysql-connector-python`)
- Exposes ports for Jupyter (8888) and Flask app (8082)

### Docker Compose Setup:
```yaml
services:
  mysql:
    build:
      context: .
      dockerfile: Dockerfile.mysql
    ports:
      - "3306:3306"
  jupyter:
    build:
      context: .
      dockerfile: Dockerfile.J
    ports:
      - "8888:8888"
    volumes:
      - ./notebooks:/app/notebooks
  flask:
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "8082:8082"
    depends_on:
      - mysql
```

### Running the Project:
```bash
docker-compose up --build
```

Visit:
- Jupyter Notebook: `http://localhost:8888/`
- Flask API: `http://localhost:8082/`

## Project Components

### **Jupyter Notebook (sales_analysis.ipynb):**
- SQLAlchemy ORM-based data loading
- Matplotlib visualizations
- EDA, preprocessing, and model training

### **Flask App (app.py):**
- Hosts ML model to predict gross sales
- Accepts inputs via HTML form
- Returns predictions through a simple UI

## Setup Instructions

1. **Clone the Repository**
```bash
git clone https://github.com/Sumedha-24/supermarket-sales-prediction.git
cd supermarket-sales-prediction
```

2. **Install Required Python Packages**
Make sure you have Python 3.11+ installed.

```bash
pip install -r requirements.txt
```

3. **Run with Docker (Recommended)**
```bash
docker-compose up --build
```

4. **Access the Interfaces**
- Jupyter Notebook: [http://localhost:8888](http://localhost:8888)
- Flask App: [http://localhost:8082](http://localhost:8082)

> Make sure Docker Desktop is running before executing the above commands.

## References

- Dataset: [Kaggle Supermarket Sales](https://www.kaggle.com/datasets/lovishbansal123/sales-of-a-supermarket)
- SQLAlchemy Docs: [ORM Tutorial](https://docs.sqlalchemy.org/en/20/tutorial/orm_data_manipulation.html)
- Flask Docs: [Flask Web Framework](https://flask.palletsprojects.com/)

**Author:** Sumedha Vadlamani  
**GitHub:** [sumedha-24](https://github.com/sumedha-24)  
**Email:** sumedha6@terpmail.umd.edu

