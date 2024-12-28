# Base image for Python
FROM python:3.11

# Set working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    ffmpeg \
    && apt-get clean

# Copy requirements and install Python dependencies
COPY ./backend/requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Install openai-whisper
RUN pip install --no-cache-dir openai-whisper

# Copy project files
COPY ./backend/ /app/

# Set PYTHONPATH
ENV PYTHONPATH=/app

# Start Celery worker
CMD ["celery", "-A", "my_project", "worker", "--loglevel=info"]
