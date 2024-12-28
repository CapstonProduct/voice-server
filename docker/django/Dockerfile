# Base image for Python
FROM python:3.11

# Set working directory
WORKDIR /app

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    && apt-get clean

# Copy requirements and install Python dependencies
COPY ./backend/requirements.txt /app/
RUN pip install --no-cache-dir -r requirements.txt

# Copy project files
COPY ./backend/ /app/

# Set PYTHONPATH
ENV PYTHONPATH=/app

# Expose Django's default port
EXPOSE 8000

# Start Django server
CMD ["gunicorn", "-b", "0.0.0.0:8000", "my_project.wsgi:application"]
