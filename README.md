# Insurance Premium Prediction - FastAPI & Streamlit

This repository demonstrates the deployment of a Machine Learning model for predicting health insurance premiums. The backend is built with FastAPI and containerized using Docker, then deployed on AWS. A Streamlit frontend is provided for user interaction.

---

## Features

- **ML Model**: Predicts health insurance premium based on user input.
- **Backend**: FastAPI, containerized with Docker, deployed on AWS.
- **Frontend**: Streamlit app for easy user interaction.
- **API Documentation**: Swagger UI via FastAPI.

---

## URLs

- **Streamlit Frontend**: [https://your-streamlit-app-url](https://health-insure-prem-api.streamlit.app)
- **FastAPI Docs**: ~~[https://your-aws-backend-url/docs](http://44.203.74.123:8000/docs)~~ # Deleted EC2 instance
- **FastAPI Docs (Updated link)**: [https://updated-render-link/docs](https://health-insurance-premium-api-latest.onrender.com/docs)  # Deployed on Render through docker registry

---

## Getting Started

### 1. Clone the Repository

```bash
git clone [git@github.com:niweshbaraj/docker-aws-fastapi-health-prem.git](https://github.com/niweshbaraj/docker-aws-fastapi-health-prem.git)
cd docker-aws-fastapi-health-prem
```

### 2. Build Docker Image

```bash
docker build -t health-insurance-premium-api . 
```

### 3. Run Docker Container Locally

```bash
docker run -d -p 8000:8000 health-insurance-premium-api
```

### 4. Steps to deploy on AWS

- create an EC2 instance on AWS.
- Connect to the EC2 instance (Terminal).
- Run the following commands.
  - sudo apt-get update
  - sudo apt-get install -y docker.io
  - sudo systemctl start docker
  - sudo systemctl enable docker
  - sudo usermod -aG docker $USER
  - exit 
- Restart a new connection to EC2 instance.
- Run the following commands:
  - docker pull niweshbaraj/health-insurance-premium-api:latest
  - docker run -p 8000:8000 niweshbaraj/health-insurance-premium-api:latest
- change security group settings to expose port 8000 for this EC2 instance.

### 5. Access FastAPI Docs

Visit: `http://[your-localhost-url](http://localhost:8000/docs)`

---

## Running the Streamlit App

1. Install dependencies:

    ```bash
    pip install streamlit requests (for running locally)
    ```

2. Run the Streamlit app:

    ```bash
    streamlit run frontend.py
    ```

3. Access the app at: [http://localhost:8501](http://localhost:8501) or the deployed URL.

---

## Example API Usage

```bash
curl -X 'POST' \
  'http://localhost:8000/predict' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "age": 21,
  "weight": 51,
  "height": 1.72,
  "income_lpa": 8,
  "smoker": true,
  "city": "Delhi",
  "occupation": "retired"
}'
```

---
