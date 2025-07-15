# Text-Summarizer

This is a full-stack NLP project focused on **text summarization** using Transformer-based models like **Google Pegasus**, implemented using modular Python scripts, trained on custom data, and deployed with Docker + AWS. It includes CI/CD automation via GitHub Actions and emphasizes best practices such as configuration-driven design, object-oriented structure, and logging.

## Overview

With this project, I learned how to:

- Build a text summarizer using Hugging Face models
- Organize and manage code using OOP and modular structure
- Automate end-to-end ML workflows with configuration files
- Train and evaluate summarization models (Pegasus)
- Deploy the model with Docker + AWS + GitHub Actions
- Set up a user interface for predictions

## Project Structure
```plaintext
Text-Summarizer/
├── .github/workflows/        # CI/CD pipeline configuration using GitHub Actions
├── config/                   # YAML configuration files (paths, parameters)
├── logs/                     # Custom logging output with timestamps and log levels
├── research/                 # Jupyter notebooks for experimentation and prototyping
├── src/textSummarizer/       # Core source code package
│   ├── components/           # Pipeline components: ingestion, validation, training, evaluation
│   ├── config/               # Configuration management 
│   ├── constants.py          # Project-wide constant definitions
│   ├── pipeline/             # Orchestrator scripts to run each pipeline stage
│   └── utils/                # Utility functions (file handling, logging, exceptions)
├── app.py                    # Optional FastAPI for prediction
├── Dockerfile                # Docker configuration for containerized deployment
├── main.py                   # Main entry point to run the full pipeline
├── requirements.txt          # Python dependencies for the project
├── setup.py                  # Setup script for packaging the module
└── README.md                 
```
## Main Components: 
Data Ingestion: Downloads and extracts datasets from a URL.

Data Validation: Checks for required files and validates file structure.

Data Transformation: Tokenizes and prepares datasets for training.

Model Training: Fine-tunes Pegasus model using Hugging Face Trainer.

Model Evaluation: Computes ROUGE scores and saves metrics to CSV.

FastAPI app: To launch a UI for testing the summarization model.

Deployment: Docker + GitHub Actions + AWS EC2.
1. Create `Dockerfile` with all required environment setup.
2. Add `.github/workflows/main.yaml`.
- On `push`, GitHub builds Docker image, pushes to ECR, and deploys to EC2.
- Uses GitHub Secrets for AWS credentials.
3. Build Docker image locally or via GitHub Actions.
- Push image to AWS ECR.
- Launch EC2 instance, pull image, and run it using `docker run`.

## Deployment with Docker

# Build the image
docker build -t text-summarizer .

# Run the container
docker run -p 8080:8080 text-summarizer


