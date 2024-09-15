# Use a base image - This sets up the container with Python 3.10 installed.
FROM python:3.10-slim

# This copies everything in your current directory to the /app directory in the container.
WORKDIR /app

# Copy the requirements file to the working directory
COPY Sampleapp/requirements.txt .

# Install the dependencies
RUN pip install -r requirements.txt

# Copy the application code to the working directory
COPY Sampleapp/app.py .

# Expose the port that the app will run on
EXPOSE 8000

# This command creates a .streamlit directory in the home directory of the container.
RUN mkdir ~/.streamlit

# This sets the default command for the container to run the app with Streamlit.
ENTRYPOINT ["streamlit", "run"]

# Health check to verify that the container is running correctly
HEALTHCHECK CMD curl --fail http://localhost:8000/ || exit 1

# Define the default command to run the application
CMD ["python", "app.py"]
