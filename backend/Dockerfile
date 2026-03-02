# backend/Dockerfile
FROM python:3.11-slim

WORKDIR /app

# 1) Copy requirements.txt and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 2) Copy all backend files
COPY . .

# 3) Train the model at build time
RUN python model/train.py

# 4) Expose port 8000
EXPOSE 8000

# 5) Launch the API with uvicorn
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]