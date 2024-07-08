# Use the official Python image with Alpine Linux
FROM python:3.10-alpine

# Set environment variables to avoid interaction during poetry install
ENV POETRY_VERSION=1.7.0

# Install Poetry using the new installation script
RUN apk add --no-cache curl && \
    curl -sSL https://install.python-poetry.org | python3 -

# Add Poetry to PATH
ENV PATH="/root/.local/bin:${PATH}"

# Set the working directory inside the Docker image
WORKDIR /app

# Copy pyproject.toml and poetry.lock to the working directory
COPY pyproject.toml poetry.lock ./

# Install dependencies
RUN pip install --no-cache-dir poetry && \
    poetry config virtualenvs.create false && \
    poetry install --no-root --no-dev

# Copy the rest of the application code to the working directory
COPY . .

# Expose port 80
EXPOSE 80

# Set the command to run the FastAPI app
CMD ["poetry", "run", "uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "80"]



