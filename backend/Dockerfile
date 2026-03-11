FROM python:3.14-slim


# WORKDIR /code


# COPY ./requirements.txt /code/requirements.txt

# Set the working directory in the container
WORKDIR /app
# RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt
# Copy the requirements file into the container and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# The container will listen on port 8000 for incoming connections
EXPOSE 8000

# CMD ["fastapi", "run", "main.py", "--host", "0.0.0.0", "--port", "80"]
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]