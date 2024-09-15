# Use a base image - This sets up the container with Python 3.10 installed.
FROM python:3.10-slim

# This sets the working directory inside the container
WORKDIR /app

# Copy the requirements file to the working directory
COPY Sampleapp/requirements.txt .

# Install the dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code to the working directory
COPY Sampleapp/app.py .

# Expose the port that the app will run on
EXPOSE 8000

# Create a .streamlit directory if needed
RUN mkdir ~/.streamlit

# Set the default command for the container to run the app with Streamlit
ENTRYPOINT ["streamlit", "run", "app.py"]

# Health check to verify that the container is running correctly
HEALTHCHECK CMD curl --fail http://localhost:8000/ || exit 1
