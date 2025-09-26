# api/Dockerfile

# Use an official Python runtime as a parent image
FROM python:3.13-slim-bullseye AS builder

# Set the working directory in the container
WORKDIR /app

# Install dependencies needed for building some python packages (e.g., psycopg2, numpy)
# Although your current requirements.txt may not need them, this is a robust practice.
RUN apt-get update && apt-get install -y --no-install-recommends gcc build-essential

# Create a virtual environment to isolate dependencies
RUN python -m venv /opt/venv

# Activate the virtual environment
ENV PATH="/opt/venv/bin:$PATH"

# Copy the requirements file first to leverage Docker cache
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# ---- Stage 2: Final Image ----
# This stage creates the final, lightweight image.
FROM python:3.13-slim-bullseye

# Set the working directory
WORKDIR /app

# Create a non-root user and group
RUN groupadd -r appgroup && useradd --no-log-init -r -g appgroup appuser

# Copy the virtual environment from the builder stage
COPY --from=builder /opt/venv /opt/venv

# Copy the rest of the backend application code
COPY . .

# Change ownership of the app directory to the new user
RUN chown -R appuser:appgroup /app

# Switch to the non-root user
USER appuser

# Make the virtual environment's binaries accessible
ENV PATH="/opt/venv/bin:$PATH"

# Make port 5000 available to the world outside this container
EXPOSE 5000

# Define the command to run the app using Gunicorn
CMD ["gunicorn", "--workers", "3", "--bind", "0.0.0.0:5000", "apiServer:app"]
